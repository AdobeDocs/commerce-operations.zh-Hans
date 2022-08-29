---
title: 数据迁移最佳实践
description: 请遵循这些数据迁移最佳实践，以确保成功从Magento1升级到Magento2。
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# 数据迁移最佳实践

本节提供了加速和简化迁移的最佳建议，以及有关可能需要多长时间的指导。

* **从Magento1实例中使用数据库的副本** 执行迁移测试时。 请勿使用Magento1存储数据库的生产实例。

* **删除过时和冗余的数据** 从Magento1数据库迁移。

此类数据可能包括日志、订单报价、最近查看或比较的产品、访客、特定于事件的类别和促销规则。

* **关注 [成功迁移的一般规则](migrate-data/overview.md#migration-overview)**.

* 为了提高性能， **启用 `direct_document_copy` 选项** 在 `config.xml` 文件：

   ```xml
   <direct_document_copy>1</direct_document_copy>
   ```

>[!NOTE]
>
>Magento1和Magento2数据库必须位于同一MySQL服务器上，并且数据库帐户必须具有对这两个数据库的访问权限。

## 基准评估

Adobe已在以下系统上测试了数据迁移：

* 虚拟盒VM、CentOS 6、2.5 GB RAM、CPU 1核心2.6 GHz
* 数据库，拥有177,000个产品、355,000个订单和214,000个客户

## 性能结果

* 设置迁移时间：~10分钟
* 数据迁移时间：~9小时（除URL外的所有数据都会重写，约占总数据的85%）
* 站点停机时间估计：重新编入索引并更改DNS设置需要几分钟。 预热页面缓存所需的其他时间。
