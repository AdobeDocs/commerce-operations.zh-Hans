---
title: ACSD-60584：允许为一个网站创建的访问令牌访问其他网站上的信息
description: 应用ACSD-60584修补程序修复了一个网站上为用户创建的访问令牌被允许访问或更改其他网站上的客户信息的问题。
feature: Customers, GraphQL
role: Admin, Developer
exl-id: ea30ba92-4b7b-44f9-a1b1-97946061d9e6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-60584：允许为一个网站创建的访问令牌访问其他网站上的信息

ACSD-60584修补程序修复了以下问题：在一个网站上为用户创建的访问令牌被允许访问或更改其他网站上的客户信息。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.53时，此修补程序可用。 修补程序ID为ACSD-60584。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在一个网站上为用户创建的API令牌允许您访问客户信息，创建购物车，以及在其他网站视图上将产品添加到购物车。

<u>重现步骤</u>：

1. 确保&#x200B;**[!DNL Share Customer Accounts configuration]**&#x200B;设置为&#x200B;**[!UICONTROL Per Website]**。
1. 创建其他&#x200B;*网站*、*商店*&#x200B;和&#x200B;*商店评论*。
1. 在上一步中，使用主&#x200B;*网站*&#x200B;和&#x200B;*网站*&#x200B;上的相同电子邮件创建两个客户。
1. 通过主网站上的[!DNL GraphQL]生成客户令牌。
1. 使用生成的令牌，发送带有标头中第二个网站的客户&#x200B;**[!DNL GraphQL]**&#x200B;查询以检索客户信息。
1. 观察返回的结果。

<u>预期的结果</u>：

返回主&#x200B;*网站*&#x200B;中的客户信息，因为主&#x200B;*网站*&#x200B;中的令牌已在[!DNL GraphQL]查询中使用。

<u>实际结果</u>：

返回来自第二个网站的客户信息。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
