---
title: “ACSD-60816： [!DNL New Relic] 由APM代理插入的浏览器监视脚本与CSP不兼容”
description: 应用ACSD-60816修补程序以修复Adobe Commerce问题，该问题导致APM代理插入的 [!DNL New Relic] 浏览器监视脚本与内容安全策略(CSP)不兼容，从而无法执行。
feature: Tools and External Services, Checkout
role: Admin, Developer
source-git-commit: 278cc668a9d6746a38845e54d173260e1a65bb22
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-60816： APM代理插入的[!DNL New Relic]浏览器监视脚本与CSP不兼容

ACSD-60816修补程序修复了APM代理插入的[!DNL New Relic]浏览器监视脚本与内容安全策略(CSP)不兼容的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51时，此修补程序可用。 修补程序ID为ACSD-60816。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.6-p6

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

APM代理插入的[!DNL New Relic]浏览器监视脚本与CSP不兼容。

<u>重现步骤</u>：

1. 将产品添加到购物车。
1. 去结帐。

<u>预期的结果</u>：

开发人员控制台中没有CSP错误。

<u>实际结果</u>：

您会收到以下错误：

```
Content-Security-Policy: The page's settings blocked an inline script (script-src-elem) from being executed because it violates the following directive: "script-src 
...
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
