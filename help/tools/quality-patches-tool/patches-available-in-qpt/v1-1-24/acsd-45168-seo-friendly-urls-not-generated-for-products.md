---
title: 'ACSD-45168：没有为已覆盖url_key属性的产品生成SEO友好的URL'
description: 应用ACSD-45168修补程序以修复Adobe Commerce问题：对于在商店视图级别覆盖url_key属性的产品，不会生成对SEO友好的URL。
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-45168：没有为已覆盖url_key属性的产品生成SEO友好的URL

ACSD-45168修补程序修复了以下问题：对于在存储视图级别覆盖了url_key属性的产品，不会生成SEO友好的URL。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24时，此修补程序可用。 修补程序ID为ACSD-45168。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对于在存储视图级别上覆盖了url_key属性的产品，不会生成SEO友好的URL。

<u>重现步骤</u>：

1. 按如下方式设置配置，方法是转到&#x200B;**[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**：
   * [!UICONTROL Use Categories Path for Product URLs] = *是*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *是*
1. 清除配置缓存。
1. 创建两个类别： [!UICONTROL Category 1]和[!UICONTROL Category 2]。
1. 创建两个产品：[!UICONTROL Category 1]中的[!UICONTROL Product 1]，[!UICONTROL Category 1]中的[!UICONTROL Product 2]。
1. 将[!UICONTROL Product 1]的作用域更改为[!UICONTROL Default Store View]。
1. 取消选中[!UICONTROL Search Engine Optimization]中的可选URL [!UICONTROL Key]。
1. 保存产品。
1. 切换回[!UICONTROL All Store Views]。
1. 将[!UICONTROL Product 1]添加到[!UICONTROL Category 2]，并将[!UICONTROL Product 2]添加到[!UICONTROL Category 2]。
1. 检查[!UICONTROL url_rewrite]表或[!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites]。

<u>预期的结果</u>：

已为[!UICONTROL Product 1]创建[!UICONTROL Category 2]的SEO友好URL。

<u>实际结果</u>：

[!UICONTROL Product 1]缺少[!UICONTROL Category 2]的SEO友好URL，因为存储视图范围覆盖了URL键属性。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
