---
title: ACSD-45424：部分退款后创建的预订补偿不正确
description: ACSD-45424修补程序修复了在部分退款后创建不正确的预订补偿的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17后，即可使用此修补程序。 修补程序ID为ACSD-45424。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
feature: Orders
role: Admin
exl-id: 94435816-9f4a-40f9-be80-05836ed7781f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# ACSD-45424：部分退款后创建的预订补偿不正确

ACSD-45424修补程序修复了在部分退款后创建不正确的预订补偿的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17时，此修补程序可用。 修补程序ID为ACSD-45424。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.4 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在部分退款后创建错误的预订补偿。

<u>重现步骤</u>：

1. 启用店内交货配送方式。
1. 创建三个库存来源，并确保每个来源（来源1、来源2、来源3）中的提货地点均有效。
1. 创建新库存，并将三个来源分配给新库存。
   * 该库存应分配给主网站。
1. 创建一个简单产品P3，并将所有源分配给它。
1. 为简单产品的来源添加以下数量并启用延交订单：
   * 默认源 — 100
   * source1 - 0
   * source2 - 10
   * source3 - 0
1. 从前端将简单产品添加到购物车并继续发送表单。
1. 选择“source1”作为配送地点。
1. 完成顺序并在数据库中执行以下查询：

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   您将在`inventory_reservation`表中获取下单记录。 数量为10，这是正确的。
1. 从后端对此订单开票。
1. 现在，仅为一个产品创建贷项通知单。 请勿选中&#x200B;*返回至Stock*&#x200B;复选框。
1. 执行步骤8中的相同查询。

<u>预期的结果</u>：

如果您在创建贷项通知单期间未选择&#x200B;*返回至库存*，则`inventory_reservation`表将没有与贷项通知单对应的记录。

<u>实际结果</u>：

即使在贷项通知单创建期间未选择&#x200B;*返回股*，它仍会向事件类型为`creditmemo_created`的`inventory_reservation`表添加记录。 此外，即使您仅为一个数量创建了贷项通知单，添加到`inventory_reservation`表中的贷项通知单记录的数量仍为10。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
