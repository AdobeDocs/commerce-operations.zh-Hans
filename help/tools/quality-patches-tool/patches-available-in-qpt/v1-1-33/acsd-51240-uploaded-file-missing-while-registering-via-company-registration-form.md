---
title: 'ACSD-51240：通过公司注册表单注册时上传的文件丢失'
description: 应用ACSD-51240修补程序以修复在通过公司注册表单注册时上传的文件缺失的Adobe Commerce问题。
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-51240：通过公司注册表单注册时上传的文件丢失

>[!NOTE]
>
>此修补程序已被[ACSD-55628](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md)替换。

ACSD-51240修补程序修复了在通过公司注册表单注册时上传的文件缺失的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33时，此修补程序可用。 修补程序ID为ACSD-51240。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)上检查兼容性。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 问题

通过公司注册表单注册时上传的文件丢失。

<u>重现步骤</u>：

1. 设置&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *是*。
1. 创建&#x200B;**[!UICONTROL File]**&#x200B;类型的新客户属性，设置&#x200B;**[!UICONTROL Show in StoreFront]** = *是*，然后选择&#x200B;**[!UICONTROL all forms]**。
1. 在店面中创建新公司并上传新属性的图像。
在店面中打开公司和管理员用户。

<u>预期的结果</u>：

将显示上传的文件。

<u>实际结果</u>：

上传的文件未显示在[!UICONTROL Commerce Admin]的公司页面或管理员客户页面上。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
