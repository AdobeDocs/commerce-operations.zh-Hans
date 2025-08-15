---
title: MDVA-41061：从管理员保存产品时，库存状态将重置为可销售
description: MDVA-41061修补程序修复了在从管理员保存产品时，库存状态重置为可销售的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5后，即可使用此修补程序。 修补程序ID为MDVA-41061。 QPT 1.1.15中提供了最新的修补程序版本，带有MDVA-41061-V3修补程序ID。 请注意，Adobe Commerce 2.4.4中已修复该问题。
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: ddbc30ef-bc88-4878-8bd8-6880823819a2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-41061：从管理员保存产品时，库存状态将重置为可销售

MDVA-41061修补程序修复了在从管理员保存产品时，库存状态重置为可销售的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5时，此修补程序可用。 修补程序ID为MDVA-41061。 QPT 1.1.15中提供了最新的修补程序版本，带有MDVA-41061-V3修补程序ID。 请注意，Adobe Commerce 2.4.4中已修复该问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.2 - 2.4.2-p2、2.4.3 - 2.4.3-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

从管理员保存产品后，库存状态将重置为可销售。

<u>先决条件</u>：

清单模块已安装。

<u>重现步骤</u>：

1. 创建数量= 1的简单产品。
1. 使用在第1步中创建的产品下订单。
1. 运行cron — 确保已执行`inventory.reservations.updateSalabilityStatus`队列，并且`cataloginventory_stock_status`表中的产品库存状态已更改为零。
1. 检查前端产品。 它应标记为&#x200B;**缺货**。
1. 将产品保存在管理员中，不做任何更改。

<u>预期的结果</u>：

* 库存状态不应更新。
* 前端产品应为&#x200B;**缺货**。

<u>实际结果</u>：

* 简单产品在前端标记为&#x200B;**In Stock**。
* 用户收到&#x200B;*请求的数量不可用*&#x200B;消息（在尝试将其添加到购物车时）。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的Quality Patches Tool[!DNL Quality Patches Tool]，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)：搜索修补程序[!DNL Quality Patches Tool]。
