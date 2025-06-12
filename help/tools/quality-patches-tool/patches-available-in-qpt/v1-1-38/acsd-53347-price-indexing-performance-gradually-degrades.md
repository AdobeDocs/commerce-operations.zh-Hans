---
title: ACSD-53347：价格索引性能逐渐降低
description: 应用ACSD-53347修补程序以修复重新索引大型产品目录的价格时性能逐渐降低的Adobe Commerce问题。
feature: Price Indexer
role: Admin
exl-id: 8986b685-55e4-47c7-852c-aca18e3b02e9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-53347：价格索引性能逐渐降低

ACSD-53347修补程序修复了在重新索引大型产品目录的价格时性能逐渐降低的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.38时，此修补程序可用。 修补程序ID为ACSD-53347。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当重新索引大型产品目录的价格时，在索引过程中执行的查询的性能逐渐降低。

<u>重现步骤</u>：

1. 创建一个大型简单目录并向这些产品分配自定义选项（自定义选项在索引期间使用临时表）。
1. 创建至少200个或更多客户组以提高问题的可见性。
1. 创建十个或更多网站，并将所有产品分配给每个网站。
1. 请注意，导入的产品几乎完全相同，只是SKU和名称不同。
1. 启用&#x200B;**[!UICONTROL DB Logging]**。
1. 执行`bin/magento index:reindex catalog_product_price`命令。
1. 检查`db.log`中来自&#x200B;`catalog_product_index_price_opt_agr_temp`*的* DELETE。

<u>预期的结果</u>：

*DB查询*&#x200B;的执行效率很高。

<u>实际结果</u>：

*DB查询*&#x200B;在临时表上的性能逐渐变慢，因此价格索引表需要很多时间才能完成。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)
* 云基础架构上的Adobe Commerce： Commerce on Cloud Infrastructure指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)

## 相关阅读

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
