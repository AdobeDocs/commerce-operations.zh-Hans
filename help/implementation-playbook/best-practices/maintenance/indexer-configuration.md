---
title: 索引器的配置最佳实践
description: 通过遵循索引器配置的最佳实践来维护和优化站点性能。
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 29168544e3a33b874b104f308bd53cb475ac2638
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# 索引器配置的最佳实践

要优化和维护站点性能，请使用本文中所述的性能最佳实践来审查和更新索引器配置。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md)，共：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 设置索引器以按计划更新

Adobe Commerce具有两种类型的索引器模式：[!UICONTROL Update on Save]和[!DNL Update on Schedule]。

- 当目录或其他数据发生更改时，**[!UICONTROL Update on Save]**&#x200B;模式会立即更新索引。 例如，如果管理员用户将新产品添加到类别，则保存更新后，将立即重新索引类别产品索引。

- **[!UICONTROL Update on Schedule]**&#x200B;模式存储有关数据更新的信息，重新索引操作和索引更新由在后台按计划时间间隔运行的cron作业管理。 cron作业并不总是在每次运行时执行重新索引。 仅当索引器更改日志中有新条目（例如，索引器上有积压）时，它才会重新索引。

大型存储区中有多个管理员在后端工作或者有许多导入和导出会触发频繁的索引更新。 如果您的网站索引配置设置为[!UICONTROL Update on Save]模式，则频繁重新索引会降低数据库性能，这会降低网站性能并导致重新索引过程的长时间延迟，尤其是对于大型商店。

要最大限度地提高网站性能，请遵循以下编制索引最佳实践：

- 查看索引配置。
- 对于大型网站以及经常更新和流量较大的网站，将索引器设置为&#x200B;_[!UICONTROL Update on Schedule]_。 请参阅[索引管理](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/tools/index-management#change-the-index-mode)。
- 遵循[性能最佳实践](../../../performance/configuration.md)来管理索引。

>[!IMPORTANT]
>
>[!DNL Customer Grid]索引器行为在2.4.8中发生了更改：
>
>- **低于2.4.8**： [!DNL Customer Grid]索引器只能使用[!UICONTROL Update on Save]选项重新编制索引，不支持[!UICONTROL Update by Schedule]选项。
>- **2.4.8及更高版本**： [!DNL Customer Grid]索引器同时支持[!UICONTROL Update on Save]和[!UICONTROL Update by Schedule]模式，并且默认为[!UICONTROL Update by Schedule]。

## 其他信息

- [管理员用户的索引管理](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [使用Magento CLI进行索引管理](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html?lang=zh-Hans)
- [针对开发人员的索引概述](https://developer.adobe.com/commerce/php/development/components/indexing/)
