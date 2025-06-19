---
title: ACSD-65195：对于没有所需区域的国家/地区，GraphQL“createCompany”突变会返回错误
description: 应用ACSD-65195修补程序以修复Adobe Commerce问题，该问题导致GraphQL“createCompany”突变向不需要地区的国家/地区引发错误。
feature: B2B, Companies, GraphQL
role: Admin, Developer
exl-id: b9eed00c-26f2-47fe-b1a0-6b020527f0c1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-65195：对于没有所需区域的国家/地区，GraphQL `createCompany`突变返回错误

ACSD-65195修补程序修复了[!UICONTROL GraphQL] `createCompany`突变向不需要区域的国家/地区引发错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63时，此修补程序可用。 修补程序ID为ACSD-65195。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p9、2.4.7 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在为不需要区域的国家指定区域时，[!UICONTROL GraphQL] `createCompany`突变返回错误。

<u>重现步骤</u>：

1. 启用&#x200B;**[!UICONTROL B2B Companies]**。
1. 为不需要区域字段的国家/地区发送具有指定区域字段的`createCompany` [!UICONTROL GraphQL]突变。 例如：[!UICONTROL country_id]：*AE*&#x200B;和[!UICONTROL region]：*迪拜*。
1. 检查GraphQL响应。

<u>预期的结果</u>：

在为不需要区域的国家指定区域时，公司应该成功创建并且不会返回错误。

<u>实际结果</u>：

不会创建公司，并返回以下错误：
`Error: Invalid value of "Dubai" provided for the region field.`

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的升级和修补程序>应用修补程序。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
