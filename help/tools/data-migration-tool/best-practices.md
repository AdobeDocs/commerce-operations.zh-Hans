---
title: 数据迁移最佳实践
description: 按照这些数据迁移最佳实践操作，以确保成功从Magento1升级到Magento2。
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# 数据迁移最佳实践

此部分提供了加速和简化迁移的最佳建议，以及有关可能需要多长时间的指导。

* **使用Magento1实例中的数据库副本** 执行迁移测试时。 请勿使用Magento1存储数据库的生产实例。

* **删除过时和冗余数据** 迁移前从Magento1数据库中删除。

此类数据可能包括日志、订单报价、最近查看或比较的产品、访客、活动特定类别和促销规则。

* **请遵循 [成功迁移的一般规则](migrate-data/overview.md#migration-overview)**.

* 为了提高性能， **启用 `direct_document_copy` option** 在您的 `config.xml` 文件：

   ```xml
   <direct_document_copy>1</direct_document_copy>
   ```

>[!NOTE]
>
>Magento1和Magento2数据库必须位于同一个MySQL服务器上，并且数据库帐户必须能够访问这两个数据库。

## 基准评估估计

Adobe已在以下系统上测试数据迁移：

* Virtual Box VM，CentOS 6,2.5 GB RAM，CPU 1 core 2.6 GHz
* 拥有177,000种产品、 355,000份订单和214,000个客户的数据库

## 性能结果

* 设置迁移时间：约10分钟
* 数据迁移时间：约9小时（除URL重写之外的所有数据，占总数据量的约85%）
* 网站停机时间估计值：需要几分钟时间来重新索引和更改DNS设置。 预热页面缓存所需的额外时间。
