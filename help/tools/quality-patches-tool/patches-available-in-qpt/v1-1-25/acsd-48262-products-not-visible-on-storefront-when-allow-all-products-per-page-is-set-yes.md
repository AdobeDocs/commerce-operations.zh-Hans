---
title: ACSD-48262：当[!UICONTROL Allow All Products Per Page]设置为[!UICONTROL Yes]时，产品在店面不可见
description: 应用ACSD-48262修补程序以修复将[!UICONTROL Allow All Products Per Page]设置设为[!UICONTROL Yes]时店面中看不到产品的Adobe Commerce问题。
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
exl-id: 733ac476-5c3c-4cbe-88b7-f436d15f1c7d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-48262：当[!UICONTROL Allow All Products Per Page]设置为&#x200B;*[!UICONTROL Yes]*&#x200B;时，产品在店面不可见

ACSD-48262修补程序修复了将[!UICONTROL Allow All Products Per Page]设置设为&#x200B;*[!UICONTROL Yes]*&#x200B;时，产品在店面中不可见的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25时，此修补程序可用。 修补程序ID为ACSD-48262。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法）>=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

ACSD-48262修补程序修复了将[!UICONTROL Allow All Products Per Page]设置设为&#x200B;*[!UICONTROL Yes]*&#x200B;时，产品在店面中不可见的问题。

<u>重现步骤</u>：

1. 创建测试类别。
1. 在测试类别中创建测试产品。
1. 浏览产品以测试店面上的类别页面，并确保产品可见。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]**&#x200B;并将[!UICONTROL Allow All Products Per Page]设置设置为&#x200B;*[!UICONTROL Yes]*。
1. 清除缓存。
1. 检查店面的类别页面。

<u>预期的结果</u>：

产品可见。

<u>实际结果</u>：

产品不可见。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
