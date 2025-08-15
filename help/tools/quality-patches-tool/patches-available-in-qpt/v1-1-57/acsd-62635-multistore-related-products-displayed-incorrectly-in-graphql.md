---
title: ACSD-62635：在 [!DNL GraphQL]中显示的多商店相关产品不正确
description: 应用ACSD-62635修补程序以修复Adobe Commerce问题，该问题导致与多商店相关的产品无法在 [!DNL GraphQL] 产品查询中正确显示。
feature: B2B
role: Admin, Developer
exl-id: 540cd37b-4dc5-42d1-a968-2989262effdd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-62635： [!DNL GraphQL]中显示的多商店相关产品不正确

ACSD-62635修补程序修复了多商店相关产品在[!DNL GraphQL]产品查询中无法正确显示的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57时，此修补程序可用。 修补程序ID为ACSD-62635。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

启用B2B后，即使请求中使用商店视图范围，[!DNL GraphQL]请求也会返回所有网站的所有相关产品。

<u>重现步骤</u>：

1. 创建两个网站、商店和商店视图。
1. 创建以下简单产品：
   * 一个主服务器，其SKU为&#x200B;*product1*，已分配给所有网站
   * 一个仅分配给&#x200B;*网站1*
   * 一个仅分配给&#x200B;*网站2*
   * 一个同时分配给&#x200B;*网站1*&#x200B;和&#x200B;*网站2*
1. 添加与&#x200B;*product1*&#x200B;相关的所有产品。
1. 启用[!UICONTROL B2B]和[!UICONTROL Shared Catalog]。
1. 将所有产品添加到默认共享目录。
1. 发送[!DNL GraphQL]请求以检索标题中商店代码为&#x200B;*Website 1*&#x200B;的&#x200B;*product1*&#x200B;及其相关产品。

<u>预期的结果</u>：

响应仅包含与请求标头中发送的商店代码对应的网站中的相关产品。

<u>实际结果</u>：

响应包含所有网站的所有相关产品，而不管请求中指定的商店代码如何。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
