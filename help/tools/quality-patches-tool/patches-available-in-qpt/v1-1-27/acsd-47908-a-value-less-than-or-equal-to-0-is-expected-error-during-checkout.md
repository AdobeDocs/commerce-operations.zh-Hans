---
title: ACSD-47908： *应为小于或等于0的值*结账过程中出错
description: 应用ACSD-47908修补程序以修复Adobe Commerce错误*在结帐期间在运输步骤中选择源和数量时，应提供一个小于或等于0的值*。
feature: Admin Workspace, Checkout, Orders
role: Admin
exl-id: f1429bd9-652d-43c0-af52-b2258e2a7643
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# ACSD-47908： *结账期间应出现小于或等于0的值*&#x200B;错误

ACSD-47908修补程序修复了错误&#x200B;*在结帐期间在送货步骤中选择源和数量时，应该有一个小于或等于0的值*。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27时，此修补程序可用。 修补程序ID为ACSD-47908。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在结帐期间选择送货步骤中的源和数量时，会引发以下错误： *应输入小于或等于0的值*。

<u>先决条件</u>：

安装Adobe Commerce Inventory management (MSI)模块。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]**&#x200B;并配置多个源。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]**&#x200B;并创建新库存。
   * 现在将源分配给新库存。
1. 转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;并编辑至少一个产品。
   * 确保将产品分配给新来源，并指定可用数量。
1. 转到&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Orders]**&#x200B;并创建新订单。
1. 将这些产品添加到订单中并下单。
1. 单击&#x200B;**[!UICONTROL Ship]**。
1. 选择要从中发运的来源。
1. 指定要发运的每个项目的数量。
1. 重新加载页面。
1. 单击&#x200B;**[!UICONTROL Proceed to Shipment]**。

<u>预期的结果</u>：

此时将打开新的装运页面，并且不会出现任何错误。

<u>实际结果</u>：

* 无法验证输入的数量。
* 引发以下错误： *请输入小于或等于0*&#x200B;的值。

  但是，该错误不一致，并且可能并不总是出现。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
