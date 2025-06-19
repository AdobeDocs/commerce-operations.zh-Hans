---
title: ACSD-66093：来宾客户名称字段允许输入电子邮件，从而导致订单电子邮件无效
description: 应用ACSD-66093修补程序以修复Adobe Commerce问题，该问题导致有可能在来宾客户**[!UICONTROL First Name]**和**[!UICONTROL Last Name]**字段中输入电子邮件地址并发送无效的订单确认电子邮件。
feature: Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 30790492-330e-4810-8069-fce87b40ebb2
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-66093：来宾客户名称字段允许输入电子邮件，从而导致订单电子邮件无效

ACSD-66093修补程序修复了在来宾客户的&#x200B;**[!UICONTROL First Name]**&#x200B;和&#x200B;**[!UICONTROL Last Name]**&#x200B;字段中输入电子邮件地址而导致订单确认电子邮件无效的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65时，此修补程序可用。 修补程序ID为ACSD-66093。 请注意，Adobe Commerce 2.4.8中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p11

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

电子邮件地址可输入到来宾客户的&#x200B;**[!UICONTROL First Name]**&#x200B;和&#x200B;**[!UICONTROL Last Name]**&#x200B;字段中，这会导致订单确认电子邮件无效。

<u>重现步骤</u>：

1. 将产品作为来宾客户添加到购物车。
2. 去结帐。
3. 在电子邮件地址中填写“test1@gmail.co”。
4. 用“<test2@gmail.co>”填充&#x200B;**[!UICONTROL First Name]**。
5. 用“<test3@gmail.co>”填充&#x200B;**[!UICONTROL Last Name]**。
6. 填写其他必填字段。
7. 下单。

<u>预期的结果</u>：

将显示验证消息，指示&#x200B;**[!UICONTROL First Name]**&#x200B;和&#x200B;**[!UICONTROL Last Name]**&#x200B;字段无效，如&#x200B;*名字无效！ 姓氏无效！*，不应下订单。

<u>实际结果</u>：

已下订单。
**[!UICONTROL First Name]**&#x200B;和&#x200B;**[!UICONTROL Last Name]**字段保存为已输入。
订单确认电子邮件会发送到所有这三封电子邮件：test1@gmail.co、test2@gmail.co和test3@gmail.co。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
