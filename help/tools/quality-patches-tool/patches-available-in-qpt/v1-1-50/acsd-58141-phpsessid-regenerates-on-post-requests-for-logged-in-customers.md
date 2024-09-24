---
title: 'ACSD-58141：为启用了L2 Redis缓存的登录客户在POST请求时重新生成PHPSESSID'
description: 应用ACSD-58141修补程序以修复以下Adobe Commerce问题：对于已启用L2 Redis缓存的登录客户，在店面区域的POST请求上重新生成“PHPSESSID”，并且通过Admin更新该客户。
feature: Customers, Cache
role: Admin, Developer
source-git-commit: 52742cbc2098958f8e4cddf8534e0c2bf79d5c3e
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---


# ACSD-58141：如果启用了L2 Redis缓存，则对已登录客户的[!DNL POST]请求重新生成PHPSESSID

ACSD-58141修补程序修复了以下问题：如果启用了L2 Redis缓存，并且从Admin更新了客户，则在[!DNL POST]请求中针对已登录的客户重新生成`PHPSESSID`。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50时，此修补程序可用。 修补程序ID为ACSD-58141。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce和Magento Open Source版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

`PHPSESSID`在启用了L2 Redis缓存的已登录客户的[!DNL POST]请求上重新生成。

<u>先决条件</u>

必须使用Redis配置至少具有3个节点的环境。

<u>重现步骤</u>：

1. 创建一个简单的产品。
1. 创建客户并登录到店面。
1. 检查`PHPSESSID`的值。
1. 发送一些[!DNL POST]请求（例如，将产品添加到购物车），并看到`PHPSESSID`保持不变。
1. 登录到&#x200B;**[!UICONTROL Admin]**&#x200B;面板并更改客户的中间名。
1. 保存中间名后，请更改它并再次保存几次。
1. 在店面，发送[!DNL POST]请求。 `PHPSESSID`应该已更新。
1. 在店面，发送另一个[!DNL POST]请求并检查`PHPSESSID`。
1. 重复上一步几次。

<u>预期的结果</u>

更改客户数据后只重新生成`PHPSESSID`一次。

<u>实际结果</u>：

每次发送[!DNL POST]请求时都会重新生成`PHPSESSID`。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
