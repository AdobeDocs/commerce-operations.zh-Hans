---
title: MDVA-39305-V3：已启用 [!DNL Google reCAPTCHA]的登录问题
description: 应用MDVA-39305-V3修补程序以修复在启用 [!DNL Google reCAPTCHA] 后注册客户无法登录的Adobe Commerce问题。 此修补程序还修复了在 [!DNL Google reCAPTCHA] 完全加载之前提交表单的问题。 此外，它还修复了以下错误*在CMS页面的非默认位置中使用块时，在null*上调用成员函数isDisabled() 。
feature: Console
role: Admin
source-git-commit: 7846079987d2b7c0e9fdd0485bb3aae4f09cd6f9
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-39305-V3：已启用[!DNL Google reCAPTCHA]的登录问题

>[!NOTE]
>
>此修补程序是[MDVA-39305](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-1/mdva-39305-login-issues-with-enabled-google-recaptcha.md)修补程序的更新。

MDVA-39305-V3修补程序修复了在启用[!DNL Google reCAPTCHA]时注册客户无法登录的问题。 此修补程序还修复了在[!DNL Google reCAPTCHA]完全加载之前提交表单的问题。 此外，它修复了在CMS页面的非默认位置中使用块时，在null *上调用成员函数isDisabled()时出现的错误*。

此修补程序已添加到[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48版本中。 QPT 1.1.58版本中更新了该版本，以包含新的Adobe Commerce版本2.4.7 - 2.4.7 - p4。 修补程序ID为MDVA-39305-V3。 请注意，Adobe Commerce版本2.4.4、2.4.5-p2和2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4、2.4.5-p2、2.4.7

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4-p1 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

### 案例I

1. 已注册客户无法使用启用的[!DNL Google reCAPTCHA]登录。
1. 表单可在[!DNL Google reCAPTCHA]完全加载之前提交。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]** > **[!DNL Google reCAPTCHA Storefront]**&#x200B;并启用&#x200B;***[!DNL Google reCAPTCHA]***。
1. 去前台。
1. 在浏览器中打开&#x200B;**[!UICONTROL Developer Tool Console]**。

<u>预期的结果</u>：

控制台中没有CSP警告。

<u>实际结果</u>：

控制台中出现CSP警告。

### 案例二

在CMS页面的非默认位置中使用块时，引发错误，说明&#x200B;*在null*&#x200B;上调用成员函数isDisabled()。

<u>重现步骤</u>：

1. 使用以下内容创建一个静态块：

   ```
   {{block class="Magento\Newsletter\Block\Subscribe" name="home.form.subscribe"
   template="Magento_Newsletter::subscribe.phtml"}}
   ```

1. 从&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Add/Edit CMS page]** > **[!UICONTROL Content]**&#x200B;向CMS页面添加静态块。
1. 保存页面。

<u>预期的结果</u>：

页面加载时没有出现错误。

<u>实际结果</u>：

店面的页面上出现500错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。


