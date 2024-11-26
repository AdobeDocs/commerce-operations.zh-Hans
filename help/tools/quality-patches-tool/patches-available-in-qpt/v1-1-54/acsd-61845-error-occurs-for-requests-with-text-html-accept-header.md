---
title: “ACSD-61845：带有text/html接受标头的请求出错”
description: 应用ACSD-61845修补程序以修复Adobe Commerce问题，该问题导致发送仅带有*text/html*接受标头的HTTP请求时出现500错误，并安装B2B模块。
feature: B2B
role: Admin, Developer
source-git-commit: 8dbf91806097281fb4f7c74e182f10b09b18e925
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-61845：使用&#x200B;*text/html*&#x200B;接受标头的请求出错

ACSD-61845修补程序修复了仅具有&#x200B;*text/html*&#x200B;接受标头的HTTP请求因响应处理中的媒体类型不匹配而导致500错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54时，此修补程序可用。 修补程序ID为ACSD-61845。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7-p1 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

发送在接受标头中仅具有&#x200B;*text/html*&#x200B;的HTTP请求时，由于媒体类型配置不匹配，出现500错误。

<u>先决条件</u>：

B2B模块已安装和启用。

<u>重现步骤</u>：

1. 按如下所示发送请求，接受标头中只包含&#x200B;*text/html*：

   ```
   curl -I --header "Accept: text/html, text/plain" http://<hostname>/pub/
   ```

<u>预期的结果</u>：

返回带有&#x200B;*200状态代码*&#x200B;的页面。

<u>实际结果</u>：

返回了500错误，`exception.log`中带有以下错误消息：

```
Magento\Framework\Webapi\Exception: Server cannot match any of the given Accept HTTP header media type(s) from the request: "text/html" with media types from the config of response renderer. in vendor/magento/framework/Webapi/Rest/Response/RendererFactory.php:84
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

[[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。