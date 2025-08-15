---
title: ACSD-62577：店面搜索性能优化
description: 应用ACSD-62577修补程序以修复因大型“search_query”表导致查询执行速度缓慢而导致店面搜索性能下降的Adobe Commerce问题。
feature: Search
role: Admin, Developer
exl-id: 211c1e3c-0739-4ff6-a25c-b27d335920d1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-62577：店面搜索性能优化

ACSD-62577修补程序通过优化查询和表索引来修复店面搜索查询性能缓慢的问题。 此修补程序在[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56中可用。修补程序ID为ACSD-62577。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.6、2.4.7-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

大的`search_query`表显着减慢店面搜索速度，由于查询效率低下和缺少优化的表索引，增加了前端响应时间。

<u>重现步骤</u>：

1. 使用性能工具包`small.xml`设置Adobe Commerce Develop。
1. 访问SQL命令行并使用以下命令删除`search_query`表：

   ```
   SET FOREIGN_KEY_CHECKS = 0;  
   DROP TABLE search_query;  
   SET FOREIGN_KEY_CHECKS = 1;  
   ```

1. 使用大量记录填充`search_query`表，例如： 400万条记录。
1. 触发重新索引和刷新缓存。

   ```
   bin/magento indexer:reindex  
   bin/magento c:c  
   bin/magento c:f  
   ```

1. 启用数据库调试日志：

   ```
   bin/magento dev:query-log:enable  
   ```

1. 在店面搜索栏中搜索术语，例如，
   `http://your_magento_instance/default/catalogsearch/result/?q=test.`
1. 检查`db.log`以了解以下SQL的查询执行时间：

   ```
   SELECT COUNT(*) FROM (  
   SELECT DISTINCT `main_table`.`query_text`  
   FROM `search_query` AS `main_table`  
   WHERE (main_table.store_id IN (1))  
   AND (main_table.num_results > 0)  
   ORDER BY `main_table`.`popularity` DESC  
   LIMIT 100  ) AS `result` WHERE (result.query_text = 'test')  
   ```

<u>预期的结果</u>：

查询执行时间已得到优化，在处理大型`search_query`表时，导致响应时间的增加不太显着。

<u>实际结果</u>：

由于处理大型`search_query`表的效率较低，查询执行时间显着增加：

```
TIME: 10.8520 seconds  
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
