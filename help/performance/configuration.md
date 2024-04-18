---
title: 配置最佳实践
description: 使用这些最佳实践优化Adobe Commerce部署的响应时间。
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 0%

---

# 配置最佳实践

Commerce提供了许多设置和工具，可用于改善页面上的响应时间并提供更高的吞吐量。

## Cron作业

中的所有异步操作 [!DNL Commerce] 使用Linux `cron` 命令。 请参阅 [配置和运行cron](../configuration/cli/configure-cron-jobs.md) 以正确配置它。

## 索引器

索引器可以在以下任一位置运行： **[!UICONTROL Update on Save]** 或 **[!UICONTROL Update on Schedule]** 模式。 此 **[!UICONTROL Update on Save]** 模式在目录或其他数据发生更改时立即进行索引。 此模式假定存储中的更新和浏览操作强度较低。 它可能会导致高负载期间出现严重延迟和数据不可用。 我们建议使用 **按计划更新** 出于性能考虑，因为它存储有关数据更新的信息，并通过特定的cron作业在后台按部分执行索引。 您可以更改每个项目的模式 [!DNL Commerce] 索引器单独在  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** 配置页面。 此 [!UICONTROL Customer Grid] 索引必须始终设置为 **[!UICONTROL Update on Save]** 模式。

>[!TIP]
>
>对MariaDB 10.4和10.6重新编制索引所花的时间比其他MariaDB或 [!DNL MySQL] 版本。 我们建议修改默认MariaDB配置设置，具体说明请参见 [安装先决条件](../installation/prerequisites/database/mysql.md).

## 缓存

在生产环境中启动应用商店时，请激活以下位置的所有缓存： **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** 页面。 我们强烈建议使用 [!DNL Varnish]，因为这是一个高效的生产页面缓存解决方案。

## 异步电子邮件通知

启用“异步电子邮件通知”设置会将处理结账和订单处理电子邮件通知的流程移至后台。 要启用此功能，请转到 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. 请参阅 [销售电子邮件](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) 在 _管理员用户指南_ 以了解更多信息。

## 异步订单数据处理

有时候，店面在进行密集销售的同时，也会出现这种情况 [!DNL Commerce] 正在执行密集订单处理。 您可以配置 [!DNL Commerce] 在数据库级别区分这两种通信模式，避免相应表中的读写操作发生冲突。 您可以异步存储和索引订单数据。 订单将置于临时存储中，并在没有任何冲突的情况下批量移至“订单管理”网格。 您可以从以下位置激活此选项 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. 请参阅 [计划的网格更新](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) 在 _管理员用户指南_ 以了解更多信息。

>[!WARNING]
>
>此 **[!UICONTROL Developer]** 选项卡和选项仅在 [开发人员模式](../configuration/cli/set-mode.md). [云基础架构上的Adobe Commerce](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) 不支持 `Developer` 模式。

## 异步配置保存

对于具有大量存储级别配置的项目，保存存储配置可能需要花费过多的时间或导致超时。 此 _异步配置_ 模块通过运行cron作业来启用异步配置保存，该作业使用使用者处理消息队列中的保存。 AsyncConfig **已禁用** 默认情况下。

可以使用命令行界面启用AsyncConfig：

```bash
bin/magento setup:config:set --config-async 1
```

此 `set` 命令将以下内容写入 `app/etc/env.php` 文件：

```conf
...
   'config' => [
       'async' => 1
   ]
```

启动以下使用者，以开始按先进先出原则处理队列中的消息：

```bash
bin/magento queue:consumers:start saveConfigProcessor --max-messages=1
```

## 延期库存更新

在销售密集时期， [!DNL Commerce] 可以延迟与订单相关的库存更新。 这样可最大限度地减少操作次数，并加快下单流程。 但是，此选项有风险，并且只能在商店中激活延交订单时使用，因为此选项可能导致存货数量为负。 对于可轻松按需重新补充库存的商店，此选项可显着提升结账流的性能。 要在您的网站上激活延期库存更新，请转到 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. 请参阅 [管理库存](https://docs.magento.com/user-guide/catalog/inventory.html) 在 _Adobe Commerce用户指南_ 以了解更多信息。

>[!INFO]
>
>此选项仅在以下情况下可用 **[!UICONTROL Backorder with any mode]** 已激活。

>[!INFO]
>
>此选项也适用于 [异步下单](high-throughput-order-processing.md#asynchronous-order-placement) 与 [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html).

## 客户端优化设置

提高您的店面响应能力 [!DNL Commerce] 在实例中，以默认或开发人员模式转到“管理员”，然后更改以下设置：

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]：**

| 设置组 | 设置 | 值 |
| ------------------- | -------------------------- | ------ |
| 网格设置 | 异步索引 | 启用 |
| CSS设置 | 缩小CSS文件 | 是 |
| [!DNL JavaScript] 设置 | Minify [!DNL JavaScript] 文件 | 是 |
| [!DNL JavaScript] 设置 | 启用 [!DNL JavaScript] 捆绑 | 是 |
| 模板设置 | 缩小HTML | 是 |

>[!INFO]
>
>此 **[!UICONTROL Developer]** 选项卡和选项仅在 [开发人员模式](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] 在云基础架构上](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) 不支持 `Developer` 模式。

