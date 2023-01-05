---
title: 将memcached用于会话存储
description: 了解如何使用memcached for Commerce会话存储。
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# 将memcached用于会话存储

Memcached是一种通用的分布式内存缓存系统。 它通常用于通过在RAM中缓存数据和对象来加快动态数据库驱动的网站的速度，以减少必须读取外部数据源（如数据库或API）的次数。

Memcached提供了一个大的哈希表，它可以分布在多台计算机上。 当表已满时，后续插入会导致以最近最少使用的(LRU)顺序清除旧数据。 此哈希表的大小通常非常大。 (来源： [memcached.org](https://www.memcached.org/))

Commerce使用memcached进行会话存储，但不用于页面缓存。 对于页面缓存，我们建议 [雷迪斯](../cache/redis-pg-cache.md) 或 [清漆](../cache/config-varnish.md).

**要将Commerce配置为使用memcached，请执行以下操作**:

1. 打开 `<your install dir>/app/etc/env.php` 在文本编辑器中。
1. 找到以下内容：

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. 更改如下：

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   memcached具有超出本指南范围的可选启动参数。 您可以在 [memcached](https://www.php.net/manual/en/memcached.sessions.php) 文档、源代码和更改日志。

1. 继续下一节。

**验证memcached与Commerce的工作**:

1. 删除Commerce安装目录下的以下目录的内容：

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. 转到店面上的任何页面。

1. 登录到管理员并浏览到多个页面。

   如果未显示错误，恭喜！ 梅姆卡兹在工作！ 您可以选择查看在下一步中讨论的缓存存储。

   如果显示错误(如HTTP 500（内部服务器错误）)，请启用开发人员模式并诊断问题。 确保memcached正在运行，且配置正确，并且 `env.php` 没有语法错误。

1. （可选。） 使用Telnet查看Memcached存储。

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   结果显示类似于以下内容：

   ```terminal
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
