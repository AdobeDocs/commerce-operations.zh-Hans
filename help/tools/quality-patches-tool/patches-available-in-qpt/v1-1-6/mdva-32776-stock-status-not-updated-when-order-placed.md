---
title: MDVA-32776：库存状态未随订单投放更新
description: MDVA-32776修补程序修复了在下订单但未发送时，库存状态未更新的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6后，即可使用此修补程序。 修补程序ID为MDVA-32776。 请注意，Adobe Commerce 2.4.2中已修复此问题。
feature: Orders
role: Admin
exl-id: 6f872c72-c96f-4c23-b6df-44e3da3a81c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-32776：库存状态未随订单投放更新

MDVA-32776修补程序修复了在下订单但未发送时，库存状态未更新的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6后，即可使用此修补程序。 修补程序ID为MDVA-32776。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.0

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

订购但未发运时，库存状态不会更新。

<u>先决条件</u>：

1. 清单模块已安装。
1. 显示缺货产品设置为&#x200B;*是*。

   若要进行设置，请转到&#x200B;**商店** > **配置** > **目录** > **库存** > **显示缺货产品** = *是*。

<u>重现步骤</u>：

1. 创建两个数量分别为11和22的简单产品。
1. 使用在第一步中创建的简单产品创建分组产品。
1. 通过将其中一个产品数量设置为11并使另一个简单产品缺货，将已分组的产品添加到购物车。
1. 完成结账并下订单。

<u>预期的结果</u>：

当关联的简单产品缺货时，分组的产品会显示`out-of-stock`标签。

<u>实际结果</u>：

1. 数量= 11的简单产品缺货。
1. 对于数量为11的产品，分组产品不显示&#x200B;*缺货*&#x200B;消息。 但是，将此产品添加到购物车会出现&#x200B;*缺货*&#x200B;错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的Quality Patches Tool[!DNL Quality Patches Tool]，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅QPT[中可用的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)修补程序部分。
