---
title: 'ACSD-50234：使用 [!DNL PayPal]下订单的确认电子邮件中的客户名称不正确'
description: 应用ACSD-50234修补程序以修复使用 [!DNL PayPal]下订单的确认电子邮件中客户名称显示不正确的Adobe Commerce问题。
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50234：使用[!DNL PayPal]下订单的确认电子邮件中的客户名称不正确

ACSD-50234修补程序修复了使用[!DNL PayPal]下订单的确认电子邮件中客户名称显示不正确的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29时，此修补程序可用。 修补程序ID为ACSD-50234。 请注意，Adobe Commerce 2.4.5中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用[!DNL PayPal]下订单的确认电子邮件显示错误的客户名称。

<u>重现步骤</u>

1. 启用&#x200B;**[!UICONTROL PayPal Express Checkout]**。
1. 作为来宾导航到前端。
1. 将产品添加到购物车。
1. 使用&#x200B;**[!UICONTROL PayPal Express Checkout]**&#x200B;作为付款方式签出。
1. 检查订单确认电子邮件。

<u>预期的结果</u>

订单确认电子邮件、发票电子邮件以及所有与发运相关的电子邮件均以客户的名称发送。

<u>实际结果</u>

订单确认电子邮件、发票电子邮件以及所有与装运相关的电子邮件均发送给&#x200B;*来宾*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
