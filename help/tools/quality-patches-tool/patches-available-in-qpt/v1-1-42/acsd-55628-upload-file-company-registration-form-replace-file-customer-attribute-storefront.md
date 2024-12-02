---
title: ACSD-55628：在公司注册表中上传文件；替换店面中客户属性的文件
description: 应用ACSD-55628修补程序以修复在公司注册表中上传文件并替换店面中客户属性的文件时出现的Adobe Commerce问题。
feature: Storefront, Attributes, B2B, Customers
role: Admin, Developer
exl-id: a008a205-ec1d-4a1d-9cd2-75f10a937057
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-55628：在公司注册表中上传文件；替换店面中客户属性的文件

>[!NOTE]
>
>此修补程序取代[ACSD-51240](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51240-uploaded-file-missing-while-registering-via-company-registration-form.md)。

ACSD-55628修补程序修复了在公司注册表中上传文件以及在店面中替换客户属性文件的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42时，此修补程序可用。 修补程序ID为ACSD-55628。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4-p2 &lt; 2.4.5和2.4.5-p1 &lt; 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

无法替换店面中客户属性的文件。

<u>重现步骤</u>：

1. 使用以下值创建新客户属性：

   * *[!UICONTROL Input Type]*： *[!UICONTROL File (Attachment)]*
   * *[!UICONTROL Show on Storefront]*： *是*
   * *[!UICONTROL Forms to Use In]*： *所有可用选项*

1. 以客户身份登录店面并打开&#x200B;**[!UICONTROL My Account]** > **[!UICONTROL Account Information]**。
1. 上传新图像并保存。
1. 刷新页面。 删除旧图像并上传新图像。 保存更改。

<u>预期的结果</u>：

将保存新图像。

<u>实际结果</u>：

仍会显示旧图像。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
