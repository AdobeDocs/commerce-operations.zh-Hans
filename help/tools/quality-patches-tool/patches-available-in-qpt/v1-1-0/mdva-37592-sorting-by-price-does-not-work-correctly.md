---
title: 'MDVA-37592：按价格排序不适用于价格为零的产品'
description: MDVA-37592 Adobe Commerce修补程序解决了按价格排序对分配给共享目录且价格为零的产品无法正常工作的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0后，即可使用此修补程序。 修补程序ID为MDVA-37592。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-37592：按价格排序不适用于价格为零的产品

MDVA-37592 Adobe Commerce修补程序解决了按价格排序对分配给共享目录且价格为零的产品无法正常工作的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0时，此修补程序可用。 修补程序ID为MDVA-37592。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云架构上的Adobe Commerce 2.4.0-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署类型） 2.3.6-2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对于分配给共享目录且价格为零的产品，按价格排序无法正确运行。

<u>先决条件</u>：

已安装B2B。

<u>重现步骤</u>：

1. 启用共享目录。
1. 使用以下价格创建四个产品，并将它们分配给一个类别 — $50、$60、$70和$80。
1. 使用上述产品创建共享目录。
1. 将价格为$70的产品自定义价格设置为零。
1. 现在创建公司用户，并将其分配给刚刚创建的共享目录。
1. 使用公司帐户登录，并浏览到产品被分配到的类别。
1. 尝试按价格排序。

<u>预期的结果</u>：

对价格为零的产品进行了正确排序。

<u>实际结果</u>：

价格为零的产品未正确排序。 而是按照原价排序。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!DNL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
