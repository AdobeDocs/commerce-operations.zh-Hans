---
title: 配置最佳实践
description: 使用这些最佳实践优化Adobe Commerce或Magento Open Source部署的响应时间。
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 配置最佳实践

商务提供了许多设置和工具，您可以使用这些设置和工具缩短页面上的响应时间，并提高吞吐量。

## Cron作业

中的所有异步操作 [!DNL Commerce] 使用Linux执行 `cron` 命令。 请参阅 [配置并运行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) 才能正确配置。

## 索引器

索引器可以在 **[!UICONTROL Update on Save]** 或 **[!UICONTROL Update on Schedule]** 模式。 的 **[!UICONTROL Update on Save]** 模式会在目录或其他数据发生更改时立即索引。 此模式假定存储中的更新和浏览操作强度较低。 在高负载期间，这可能导致显着的延迟和数据不可用。 我们建议使用 **按计划更新** 模式，因为它存储有关数据更新的信息，并通过特定cron作业按后台的各个部分执行索引。 您可以更改每个 [!DNL Commerce] 索引器  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** 配置页面。

与其他MariaDB或 [!DNL MySQL] 版本。 作为解决方法，我们建议修改默认的MariaDB配置并设置以下参数：

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

## 缓存

在生产中启动存储时，激活 **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** 页面。 我们强烈建议使用 [!DNL Varnish]，因为它是一个高效的生产页面缓存解决方案。

## 异步电子邮件通知

启用“异步电子邮件通知”设置会将处理结帐和订单处理电子邮件通知的进程移到后台。 要启用此功能，请转到 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. 请参阅 [销售电子邮件](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) 在 _Magento Open Source用户指南_ 以了解更多信息。

## 异步订单数据处理

有时，在店面进行密集销售的同时， [!DNL Commerce] 正在执行密集订单处理。 您可以配置 [!DNL Commerce] 在数据库级别上区分这两种流量模式，以避免相应表中的读操作和写操作之间的冲突。 您可以异步存储和索引订单数据。 订单将放入临时存储中，并在不发生任何冲突的情况下批量移动到Oracle Order Management网格中。 您可以从 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. 请参阅 [计划网格更新](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) 在 _Magento Open Source用户指南_ 以了解更多信息。

>[!WARNING]
>
>的 **[!UICONTROL Developer]** 选项卡和选项仅在 [开发人员模式](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-mode.html). [Adobe Commerce云基础架构](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) 不支持 `Developer` 模式。

## 延期库存更新

在密集销售时， [!DNL Commerce] 可以推迟与订单相关的库存更新。 这样可以最大限度地减少操作次数并加快订单放置过程。 但是，此选项是有风险的，并且仅在商店中激活延交订单时才使用，因为此选项可能会导致负库存数量。 此选项可以显着改善可轻松按需重新填充库存的商店的结帐流程性能。 要在您的网站上激活延迟的库存更新，请转到 **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. 请参阅 [管理库存](https://docs.magento.com/user-guide/catalog/inventory.html) 在 _Adobe Commerce用户指南_ 以了解更多信息。

>[!INFO]
>
>此选项仅在 **[!UICONTROL Backorder with any mode]** 激活。

## 客户端优化设置

要提高店面的响应速度，请 [!DNL Commerce] 实例中，转到默认或开发人员模式下的管理员，然后更改以下设置：

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| 设置组 | 设置 | 值 |
| ------------------- | -------------------------- | ------ |
| 网格设置 | 异步索引 | 启用 |
| CSS设置 | 缩小CSS文件 | 是 |
| [!DNL JavaScript] 设置 | 缩小 [!DNL JavaScript] 文件 | 是 |
| [!DNL JavaScript] 设置 | 启用 [!DNL JavaScript] 捆绑 | 是 |
| 模板设置 | 缩小HTML | 是 |

>[!INFO]
>
>的 **[!UICONTROL Developer]** 选项卡和选项仅在 [开发人员模式](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-mode.html). [Adobe [!DNL Commerce] 云基础架构](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) 不支持 `Developer` 模式。

激活 **[!UICONTROL Enable [!DNL JavaScript] Bundling]** 选项，则允许Commerce将所有JS资源合并到一个或一组在店面页面中加载的包中。 捆绑JS可减少对服务器的请求，从而提高页面性能。 它还可帮助浏览器在首次调用时缓存JS资源，并重复使用这些资源以供所有进一步浏览。 此选项还会带来延迟评估，因为所有JS都会作为文本加载。 只有在页面上触发特定操作后，它才会启动代码分析和评估。 但是，对于首次页面加载时间极其关键的存储，不建议使用此设置，因为所有JS内容都将在首次调用中加载。

>[!INFO]
>
>请参阅 [在云基础架构和Adobe Commerce上对Adobe Commerce上的CSS和Javascript文件进行优化](https://support.magento.com/hc/en-us/articles/360044482152) 位于Adobe Commerce帮助中心_ ，以了解有关优化CSS和Javascript的更多信息。

### 捆绑提示

* 我们建议您使用第三方工具进行缩小和捆绑(例如 [r.js](https://requirejs.org/))。 [!DNL Commerce] 内置机制不是最佳机制，将作为备用替代产品提供。
* 激活HTTP2协议是使用JS捆绑的一个好替代方法。 该协议提供了几乎相同的好处。
* 我们不建议使用已弃用的设置，如合并JS和CSS文件，因为这些设置仅适用于页面HEAD部分中同步加载的JS。 使用此技术可能会导致捆绑和要求JS逻辑无法正确工作。

## 数据库维护计划 {#database}

我们建议为您的暂存和生产实例执行定期数据库备份。 由于备份操作的I/O密集性，您可能会遇到备份速度较慢和潜在问题。 由于可用资源争用，同时为多个环境运行数据库进程可能会运行较慢。

为了提高性能，请安排备份在非高峰时间连续运行，一次运行一次。 此方法避免了I/O争用，并缩短了完成的时间，特别是对于较小的实例、较大的数据库等。

例如，我们建议在您的商店遇到访问次数较低时，安排生产数据库的备份，然后再安排暂存数据库。
