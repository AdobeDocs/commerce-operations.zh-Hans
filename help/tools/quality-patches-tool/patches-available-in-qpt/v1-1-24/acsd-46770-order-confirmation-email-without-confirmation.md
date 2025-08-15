---
title: ACSD-46770：即使未选中[!UICONTROL Email Order Confirmation]，也会发送订单确认电子邮件
description: 应用ACSD-46770修补程序以修复在未选择[!UICONTROL Email Order Confirmation]的情况下发送订单确认电子邮件的Adobe Commerce问题。
feature: Communications, Orders
role: Admin
exl-id: d25ca121-7551-417c-b598-d8ed3a3da969
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-46770：即使未选中&#x200B;**[!UICONTROL Email Order Confirmation]**，也会发送订单确认电子邮件

ACSD-46770修补程序修复了以下问题：即使未选择&#x200B;**[!UICONTROL Email Order Confirmation]**，也可以通过REST API以访客用户身份下达订单。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24时，此修补程序可用。 修补程序ID为ACSD-46770。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

即使未选择&#x200B;**[!UICONTROL Email Order Confirmation]**，也会发送订单确认电子邮件。

<u>重现步骤</u>：

1. 创建客户帐户。
1. 转到&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Order]**&#x200B;并单击&#x200B;**[!UICONTROL Create New Order]**。
1. 选择客户，将产品添加到订单中，填写地址，然后选择送货和付款方式。
1. 在提交订单之前，取消选中&#x200B;**[!UICONTROL Email Order confirmation]**&#x200B;复选框。
1. 单击&#x200B;**[!UICONTROL Submit Order]**&#x200B;以创建订单。

<u>预期的结果</u>：

如果未选择&#x200B;**[!UICONTROL Email Order Confirmation]**，则不应发送订单确认电子邮件。

<u>实际结果</u>：

无论是否选中&#x200B;**[!UICONTROL Email Order Confirmation]**&#x200B;复选框，都会发送订单确认电子邮件。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)：搜索修补程序[!DNL Quality Patches Tool]。
