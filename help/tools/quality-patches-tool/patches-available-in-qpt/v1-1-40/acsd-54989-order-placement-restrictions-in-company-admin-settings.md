---
title: ACSD-54989：当[!UICONTROL Enable Purchase Orders]设置为“是”且[!UICONTROL Purchase Order]设置为“否”时，公司管理员无法订购
description: 应用ACSD-54989修补程序以修复以下问题：如果[!UICONTROL Enable Purchase Orders]设置为“是”且[!UICONTROL Purchase Order]设置为“否”，则公司管理员无法下单Adobe Commerce。
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: 13830361-dd0c-486f-b07f-34280a17ab76
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-54989：当&#x200B;*[!UICONTROL Enable Purchase Orders]*&#x200B;设置为&#x200B;*是*&#x200B;且&#x200B;*[!UICONTROL Purchase Order]*&#x200B;设置为&#x200B;*否*&#x200B;时，公司管理员无法订购

ACSD-54989修补程序修复了当&#x200B;**[!UICONTROL Enable Purchase Orders]**&#x200B;设置为&#x200B;*是*&#x200B;且&#x200B;**[!UICONTROL Purchase Order]**&#x200B;设置为&#x200B;*否*&#x200B;时无法下订单的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40时，此修补程序可用。 修补程序ID为ACSD-54989。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当&#x200B;**[!UICONTROL Enable Purchase Orders]**&#x200B;设置为&#x200B;*是*&#x200B;且&#x200B;**采购订单**&#x200B;设置为&#x200B;*否*&#x200B;时，公司管理员无法下订单。

<u>先决条件</u>：

安装[!DNL B2B]模块。

<u>重现步骤</u>：

1. 启用公司并离开[!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *否*。
1. 创建一个价格为100的简单产品。
1. 通过管理员创建新公司。
1. 将&#x200B;[!UICONTROL **启用采购订单**]&#x200B;设置为&#x200B;*是*。
1. 以公司管理员身份登录店面。
1. 将创建的简单产品添加到购物车。
1. 进入结帐页面，然后单击&#x200B;**[!UICONTROL Place Order]**&#x200B;以完成购买。

<u>预期的结果</u>：

您可以成功下订单。

<u>实际结果</u>：

**[!UICONTROL My Account]**&#x200B;页面打开，但未下订单。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
