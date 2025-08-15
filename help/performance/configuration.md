---
title: 配置最佳实践
description: 使用这些最佳实践优化Adobe Commerce部署的响应时间。
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 0%

---

# 配置最佳实践

Commerce提供了许多设置和工具，可用于改善页面上的响应时间并提供更高的吞吐量。

## Cron作业

使用Linux [!DNL Commerce]命令执行`cron`中的所有异步操作。 请参阅[配置和运行cron](../configuration/cli/configure-cron-jobs.md)以正确配置。

## 索引器

索引器可在&#x200B;**[!UICONTROL Update on Save]**&#x200B;或&#x200B;**[!UICONTROL Update on Schedule]**&#x200B;模式下运行。 当目录或其他数据发生更改时，**[!UICONTROL Update on Save]**&#x200B;模式会立即进行索引。 此模式假定存储中的更新和浏览操作强度较低。 它可能会导致高负载期间出现严重延迟和数据不可用。 出于性能考虑，我们建议使用&#x200B;**计划**&#x200B;更新，因为它存储有关数据更新的信息，并通过特定的cron作业在后台按部分执行索引。 您可以在[!DNL Commerce] > **[!UICONTROL System]** > [!UICONTROL Tools]配置页面上单独更改每个&#x200B;**[!UICONTROL Index Management]**&#x200B;索引器的模式。 [!UICONTROL Customer Grid]索引必须始终设置为&#x200B;**[!UICONTROL Update on Save]**&#x200B;模式。

>[!TIP]
>
>与其他MariaDB或[!DNL MySQL]版本相比，在MariaDB 10.4和10.6上重新索引需要更多时间。 我们建议修改默认的MariaDB配置设置，如[安装先决条件](../installation/prerequisites/database/mysql.md)中所述。

## 缓存

在生产环境中启动商店时，请从&#x200B;**[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]**&#x200B;页面激活所有缓存。 我们强烈建议使用[!DNL Varnish]，因为这是一个高效的生产页面缓存解决方案。

## 异步电子邮件通知

启用“异步电子邮件通知”设置会将处理结账和订单处理电子邮件通知的流程移至后台。 要启用此功能，请转到&#x200B;**[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**。 有关详细信息，请参阅[管理员用户指南](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/config/sales/sales-emails)中的&#x200B;_销售电子邮件_。

## 异步订单数据处理

有时候，店面在进行密集销售的同时，[!DNL Commerce]还会执行密集订单处理。 您可以配置[!DNL Commerce]，以便在数据库级别区分这两种通信模式，以避免相应表中的读取和写入操作发生冲突。 您可以异步存储和索引订单数据。 订单将置于临时存储中，并批量移至Order Management网格，不会出现任何冲突。 您可以从&#x200B;**[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**&#x200B;激活此选项。 有关详细信息，请参阅[管理员用户指南](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations#enable-scheduled-grid-updates-and-reindexing)中的&#x200B;_计划网格更新_。

>[!WARNING]
>
>**[!UICONTROL Developer]**&#x200B;选项卡和选项仅在[开发人员模式](../configuration/cli/set-mode.md)下可用。 云基础架构上的[Adobe Commerce](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test)不支持`Developer`模式。

## 异步配置保存

对于具有大量存储级别配置的项目，保存存储配置可能需要花费过多的时间或导致超时。 _异步配置_&#x200B;模块通过运行使用使用者处理消息队列中的保存的cron作业来启用异步配置保存。 AsyncConfig默认为&#x200B;**已禁用**。

可以使用命令行界面启用AsyncConfig：

```bash
bin/magento setup:config:set --config-async 1
```

`set`命令将以下内容写入`app/etc/env.php`文件：

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

在密集销售期间，[!DNL Commerce]可以延迟与订单相关的库存更新。 这样可最大限度地减少操作次数，并加快下单流程。 但是，此选项有风险，并且只能在商店中激活延交订单时使用，因为此选项可能导致存货数量为负。 对于可轻松按需重新补充库存的商店，此选项可显着提升结账流的性能。 要在您的网站上激活延期库存更新，请转到&#x200B;**[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**。 有关详细信息，请参阅[Adobe Commerce用户指南](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud)中的&#x200B;_管理库存_。

>[!INFO]
>
>此选项仅在激活&#x200B;**[!UICONTROL Backorder with any mode]**&#x200B;时可用。

>[!INFO]
>
>此选项也适用于[异步下单](high-throughput-order-processing.md#asynchronous-order-placement)和[Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html?lang=zh-Hans)。

## 客户端优化设置

要提高[!DNL Commerce]实例的店面响应速度，请在“默认”或“开发人员”模式下转到“管理员”并更改以下设置：

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]：**

| 设置组 | 设置 | 值 |
| ------------------- | -------------------------- | ------ |
| 网格设置 | 异步索引 | 启用 |
| CSS设置 | 缩小CSS文件 | 是 |
| [!DNL JavaScript]设置 | 缩小[!DNL JavaScript]个文件 | 是 |
| [!DNL JavaScript]设置 | 启用[!DNL JavaScript]捆绑 | 是 |
| 模板设置 | 缩小HTML | 是 |

