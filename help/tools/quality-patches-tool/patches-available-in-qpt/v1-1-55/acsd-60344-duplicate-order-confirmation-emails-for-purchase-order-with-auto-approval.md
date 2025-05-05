---
title: ACSD-60344：有关使用自动审批[!UICONTROL Purchase Order]的重复订单确认电子邮件
description: 应用ACSD-60344修补程序以修复在使用自动审批[!UICONTROL Purchase Order]时发送重复订单确认电子邮件的Adobe Commerce问题。
feature: Purchase Orders
role: Admin, Developer
source-git-commit: afa03b31e4af0be1ebc0d12aabd4f9d8be17d1fe
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# ACSD-60344：有关使用自动审批&#x200B;*[!UICONTROL Purchase Order]*&#x200B;的重复订单确认电子邮件

ACSD-60344修补程序修复了在使用&#x200B;*[!UICONTROL Purchase Order]*&#x200B;进行自动批准时发送重复订单确认电子邮件的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55时，此修补程序可用。 修补程序ID为ACSD-60344。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.6-p4

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在自动批准中使用&#x200B;*[!UICONTROL Purchase Order]*&#x200B;时会发送重复的订单确认电子邮件。

<u>先决条件</u>

启用B2B模块和&#x200B;*[!UICONTROL Purchase Order]*。

<u>重现步骤</u>：

1. 创建公司帐户并为其启用&#x200B;*[!UICONTROL Purchase Order]*。
1. 创建常规用户帐户，并将其作为公司用户添加到公司帐户。
1. 使用此帐户下订单。
1. 运行cron并检查电子邮件。

<u>预期的结果</u>：

每个订单仅接收一封订单确认电子邮件。

<u>实际结果</u>：

收到两封订单确认电子邮件。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
