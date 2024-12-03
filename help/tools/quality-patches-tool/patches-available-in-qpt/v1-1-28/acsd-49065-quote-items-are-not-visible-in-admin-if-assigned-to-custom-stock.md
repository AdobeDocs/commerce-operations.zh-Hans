---
title: ACSD-49065：报价单项目在管理员中不可见
description: Adobe Commerce应用ACSD-49065修补程序以修复以下问题：如果报价项目仅分配给自定义库存，则无法在管理员中看到这些报价项目。
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
exl-id: fc3bea92-305b-4598-9915-3422d61c76ec
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-49065：报价单项目在管理员中不可见

ACSD-49065修补程序修复了报价单项目仅分配给自定义库存时无法在管理员中显示的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28时，此修补程序可用。 修补程序ID为ACSD-49065。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果报价项目仅分配给自定义库存，则无法在管理员中显示。

先决条件：

必须安装&#x200B;**[!UICONTROL B2B]**&#x200B;和&#x200B;**[!UICONTROL Inventory]**&#x200B;模块。

<u>重现步骤</u>：

1. 在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**&#x200B;下启用&#x200B;**[!UICONTROL Company]**&#x200B;和&#x200B;**[!UICONTROL B2B Quote]**。
1. 创建辅助&#x200B;**[!UICONTROL Inventory Source]**&#x200B;并将其分配给辅助&#x200B;**[!UICONTROL Inventory Stock]**。
1. 通过仅分配辅助（非默认）**[!UICONTROL Inventory Source]**&#x200B;创建新产品。
1. 转到店面并创建新公司帐户。 以&#x200B;**[!UICONTROL Company Admin]**&#x200B;身份登录，然后将创建的产品添加到购物车。
1. 导航到购物车和&#x200B;*[!UICONTROL Request a Quote]*。
1. 转到管理员并在&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Quotes]**&#x200B;查看请求的报价。

<u>预期的结果</u>：

项目会显示在使用新产品创建的新报价中，而无需重新保存产品。

<u>实际结果</u>：

*[!UICONTROL Items Quoted]*&#x200B;部分为空。 如果重新保存新创建的产品，则会显示相应的项目。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