>[!INFO]
>
>**[!UICONTROL Developer]**&#x200B;选项卡和选项仅在[开发人员模式](../configuration/cli/set-mode.md)下可用。 云基础架构[上的 [!DNL Commerce] Adobe](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test)不支持`Developer`模式。

激活&#x200B;**[!UICONTROL Enable [!DNL JavaScript] Bundling]**&#x200B;选项后，您允许Commerce将所有JS资源合并到一个或一组加载到店面页面中的捆绑包中。 捆绑JS可减少向服务器发出的请求，从而改善页面性能。 它还有助于浏览器在首次调用时缓存JS资源，并在所有进一步浏览中重复使用它们。 此选项还会带来延迟评估，因为所有JS都作为文本加载。 它仅在页面上触发特定操作后才启动代码分析和评估。 但是，对于首次页面加载时间极其关键的存储区，不建议使用此设置，因为所有JS内容都将在首次调用时加载。

>[!INFO]
>
>有关优化CSS和Javascript的更多信息，请参阅Adobe Commerce帮助中心_中的Adobe Commerce上的[CSS和Javascript文件优化以及Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) 。

### 捆绑提示

* 我们建议您使用第三方工具进行缩小和捆绑（如[r.js](https://requirejs.org/)）。 [!DNL Commerce]内置机制不是最佳的，已作为备用机制发货。
* 激活HTTP/2协议可能是使用JS捆绑包的良好替代方法。 该协议提供了许多相同的好处。 默认情况下，在云基础架构项目上的Adobe Commerce中会启用此功能。
* 我们不建议使用已弃用的设置，例如合并JS和CSS文件，因为它们仅为页面的HEAD部分中的同步加载JS而设计。 使用此技术可能会导致捆绑销售，并要求JS逻辑无法正常工作。

## 客户区段验证

具有大量[客户区段](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/customers/segments/customer-segments)的商家可能会因客户操作（如客户登录和将产品添加到购物车）而遇到性能显着下降的情况。

客户操作会触发客户区段的验证过程，这可能导致性能下降。 默认情况下，Adobe Commerce会实时验证每个区段，以定义哪些客户区段匹配，哪些客户区段不匹配。

为避免性能下降，您可以将&#x200B;**[!UICONTROL Real-time Check if Customer is Matched by Segment]**&#x200B;系统配置选项设置为&#x200B;**否**，以通过单个组合条件SQL查询来验证客户区段。

要启用此优化，请转到&#x200B;**[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**。

如果系统中有许多客户区段，则此设置可提高客户区段验证的性能。 但是，它不适用于[拆分数据库](../configuration/storage/multi-master.md)实现或没有注册客户时。

## 数据库维护计划 {#database}

我们建议为暂存实例和生产实例执行定期数据库备份。 由于备份操作的I/O密集性质，您可能会遇到备份速度较慢和潜在问题。 同时为多个环境运行数据库进程可能会由于可用资源争用而降低运行速度。

为了获得更好的性能，请安排您的备份在离峰时间连续运行，一次运行一个。 此方法可避免I/O争用，并缩短完成时间，尤其是对于较小的实例、较大的数据库等。

例如，当您的商店访问次数较少时，我们建议先计划生产数据库的备份，然后再计划暂存数据库。

## 限制网格中的产品数

要提高大型目录的产品网格性能，我们建议使用&#x200B;**[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]**&#x200B;系统配置设置来限制网格中的产品数量。

默认情况下，此系统配置设置处于禁用状态。 启用此选项后，您可以将网格中的产品数量限制为特定值。 **[!UICONTROL Records Limit]**&#x200B;是可自定义的设置，其默认最小值为`20000`。
启用&#x200B;**[!UICONTROL Limit Number of Products in Grid]**&#x200B;设置且网格中的产品数大于记录限制时，将返回有限制的记录集合。 当达到限制时，将在网格标题中隐藏找到的记录总数、选定的记录数和分页元素。

当网格中的产品总数有限时，它不会影响产品网格中的批量操作。 它只影响产品网格表示层。 例如，网格中的`20000`产品数量有限，用户单击&#x200B;**[!UICONTROL Select All]**，选择&#x200B;**[!UICONTROL Update attributes]**&#x200B;批量操作，并更新某些属性。 因此，所有产品都已更新，而不是有限的`20000`记录集合。

产品网格限制仅影响UI组件使用的产品集合。 因此，并非所有产品网格都受此限制的影响。 仅限使用`Magento\Catalog\Ui\DataProvider\Product\ProductCollection`的用户。
您只能在以下页面上限制产品网格集合：

* 目录产品网格
* 添加相关/向上销售/交叉销售产品网格
* 将产品添加到捆绑产品
* 将产品添加到组产品
* 管理员创建订单页面

如果您不希望限制产品网格，我们建议您更准确地使用过滤器，以便结果集合的项目数少于&#x200B;**[!UICONTROL Records Limit]**。
