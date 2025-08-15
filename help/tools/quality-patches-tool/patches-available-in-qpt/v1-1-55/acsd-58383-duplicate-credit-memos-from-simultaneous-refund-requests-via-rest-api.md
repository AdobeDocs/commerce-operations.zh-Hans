---
title: ACSD-58383：通过 [!DNL REST API]同步退款请求中的重复贷项通知单
description: 应用ACSD-58383修补程序以修复Adobe Commerce问题，该问题导致通过 [!DNL REST API] 同时执行两个相同请求时发出退款，从而创建重复的贷项通知单。
feature: REST, Payments, Returns
role: Admin, Developer
exl-id: 962970d5-22e7-4bdc-afa0-70e1fa21ecec
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-58383：通过[!DNL REST API]同步退款请求中的重复贷项通知单

ACSD-58383修补程序修复了以下问题：通过[!DNL REST API]发出退款，其中有两个同时执行的相同请求，从而导致重复的贷项通知单。

安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55时，此修补程序可用。 修补程序ID为ACSD-58383。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

重复贷项通知单产生于同时创建的两个退款。

<u>重现步骤</u>：

1. 在Commerce [!DNL Paypal Express]中配置[!UICONTROL Admin]。
1. 将付款操作设置为&#x200B;*销售*。
1. 在[!DNL PayPal]沙盒网站上配置[!DNL PayPal] IPN（即时付款通知）。
1. [!DNL PayPal]沙盒网站上的问题退款。
1. 使用开发人员工具模拟来自[!DNL PayPal]的IPN消息。 IPN必须创建贷项通知单。
1. 使用[!DNL API]调用创建另一张贷项通知单。

<u>预期的结果</u>：

仅为同一物料创建一个贷项通知单。


<u>实际结果</u>：

系统会为同一物料创建两个贷项通知单。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
