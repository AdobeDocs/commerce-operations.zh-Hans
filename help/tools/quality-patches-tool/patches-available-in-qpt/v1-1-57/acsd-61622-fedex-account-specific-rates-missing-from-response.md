---
title: ACSD-61622： REST API响应中缺少 [!DNL FedEx] 帐户特定费率
description: 应用ACSD-61622修补程序以修复REST API响应中缺少 [!DNL FedEx] 特定于帐户的费率的Adobe Commerce问题。
feature: Shipping/Delivery
role: Admin, Developer
source-git-commit: 24acc5f369e0001c8aeab3f81a2e1b51bc523333
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-61622： REST API响应中缺少[!DNL FedEx]帐户特定费率

ACSD-61622修补程序解决了REST API响应中缺少[!DNL FedEx's]帐户特定速率的问题。 它将`ACCOUNT`速率请求类型添加到从Adobe Commerce发送到[!DNL FedEx]的REST API请求中，从而返回与SOAP API响应类似的响应。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57时，此修补程序可用。 修补程序ID为ACSD-61622。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6-p1 - 2.4.6-p8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

REST API响应中缺少[!DNL FedEx's]帐户特定费率。

<u>重现步骤</u>：

1. 安装干净的Adobe Commerce实例。
1. 创建一个重量为5磅的简单产品。
1. 为REST API配置[!DNL FedEx]。
1. 启用[!DNL FedEx]配送方式并清除缓存。
1. 开始观察日志文件： `var/log/shipping.log`
1. 将简单产品添加到购物车，并在结帐时转到送货页面。 客户数据示例：

   * 邮政编码：58601
   * 姓名：John Doe
   * 地址：196 Eulalia Burg
   * 国家/地区：美国
   * 州：北达科他州
   * 电话号码：187-563-3627

<u>预期的结果</u>：

`PAYOR_ACCOUNT_PACKAGE`费率在REST API响应中可用，类似于SOAP API响应。

<u>实际结果</u>：

响应中只有`PAYOR_LIST_PACKAGE`费率可用，这意味着没有来自[!DNL FedEx]的协商（帐户）费率。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
