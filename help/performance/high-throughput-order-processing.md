---
title: 签出性能最佳实践
description: 了解如何优化Adobe Commerce网站上的签出体验的性能。
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: e4c1832076bb81cd3e70ff279a6921ffb29ea631
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---


# 签出性能最佳实践

此 [结账](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) Adobe Commerce中的流程是店面体验的关键方面。 它依赖于内置的 [购物车](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart) 和 [结账](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page) 功能。

性能是保持良好用户体验的关键。 查看 [性能基准摘要](../implementation-playbook/infrastructure/performance/benchmarks.md) 了解更多有关性能期望的信息。 您可以通过为配置以下选项来优化签出性能 **高吞吐量订单处理**：

- [AsyncOrder](#asynchronous-order-placement) — 使用队列异步处理订单。
- [延迟总计计算](#deferred-total-calculation) — 在结账之前延迟订单总额的计算。
- [购物车加载时的库存检查](#disable-inventory-check) — 选择以跳过购物车项目的库存验证。
- [负载平衡](#load-balancing) — 为MySQL数据库和Redis实例启用辅助连接。

AsyncOrder、Deferred Total Calculation和Inventory Check on Cart Load配置选项均可独立工作。 您可以同时使用全部三个功能，也可以任意组合启用和禁用这些功能。

>[!NOTE]
>
>请勿使用自定义PHP代码来自定义内置购物车和签出功能。 除了潜在的性能问题之外，使用自定义PHP代码可能会导致复杂的升级和维护挑战。 这些问题会增加您的总拥有成本。 如果基于PHP的购物车和结账定制无法避免，请使用 [Adobe Commerce市场](https://commercemarketplace.adobe.com/)仅批准扩展。 所有Marketplace扩展都受 [广泛审查](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/) 验证它们是否符合Adobe Commerce编码标准和最佳实践。

## 异步下单

此 _异步订单_ 模块启用异步订单放置，这会将订单标记为 `received`，将订单放入队列中，并按照先进先出原则处理队列中的订单。 异步顺序为 **已禁用** 默认情况下。

例如，客户将产品添加到其购物车并选择 **[!UICONTROL Proceed to Checkout]**. 他们填写 **[!UICONTROL Shipping Address]** 表单，选择其首选的 **[!UICONTROL Shipping Method]**，选择支付方式并下单。 购物车已清除，订单标记为 **[!UICONTROL Received]**，但尚未调整产品数量，也不会向客户发送销售电子邮件。 已收到订单，但订单详细信息尚不可用，因为尚未完全处理该订单。 它将保留在队列中，直到 `placeOrderProcess` 消费者开始，验证订单 [库存检查](#disable-inventory-check) 功能（默认启用），并按如下方式更新顺序：

- **可用的产品** — 订单状态更改为 _待处理_，调整产品数量，向客户发送一封包含订单详细信息的电子邮件，并在以下位置查看成功的订单详细信息： **订单和退货** 列出可操作选项，例如重新排序。
- **产品缺货或供应不足** — 订单状态更改为 _被拒绝_，不调整产品数量，向客户发送一封包含有关问题的订单详细信息的电子邮件，并且被拒绝的订单详细信息可在 **订单和退货** 列表没有可操作选项。

使用命令行界面启用这些功能，或者编辑 `app/etc/env.php` 文件根据中定义的相应自述文件 [_模块参考指南_](https://developer.adobe.com/commerce/php/module-reference/).

**启用AsyncOrder**：

可使用命令行界面启用AsyncOrder：

```bash
bin/magento setup:config:set --checkout-async 1
```

此 `set` 命令将以下内容写入 `app/etc/env.php` 文件：

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

请参阅 [AsyncOrder](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) 在 _模块参考指南_.

**禁用AsyncOrder**：

>[!WARNING]
>
>在禁用AsyncOrder模块之前，必须验证 _所有_ 异步订购流程已完成。

您可以使用命令行界面禁用AsyncOrder：

```bash
bin/magento setup:config:set --checkout-async 0
```

此 `set` 命令将以下内容写入 `app/etc/env.php` 文件：

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### AsyncOrder兼容性

AsyncOrder支持有限的Adobe Commerce功能集。

| 类别 | 支持的功能 |
|------------------|--------------------------------------------------------------------------|
| 签出类型 | OnePage签出<br>标准签出<br>B2B可协商报价 |
| 支付方式 | 支票/汇票<br>货到付款<br>Braintree<br>PayPal PayFlow Pro |
| 配送方式 | 支持所有配送方式。 |

以下功能为 **非** 受AsyncOrder支持，但可继续同步工作：

- 支持的功能列表中未包含支付方式
- 多地址签出
- 管理订单创建

#### Web API支持

启用AsyncOrder模块后，将异步运行以下REST端点和GraphQL突变：

**REST：**

- [`POST /V1/carts/mine/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/cartsminepayment-information#operation/PostV1CartsMinePaymentinformation)
- [`POST /V1/guest-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/guest-cartscartIdpayment-information#operation/PostV1GuestcartsCartIdPaymentinformation)
- [`POST /V1/negotiable-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/negotiable-cartscartIdpayment-information#operation/PostV1NegotiablecartsCartIdPaymentinformation)

**GraphQL：**

- [`placeOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/)
- [`setPaymentMethodAndPlaceOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/set-payment-place-order/)

>[!INFO]
>
>GraphQL不支持异步下可转让报价单。

#### 不包括支付方式

开发人员可以通过将某些支付方法添加到 `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` 数组。 使用排除的支付方法的订单将同步处理。

### 可协商的报价异步订单

此 _可协商的报价异步订单_ 通过B2B模块，您可以异步保存订单项目用于 `NegotiableQuote` 功能。 您必须启用AsyncOrder和NegotiableQuote。

## 延迟总计计算

此 _延迟总计计算_ 模块通过将总计算延迟到对购物车发出请求或在最终结账步骤期间来优化结账过程。 启用后，只有小计会在客户将产品添加到购物车时进行计算。

递延总计计算为 **已禁用** 默认情况下。 使用命令行界面启用这些功能，或者编辑 `app/etc/env.php` 文件根据中定义的相应自述文件 [_模块参考指南_](https://developer.adobe.com/commerce/php/module-reference/).

**启用DeferredTotalCalculation**：

您可以使用命令行界面启用DeferredTotalCalculation：

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

此 `set` 命令将以下内容写入 `app/etc/env.php` 文件：

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**禁用DeferredTotalCalculation**：

您可以使用命令行界面禁用DeferredTotalCalculation：

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

此 `set` 命令将以下内容写入 `app/etc/env.php` 文件：

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

请参阅 [DeferredTotalCalculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/) 在 _模块参考指南_.

### 固定产品税

启用递延总计计算后，将产品添加到购物车后，固定产品税(FPT)不会包含在迷你购物车的产品价格和购物车小计中。 将产品添加到迷你购物车时，会延迟FPT计算。 继续进行最终结帐后，FPT在购物车中正确显示。

## 禁用清单检查

此 _在购物车加载时启用库存_ 全局设置确定在购物车中加载产品时是否执行库存检查。 禁用库存检查流程可提高所有检查步骤的性能，在处理购物车中的批量产品时尤其如此。

禁用后，将产品添加到购物车时不会进行库存检查。 如果跳过此库存检查，则某些缺货方案可能会引发其他类型的错误。 库存检查 _始终_ 在订购步骤中发生，即使处于禁用状态也是如此。

**在购物车加载时启用库存检查** 默认启用（设置为“是”）。 要在加载购物车时禁用库存检查，请设置 **[!UICONTROL Enable Inventory Check On Cart Load]** 到 `No` 在Admin UI中 **商店** > **配置** > **目录** > **库存** > **股票期权** 部分。 请参阅 [配置全局选项](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options) 和 [目录清单](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) 在 _用户指南_.

## 负载平衡

通过为MySQL数据库和Redis实例启用辅助连接，您可以帮助平衡不同节点的负载。

Adobe Commerce可以异步读取多个数据库或Redis实例。 如果您在云基础架构上使用Commerce，则可以通过编辑 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) 和 [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) 中的值 `.magento.env.yaml` 文件。 只有一个节点需要处理读写通信，因此将变量设置为 `true` 会导致为只读流量创建辅助连接。 将值设置为 `false` 要从 `env.php` 文件。

示例 `.magento.env.yaml` 文件：

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
