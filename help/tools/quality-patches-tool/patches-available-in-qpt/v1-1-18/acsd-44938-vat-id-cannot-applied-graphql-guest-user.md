---
title: ACSD-44938：无法在 [!DNL GraphQL] 来宾用户的请求中应用VAT_ID
description: ACSD-44938修补程序修复了无法在访客用户的 [!DNL GraphQL] 请求中应用“VAT_ID”的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18后，即可使用此修补程序。 修补程序ID为ACSD-44938。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
feature: Admin Workspace, GraphQL
role: Admin
exl-id: 62d36c27-545a-4c32-be69-a92e4b3ca2ca
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-44938：无法在[!DNL GraphQL]访客用户的请求中应用VAT_ID

ACSD-44938修补程序修复了无法在访客用户的[!DNL GraphQL]请求中应用`VAT_ID`的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18时，此修补程序可用。 修补程序ID为ACSD-44938。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

`VAT_ID`无法应用于[!DNL GraphQL]访客用户的请求。

<u>重现步骤</u>：

1. 按照开发人员文档的[[!DNL GraphQL] 教程](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/)中所述的步骤创建访客购物车。
1. 尝试使用[!DNL GraphQL]为来宾用户应用`VAT_ID`。

<u>预期的结果</u>：

`VAT_ID`的应用方式与注册客户的相同。 请参阅我们的开发人员文档中的[`createCustomerAddress`突变](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/create-address/)文章。

<u>实际结果</u>：

无法使用[!DNL GraphQL]将`VAT_ID`应用于来宾用户。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
