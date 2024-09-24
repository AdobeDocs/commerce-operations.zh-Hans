---
title: “ACSD-45241：虚拟产品的库存数量计算错误”
description: ACSD-45241修补程序修复了在创建贷项通知单后虚拟产品的库存数量计算错误的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17后，即可使用此修补程序。 修补程序ID为ACSD-45241。 请注意，Adobe Commerce 2.4.4中已修复此问题。
feature: Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# ACSD-45241：虚拟产品的库存数量计算错误

ACSD-45241修补程序修复了在创建贷项通知单后虚拟产品的库存数量计算错误的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17时，此修补程序可用。 修补程序ID为ACSD-45241。 请注意，Adobe Commerce 2.4.4中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.5 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

创建贷项通知单后，虚拟产品的库存数量计算错误。

<u>重现步骤</u>：

1. 在Commerce管理员中创建可配置产品，并将虚拟产品作为子产品。
1. 请确保在步骤1中创建的两个产品均有库存。
1. 将步骤1中创建的虚拟产品的数量标记为100，同时保留可销售数量100。
1. 将产品添加到购物车。
1. 使用在步骤1中创建的虚拟产品下订单。
1. 将订单状态保持为“待处理”。 无需处理付款。
1. 在`inventory_reservation`中创建了`order_created`记录。 虚拟产品数量显示为100，可销售数量为99。
1. 打开订单，然后转到&#x200B;**发票** > **提交发票**。
1. 在`inventory_reservation`中创建了`invoice_created`记录。 现在，虚拟产品数量为99，可销售数量也为99。
1. 创建贷项通知单，而不选择&#x200B;**返回至库存**。

<u>预期的结果</u>：

在`inventory_reservation`中未创建任何新记录，并且虚拟产品的库存数量保持不变。

<u>实际结果</u>：

在`inventory_reservation`中创建了`creditmemo_created`记录，虚拟产品库存数量已调整为98，可销售数量为99。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
