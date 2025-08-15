---
title: 数据迁移最佳实践
description: 按照这些数据迁移最佳实践操作，以确保成功从Magento 1升级到Magento 2。
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
feature: Best Practices, Configuration
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# 数据迁移最佳实践

此部分提供了加速和简化迁移的最佳建议，以及有关可能需要多长时间的指导。

* **在执行迁移测试时，使用Magento 1实例中的数据库副本**。 请勿使用Magento 1商店数据库的生产实例。

* 在迁移之前，从Magento 1数据库中删除过时的冗余数据&#x200B;**。**

此类数据可能包括日志、订单报价、最近查看或比较的产品、访客、特定于事件的类别以及促销规则。

* **按照[常规规则成功迁移](migrate-data/overview.md#migration-overview)**。

* 若要提高性能，请在&#x200B;**文件中`direct_document_copy`启用**&#x200B;选项`config.xml`：

  ```xml
  <direct_document_copy>1</direct_document_copy>
  ```

>[!NOTE]
>
>Magento 1和Magento 2数据库必须位于同一个MySQL服务器上，并且数据库帐户必须能够访问这两个数据库。

## 基准测试评估

Adobe已在以下系统上测试数据迁移：

* Virtual Box VM，CentOS 6,2.5 GB RAM，CPU 1核2.6 GHz
* 拥有177,000种产品、 355,000份订单和214,000个客户的数据库

## 性能结果

* 设置迁移时间：约10分钟
* 数据迁移时间：约9小时（除URL重写之外的所有数据，占总数据量的约85%）
* 网站停机时间估计值：需要几分钟来重新索引和更改DNS设置。 预热页面缓存所需的额外时间。
