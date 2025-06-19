---
title: MDVA-41399：如果客户将产品添加到愿望清单，则无法访问管理购物车
description: MDVA-41399修补程序解决了当客户将产品添加到愿望清单时，管理员用户无法访问“管理购物车”页面的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6后，即可使用此修补程序。 修补程序ID为MDVA-41399。 请注意，Adobe Commerce 2.4.2中已修复此问题。
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: 81a128b5-0c38-4f8f-b297-1f264952d431
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-41399：如果客户将产品添加到愿望清单，则无法访问管理购物车

MDVA-41399修补程序解决了当客户将产品添加到愿望清单时，管理员用户无法访问“管理购物车”页面的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6后，即可使用此修补程序。 修补程序ID为MDVA-41399。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.3.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果客户将产品添加到愿望清单，管理员用户将无法访问“管理购物车”页面。

<u>先决条件</u>：

1. 创建两个或更多产品。
1. 创建客户。
1. 启用开发人员模式。

<u>重现步骤</u>：

1. 前往Storefront并以客户的身份登录，前提条件是：
1. 将产品添加到愿望清单。
1. 转到“管理员”面板，导航到已创建的客户编辑页面，然后单击&#x200B;**管理购物车**&#x200B;按钮。

<u>预期的结果</u>：

管理员用户能够管理购物车。

<u>实际结果</u>：

管理员用户收到错误消息： *发生错误。 有关详细信息，请参阅错误日志。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修补程序部分。
