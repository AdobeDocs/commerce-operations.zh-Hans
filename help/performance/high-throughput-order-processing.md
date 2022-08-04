---
title: 高吞吐量订单处理
description: 为您的Adobe Commerce或Magento Open Source部署优化订单投放和结帐体验。
source-git-commit: 4ce6f01ab6c3e0bb408657727b65bcb2f84dd954
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 0%

---


# 高吞吐量订单处理

您可以通过为 **高吞吐量订单处理**:

- [AsyncOrder](#asynchronous-order-placement) — 使用队列异步处理订单。
- [延期总计算](#deferred-total-calculation) — 在结帐开始之前，默认计算订单总额。
- [报价加载时的库存检查](#disable-inventory-check) — 选择跳过购物车项目的库存验证。

所有功能（AsyncOrder、延期总计算和库存检查）均可独立工作。 您可以同时使用所有这三种功能，也可以在任意组合中启用或禁用这些功能。

## 异步订单放置

的 _异步订购_ 模块会启用异步订单放置，该操作会将订单标记为 `received`，将订单放入队列中，并按先入先出原则处理来自队列的订单。 AsyncOrder是 **已禁用** 默认情况下。

例如，客户将产品添加到其购物车并选择 **[!UICONTROL Proceed to Checkout]**. 他们填满 **[!UICONTROL Shipping Address]** 表单，选择首选 **[!UICONTROL Shipping Method]**，选择付款方式并下订单。 购物车清除，订单标记为 **[!UICONTROL Received]**，但尚未调整产品数量，也未向客户发送销售电子邮件。 已收到订单，但订单详细信息尚不可用，因为订单尚未完全处理。 它会一直保留在队列中，直到 `placeOrderProcess` 消费者开始，验证订单 [库存检查](#disable-inventory-check) 功能（默认启用），并按如下方式更新顺序：

- **可用产品** — 顺序状态更改为 _待定_，则会调整产品数量，向客户发送一封包含订单详细信息的电子邮件，并且成功的订单详细信息可在 **订单和退货** 列表，其中包含可操作选项，例如重新排序。
- **产品缺货或供应不足** — 顺序状态更改为 _被拒绝_，则不会调整产品数量，向客户发送一封包含问题订单详细信息的电子邮件，并且拒绝的订单详细信息将在 **订单和退货** 列表中没有可用选项。

使用命令行界面启用这些功能，或编辑 `app/etc/env.php` 文件，根据 [_模块参考指南_][mrg].

**启用AsyncOrder**:

您可以使用命令行界面启用AsyncOrder:

```bash
bin/magento setup:config:set --checkout-async 1
```

的 `set` 命令将以下内容写入 `app/etc/env.php` 文件：

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

请参阅 [AsyncOrder] 在 _模块参考指南_.

**禁用AsyncOrder**:

>[!WARNING]
>
>在禁用AsyncOrder模块之前，您必须验证 _全部_ 异步订单流程已完成。

您可以使用命令行界面禁用AsyncOrder:

```bash
bin/magento setup:config:set --checkout-async 0
```

的 `set` 命令将以下内容写入 `app/etc/env.php` 文件：

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### AsyncOrder兼容性

AsyncOrder支持一组有限的 [!DNL Commerce] 功能。

| 类别 | 支持的功能 |
|---------------- | -----------------------|
| 结帐类型 | OnePage结账<br>标准结账<br>B2B可转让报价 |
| 付款方法 | 支票/货币订单<br>交付现金<br>Braintree<br>PayPal PayFlow Pro |
| 装运方法 | 支持所有装运方法。 |

以下功能包括 **not** 受AsyncOrder支持，但可以继续同步工作：

- 支持的功能列表中未包含的付款方法
- 多地址结账
- 管理订单创建

#### Web API支持

启用AsyncOrder模块后，将异步运行以下REST端点和GraphQL突变：

**REST:**

- `POST /V1/carts/mine/payment-information`
- `POST /V1/guest-carts/:cartId/payment-information`
- `POST /V1/negotiable-carts/:cartId/payment-information`

**GraphQL:**

- [`placeOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/place-order.html)
- [`setPaymentMethodAndPlaceOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/set-payment-place-order.html)

>[!INFO]
>
>GraphQL不支持异步放置可转让报价单。

#### 排除付款方法

开发人员可以通过将某些付款方法添加到 `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` 数组。 使用排除的付款方法的订单将同步处理。

### 可转让报价异步订单

的 _可转让报价异步订单_ B2B模块允许您异步保存 `NegotiableQuote` 功能。 您必须启用AsyncOrder和PociateQuote。

## 延期总计算

的 _延期总计算_ 模块会通过延迟总计算来优化结帐流程，直到为购物车或在最终结帐步骤中请求总计计算为止。 启用后，当客户将产品添加到购物车时，只会计算小计。

DeferredTotalCalculation为 **已禁用** 默认情况下。 使用命令行界面启用这些功能，或编辑 `app/etc/env.php` 文件，根据 [_模块参考指南_][mrg].

**启用DeferredTotalCalculation**:

可以使用命令行界面启用DeferredTotalCalculation:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

的 `set` 命令将以下内容写入 `app/etc/env.php` 文件：

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**禁用DeferredTotalCalculation**:

可以使用命令行界面禁用DeferredTotalCalculation:

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

的 `set` 命令将以下内容写入 `app/etc/env.php` 文件：

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

请参阅 [DereverdTotalCalculating] 在 _模块参考指南_.

### 固定产品税

启用DeferredTotalCalculation后，将产品添加到购物车后，微型购物车的产品价格和购物车小计中不包含固定产品税(FPT)。 将产品添加到迷你购物车时，FPT计算会延期。 进入最终结帐后，FPT在购物车中正确显示。

## 禁用清单检查

的 _在购物车加载时启用库存_ 全局设置确定在购物车中加载产品时是否执行库存检查。 禁用库存检查流程可提高所有结帐步骤的性能，特别是在处理购物车中的批量产品时。

禁用后，在将产品添加到购物车时，不会进行库存检查。 如果跳过此库存检查，则某些缺货情景可能会引发其他类型的错误。 清单检查 _always_ 在订单放置步骤中发生，即使处于禁用状态也是如此。

**在购物车加载时启用库存检查** 默认启用（设置为“是”）。 要在加载购物车时禁用库存检查，请设置 **[!UICONTROL Enable Inventory Check On Cart Load]** to `No` 在管理员UI中 **商店** > **配置** > **目录** > **库存** > **股票期权** 中。 请参阅 [配置全局选项][global] 和 [目录库存][inventory] 在 _用户指南_.

<!-- link definitions -->

[Apply patches]: https://devdocs.magento.com/cloud/project/project-patch.html
[global]: https://docs.magento.com/user-guide/catalog/inventory-options-global.html
[inventory]: https://docs.magento.com/user-guide/configuration/catalog/inventory.html
[Install extensions]: https://devdocs.magento.com/extensions/install/
[cloud-extensions]: https://devdocs.magento.com/cloud/howtos/install-components.html

[mrg]: https://developer.adobe.com/commerce/php/module-reference/
[AsyncOrder]: https://devdocs.magento.com/guides/v2.4/mrg/module-async-order.html
[DereverdTotalCalculating]: https://devdocs.magento.com/guides/v2.4/mrg/module-deferred-total-calculating.html
[NegotiableQuoteAsyncOrder]: https://devdocs.magento.com/guides/v2.4/mrg/module-negotiable-quote-async-order.html
