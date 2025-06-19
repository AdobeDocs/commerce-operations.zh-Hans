---
title: ACSD-63090：从管理员删除产品会清空购物车
description: 应用ACSD-63090修补程序以修复Adobe Commerce问题：当某个产品添加到购物车后，该产品的删除导致客户的购物车项目消失。
feature: Shopping Cart, Quotes
role: Admin, Developer
exl-id: c07778cb-390f-4202-9539-7bb159e4b714
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63090：从管理员删除产品会清空购物车

ACSD-63090修补程序解决了以下问题：在客户的购物车项目添加到购物车后，该产品会从管理员那里被删除，从而导致该客户的购物车项目消失。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58时，此修补程序可用。 修补程序ID为ACSD-63090。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当产品在添加到购物车后被删除时，购物车项目消失。

<u>重现步骤</u>：

1. 创建具有两个子产品的可配置产品。
1. 以注册客户的身份登录。
1. 将两个子产品添加到购物车。
1. 注销帐户。
1. 从目录中删除其中一个子产品。
1. 使用API更新其他子产品的价格。

<u>预期的结果</u>：

其余产品显示在购物车中，现有报价在`quote`数据库表中更新。

<u>实际结果</u>：

* 迷你购物车是空的。
* 将在`quote`数据库表中生成新的报价记录。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
