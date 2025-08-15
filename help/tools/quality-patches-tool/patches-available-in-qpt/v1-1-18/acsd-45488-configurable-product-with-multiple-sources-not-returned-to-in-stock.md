---
title: ACSD-45488：具有多个来源的可配置产品不会自动退货
description: ACSD-45488修补程序解决了具有多个来源的可配置产品无法自动退订的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18后，即可使用此修补程序。 修补程序ID为ACSD-45488。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
feature: Configuration, Orders, Products, Returns
role: Admin
exl-id: 53f34e8e-00bd-4386-bebf-b15882e36da1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-45488：具有多个来源的可配置产品不会自动退货

ACSD-45488修补程序解决了具有多个来源的可配置产品无法自动退订的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18时，此修补程序可用。 修补程序ID为ACSD-45488。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

具有多个来源的可配置产品不会自动返回到库存中。

<u>重现步骤</u>：

1. 创建辅助库存来源。
1. 创建具有两个关联虚拟产品的可配置产品。
1. 将关联产品分配给默认库存来源，并将数量设置为1。
1. 检查`stock_status`中的`cataloginventory_stock_status`。
1. 将两个关联产品都设置为&#x200B;*缺货*。
1. 检查`stock_status`中的`cataloginventory_stock_status`。
1. 将两个关联产品设置为&#x200B;*库存*。
1. 检查`stock_status`中的`cataloginventory_stock_status`。

<u>预期的结果</u>：

当关联产品设置为有库存时，可配置产品的库存状态将更新为&#x200B;*库存*。

<u>实际结果</u>：

当关联产品设置为有库存时，可配置产品的库存状态未更新为&#x200B;*库存*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的Quality Patches Tool[!DNL Quality Patches Tool]，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
