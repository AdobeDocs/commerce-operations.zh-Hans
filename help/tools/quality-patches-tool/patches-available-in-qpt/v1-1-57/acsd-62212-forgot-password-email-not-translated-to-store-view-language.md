---
title: ACSD-62212： [!UICONTROL Forgot Password]电子邮件未翻译为存储视图语言
description: 应用ACSD-62212修补程序以修复Adobe Commerce问题，该问题导致*[!UICONTROL Forgot Password]*电子邮件的内容未翻译成商店视图的语言。
feature: GraphQL
role: Admin, Developer
exl-id: 29e6f2fa-574f-4ab1-82f5-88e1eb1de83e
source-git-commit: 8f39f7838d5c98a1dcc584edf766393012ec8820
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-62212： *[!UICONTROL Forgot Password]*&#x200B;电子邮件未翻译为存储视图语言

ACSD-62212修补程序修复了&#x200B;*[!UICONTROL Forgot Password]*&#x200B;电子邮件的内容未翻译为商店视图语言的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57时，此修补程序可用。 修补程序ID为ACSD-62212。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在注册商店视图以外的商店视图中通过GraphQL重置密码时，重置密码链接与从中启动它的商店视图不匹配。

<u>重现步骤</u>：

1. 在&#x200B;*[!UICONTROL Main Website Store]*&#x200B;下创建辅助存储视图。
1. 在辅助存储视图作用域中将&#x200B;*[!UICONTROL Locale]*&#x200B;切换为&#x200B;*[!UICONTROL French (France)]*。
1. 安装法语语言包以进行翻译。
1. 创建客户帐户。
1. 将以下GraphQL突变与&#x200B;*存储*&#x200B;标头配合使用辅助存储视图代码。

   ```
   mutation {
       requestPasswordResetEmail(
           email: "test@gmail.com"
       )
   }
   ```

1. 检查电子邮件。

<u>预期的结果</u>：

* 电子邮件主题、链接及其内容的语言与商店视图区域设置一致。
* 无论请求中的商店标头如何，密码重置请求都会从客户帐户实际注册的商店发送。

<u>实际结果</u>：

在电子邮件中可能会看到以下内容：

* 重置密码链接具有“默认”存储代码。
* 这个题目是英文的。
* 内容为法语。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
