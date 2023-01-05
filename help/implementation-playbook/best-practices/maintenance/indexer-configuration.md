---
title: 索引器配置最佳实践
description: 按照索引器配置的最佳实践维护和优化网站性能。
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: ae9573f3766c59887aea177cb85bf889c2161bfc
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---


# 索引器配置的最佳实践

要优化和维护站点性能，请使用本文中描述的性能最佳实践查看和更新索引器配置。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 设置索引器以按计划更新

Adobe Commerce有两种索引器模式： [!UICONTROL Update on Save] （默认设置）和 [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** 模式会在目录或其他数据发生更改时立即更新索引。 例如，如果管理员用户将新产品添加到类别，则在保存更新后会立即将类别产品索引重新编制索引。

- **[!UICONTROL Update on Schedule]** 模式存储有关数据更新的信息，并且重新索引操作和索引更新由在后台以预定时间间隔运行的cron作业管理。

如果拥有一个大型存储区，且多个管理员在后端工作，或者拥有多个导入和导出，则会频繁更新索引。 如果网站索引配置设置为 [!UICONTROL Update on Save] 模式下，频繁的重新索引会降低数据库性能，这会降低站点性能，并导致重新索引过程中出现较长的延迟，特别是对于大型存储。

要最大限度地提高网站性能，请遵循以下索引最佳实践：

- 查看索引配置。
- 将索引器设置为 _[!UICONTROL Update on Schedule]_适用于大型网站和频繁更新和流量较大的网站。 请参阅 [索引管理](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- 关注 [性能最佳实践](../../../performance/configuration.md) 用于管理索引。

>[!IMPORTANT]
>
>的 [!DNL Customer Grid] 只能使用 [!UICONTROL Update on Save] 选项。 此索引不支持 `Update by Schedule` 选项。

## 其他信息

- [管理员用户的索引管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [使用MagentoCLI进行索引管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [面向开发人员的索引概述](https://developer.adobe.com/commerce/php/development/components/indexing/)
