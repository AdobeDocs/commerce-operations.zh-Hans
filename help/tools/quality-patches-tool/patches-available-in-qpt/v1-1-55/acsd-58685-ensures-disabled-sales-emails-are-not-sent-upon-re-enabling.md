---
title: ACSD-58685：重新启用时会发送禁用的销售电子邮件
description: 应用ACSD-58685补丁以修复Adobe Commerce问题，该问题导致在禁用电子邮件通信时启动的销售电子邮件在重新启用电子邮件通信后会被发送。
feature: Configuration
role: Admin, Developer
exl-id: 773c0e0e-92c3-42b1-8fbf-fcb05e0e8311
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-58685：重新启用时会发送禁用的销售电子邮件

ACSD-58685修补程序修复了在禁用电子邮件通信时启动的销售电子邮件在重新启用电子邮件通信后会被发送的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55时，此修补程序可用。 修补程序ID为ACSD-58685。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

禁用电子邮件通信时启动的销售电子邮件会在重新启用电子邮件通信后发送。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Mail Sending Settings]**&#x200B;并将&#x200B;**[!UICONTROL Disable Email Communications]**&#x200B;设置为&#x200B;*[!UICONTROL No]*。
1. 导航到&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales Emails]** > **[!UICONTROL General Settings]**&#x200B;并将&#x200B;**[!UICONTROL Asynchronous Sending]**&#x200B;设置为&#x200B;*[!UICONTROL Yes]*。
1. 清除配置缓存。
1. 下订单。
1. 启用电子邮件通信。
1. 下另一张订单。
1. 快去开箱。

<u>预期的结果</u>：

只发送第二张订单的电子邮件。

<u>实际结果</u>：

同时发送第一订单和第二订单的电子邮件。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

[[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
