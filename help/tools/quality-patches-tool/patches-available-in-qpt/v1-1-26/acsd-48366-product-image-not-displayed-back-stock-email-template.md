---
title: ACSD-48366：[!UICONTROL Back to Stock]电子邮件模板上未显示产品图像
description: 应用ACSD-48366修补程序以修复产品库存警报电子邮件中未显示产品缩略图图像的Adobe Commerce问题。
feature: Admin Workspace, Communications, Orders, Products
role: Admin
exl-id: a721f399-f50a-4a13-9f5d-17ae7f3985f6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48366：[!UICONTROL Back to Stock]电子邮件模板上未显示产品图像

ACSD-48366修补程序修复了产品库存警报电子邮件中未显示产品缩略图图像的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26时，此修补程序可用。 修补程序ID为ACSD-48366。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品图像未显示在[!UICONTROL Back to Stock]电子邮件模板上。

<u>重现步骤</u>：

1. 通过转至&#x200B;**[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]*&#x200B;为&#x200B;*[!UICONTROL Back in Stock]*&#x200B;启用&#x200B;*[!UICONTROL Product Alert]*。
1. 启用&#x200B;*[!UICONTROL Display Out of Stock Products]*，方法是转到&#x200B;**[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]*。
1. 创建数量= 0的简单产品。
1. 从店面创建客户并订阅上述产品，以便在有存货时获取产品提醒。
1. 使产品有货。
1. 执行产品警报cron。

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. 启动客户的产品警报。

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. 检查电子邮件。 库存警报电子邮件现在应可在邮件收集器中使用。

<u>预期的结果</u>：

产品图像会显示在库存警报电子邮件中。

<u>实际结果</u>：

产品图像在库存警报电子邮件中不可用。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
