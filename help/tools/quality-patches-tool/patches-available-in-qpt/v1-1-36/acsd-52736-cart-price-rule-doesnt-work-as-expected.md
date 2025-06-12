---
title: ACSD-52736： [!UICONTROL Cart Price Rule]无法按预期工作
description: 应用ACSD-52736修补程序以修复Adobe Commerce问题，该问题导致包含可配置产品数量要求的[!UICONTROL Cart Price Rule]无法按预期工作。
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 80c3b14e-62ce-4cfc-b1ff-968e70e3a6f8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-52736： [!UICONTROL Cart Price Rule]无法按预期工作

ACSD-52736修补程序修复了包含可配置产品数量要求的[!UICONTROL Cart Price Rule]无法按预期工作的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.36时，此修补程序可用。 修补程序ID为ACSD-52736。 请注意，Adobe Commerce 2.4.6中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

包含可配置产品数量要求的[!UICONTROL Cart Price Rule]无法按预期工作。

<u>重现步骤</u>：

1. 创建购物车规则：
   * [!UICONTROL Apply] =产品价格折扣百分比
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * 仅将规则应用于符合以下条件的购物车项目：购物车中的数量为1
2. 将具有[!UICONTROL Qty] = 2的产品添加到购物车。
3. 检查购物车价格。

<u>预期的结果</u>：

未应用该规则，因为购物车中的产品数量为&#x200B;*2*。

<u>实际结果</u>：

将应用折扣。

<u>安装修补程序后所需的其他步骤</u>：

应用修补程序后，必须删除使用&#x200B;*Quantity*&#x200B;属性的购物车规则条件，然后重新添加。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
