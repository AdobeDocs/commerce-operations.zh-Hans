---
title: MDVA-39153：在管理员中重新排序时计算的折扣金额不正确
description: MDVA-39153修补程序修复了在管理员中重新排序期间折扣金额计算不正确的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8后，即可使用此修补程序。 修补程序ID为MDVA-39153。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
exl-id: e8fe58ca-1218-4e76-b5fb-c7f935029cd2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39153：在管理员中重新排序时计算的折扣金额不正确

MDVA-39153修补程序修复了在管理员中重新排序期间折扣金额计算不正确的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8时，此修补程序可用。 修补程序ID为MDVA-39153。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在管理员中重新排序期间折扣金额计算不正确。

<u>重现步骤</u>：

1. 转到&#x200B;**管理员** > **商店** > **配置** > **销售** > **税费**。
1. 打开购物车中显示税项的运输税。
1. 启用并配置表费率配送方式($15)。
1. 为内置税率（适用于CA）创建税则。
1. 创建购物车价格规则，并将固定的$5折扣应用于整个购物车和装运金额。
1. 将价格为$12的产品添加到购物车，然后转到购物车页面。
1. 将折扣应用到购物车。
1. 将“预计”部分中的配送方式设置为“统一费率”。
1. 继续结帐，直到完成审阅步骤（请勿下订单）。
1. 转到主页，然后返回购物车。
1. 将“估计”部分中的配送方式更改为“表费率”。

<u>预期的结果</u>：

折扣保持不变，为5美元。

<u>实际结果</u>：

折扣是6.31美元。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的Quality Patches Tool[!DNL Quality Patches Tool]，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)：搜索修补程序[!DNL Quality Patches Tool]。
