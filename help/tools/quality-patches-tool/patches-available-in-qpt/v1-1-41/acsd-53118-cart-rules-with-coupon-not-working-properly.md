---
title: ACSD-53118：包含优惠券的购物车规则无法正常工作
description: 应用ACSD-53118修补程序以修复Adobe Commerce问题：当购物车中的产品具有空的匹配属性时，使用优惠券代码应用购物车价格规则。
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 8957790e-c22b-4a25-939b-94d7a9fb1cc7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-53118：包含优惠券的购物车规则无法正常工作

ACSD-53118修补程序修复了以下问题：当购物车中的产品具有空的匹配属性时，使用优惠券代码应用购物车价格规则。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41时，此修补程序可用。 修补程序ID为ACSD-53118。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当购物车中的产品具有空的匹配属性时，使用优惠券代码应用购物车价格规则。

<u>重现步骤</u>：

1. 创建价格属性并将其添加到属性集。 使属性在促销规则条件中可用。
1. 创建产品并将新属性留空。
1. 创建具有特定优惠券和以下条件的购物车价格规则：

   * 如果在购物车中找到项目，且满足以下所有条件：属性1为0。

1. 将步骤2中创建的产品添加到购物车。
1. 为步骤3中创建的购物车规则使用优惠券代码。

<u>预期的结果</u>：

折扣不适用于购物车。

<u>实际结果</u>：

折扣适用于购物车。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
