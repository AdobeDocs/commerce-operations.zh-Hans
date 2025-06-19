---
title: ACSD-48570：修复了URL中的存储代码存在的管理员重置密码链接问题
description: 应用ACSD-48570修补程序以修复启用[!UICONTROL Add Store Code to URLs]配置时无法通过管理员重置密码链接访问重置密码页面的Adobe Commerce问题。
feature: Security, User Account
role: Admin, Developer
exl-id: 049a82ff-80e3-46a1-8472-ac74de0e365f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48570：修复了URL中的存储代码存在的管理员重置密码链接问题

ACSD-48570修补程序，用于修复启用&#x200B;*[!UICONTROL Add Store Code to URLs]*&#x200B;配置时无法通过管理员重置密码链接访问“重置密码”页面的Adobe Commerce问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58时，此修补程序可用。 修补程序ID为ACSD-48570。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

启用&#x200B;**[!UICONTROL Add Store Code to URLs]**&#x200B;设置后，管理员重置密码功能无法正常工作。
在管理员用户请求重置密码并单击电子邮件中的恢复链接后，他们将被重定向到登录页面或收到404错误，而不是被带入重置密码表单。 这可以防止管理员无需手动干预即可恢复其帐户。

<u>重现步骤</u>：

1. 在&#x200B;**[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL URL Options]**&#x200B;处启用&#x200B;**[!UICONTROL Add Store Code to URLs]**&#x200B;配置。
1. 从管理员面板注销，然后单击管理员登录页面上的&#x200B;**[!UICONTROL Forgot your password?]**&#x200B;链接。
1. 输入管理员用户的电子邮件，传递验证码，然后单击&#x200B;**[!UICONTROL Retrieve Password]**。
1. 打开密码重置电子邮件并单击密码恢复链接。

<u>预期的结果</u>：

应显示重置密码表单。

<u>实际结果</u>：

此时将显示登录页面或404错误页面，而不是重置密码表单。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
