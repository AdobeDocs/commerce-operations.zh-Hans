---
title: ACSD-51636：公司管理员无法从客户帐户部分添加新用户
description: 应用ACSD-51636修补程序以修复Adobe Commerce问题，该问题导致公司管理员无法从客户帐户部分添加新用户，尽管他们拥有所有必要的角色和权限。
feature: Admin Workspace, B2B, Companies, Customer Service
role: Admin
exl-id: 46e79ae3-ea24-4cb2-b06e-e82cec33b16c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-51636：公司管理员无法从客户帐户部分添加新用户

ACSD-51636修补程序修复了以下问题：公司管理员无法从客户帐户部分添加新用户，尽管他们拥有所有必要的角色和权限。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34时，此修补程序可用。 修补程序ID为ACSD-51636。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

尽管公司管理员拥有所有必要的角色和权限，但仍无法从客户帐户部分添加新用户。

先决条件：

* B2B模块已安装。
* 已启用公司功能。

<u>重现步骤</u>：

1. 创建新公司。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**。
1. 编辑&#x200B;*客户*&#x200B;的&#x200B;**[!UICONTROL Company Admin]**&#x200B;类型。
1. 以客户身份登录。
1. 转到&#x200B;**[!UICONTROL My Account]** > **[!UICONTROL Company Users]** > **[!UICONTROL Add User]**&#x200B;并添加用户的详细信息并将其激活。
1. 保存新用户。

<u>预期的结果</u>

管理员用户能够添加新用户。

<u>实际结果</u>

* 管理员用户收到错误消息： *出现错误*。
* 管理员用户无法创建新客户。
* 日志包含以下错误：

  ```PHP
      report.CRITICAL: Error: Call to a member function __toArray() on null in app/code/Magento/LoginAsCustomerLogging/Observer/LogSaveCustomerObserver.php:123
  ```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)。
