---
title: ACSD-54026：updateCompanyRole GraphQL请求的错误消息不正确
description: 应用ACSD-54026修补程序以修复Adobe Commerce问题，该问题导致非授权用户的updateCompanyRole GraphQL请求出现不正确的错误消息。
feature: Roles/Permissions
role: Admin, Developer
exl-id: 21695333-5f18-48db-acde-246f269dd691
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-54026： `updateCompanyRole` GraphQL请求的错误消息不正确

ACSD-54026修补程序修复了以下问题：针对非授权用户的`updateCompanyRole` GraphQL请求存在不正确的错误消息。 安装[!DNL Quality Patches Tool (QPT)] 1.1.39时，此修补程序可用。 修补程序ID为ACSD-54026。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

为非授权用户获取`updateCompanyRole` GraphQL请求的不正确错误消息。

<u>重现步骤</u>：

1. 在配置中启用B2B公司。
1. 创建公司。
1. 在不传递持有者令牌或持有者令牌无效的情况下发送`updateCompanyRole`个GraphQL请求。
1. 观察GraphQL响应中的错误消息。

<u>预期的结果</u>：

您收到以下错误消息： *当前客户未获得授权。*

<u>实际结果</u>：

您收到以下错误消息：*客户不是公司用户。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
