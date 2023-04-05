---
title: 数据库复制
description: 请参阅配置数据库复制的好处。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---


# 数据库复制

{{ee-only}}

{{deprecate-split-db}}

设置数据库复制具有以下好处：

- 提供数据备份
- 在不影响主控数据库的情况下支持数据分析
- 可扩展性

MySQL数据库以异步方式复制，这意味着从服务器无需永久连接即可从主控接收更新。

## 配置数据库复制

对数据库复制的深入讨论不在本指南的范围之内。 要进行设置，您可以查阅资源，如：

- [MySQL文档](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [如何在MySQL(digitalocean)中设置主控从复制](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

商务为从数据库提供MySQL配置示例。 提供了简单的配置 `ResourceConnections` 类 `README.md`.

以下更高级，仅供参考：

```php
   return array (
      //...
      'db' =>
         array (
            'connection' =>
               array (
                  'indexer' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                        'persistent' => NULL,
                     ),
                  'default' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-master-host',
                        'dbname' => 'checkout',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-master-host',
                        'dbname' => 'sales',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
               ),
            'slave_connection' =>
               array (
                  'default' =>
                     array (
                        'host' => 'default-slave-host',
                        'dbname' => 'magento',
                        'username' => 'read_only',
                        'password' => 'password',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-slave-host',
                        'dbname' => 'checkout',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-slave-host',
                        'dbname' => 'sales',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  ),
               'table_prefix' => '',
   ),
   //.......
```

## 性能改进

为了提高主控从复制的性能，您可以在从实例上过滤一些表。 我们建议过滤所有具有名称模式的临时表 `search\_tmp\_%` 用于目录搜索的ID和ID。

为此，请将以下行添加到 `my.cnf` 文件：

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
