---
title: ACSD-61969：需要键入配置为大写或小写的优惠券代码
description: 应用ACSD-61969修补程序以修复Adobe Commerce问题，该问题要求用户完全按照其配置的大写或小写形式键入优惠券代码。
feature: Price Rules
role: Admin, Developer
exl-id: 4bdf797b-2570-49f8-8e03-952b49ed1d18
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61969：需要键入配置为大写或小写的优惠券代码

ACSD-61969修补程序修复了以下问题：要求用户输入与配置为大写或小写完全相同的优惠券代码。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53时，此修补程序可用。 修补程序ID为ACSD-61969。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

从后端应用优惠券时，需要完全按照大写或小写配置键入优惠券代码。 它们在创建管理员订单时区分大小写，但在店面中不区分大小写。

<u>重现步骤</u>：

1. 创建具有特定优惠券&#x200B;*TEST*&#x200B;的&#x200B;*[!UICONTROL Cart Price Rule]*。 确保优惠券代码为大写。
1. 在管理员中创建订单。
1. 将&#x200B;*test*&#x200B;添加到&#x200B;*[!UICONTROL Apply Coupon Code]*&#x200B;字段，然后单击字段附近的箭头以应用优惠券。
1. 观察结果。

<u>预期的结果</u>：

已成功应用优惠券。 优惠券字段不区分大小写。

<u>实际结果</u>：

未应用优惠券。 将显示以下错误：

*“测试”优惠券代码无效。 请验证代码并重试。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

[[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