当您激活 **[!UICONTROL Enable [!DNL JavaScript] Bundling]** 选项，您允许Commerce将所有JS资源合并到一个或一组在店面页面中加载的捆绑包中。 捆绑JS可减少向服务器发出的请求，从而改善页面性能。 它还有助于浏览器在首次调用时缓存JS资源，并在所有进一步浏览中重复使用它们。 此选项还会带来延迟评估，因为所有JS都作为文本加载。 它仅在页面上触发特定操作后才启动代码分析和评估。 但是，对于首次页面加载时间极其关键的存储区，不建议使用此设置，因为所有JS内容都将在首次调用时加载。

>[!INFO]
>
>请参阅 [云基础架构和Adobe Commerce上的Adobe Commerce上的CSS和Javascript文件优化](https://support.magento.com/hc/en-us/articles/360044482152) Adobe Commerce ，以了解有关优化CSS和Javascript的更多信息。

### 捆绑提示

* 我们建议您使用第三方工具进行缩小和捆绑(例如 [r.js](https://requirejs.org/))。 [!DNL Commerce] 内置机制并非最佳方案，而是作为备用方案提供。
* 激活HTTP/2协议可能是使用JS捆绑包的良好替代方法。 该协议提供了许多相同的好处。 默认情况下，在云基础架构项目上的Adobe Commerce中会启用此功能。
* 我们不建议使用已弃用的设置，例如合并JS和CSS文件，因为它们仅为页面的HEAD部分中的同步加载JS而设计。 使用此技术可能会导致捆绑销售，并要求JS逻辑无法正常工作。

## 客户区段验证

商户拥有大量的 [客户区段](https://docs.magento.com/user-guide/marketing/customer-segments.html) 客户操作（如客户登录和将产品添加到购物车）可能会导致性能显着下降。

客户操作会触发客户区段的验证过程，这可能导致性能下降。 默认情况下，Adobe Commerce会实时验证每个区段，以定义哪些客户区段匹配，哪些客户区段不匹配。

为避免性能下降，您可以设置 **[!UICONTROL Real-time Check if Customer is Matched by Segment]** 系统配置选项 **否** 通过单个组合条件SQL查询验证客户区段。

要启用此优化，请转到 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

如果系统中有许多客户区段，则此设置可提高客户区段验证的性能。 但是，它不适用于 [拆分数据库](../configuration/storage/multi-master.md) 实施或没有注册客户时。

## 数据库维护计划 {#database}

我们建议为暂存实例和生产实例执行定期数据库备份。 由于备份操作的I/O密集性质，您可能会遇到备份速度较慢和潜在问题。 同时为多个环境运行数据库进程可能会由于可用资源争用而降低运行速度。

为了获得更好的性能，请安排您的备份在离峰时间连续运行，一次运行一个。 此方法可避免I/O争用，并缩短完成时间，尤其是对于较小的实例、较大的数据库等。

例如，当您的商店访问次数较少时，我们建议先计划生产数据库的备份，然后再计划暂存数据库。

## 限制网格中的产品数

为了提高大型目录的产品网格性能，我们建议使用限制网格中的产品数量 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]** 系统配置设置。

默认情况下，此系统配置设置处于禁用状态。 启用此选项后，您可以将网格中的产品数量限制为特定值。 **[!UICONTROL Records Limit]** 是可自定义的设置，其默认最小值为 `20000`.
当 **[!UICONTROL Limit Number of Products in Grid]** 如果启用了设置并且网格中的产品数大于记录限制，则会返回有限制的记录集合。 当达到限制时，将在网格标题中隐藏找到的记录总数、选定的记录数和分页元素。

当网格中的产品总数有限时，它不会影响产品网格中的批量操作。 它只影响产品网格表示层。 例如，有限数量的 `20000` 产品时，用户单击 **[!UICONTROL Select All]**，选择 **[!UICONTROL Update attributes]** 批量操作，并更新某些属性。 因此，所有产品都会更新，而不是有限的集合 `20000` 记录。

产品网格限制仅影响UI组件使用的产品集合。 因此，并非所有产品网格都受此限制的影响。 仅使用 `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`.
您只能在以下页面上限制产品网格集合：

* 目录产品网格
* 添加相关/向上销售/交叉销售产品网格
* 将产品添加到捆绑产品
* 将产品添加到组产品
* 管理员创建订单页面

如果您不希望限制产品网格，我们建议您更准确地使用过滤器，以使结果集合的项目数量少于 **[!UICONTROL Records Limit]**.
