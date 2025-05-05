---
title: “ACSD-59967： JavaScript错误导致 [!DNL Google Maps] 无法正确呈现”
description: 应用ACSD-59967修补程序以修复JavaScript错误导致 [!DNL Google Maps] 无法正确呈现的Adobe Commerce问题。
feature: Admin Workspace, Page Builder, CMS
role: Admin, Developer
source-git-commit: 5fe2f494e0832e9f736fbd797da31f5815934a61
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-59967： JavaScript错误导致[!DNL Google Maps]无法正确呈现

ACSD-59967修补程序修复了JavaScript错误导致[!DNL Google Maps]无法正确呈现的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51时，此修补程序可用。 修补程序ID为ACSD-59967。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.4-p3

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

JavaScript错误导致[!DNL Google Maps]无法正确呈现。

<u>重现步骤</u>：

1. 生成有效的[!DNL Google Maps]密钥。
1. 在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Content Management]**&#x200B;下配置[!DNL Google Maps] API密钥。
1. 将您的[!DNL Google API Key]添加到&#x200B;**[!UICONTROL Google Maps API Key]**&#x200B;字段并保存配置。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Create New Page]**。
1. 添加&#x200B;**[!UICONTROL Row]**&#x200B;元素和&#x200B;**[!UICONTROL Maps]**&#x200B;元素。

<u>预期的结果</u>：

控制台中不存在JavaScript错误，并且映射在&#x200B;*店面*&#x200B;和&#x200B;*管理员*&#x200B;上正确呈现。

<u>实际结果</u>：

JavaScript错误会显示在控制台中，并且映射无法正确呈现。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
