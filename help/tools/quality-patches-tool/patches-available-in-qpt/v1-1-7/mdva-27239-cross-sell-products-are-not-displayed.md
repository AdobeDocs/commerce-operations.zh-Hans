---
title: MDVA-27239：不显示交叉销售产品
description: MDVA-27239修补程序修复了未显示交叉销售产品的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7后，即可使用此修补程序。 请注意，Adobe Commerce 2.3.6中已修复此问题。
feature: Products
role: Admin
exl-id: ab8fe64d-adbe-4756-be43-1a35ba6b4123
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-27239：不显示交叉销售产品

MDVA-27239修补程序修复了未显示交叉销售产品的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7时，此修补程序可用。 请注意，Adobe Commerce 2.3.6中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法）2.3.4、2.4.0

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.0 - 2.3.5-p2、2.4.0 - 2.4.0-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

交叉销售产品不会显示在购物车页面的交叉销售块中。

<u>先决条件</u>：

1. 禁用Magento_TargetRule模块或从布局块Magento\TargetRule\Block\Checkout\Cart\Crosssell中删除。
1. 创建产品1。
1. 为产品1创建计划更新，以使新创建的产品的row_id不同于entity_id。
1. 创建产品2、产品3和产品4。
1. 将产品3设置为产品4的交叉销售。
1. 将产品4设置为产品2的交叉销售。

<u>重现步骤</u>：

1. 将产品4和产品2添加到购物车。
1. 检查购物车页面。

<u>预期的结果</u>：

产品3显示在交叉销售块中。

<u>实际结果</u>：

交叉销售区段为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
