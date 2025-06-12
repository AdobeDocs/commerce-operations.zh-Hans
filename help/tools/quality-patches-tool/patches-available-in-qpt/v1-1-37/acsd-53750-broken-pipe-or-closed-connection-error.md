---
title: ACSD-53750：多线程catalog_product_price重新索引期间出现“管道断开或连接关闭”错误
description: 应用ACSD-53750修补程序以修复在多线程catalog_product_price重新索引期间出现*管道断开或连接关闭*错误的Adobe Commerce问题。
feature: Products
role: Admin, Developer
exl-id: 6c2f092f-a98e-4990-839c-a7291635f8af
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-53750：多线程`catalog_product_price`重新索引期间出现&#x200B;*管道断开或连接关闭*&#x200B;错误

ACSD-53750修补程序修复了在多线程`catalog_product_price`重新索引期间出现&#x200B;*管道中断或连接关闭*&#x200B;错误的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.37时，此修补程序可用。 修补程序ID为ACSD-53750。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在多线程`catalog_product_price`重新索引期间出现&#x200B;*管道断开或连接关闭*&#x200B;错误。

<u>重现步骤</u>：

1. 配置RabbitMq。
1. 使用附加的`small.xml`文件生成示例数据。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]**&#x200B;并设置&#x200B;**[!UICONTROL Stock/Source reindex strategy]** = **[!UICONTROL Asynchronous]**。
1. 为支持该操作的索引设置维度模式。 例如，`catalog_product_price_website_and_customer_group`或`customer_group`。

   ```
   bin/magento indexer:set-dimensions-mode catalog_product_price customer_group
   ```

1. 为`catalog_product_price`运行索引器的重置。

   ```
   bin/magento indexer:reset catalog_product_price
   ```

1. 使用多个线程为重置索引器运行索引器。

   ```
   MAGE_INDEXER_THREADS_COUNT=10 bin/magento indexer:reindex catalog_product_price
   ```

<u>预期的结果</u>：

没有发生错误。

<u>实际结果</u>：

AMQP连接导致以下错误： *管道断开或连接关闭*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
