---
title: 高吞吐量订单处理
description: 为您的Adobe Commerce或Magento Open Source部署优化订单投放和结账体验。
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1048'
ht-degree: 0%

---

# 高吞吐量订单处理

您可以通过为配置以下模块集来优化订单投放和结账体验 **高吞吐量订单处理**：

- [AsyncOrder](#asynchronous-order-placement) — 使用队列异步处理订单。
- [延迟总计计算](#deferred-total-calculation) — 在结帐开始之前，延迟订单总额的计算。
- [报价加载时的库存检查](#disable-inventory-check) — 选择以跳过购物车项目的库存验证。

所有特征（“异步订购”、“延迟的总计计算”和“库存检查”）均独立工作。 您可以同时使用全部三个功能，也可以任意组合启用和禁用功能。

## 异步下单

此 _异步订单_ 模块启用异步订单放置，这会将订单标记为 `received`，将订单放入队列中，并按照先进先出原则处理队列中的订单。 AsyncOrder **已禁用** 默认情况下。

例如，客户将产品添加到其购物车并选择 **[!UICONTROL Proceed to Checkout]**. 他们填写 **[!UICONTROL Shipping Address]** 表单，选择其首选的 **[!UICONTROL Shipping Method]**，选择支付方式，然后下订单。 购物车已清除，订单标记为 **[!UICONTROL Received]**，但产品数量尚未调整，也不会向客户发送销售电子邮件。 已收到订单，但订单详细信息尚不可用，因为订单尚未完全处理。 它会一直保留在队列中，直到 `placeOrderProcess` 消费者开始，验证订单 [库存检查](#disable-inventory-check) 功能（默认启用），并按如下方式更新顺序：

- **可用的产品** — 订单状态更改为 _待处理_，调整产品数量，向客户发送一封包含订单详细信息的电子邮件，然后便可以在中查看成功的订单详细信息 **订单和退货** 列表包含可操作选项，例如重新排序。
- **产品缺货或供应不足** — 订单状态更改为 _已拒绝_，不调整产品数量，向客户发送一封包含有关问题的订单详细信息的电子邮件，并且被拒绝的订单详细信息可在 **订单和退货** 列表没有可操作选项。

使用命令行界面启用这些功能，或编辑 `app/etc/env.php` 文件，该文件与中定义的相应README文件 [_模块参考指南_][mrg].

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

参见 [AsyncOrder] 在 _模块参考指南_.

**禁用AsyncOrder**：

>[!WARNING]
>
>在禁用AsyncOrder模块之前，必须验证 _所有_ 异步订购过程完成。

可以使用命令行界面禁用AsyncOrder：

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

AsyncOrder支持有限的 [!DNL Commerce] 功能。

| 类别 | 支持的功能 |
|------------------|--------------------------------------------------------------------------|
| 结帐类型 | OnePage结账<br>标准结帐<br>B2B可协商报价 |
| 支付方式 | 支票/汇票<br>货到付款<br>Braintree<br>PayPal PayFlow Pro |
| 配送方式 | 支持所有配送方式。 |

以下功能包括 **非** 受AsyncOrder支持，但可继续同步工作：

- 支付方式未包含在支持的功能列表中
- 多地址签出
- 管理订单创建

#### Web API支持

启用AsyncOrder模块后，以下REST端点和GraphQL突变将异步运行：

**REST：**

- `POST /V1/carts/mine/payment-information`
- `POST /V1/guest-carts/:cartId/payment-information`
- `POST /V1/negotiable-carts/:cartId/payment-information`

**GraphQL：**

- [`placeOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/place-order.html)
- [`setPaymentMethodAndPlaceOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/set-payment-place-order.html)

>[!INFO]
>
>GraphQL不支持异步下可转让报价单。

#### 不包括支付方式

开发人员可以通过将某些支付方法添加到，明确将其从异步下单中排除。 `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` 数组。 使用排除的支付方法的订单将同步处理。

### 可转让报价异步订单

此 _可转让报价异步订单_ 通过B2B模块，您可以异步保存订单项目 `NegotiableQuote` 功能。 您必须启用AsyncOrder和NegotiableQuote。

## 延迟总计计算

此 _延迟总计计算_ 模块通过将总计算推迟到对购物车发出请求或在最终结帐步骤期间来优化结帐过程。 启用后，只有小计会在客户将产品添加到购物车时进行计算。

DeferredTotalCalculation为 **已禁用** 默认情况下。 使用命令行界面启用这些功能，或编辑 `app/etc/env.php` 文件，该文件与中定义的相应README文件 [_模块参考指南_][mrg].

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

参见 [DeferredTotalComputing] 在 _模块参考指南_.

### 固定产品税

启用DeferredTotalCalculation后，将产品添加到购物车后，固定产品税(FPT)不会包含在迷你购物车的产品价格和购物车小计中。 向迷你购物车添加产品时，会延迟FPT计算。 继续进行最终结帐后，FPT在购物车中正确显示。

## 禁用库存检查

此 _在购物车加载时启用库存_ 全局设置确定在购物车中加载产品时是否执行库存检查。 禁用库存检查流程可提高所有检查步骤的性能，特别是在处理购物车中的批量产品时。

禁用后，将产品添加到购物车时不会进行库存检查。 如果跳过此库存检查，则某些缺货情况可能会引发其他类型的错误。 库存检查 _始终_ 在订单放置步骤中发生，即使处于禁用状态也是如此。

**在购物车加载时启用库存检查** 默认启用（设置为“是”）。 要在加载购物车时禁用库存检查，请设置 **[!UICONTROL Enable Inventory Check On Cart Load]** 到 `No` 在Admin UI中 **商店** > **配置** > **目录** > **库存** > **股票期权** 部分。 参见 [配置全局选项][global] 和 [目录库存][inventory] 在 _用户指南_.

## 负载平衡

您可以为MySQL数据库和Redis实例启用辅助连接，从而帮助平衡不同节点之间的负载。

Adobe Commerce可以异步读取多个数据库或Redis实例。 如果您在云基础架构上使用Commerce，则可以通过编辑 [MYSQL_USE_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#mysql_use_slave_connection) 和 [REDIS_USE_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_use_slave_connection) 中的值 `.magento.env.yaml` 文件。 只有一个节点需要处理读写通信，因此将变量设置为 `true` 会导致为只读流量创建辅助连接。 将值设置为 `false` 以从 `env.php` 文件。

示例 `.magento.env.yaml` 文件：

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

<!-- link definitions -->

[global]: https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/global-options.html
[inventory]: https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html
[mrg]: https://developer.adobe.com/commerce/php/module-reference/
[AsyncOrder]: https://developer.adobe.com/commerce/php/module-reference/module-async-order/
[DeferredTotalComputing]: https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/
