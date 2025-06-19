---
title: ACSD-61522：*名字和姓氏*字段中的电子邮件地址会发送无效的订单确认
description: 应用ACSD-61522修补程序以修复Adobe Commerce问题，该问题导致有可能在来宾客户的*[!UICONTROL First Name]*和*[!UICONTROL Last Name]*字段中输入电子邮件地址，从而导致发送无效的订单确认电子邮件。
feature: Checkout, Customers
role: Admin, Developer
exl-id: e1ed7a57-4054-44db-bc17-9b9056096fce
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-61522： *名字和姓氏*&#x200B;字段中的电子邮件地址会发送无效的订单确认

ACSD-61522修补程序修复了在来宾客户的&#x200B;*[!UICONTROL First Name]*&#x200B;和&#x200B;*[!UICONTROL Last Name]*&#x200B;字段中输入电子邮件地址而导致发送订单确认电子邮件无效的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54时，此修补程序可用。 修补程序ID为ACSD-61522。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p9

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

系统允许在来宾客户的&#x200B;*[!UICONTROL First Name]*&#x200B;和&#x200B;*[!UICONTROL Last Name]*&#x200B;字段中输入电子邮件地址，从而导致发送无效的订单确认电子邮件。

<u>重现步骤</u>：

1. 将任何产品作为来宾客户添加到购物车。
1. 转到&#x200B;**[!UICONTROL Checkout]**。
1. 使用&#x200B;*test1@example.com*&#x200B;填充&#x200B;*[!UICONTROL Email Address]*&#x200B;字段。
1. 使用&#x200B;*<test2@example.com>*&#x200B;填充&#x200B;*[!UICONTROL First Name]*&#x200B;字段。
1. 用&#x200B;*<test3@example.com>*&#x200B;填充&#x200B;*[!UICONTROL Last Name]*。
1. 填写其他必填字段。
1. 下订单。

<u>预期的结果</u>：

无法在&#x200B;*[!UICONTROL First Name]*&#x200B;和&#x200B;*[!UICONTROL Last Name]*&#x200B;字段中使用电子邮件地址。

<u>实际结果</u>：

1. 下订单。
1. *[!UICONTROL First Name]*&#x200B;和&#x200B;*[!UICONTROL Last Name]*&#x200B;字段保存为已输入。
1. 订单确认电子邮件会发送到所有这三封电子邮件。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
