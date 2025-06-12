---
title: ACSD-51666：错误“会话已过期，请重新登录。” 登录之后
description: 应用ACSD-51666修补程序以修复错误*会话已过期的Adobe Commerce问题，请重新登录。*在您尝试登录后发生。
feature: Customers
role: Admin, Developer
exl-id: 8968b314-6625-45fa-9733-20560cca7089
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# ACSD-51666：错误&#x200B;*会话已过期，请重新登录。登录后*

ACSD-51666修补程序修复了错误&#x200B;*会话已过期的问题，请重新登录。*&#x200B;在您尝试登录后发生。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.36时，此修补程序可用。 修补程序ID为ACSD-51666。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

您收到错误&#x200B;*会话已过期，请重新登录。在另一台设备上重置密码后，尝试使用新密码从一台设备登录时出现*。 仅当自定义模块添加的页面上有其他Ajax请求时，才会发生这种情况。

<u>重现步骤</u>：

1. 安装自定义模块，在店面的每个页面上添加一个Ajax请求。
1. 创建新帐户。
1. 注销并返回登录页面。
1. 在其他浏览器中打开&#x200B;*忘记密码*&#x200B;链接，并发送&#x200B;*重置密码*&#x200B;电子邮件。
1. 在第一个浏览器中打开重置密码电子邮件并设置新密码。
1. 尝试在第二个浏览器中登录。

<u>预期的结果</u>：

第一次尝试时您能够成功登录。

<u>实际结果</u>：

* 您看到&#x200B;*会话已过期，请重新登录。*&#x200B;错误。
* 您未登录并重定向到主页。
* 第二次登录尝试成功。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
