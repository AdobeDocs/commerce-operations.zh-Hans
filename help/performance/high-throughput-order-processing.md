---
title: 签出性能最佳实践
description: 了解如何优化Adobe Commerce网站上的签出体验的性能。
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '1121'
ht-degree: 0%

---


# 签出性能最佳实践

Adobe Commerce中的[结帐](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process)流程是店面体验的关键方面。 它依赖于内置[购物车](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/start/storefront/storefront#shopping-cart)和[结帐](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/start/storefront/storefront#checkout-page)功能。

性能是保持良好用户体验的关键。 您可以通过为&#x200B;**高吞吐量订单处理**&#x200B;配置以下选项来优化签出性能：

- [AsyncOrder](#asynchronous-order-placement) — 使用队列异步处理订单。
- [延迟总计计算](#deferred-total-calculation) — 延迟订单总计计算，直到结帐开始。
- [购物车加载时的库存检查](#disable-inventory-check) — 选择跳过购物车项目的库存验证。
- [负载平衡](#load-balancing) — 为MySQL数据库和Redis实例启用辅助连接。

AsyncOrder、Deferred Total Calculation和Inventory Check on Cart Load配置选项均可独立工作。 您可以同时使用全部三个功能，也可以任意组合启用和禁用这些功能。

>[!NOTE]
>
>请勿使用自定义PHP代码来自定义内置购物车和签出功能。 除了潜在的性能问题之外，使用自定义PHP代码可能会导致复杂的升级和维护挑战。 这些问题会增加您的总拥有成本。 如果基于PHP的购物车和结账自定义无法避免，则仅使用[Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/)批准的扩展。 所有Marketplace扩展都需要[全面审查](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/)，以验证它们是否符合Adobe Commerce编码标准和最佳实践。

## 异步下单

_异步订单_&#x200B;模块启用异步订单下达，该功能将订单标记为`received`，将订单放入队列中，并以先进先出原则处理来自队列的订单。 AsyncOrder默认为&#x200B;**已禁用**。

例如，客户将产品添加到购物车并选择&#x200B;**[!UICONTROL Proceed to Checkout]**。 他们填写&#x200B;**[!UICONTROL Shipping Address]**&#x200B;表单，选择他们首选的&#x200B;**[!UICONTROL Shipping Method]**，选择付款方式，然后下订单。 购物车已清空，订单标记为&#x200B;**[!UICONTROL Received]**，但产品数量尚未调整，也不会向客户发送销售电子邮件。 已收到订单，但订单详细信息尚不可用，因为尚未完全处理该订单。 它将保留在队列中，直到`placeOrderProcess`使用者开始，使用[库存检查](#disable-inventory-check)功能验证订单（默认启用），并按如下方式更新订单：

- **可用产品** — 订单状态更改为&#x200B;_待定_，产品数量已调整，已向客户发送一封包含订单详细信息的电子邮件，并且成功的订单详细信息可在&#x200B;**订单和退货**&#x200B;列表中查看，并带有可操作选项，例如重新订购。
- **产品缺货或供应不足** — 订单状态更改为&#x200B;_已拒绝_，未调整产品数量，已向客户发送一封包含有关问题的订单详细信息的电子邮件，并且已拒绝的订单详细信息将在&#x200B;**订单和退货**&#x200B;列表中可用，且没有可操作选项。

使用命令行界面启用这些功能，或根据&#x200B;[_模块参考指南_](https://developer.adobe.com/commerce/php/module-reference/)中定义的相应README文件编辑`app/etc/env.php`文件。

**启用AsyncOrder**：

可使用命令行界面启用AsyncOrder：

```bash
bin/magento setup:config:set --checkout-async 1
```

`set`命令将以下内容写入`app/etc/env.php`文件：

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

请参阅&#x200B;_模块参考指南_&#x200B;中的[异步订单](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)。

**禁用AsyncOrder**：

>[!WARNING]
>
>在禁用AsyncOrder模块之前，必须验证&#x200B;_所有_&#x200B;异步订单流程是否已完成。

您可以使用命令行界面禁用AsyncOrder：

```bash
bin/magento setup:config:set --checkout-async 0
```

`set`命令将以下内容写入`app/etc/env.php`文件：

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
| 签出类型 | OnePage Checkout<br>标准签出<br>B2B可转让报价 |
| 支付方式 | 支票/汇票<br>货到付款<br>Braintree<br>PayPal PayFlow Pro |
| 配送方式 | 支持所有配送方式。 |

以下功能&#x200B;**不受AsyncOrder支持**，但可以继续同步工作：

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

开发人员可以通过将某些付款方法添加到`Magento\AsyncOrder\Model\OrderManagement::paymentMethods`数组，将其从异步下单中明确排除。 使用排除的支付方法的订单将同步处理。

### 可协商的报价异步订单

_可转让报价异步订单_ B2B模块允许您异步保存`NegotiableQuote`功能的订单项目。 您必须启用AsyncOrder和NegotiableQuote。

## 延迟总计计算

_延迟总计计算_&#x200B;模块通过将总计计算延迟到购物车请求时或在最终结帐步骤期间来优化结帐过程。 启用后，只有小计会在客户将产品添加到购物车时进行计算。

延迟总计计算默认为&#x200B;**禁用**。 使用命令行界面启用这些功能，或根据&#x200B;[_模块参考指南_](https://developer.adobe.com/commerce/php/module-reference/)中定义的相应README文件编辑`app/etc/env.php`文件。

**启用DeferredTotalCalculation**：

您可以使用命令行界面启用DeferredTotalCalculation：

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

`set`命令将以下内容写入`app/etc/env.php`文件：

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

`set`命令将以下内容写入`app/etc/env.php`文件：

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

请参阅&#x200B;_模块参考指南_&#x200B;中的[DeferredTotalCalculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/)。

### 固定产品税

启用递延总计计算后，将产品添加到购物车后，固定产品税(FPT)不会包含在迷你购物车的产品价格和购物车小计中。 将产品添加到迷你购物车时，会延迟FPT计算。 继续进行最终结帐后，FPT在购物车中正确显示。

## 禁用清单检查

_在购物车加载时启用库存_&#x200B;全局设置确定在购物车中加载产品时是否执行库存检查。 禁用库存检查流程可提高所有检查步骤的性能，在处理购物车中的批量产品时尤其如此。

禁用后，将产品添加到购物车时不会进行库存检查。 如果跳过此库存检查，则某些缺货方案可能会引发其他类型的错误。 库存检查&#x200B;_始终_&#x200B;发生在订单下达步骤，即使已禁用也是如此。

**默认情况下启用“购物车加载时启用库存检查”**（设置为“是”）。 要在加载购物车时禁用库存检查，请在管理员UI **商店** > **配置** > **目录** > **库存** > **库存选项**&#x200B;分区中将&#x200B;**[!UICONTROL Enable Inventory Check On Cart Load]**&#x200B;设置为`No`。 请参阅&#x200B;_用户指南_&#x200B;中的[配置全局选项](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/inventory/configuration/global-options)和[目录清单](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/inventory/guide-overview)。

## 负载平衡

通过为MySQL数据库和Redis实例启用辅助连接，您可以帮助平衡不同节点的负载。

Adobe Commerce可以异步读取多个数据库或Redis实例。 如果在云基础架构上使用Commerce，则可通过编辑`.magento.env.yaml`文件中的[MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection)和[REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection)值来配置辅助连接。 只有一个节点需要处理读写通信，因此将变量设置为`true`会导致为只读通信创建辅助连接。 将值设置为`false`以从`env.php`文件中删除任何现有的只读连接数组。

`.magento.env.yaml`文件示例：

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
