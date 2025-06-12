---
title: ACSD-54472：被拒绝公司的客户仍然可以进行身份验证
description: 应用ACSD-54472修补程序以修复Adobe Commerce问题，该问题导致被拒绝公司的客户仍然可以执行身份验证，被阻止和被拒绝公司的客户仍然可以下订单。
feature: B2B
role: Admin, Developer
exl-id: c0bd960f-609b-4253-9fc8-dc47fbbddc93
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-54472：被拒绝公司的客户仍然可以进行身份验证

ACSD-54472修补程序修复了以下问题：被拒绝公司的客户仍然可以进行身份验证，被阻止和被拒绝公司的客户仍然可以下订单。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40时，此修补程序可用。 修补程序ID为ACSD-54472。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

被拒绝公司的客户仍然可以进行身份验证，被阻止和被拒绝公司的客户仍然可以下订单。

<u>重现步骤</u>：

1. 创建公司。
1. 通过[!DNL GraphQL]将产品添加到购物车。
1. 将公司状态更改为&#x200B;*已阻止*。
1. 发送[!DNL GraphQL]请求以下订单并创建可转让报价。
1. 将公司状态更改为&#x200B;*已拒绝*。
1. 发送[!DNL GraphQL]请求以获取公司的用户授权令牌。
1. 将客户状态设置为&#x200B;*不活动*。
1. 发送[!DNL GraphQL]请求以获取公司的用户授权令牌。

<u>预期的结果</u>：

* *已阻止*&#x200B;公司的用户未下达订单和可转让报价。
* 未获取&#x200B;*Rejected*&#x200B;公司的用户的授权令牌。
* 未获得&#x200B;*不活动*&#x200B;客户的授权令牌。

<u>实际结果</u>：

* 订单和可转让报价由&#x200B;*已阻止*&#x200B;公司的用户下单。
* 已为&#x200B;*Rejected*&#x200B;公司的用户获取授权令牌。
* 已为&#x200B;*不活动*&#x200B;客户获取授权令牌。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
