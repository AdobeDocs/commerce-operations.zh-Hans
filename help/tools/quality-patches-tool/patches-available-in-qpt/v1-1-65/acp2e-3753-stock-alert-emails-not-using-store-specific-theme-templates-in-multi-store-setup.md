---
title: ACP2E-3753：库存警报电子邮件未在多商店设置中使用商店特定的主题模板
description: 应用ACP2E-3753修补程序以修复Adobe Commerce问题，该问题导致多商店设置中的产品警报电子邮件始终使用默认主题发送，而不管该商店或主题配置如何。
feature: Themes, Personalization
role: Admin, Developer
source-git-commit: 6af6dc5d4880cc0cb80c443cab98cfb562949101
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# ACP2E-3753：库存警报电子邮件未在多商店设置中使用商店特定的主题模板

ACP2E-3753修补程序修复了以下问题：多商店设置中的产品警报电子邮件始终使用默认主题发送，而不管该商店或主题配置如何。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65时，此修补程序可用。 修补程序ID为ACP2E-3753。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p11

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

多商店设置中的产品警报电子邮件始终使用默认主题发送，无论商店或主题配置如何。

<u>重现步骤</u>：

1. 创建两个网站、商店和商店视图。
1. 创建两个单独的主题，并将它们分配给不同的商店。
1. 产品警报设置是每分钟运行的默认范围。
1. 为两个主题覆盖/添加一些内容到`stock.phtml`文件。 文件位置示例：

   ```
   app\design\frontend\Adobe\Taiwan\Magento_ProductAlert\templates\email\stock.phtml
   app\design\frontend\Adobe\Japan\Magento_ProductAlert\templates\email\stock.phtml
   ```

1. 为每个商店创建用户并订阅产品库存警报。
1. 触发产品库存警报以发送电子邮件。

<u>预期的结果</u>：

电子邮件应包括主题级别的更改。

<u>实际结果</u>：

电子邮件不包括相应网站/商店中设置的模板。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
