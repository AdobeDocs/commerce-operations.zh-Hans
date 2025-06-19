---
title: ACSD-52160：根据购物车价格规则得出的产品验证结果
description: 应用ACSD-52160修补程序以修复Adobe Commerce问题，该问题导致根据购物车价格规则的产品验证结果未根据规则条件*[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*进行正确评估。
exl-id: 8f8799c9-850a-4c8f-bde4-68df64e46c85
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52160：未正确评估购物车价格规则的产品验证结果

ACSD-52160修补程序修复了基于规则条件&#x200B;*[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*&#x200B;未正确评估购物车价格规则的产品验证结果的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34时，此修补程序可用。 修补程序ID为ACSD-52160。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

未根据规则条件&#x200B;*[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*&#x200B;正确评估购物车价格规则的产品验证结果。

<u>重现步骤</u>：

1. 创建分配给两个不同类别的两个产品。
1. 创建&#x200B;**[!UICONTROL Cart Price Rule]**，其条件如下：

   * *[!UICONTROL FOUND]*&#x200B;参数中的&#x200B;**SKU 1**
   * *[!UICONTROL NOT FOUND]*&#x200B;参数中的&#x200B;**SKU 2**

1. 将两个产品都添加到购物车。
1. 应用优惠券代码。

<u>预期的结果</u>

不应用优惠券代码，因为购物车包含来自受限类别的产品。

<u>实际结果</u>

将应用优惠券代码。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)。
