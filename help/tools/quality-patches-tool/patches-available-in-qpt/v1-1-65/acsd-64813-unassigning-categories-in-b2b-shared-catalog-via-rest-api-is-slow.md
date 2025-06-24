---
title: ACSD-64813：通过REST API取消分配 [!DNL B2B] 共享目录中的类别缓慢
description: 应用ACSD-64813修补程序以修复通过REST API在 [!DNL B2B] 共享目录中取消分配类别速度缓慢的Adobe Commerce问题。
feature: B2B, REST, Categories
role: Admin, Developer
type: Troubleshooting
exl-id: e6fd89c2-d3c0-462f-b328-7a80b456d96d
source-git-commit: 239a9efcc2ae231b337f654e4e36e6119e6eff7e
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-64813：通过REST API取消分配[!DNL B2B]共享目录中的类别缓慢

ACSD-64813修补程序修复了通过REST API取消分配[!DNL B2B]共享目录中的类别速度缓慢的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65时，此修补程序可用。 修补程序ID为ACSD-64813。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过REST API取消分配[!DNL B2B]共享目录中的类别的操作缓慢。

<u>重现步骤</u>：

1. 启用&#x200B;**[!UICONTROL B2B]**、**[!UICONTROL Company]**&#x200B;和&#x200B;**[!UICONTROL Shared Catalog]**。
1. 生成30,000个现成库存产品。
1. 创建[自定义共享目录](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared#actions-controls)并为其分配所有产品。
1. 在默认根类别下创建一个新类别，并为其分配几个产品。
1. 使用管理令牌以使用新类别ID调用REST API端点`rest/all/V1/sharedCatalog/<shared_catalog_id>/assignCategories`。

   ```
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

1. 确认响应为&#x200B;*true*。
1. 运行`bin/magento cron:run`两次或执行重新索引。
1. 使用管理令牌以使用新类别ID调用REST API端点`rest/all/V1/sharedCatalog/<shared_catalog_id>/unassignCategories`。

   ```
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

<u>预期的结果</u>：

操作应在合理的时间内完成（在几分钟内）。

<u>实际结果</u>：

执行大约需要30分钟或导致超时错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
