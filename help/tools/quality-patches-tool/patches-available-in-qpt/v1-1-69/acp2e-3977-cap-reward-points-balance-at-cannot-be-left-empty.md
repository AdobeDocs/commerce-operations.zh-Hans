---
title: ACP2E-3977：[!UICONTROL Cap Reward Points Balance At]字段不能留空
description: 应用ACP2E-3977修补程序以修复Adobe Commerce问题，该问题导致设置**[!UICONTROL Cap Reward Points Balance At]**字段时无法将**[!UICONTROL Rewards Points Balance Redemption Threshold]**字段留空，从而导致验证错误。
feature: Configuration, Rewards
role: Admin, Developer
type: Troubleshooting
exl-id: 5275911f-4f8c-4b37-af11-24ceb69406c9
source-git-commit: 83ce590c5078d70f0414276e2f03a71bdcdad321
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# ACP2E-3977：**[!UICONTROL Cap Reward Points Balance At]**&#x200B;字段不能留空

ACP2E-3977修补程序修复了&#x200B;**[!UICONTROL Cap Reward Points Balance At]**&#x200B;字段不能留空的问题，即使应允许字段留空也是如此。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69时，此修补程序可用。 修补程序ID为ACP2E-3977。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p10

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将&#x200B;**[!UICONTROL Cap Reward Points Balance At]**&#x200B;留空会触发验证错误，即使将其留空时应禁用上限。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward points]**。
1. 设置&#x200B;**[!UICONTROL Rewards Points Balance Redemption Threshold]** = *30*。
1. 将&#x200B;**[!UICONTROL Cap Reward Points Balance At]**&#x200B;留空。
1. 保存。

<u>预期的结果</u>：

**[!UICONTROL Cap Reward Points Balance At]**&#x200B;允许为空值，并禁用该限制。

<u>实际结果</u>：

*上限奖励积分余额无效。 余额必须为正数或留空。 验证并重试。显示*&#x200B;错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
