---
title: 'ACSD-53239：库存索引器清理所有缓存'
description: 应用ACSD-53239修补程序以修复清单索引器在[!UICONTROL Update on Schedule]模式下清理所有缓存的Adobe Commerce问题。
feature: GraphQL, Inventory, Catalog Management
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# ACSD-53239：清单索引器清理[!UICONTROL Update on Schedule]模式中的所有缓存

ACSD-53239修补程序修复了清单索引器在[!UICONTROL Update on Schedule]模式下清理所有缓存的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.36时，此修补程序可用。 修补程序ID为ACSD-53239。 请注意，Adobe Commerce 2.4.6中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.5-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

库存索引器清理[!UICONTROL Update on Schedule]模式中的所有缓存。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Catalog Products]**&#x200B;并选择大约&#x200B;*1200*&#x200B;个产品。
2. 将&#x200B;*[!UICONTROL Qty]*&#x200B;更新为新值，然后单击&#x200B;**[!UICONTROL Save]**。
3. 保存后立即运行`bin/magento cron:run`。
4. 运行以下GraphQL查询：

   ```GraphQL
   {
     storeConfig {
     absolute_footer
     }
   }
   ```

<u>预期的结果</u>

在通常的时间内处理查询。

<u>实际结果</u>

处理查询的速度异常慢。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
