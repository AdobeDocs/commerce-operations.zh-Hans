---
title: 数据库复制
description: 了解配置数据库复制的好处。
recommendations: noCatalog
exl-id: 0e41dca0-5a23-4d12-96fe-241c511ae366
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---

# 数据库复制

{{ee-only}}

{{deprecate-split-db}}

设置数据库复制具有以下优点：

- 提供数据备份
- 在不影响master数据库的情况下启用数据分析
- 可扩展性

MySQL数据库以异步方式复制，这意味着无需永久连接从属进程即可从主数据库接收更新。

## 配置数据库复制

有关数据库复制的深入讨论超出了本指南的范围。 要设置此功能，您可以咨询以下资源：

- [MySQL文档](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [如何在MySQL (digitalocean)中设置主从复制](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerce为从属数据库提供了示例MySQL配置。 简单的配置提供了 `ResourceConnections` 类 `README.md`.

下面是更高级的描述，仅供您参考：

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

为了提高主从复制的性能，可以过滤从实例上的某些表。 我们建议使用名称模式筛选所有临时表 `search\_tmp\_%` 用于目录搜索的内容。

为此，请将以下行添加到 `my.cnf` 从实例上的文件：

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
