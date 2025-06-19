---
title: ACSD-53925：无法使用[!UICONTROL Product Carousel]保存CMS块
description: Adobe Commerce应用ACSD-53925修补程序以修复以下问题：将“catalog_product_price”的维度模式设置为“website”时，管理员无法通过产品轮播保存CMS块。
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: f6d286ab-d904-4f08-8265-99632f74b88a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-53925：无法使用&#x200B;*[!UICONTROL Product Carousel]*&#x200B;保存CMS块

ACSD-53925修补程序修复了将`catalog_product_price`的维度模式设置为网站时，管理员无法将CMS块与&#x200B;*[!UICONTROL Product Carousel]*&#x200B;一起保存的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.43时，此修补程序可用。 修补程序ID为ACSD-53925。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当`catalog_product_price`的维度模式设置为网站时，管理员无法保存带&#x200B;*[!UICONTROL Product Carousel]*&#x200B;的CMS块。

<u>重现步骤</u>：

1. 创建两个简单的产品：
   * 简单1 - $10
   * 简单2 - 20美元
1. 创建捆绑产品“*bundle1-dyn*”，该捆绑产品具有基于简单产品SKU的两个选项。
1. 为产品价格索引器设置维度模式：

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. 转到&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Blocks]**，然后创建新的CMS块。
1. 使用[!DNL Page Builder]编辑内容：
   * 添加&#x200B;*[!UICONTROL Row]*&#x200B;元素
   * 添加&#x200B;*[!UICONTROL Products]*&#x200B;元素
   * 选择&#x200B;*[!UICONTROL Product Carousel]*
   * 输入产品SKU - *bundle1-dyn*
1. 保存CMS块。

<u>预期的结果</u>：

用户能够添加产品轮播且没有错误。

<u>实际结果</u>：

* UI中抛出一条消息： *很抱歉，生成此内容时出错*
* `var/log/exception.log`包含以下错误：

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
