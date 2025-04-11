---
title: ACSD-64209： Cron计划程序检索可协商的报价而不排除[!UICONTROL Ordered]报价
description: 应用ACSD-64209修补程序以修复Adobe Commerce问题，该问题导致cron计划程序检索所有可协商的引号，但不排除状态为[!UICONTROL Ordered]的引号，从而触发电子邮件或电子邮件。
feature:  B2B, Communications
role: Admin, Developer
source-git-commit: 6fbe987dca81065071b611bfe0bfd0cb7baf1938
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-64209： Cron计划程序检索可协商的报价而不排除[!UICONTROL Ordered]报价

ACSD-64209修补程序修复了cron计划程序检索所有可协商引号而不排除状态为&#x200B;**[!UICONTROL Ordered]**&#x200B;的可协商引号导致触发电子邮件或电子邮件的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61时，此修补程序可用。 修补程序ID为ACSD-64209。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

cron计划程序检索所有可协商的报价单，但不排除状态为&#x200B;**[!UICONTROL Ordered]**&#x200B;的报价，从而导致触发电子邮件或电子邮件。

<u>重现步骤</u>：


1. 在&#x200B;*管理员*&#x200B;侧边栏中，转到&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]**&#x200B;并启用公司和B2B报价。
1. 在&#x200B;*管理员* > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]**&#x200B;中将&#x200B;**[!UICONTROL Default Expiration Period]**&#x200B;设置为&#x200B;*1*。
1. 创建并激活公司，然后以公司管理员身份登录。
1. 将产品添加到购物车。
1. 请求报价。
1. 在&#x200B;*管理员*&#x200B;侧边栏上，转到&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Quotes]**。
1. 选择已创建的报价，然后单击&#x200B;**[!UICONTROL Send]**&#x200B;以将报价发送回采购员。
1. 以公司管理员身份登录店面。
1. 选择报价并单击&#x200B;**[!UICONTROL Proceed to checkout]**&#x200B;以完成购买。
1. 检查报价的状态是否为&#x200B;**[!UICONTROL Ordered]**，店面中不会再有操作。
1. 触发`negotiable_quote_send_emails` cron作业。


<u>预期的结果</u>：

由于报价已下单，且无法执行进一步的操作，因此不应发送有关报价到期的电子邮件。

<u>实际结果</u>：

已发送电子邮件&#x200B;*报价即将过期*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
