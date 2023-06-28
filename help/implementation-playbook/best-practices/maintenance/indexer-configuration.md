---
title: 索引器的配置最佳实践
description: 通过遵循索引器配置的最佳实践来维护和优化站点性能。
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# 索引器配置的最佳实践

要优化和维护站点性能，请使用本文中所述的性能最佳实践来查看和更新索引器配置。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 设置索引器以按计划更新

Adobe Commerce有两种类型的索引器模式： [!UICONTROL Update on Save] （默认设置）和 [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** 模式会在目录或其他数据发生更改时立即更新索引。 例如，如果管理员用户将新产品添加到类别，则保存更新后，将立即重新索引类别产品索引。

- **[!UICONTROL Update on Schedule]** 模式存储有关数据更新的信息，重新索引操作和索引更新由cron作业管理，该作业按计划间隔在后台运行。

大型存储区中有多个管理员在后端工作或者有许多导入和导出，会触发频繁的索引更新。 如果您的站点索引配置设置为 [!UICONTROL Update on Save] 模式，频繁的重新索引会降低数据库性能，从而减慢网站性能并导致重新索引过程的长时间延迟，尤其是对于大型商店。

要最大限度地提高网站性能，请遵循以下最佳实践编制索引：

- 查看索引配置。
- 将索引器设置为 _[!UICONTROL Update on Schedule]_适用于经常更新和流量较大的大型网站和网站。 参见 [索引管理](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- 关注 [性能最佳实践](../../../performance/configuration.md) 用于管理索引。

>[!IMPORTANT]
>
>此 [!DNL Customer Grid] 只能使用 [!UICONTROL Update on Save] 选项。 此索引不支持 `Update by Schedule` 选项。

## 其他信息

- [管理员用户的索引管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [使用MagentoCLI进行索引管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [面向开发人员的索引概述](https://developer.adobe.com/commerce/php/development/components/indexing/)
