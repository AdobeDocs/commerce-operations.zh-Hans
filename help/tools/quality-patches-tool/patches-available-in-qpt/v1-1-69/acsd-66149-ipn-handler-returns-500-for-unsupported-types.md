---
title: ACSD-66149：对于不支持的类型，IPN处理程序返回*500*
description: 应用ACSD-66149修补程序以修复Adobe Commerce问题，该问题导致IPN处理程序不会忽略不支持的或未知的IPN类型，从而导致该问题无法记录、中断进程并返回500错误。
feature: Payments
role: Admin, Developer
type: Troubleshooting
exl-id: d4794e24-1b6b-4bb5-b54c-9a248fa5f3bd
source-git-commit: cf0f5992c7b2a51b270a4a1a81fd50305a92759c
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-66149：对于不支持的类型，IPN处理程序返回&#x200B;*500*

ACSD-66149修补程序修复了IPN（即时付款通知）处理程序对不支持或未知的IPN类型返回500错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69时，此修补程序可用。 修补程序ID为ACSD-66149。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

问题是IPN处理程序对于不支持的或未知的IPN类型返回&#x200B;*500*&#x200B;错误。 当Paypal发送IPN时缺少某些字段时会发生这种情况。

<u>重现步骤</u>：

1. 创建一个自定义模块，以模拟PayPal中的各种未知IPN类型。
1. 至少创建一个产品。
1. 使用您自己的凭据配置PayPal Express。
1. 向Paypal Express下订单。
1. 运行PayPal模拟器。

<u>预期的结果</u>：

应用程序IPN处理程序忽略不正确的IPN类型，并且不会生成&#x200B;*500*&#x200B;错误：

```Order 000000001: Status processing — HTTP 500```

<u>实际结果</u>：

应用程序在处理不正确的IPN期间生成许多&#x200B;*500*&#x200B;错误，如果预期字段不存在，则偶尔不会处理某些订单。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]
* 云基础架构上的Adobe Commerce： Commerce on Cloud Infrastructure指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： Tools指南中用于优质修补程序的Self-service工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
