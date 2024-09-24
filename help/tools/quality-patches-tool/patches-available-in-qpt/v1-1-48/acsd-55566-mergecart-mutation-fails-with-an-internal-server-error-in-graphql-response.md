---
title: 'ACSD-55566： [!UICONTROL mergeCart]变异失败，出现 [!DNL GraphQL] 响应中的内部服务器错误'
description: 应用ACSD-55566修补程序以修复Adobe Commerce问题，该问题导致在合并具有相同捆绑项目的源和目标购物车时，“mergeCart”突变失败，并出现 [!DNL GraphQL] 响应中的内部服务器错误。
feature: GraphQL, Shopping Cart
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-55566： `mergeCart`变异失败，在[!DNL GraphQL]响应中出现内部服务器错误

ACSD-55566修补程序修复了以下问题： `mergeCart`突变失败，[!DNL GraphQL]响应中出现内部服务器错误。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48时，此修补程序可用。 修补程序ID为ACSD-55566。 请注意，该问题计划在Adobe Commerce 2.5.0中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

合并具有相同捆绑项的源和目标购物车时，`mergeCart`变异失败，出现[!DNL GraphQL]响应中的内部服务器错误。

<u>重现步骤</u>：

1. 创建自定义源和自定义库存。
1. 将创建的股票分配给主网站。
1. 创建一个简单产品，并将已创建的源（数量=2）分配给该产品。
1. 创建一个包含一个选项和一个子产品的捆绑产品（在步骤3中创建的产品）。
1. 通过[!DNL GraphQL]创建访客购物车。
1. 添加同时选择了两个选项的捆绑产品。
1. 保存&#x200B;*cartID*。
1. 创建客户并生成客户令牌。
1. 创建客户购物车。
1. 将具有相同配置的相同捆绑包产品添加到购物车。
1. 尝试将访客购物车与客户购物车合并。

<u>预期的结果</u>：

客户购物车包含来自两个购物车的产品。

<u>实际结果</u>：

您收到内部错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
