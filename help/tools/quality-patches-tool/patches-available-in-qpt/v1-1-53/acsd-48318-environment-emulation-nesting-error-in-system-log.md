---
title: “ACSD-48318：‘system.log’中出现环境模拟嵌套错误”
description: 应用ACSD-48318修补程序以修复Adobe Commerce问题，该问题导致每次发送发票电子邮件时都在“system.log”中显示错误消息*main.ERROR：不允许进行环境仿真嵌套*。
feature: System, Orders
role: Admin, Developer
source-git-commit: 94b68d18bc46065b5803a2eb88f0e844f71f0386
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-48318： `system.log`中的环境模拟嵌套错误

ACSD-48318修补程序修复了错误消息&#x200B;*main的问题。错误：每次发送发票电子邮件时，`system.log`中都会出现环境模拟嵌套*。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53时，此修补程序可用。 修补程序ID为ACSD-48318。 请注意，Adobe Commerce 2.4.7中已修复该问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

每次发送发票电子邮件时，`system.log`中都会显示错误消息&#x200B;*不允许环境模拟嵌套*。

<u>重现步骤</u>：

1. 下达订单并生成发票。
1. 从管理员处打开发票，然后单击&#x200B;**[!UICONTROL Send Email]**。
1. 单击&#x200B;**[!UICONTROL Send Email]**，对&#x200B;*贷项通知单*&#x200B;和&#x200B;*装运*&#x200B;执行相同的步骤。

<u>预期的结果</u>：

`system.log`中没有错误。

<u>实际结果</u>：

`system.log`被&#x200B;*main淹没。错误：不允许环境仿真嵌套*&#x200B;错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

[[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。