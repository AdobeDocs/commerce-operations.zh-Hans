---
title: AC-14985：使用TLS发送SMTP电子邮件时出错
description: 应用AC-14985修补程序以修复在使用传输层安全性(TLS)发送简单邮件传输协议(SMTP)电子邮件时出现错误的Adobe Commerce问题。
feature: Configuration
role: Admin, Developer
type: Troubleshooting
source-git-commit: ed50e166c1fd34f5c19066297008cd74f36ccaaa
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# AC-14985：使用TLS发送SMTP电子邮件时出错

AC-14985修补程序修复了在使用传输层安全性(TLS)发送简单邮件传输协议(SMTP)电子邮件时出现错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67时，此修补程序可用。 修补程序ID为AC-14985。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过启用了TLS的SMTP发送电子邮件时出现错误。

<u>重现步骤</u>：

1. 按如下方式设置SMTP配置：
* 传输： SMTP
* 主机：url.to.smtp.host
* 端口：587
* SSL： TLS

<u>预期的结果</u>：

成功发送电子邮件，且未出现错误。

<u>实际结果</u>：

出现以下错误：

```
error:1408F10B:SSL routines:ssl3_get_record:wrong version number [] []
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
