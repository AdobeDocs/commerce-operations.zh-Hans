---
title: ACSD-61799：对报价应用了多个固定折扣购物车规则时，总折扣计算不正确
description: 应用ACSD-61799修补程序以修复以下问题：当对报价应用了多个具有固定折扣的购物车规则时，Adobe Commerce计算的总折扣有误。
feature: Price Rules
role: Admin, Developer
exl-id: a87ec1cd-f141-43b9-bde1-eca354c12d4e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-61799：对报价应用了多个固定折扣购物车规则时，总折扣计算不正确

ACSD-61799修补程序解决了/修复了在将多个具有固定折扣的购物车规则应用于报价时错误计算总折扣的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54时，此修补程序可用。 修补程序ID为ACSD-61799。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将多个具有&#x200B;*[!UICONTROL Fixed amount discount for the whole cart]*&#x200B;的购物车规则应用于购物车时，总折扣计算不正确。

<u>重现步骤</u>：

1. 创建4个价格为$1000的产品。
1. 创建三个购物车价格规则，且不设置任何为整个购物车提供$100折扣的条件。
1. 再创建一个购物车价格规则，对整个购物车提供$100的折扣，但有一个条件阻止应用该规则。
1. 禁用规则。
1. 将三种产品添加到购物车并观察购物车中的折扣。
1. 将其他产品添加到购物车，并观察购物车中的折扣。
1. 启用禁用的购物车价格规则。
1. 更新购物车页面并观察购物车中的折扣。

<u>预期的结果</u>：

1. 将其他产品添加到购物车不会更改折扣金额。
1. 在不适用的条件下启用购物车价格规则不会更改折扣金额。

<u>实际结果</u>：

1. 将其他产品添加到购物车会更改折扣金额。
1. 在不适用的条件下启用购物车价格规则将更改折扣金额。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
