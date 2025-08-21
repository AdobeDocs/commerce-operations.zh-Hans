---
title: ACSD-66865：保存[!UICONTROL Catalog Price Rule]将使索引器失效，并且提供替代方法，以仅对受影响的产品重新索引
description: 应用ACSD-66865修补程序以修复Adobe Commerce问题，其中  保存[!UICONTROL Catalog Price Rules]将使索引器失效，并且提供了替代方法，可仅对受影响的产品重新编制索引。
feature: Price Rules, Price Indexer
role: Admin, Developer
type: Troubleshooting
source-git-commit: fe36522b99ec3fe7189d164cfca6127c9119e06e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# ACSD-66865：保存&#x200B;**[!UICONTROL Catalog Price Rule]**&#x200B;将使索引器失效，并且提供替代方法，以仅对受影响的产品重新索引

ACSD-66865修补程序修复了保存&#x200B;**[!UICONTROL Catalog Price Rule]**&#x200B;使索引器失效的问题，并提供了替代方法，可仅对受影响的产品重新索引。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68时，此修补程序可用。 修补程序ID为ACSD-66865。 请注意，此问题已在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

保存&#x200B;**[!UICONTROL Catalog Price Rule]**&#x200B;导致所有索引器失效，触发完整的重新索引，而不是仅重新索引受影响的产品。

<u>重现步骤</u>：

1. 确保cron未运行，并且所有索引器都设置为按计划更新（除了可以在保存时更新的`customer_grid`）。
2. 使用以下命令运行完全手动重新索引： `php bin/magento indexer:reindex`。
3. 验证所有索引是否显示积压中具有&#x200B;*[!UICONTROL Ready]* 0 *个项目的状态*。
4. 在管理员侧边栏上，转到&#x200B;**[!UICONTROL Marketing]** > *[!UICONTROL Promotions]* > **[!UICONTROL Catalog Price Rule]**。 为单个产品创建有效的目录价格规则（例如，使用&#x200B;*SKU*&#x200B;条件）。
5. 运行命令： `php bin/magento indexer:status`以检查索引器状态。
6. 请注意，即使只有一个产品受到影响，多个索引仍标记为&#x200B;**[!UICONTROL Reindex Required]**。

<u>预期的结果</u>：

仅识别受影响的产品数据，并触发部分重新索引，而不是在所有索引器上触发完全重新索引。

<u>实际结果</u>：

所有索引器都会触发完全重新索引，即使仅单个产品受&#x200B;**[!UICONTROL Catalog Price Rule]**&#x200B;影响也是如此。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
