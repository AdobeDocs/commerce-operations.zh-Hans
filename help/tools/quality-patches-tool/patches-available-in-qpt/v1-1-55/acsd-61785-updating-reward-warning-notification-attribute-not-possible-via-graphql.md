---
title: ACSD-61785：无法通过GraphQL突变和REST API调用更新reward_warning_notification属性
description: 应用ACSD-61785修补程序以修复无法通过Adobe Commerce突变和REST API调用更新“reward_warning_notification”属性的GraphQL问题。
feature: REST, GraphQL, Rewards
role: Admin, Developer
source-git-commit: 87ce6004a632f860447d55c13c08f78533ab093e
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61785：无法通过GraphQL突变和REST API调用更新reward_warning_notification属性

ACSD-61785修补程序修复了无法通过GraphQL突变和REST API调用更新`reward_warning_notification`属性的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55时，此修补程序可用。 修补程序ID为ACSD-61785。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.7-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

无法通过GraphQL突变和REST API调用更新`reward_warning_notification`属性。

<u>重现步骤</u>：

1. 查看&#x200B;*的GraphQL和REST API架构/文档*&#x200B;订阅余额更新&#x200B;*订阅积分到期通知*。

<u>预期的结果</u>：

可以通过GraphQL和REST API订阅&#x200B;*奖励余额更新*&#x200B;和&#x200B;*点到期通知*。

<u>实际结果</u>：

GraphQL和REST API缺少此功能。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
