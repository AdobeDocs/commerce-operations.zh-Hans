---
title: ACSD-52929：重新索引默认源项的冗余请求
description: 应用ACSD-52929补丁程序，以修复在异步模式下配置清单索引器时存在重新索引默认源项目的冗余请求的Adobe Commerce问题。
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 904aed0e-a6cd-4a0f-949d-bb32fcd77356
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-52929：重新索引默认源项的冗余请求

ACSD-52929修补程序修复了在异步模式下配置清单索引器时，重新索引默认源项目的请求存在冗余的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.38时，此修补程序可用。 修补程序ID为ACSD-52929。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在异步模式下配置库存索引器时，重新索引默认源项目的请求存在冗余。

<u>重现步骤</u>：

1. 配置[!DNL RabbitMQ]。
1. 通过转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]**&#x200B;启用异步重新索引策略，并设置&#x200B;**[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**。
1. 创建自定义库存来源。
1. 登录到[!DNL RabbitMQ]仪表板并转到“队列”选项卡。
1. 检查`inventory.indexer.sourceItem`队列，并确保它没有消息。
1. 从后端打开一个简单产品，并将&#x200B;*[!UICONTROL stock only]*&#x200B;添加到自定义源并保存该产品。
1. 在`inventory.indexer.sourceItem`仪表板中加载[!DNL RabbitMQ]队列，然后检查消息。

<u>预期的结果</u>：

自定义源的队列中只有一条消息。

<u>实际结果</u>：

队列中显示两条消息：一条用于默认源，另一条用于自定义源。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)：搜索修补程序[!DNL Quality Patches Tool]。
