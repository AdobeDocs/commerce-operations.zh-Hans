---
title: MDVA-42645：管理员无法退还禁用商店点数的奖励积分
description: MDVA-42645修补程序解决了在禁用商店点数功能时，管理员无法退款奖励点数的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-42645。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
exl-id: 8053fcc7-d30c-424a-9494-df6e8630b095
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4069cee6-4dc8-5a83-81de-232af6a7c9e9
    internal-label: Rewards
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%
---
# MDVA-42645：管理员无法退还禁用商店点数的奖励积分

MDVA-42645修补程序解决了在禁用商店点数功能时，管理员无法退款奖励点数的问题。 安装[Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-42645。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果禁用商店点数功能，则管理员无法退款奖励积分。

<u>重现步骤</u>：

1. 创建一个简单的产品。
1. 创建新的客户帐户并添加一些奖励积分。
1. 通过转至&#x200B;**商店** >设置> **配置** > **客户** > **客户配置** > **商店点数选项**&#x200B;来禁用商店点数功能。
1. 以已分配奖励积分的客户身份登录。
1. 将产品添加到购物车并导航到结帐。
1. 使用支付部分的奖励点数下达订单。
1. 在管理员中打开订单并开具发票。
1. 单击&#x200B;**贷项通知单**&#x200B;链接以创建新的贷项通知单。
1. 勾选底部的“退款奖励积分”选项，然后单击“离线退款”****。

<u>预期的结果</u>：

* 已成功创建贷项通知单。
* 奖励积分已成功退款。

<u>实际结果</u>：

您收到以下错误消息： *您不能使用超过订单金额的商店积分。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
