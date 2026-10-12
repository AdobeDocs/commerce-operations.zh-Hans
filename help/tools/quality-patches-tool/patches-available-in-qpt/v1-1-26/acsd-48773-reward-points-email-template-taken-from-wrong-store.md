---
title: ACSD-48773：从错误的商店获取的奖励积分电子邮件模板
description: 应用ACSD-48773修补程序以修复从错误商店获取奖励点电子邮件模板的Adobe Commerce问题。
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
exl-id: db8b6196-3e13-4c1b-8ae8-040487180817
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: 4069cee6-4dc8-5a83-81de-232af6a7c9e9
    internal-label: Rewards
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
source-wordcount: '482'
ht-degree: 0%
---
# ACSD-48773：从错误的商店获取的奖励积分电子邮件模板

ACSD-48773修补程序修复了从错误的商店获取奖励点电子邮件模板的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.26时，此修补程序可用。 修补程序ID为ACSD-48773。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果捆绑产品未分配给任何网站，则产品价格重新索引不起作用。

<u>重现步骤</u>：

1. 创建2个网站、2个商店和2个商店视图。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]**&#x200B;并启用&#x200B;**[!UICONTROL Reviews]**。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]**。
切换到&#x200B;**[!DNL default website scope]**&#x200B;并设置&#x200B;**[!UICONTROL Customer Support Sender Email]**&#x200B;地址（例如： *support_base@example.com*）。
切换到&#x200B;**[!DNL second website scope]**，并将&#x200B;**[!UICONTROL Customer Support Sender Email]**&#x200B;地址设置为另一个值（例如： *support_second@example.com*）。
1. 前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]**，并为每个网站设置&#x200B;**[!UICONTROL Share Customer Accounts]** = **。
1. 在&#x200B;**[!UICONTROL Reward Points]**&#x200B;下，设置以下内容：
   **[!UICONTROL Enable Reward Points Functionality]** = *是*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *是*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]**&#x200B;并设置&#x200B;**[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]**&#x200B;并设置&#x200B;**[!UICONTROL Email Sender]** = *客户支持*
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]**，并为&#x200B;**[!UICONTROL Points/Currency]**&#x200B;和&#x200B;**[!UICONTROL Currency/Points]**&#x200B;设置第二个网站的汇率。
1. 在第二个网站上创建客户帐户。
1. 以客户身份登录第二个网站。
1. 确保为&#x200B;**[!UICONTROL Balance Updates]**&#x200B;启用&#x200B;**[!UICONTROL Subscribe]**。
1. 提交产品评论。
1. 转到&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]**。
1. 将新审阅的状态更改为&#x200B;***[!UICONTROL Approved]***&#x200B;和&#x200B;**[!UICONTROL Save]**。
1. 等待电子邮件到达。

<u>预期的结果</u>：

奖励积分更新电子邮件应由在第二个网站范围上配置的电子邮件发件人发送。

<u>实际结果</u>：

奖励积分更新电子邮件是由在默认网站范围上配置的电子邮件发件人发送的。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
