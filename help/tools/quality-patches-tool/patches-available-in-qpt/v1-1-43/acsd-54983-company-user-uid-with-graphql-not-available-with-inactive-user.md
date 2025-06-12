---
title: ACSD-54983：带GraphQL的公司用户UID不适用于非活动用户
description: 应用ACSD-54983修补程序以修复Adobe Commerce问题：当用户状态设置为不活动时，无法通过GraphQL请求获取公司用户UID。
feature: GraphQL
role: Admin, Developer
exl-id: b188270f-5454-41c9-8370-f4c396095297
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54983：带GraphQL的公司用户UID不适用于非活动用户

ACSD-54983修补程序修复了以下问题：当用户状态设置为不活动时，无法通过GraphQL请求获取公司用户UID。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43时，此修补程序可用。 修补程序ID为ACSD-54983。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当用户状态设置为不活动时，无法使用GraphQL请求获取公司用户UID。

<u>重现步骤</u>：

1. 创建具有管理员用户的公司。 例如，company@test.com。
1. 创建新客户。
1. 将新客户分配给公司。
1. 获取&#x200B;**[!UICONTROL company admin token]**。
1. 使用&#x200B;**[!UICONTROL company admin token]**&#x200B;获取公司结构。 请参阅我们的开发人员文档中的[返回公司结构](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure)。
1. 响应仅包含&#x200B;*ACTIVE*&#x200B;客户的ID。
1. 将公司用户更新为&#x200B;*非活动*。
1. 再次获取公司结构。

<u>预期的结果</u>：

可以将状态设置为不活动时，获取公司用户UID。

<u>实际结果</u>：

非活动客户不在列表中。 当状态设置为不活动时，无法获取公司用户UID。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
