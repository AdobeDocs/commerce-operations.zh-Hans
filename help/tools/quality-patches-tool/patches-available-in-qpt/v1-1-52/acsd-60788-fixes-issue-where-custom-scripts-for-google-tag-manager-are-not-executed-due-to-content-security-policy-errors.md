---
title: “ACSD-60788：由于CSP错误， [!DNL Google Tag Manager] 的自定义脚本未执行”
description: 应用ACSD-60788修补程序以修复由于内容安全策略(CSP)错误而无法执行 [!DNL Google Tag Manager] 的自定义脚本的Adobe Commerce问题。
feature: Security
role: Admin, Developer
source-git-commit: d1c643da36a200c6fb0a17139b12b6b91d9568e1
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-60788：由于内容安全策略错误，未执行[!DNL Google Tag Manager]的自定义脚本

ACSD-60788修补程序修复了由于内容安全策略错误而无法执行[!DNL Google Tag Manager]的自定义脚本的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52时，此修补程序可用。 修补程序ID为ACSD-60788。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.7-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

由于内容安全策略(CSP)错误，[!DNL Google Tag Manager]的自定义脚本未执行。

<u>重现步骤</u>：

1. 设置&#x200B;*[!DNL Google Tag Manager]*&#x200B;变量。
1. 设置&#x200B;*[!DNL Google Tag Manager]*&#x200B;自定义HTML标记。
1. 将以下JavaScript代码放置在第一个标记中：

   ```
   <script nonce="{{gtmNonce}}">
   console.log("Nonce from simple JS {{gtmNonce}}");
   </script>
   ```

1. 设置&#x200B;*GTM*&#x200B;后刷新缓存。
1. 在浏览器中打开开发人员控制台。
1. 打开主页。

<u>预期的结果</u>：

浏览器开发控制台显示来自简单JS的&#x200B;*Nonce（随机字符）*。

<u>实际结果</u>：

浏览器开发控制台显示&#x200B;*未定义简单JS中的* Nonce。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。