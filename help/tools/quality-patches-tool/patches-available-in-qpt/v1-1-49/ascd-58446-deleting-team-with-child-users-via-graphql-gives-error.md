---
title: ACSD-58446：通过GraphQL删除具有子用户或团队的团队时，会显示一条信息不明确的错误消息
description: 应用ACSD-58446修补程序以修复Adobe Commerce问题，该问题导致通过GraphQL删除具有子用户或团队的团队时，返回与UI不一致的消息性错误消息。
feature: GraphQL
role: Admin, Developer
exl-id: 943ab281-cc41-4b96-8a7c-fff8c074267c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-58446：通过GraphQL删除具有子用户或团队的团队时，会显示一条信息不明确的错误消息

ACSD-58446修补程序修复了Adobe Commerce的问题，该问题导致通过GraphQL删除具有子用户或团队的团队时，返回与UI不一致的消息性错误消息。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49时，此修补程序可用。 修补程序ID为ACSD-58446。 请注意，该问题计划在Adobe Commerce B2B 1.5.1中修复

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过GraphQL删除具有子用户或团队的团队会返回一条与UI不一致的无法提供信息的错误消息。

## 先决条件：

已安装Adobe Commerce B2B模块。

<u>重现步骤</u>：

1. 启用&#x200B;*[!UICONTROL Company]*&#x200B;功能。
1. 创建新的公司帐户。
1. 登录到&#x200B;**[!UICONTROL Admin]**&#x200B;并激活公司帐户。
1. 检查电子邮件并为新的公司帐户设置密码。
1. 为公司创建新团队。
1. 以公司用户身份登录店面，并为创建的团队添加新用户。
1. 登录到&#x200B;**[!UICONTROL Admin]**，禁用公司用户，然后设置&#x200B;*[!UICONTROL Customer Active]* = *否*
1. 确保通过GraphQL删除创建的团队。

   ```
   mutation {
     deleteCompanyTeam(
       id: "MQ=="
     ) {
       success
     }
   }
   ```

<u>预期的结果</u>：

返回与UI一致的信息性错误消息。

<u>实际结果</u>：

返回与UI不一致的通用内部服务器错误消息。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
