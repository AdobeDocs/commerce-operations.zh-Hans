---
title: MDVA-40609： cataloginventory_stock_status表中缺少已禁用的产品数据
description: MDVA-40609修补程序解决了禁用产品数据未显示在“cataloginventory_stock_status”索引表中，从而导致显示错误产品数量的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6后，即可使用此修补程序。 修补程序ID为MDVA-40609。 请注意，Adobe Commerce 2.4.3中已修复此问题。
feature: Catalog Management, Inventory, Orders, Products
role: Admin
exl-id: e207ee55-b6ce-4065-bae1-2be89dcf5092
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# MDVA-40609： cataloginventory_stock_status表中缺少已禁用的产品数据

MDVA-40609修补程序解决了`cataloginventory_stock_status`索引表中未显示禁用产品数据，从而导致显示错误产品数量的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6后，即可使用此修补程序。 修补程序ID为MDVA-40609。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

已禁用的产品数据未显示在`cataloginventory_stock_status`索引表中，导致显示不正确的产品数量。

<u>先决条件</u>：

清单模块已安装。

<u>重现步骤</u>：

1. 设置两个网站，分别包含商店和商店视图。
1. 创建附加源和库存。
1. 添加简单的产品：
   * 将“启用产品”设置为&#x200B;*否*。
   * 分配两个来源，Source物料状态= Instock和数量大于零。
1. 保存产品。
1. 检查&#x200B;**产品可销售数量**&#x200B;选项卡。

<u>预期的结果</u>：

两个股票输入的值都大于零。

<u>实际结果</u>：

一种股票的价值为零。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修补程序部分。
