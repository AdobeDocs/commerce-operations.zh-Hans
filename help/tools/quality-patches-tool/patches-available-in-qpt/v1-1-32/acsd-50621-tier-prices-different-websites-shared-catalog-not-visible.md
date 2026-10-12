---
title: ACSD-50621：共享目录中不同网站的分层价格不可见
description: 应用ACSD-50621修补程序以修复Adobe Commerce问题，该问题导致在多个网站环境中编辑共享目录中的不同网站时，无法看到这些网站的层价格。
feature: Catalog Management, Orders
role: Admin
exl-id: 2256dee7-e544-4723-9753-ba9cf7247880
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%
---
# ACSD-50621：共享目录中不同网站的分层价格不可见

ACSD-50621修补程序修复了在多网站环境中编辑共享目录中不同网站的层价格时不可见的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.32时，此修补程序可用。 修补程序ID为ACSD-50621。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在多网站环境中编辑共享目录中的不同网站时，不会显示这些网站的分层价格。

<u>重现步骤</u>：

1. 将&#x200B;**[!UICONTROL Catalog Price Scope]**&#x200B;设置为&#x200B;**[!UICONTROL Website]**。
1. 创建其他网站、商店和商店评论。
1. 创建一个简单的产品并将其分配给所有网站。
1. 创建自定义共享目录。
1. 转到您创建的自定义共享目录的&#x200B;**[!UICONTROL Set Pricing and Structure]**。
1. 在第1步中：为目录选择产品。 添加您创建的简单产品。
1. 在第2步中：设置自定义价格并单击&#x200B;**[!UICONTROL Configure]**。
1. 为不同的网站设置不同的层级价格。
1. 选择&#x200B;**[!UICONTROL Done]**&#x200B;并单击&#x200B;**[!UICONTROL Generate Catalog]**，然后单击&#x200B;**[!UICONTROL Save]**。
1. 运行cron。
1. 导航到&#x200B;**[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]**&#x200B;并验证层价格。

<u>预期的结果</u>：

以前为不同网站配置的所有层价格均存在。

<u>实际结果</u>：

先前配置的层价格不存在。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
