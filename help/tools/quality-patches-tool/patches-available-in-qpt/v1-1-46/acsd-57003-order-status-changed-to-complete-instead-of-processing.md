---
title: ACSD-57003：订单状态更改为*完成*，而不是更改为*正在处理*
description: 应用ACSD-57003修补程序以修复订单状态更改为*Complete*而不是更改为*Processing*的Adobe Commerce问题。
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: a28ecc35-5c9a-4bba-b0b9-67fbe37ed8c3
source-git-commit: 128107310416e97edca3b122e97456138d04073f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# ACSD-57003：订单状态更改为&#x200B;*完成*，而不是更改为&#x200B;*正在处理*

ACSD-57003修补程序修复了订单状态更改为&#x200B;*完成*&#x200B;而不是更改为&#x200B;*正在处理*&#x200B;的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.46时，此修补程序可用。 修补程序ID为ACSD-57003。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p3、2.4.6-p8、2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p9、2.4.7-p2 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

订单部分退款和部分装运时，订单状态更改为&#x200B;*完成*，而不是更改为&#x200B;*正在处理*。

<u>重现步骤</u>：

1. 创建包含两个可配置产品的订单。
1. 为所有项目开票。
1. 只发运第一个项目。
1. 仅为装运的项目（*第一个项目*）退款/创建贷项通知单。
1. 检查订单状态。

<u>预期的结果</u>：

订单状态应为&#x200B;_正在处理_&#x200B;状态。

<u>实际结果</u>：

为部分发运的项目创建贷项通知单后，订单状态更改为&#x200B;*完成*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
