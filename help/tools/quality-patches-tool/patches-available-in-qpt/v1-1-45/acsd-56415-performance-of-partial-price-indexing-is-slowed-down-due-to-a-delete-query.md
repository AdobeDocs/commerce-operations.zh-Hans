---
title: ACSD-56415：由于“DELETE”查询，[!UICONTROL Partial Price Indexing]的性能变慢
description: 应用ACSD-56415修补程序以修复Adobe Commerce问题：当数据库包含大量要索引的部分价格数据时，由于“DELETE”查询导致[!UICONTROL Partial Price Indexing]的性能变慢。
feature: Catalog Service
role: Admin, Developer
exl-id: c877844e-79d3-4756-97a5-de44e6fb5170
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-56415：由于`DELETE`查询，[!UICONTROL Partial Price Indexing]的性能变慢

ACSD-56415修补程序修复了在数据库具有大量部分价格数据索引时，[!UICONTROL Partial Price Indexing]的性能因`DELETE`查询而减慢的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45时，此修补程序可用。 修补程序ID为ACSD-56023。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当数据库具有大量部分价格数据索引时，由于`DELETE`查询，[!UICONTROL Partial Price Indexing]的性能减慢。

<u>重现步骤</u>：

1. 使用大型性能配置文件创建&#x200B;*300000产品*&#x200B;和&#x200B;*10网站*。
1. 登录到“管理面板”。
1. 创建&#x200B;*10个客户组*。
1. 执行以下查询以将产品添加到`_cl`表：

   ``
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 ``

1. 执行以下命令以触发部分价格索引过程：

   ``
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 ``

<u>预期的结果</u>：

快速执行来自`catalog_product_index_price`的SQL查询DELETE`main_table`。

<u>实际结果</u>：

来自`catalog_product_index_price`的SQL查询DELETE`main_table`的执行速度非常慢。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)
* 云基础架构上的Adobe Commerce： Commerce on Cloud Infrastructure指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)

## 相关阅读

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
