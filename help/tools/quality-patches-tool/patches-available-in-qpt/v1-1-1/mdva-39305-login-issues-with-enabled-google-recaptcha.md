---
title: MDVA-39305：启用了Google reCAPTCHA的登录问题
description: 应用MDVA-39305修补程序以修复在启用Adobe Commerce reCAPTCHA后注册客户无法登录的Google问题。
feature: Console
role: Admin
exl-id: c40fd84a-73dc-42bd-8cda-58738615fbba
source-git-commit: 007fcb1308ba2c5b42755ee4c4c2ca598eb0e62e
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-39305：启用了Google reCAPTCHA的登录问题

>[!NOTE]
>
>此修补程序已更新，最新的修补程序ID为MDVA-39305-V3。 新修补程序是为Adobe Commerce版本2.4.4、2.4.5-p2和2.4.7创建的。有关详细信息，请参阅[MDVA-39305-V3](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/mdva-39305-v3-login-issue-with-enabled-google-recaptcha)修补程序文章。

MDVA-39305修补程序修复了启用Google reCAPTCHA后，已注册客户无法登录的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.1时，此修补程序可用。 修补程序ID为MDVA-39305。 请注意，Adobe Commerce版本2.4.4和2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云基础架构上的Adobe Commerce 2.4.2-p1、2.4.3-p3、2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1-p1 - 2.4.3-p3、2.4.4-p1 - 2.4.4-p5、2.4.5 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

注册客户无法使用启用的Google reCAPTCHA登录。

<u>重现步骤</u>：

1. 转到&#x200B;**存储** > **配置** > **安全性** > **Google reCAPTCHA存储**&#x200B;并启用&#x200B;**Google reCAPTCHA**。
1. 转到&#x200B;**前端**。
1. 在浏览器中打开&#x200B;**开发人员工具控制台**。

<u>预期的结果</u>：

控制台中没有CSP警告。

<u>实际结果</u>：

控制台中出现CSP警告。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
