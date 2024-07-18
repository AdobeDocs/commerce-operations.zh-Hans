---
title: 使用内存缓存进行会话存储
description: 了解如何将memcached用于Commerce会话存储。
feature: Configuration, Cache, Storage
exl-id: 24077929-e732-4579-8d7d-717a4902fc64
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# 使用内存缓存进行会话存储

Memcached是一种通用分布式内存缓存系统。 它通常用于通过在RAM中缓存数据和对象来加快动态数据库驱动网站的速度，以减少必须读取外部数据源（如数据库或API）的次数。

Memcached提供了一个可在多台计算机上分发的大型哈希表。 当表已满时，后续插入会导致按最近使用最少(LRU)的顺序清除旧数据。 此哈希表的大小通常非常大。 (Source： [memcached.org](https://www.memcached.org/))

Commerce将memcached用于会话存储，但不用于页面缓存。 对于页面缓存，我们建议[Redis](../cache/redis-pg-cache.md)或[Varnish](../cache/config-varnish.md)。

**要将Commerce配置为使用memcached**：

1. 在文本编辑器中打开`<your install dir>/app/etc/env.php`。
1. 找到以下内容：

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. 按如下方式更改：

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   memcached具有本指南范围之外的启动参数。 您可以在[memcached](https://www.php.net/manual/en/memcached.sessions.php)文档、源代码和更改日志中找到有关它们的更多信息。

1. 继续下一部分。

**要验证memcached是否可用于Commerce**：

1. 删除Commerce安装目录下以下目录的内容：

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. 前往店面上的任何页面。

1. 登录到管理员并浏览多个页面。

   如果没有显示错误，恭喜您！ memcached正在工作！ 您可以选择查看内存缓存存储，如下一步骤中所述。

   如果显示错误(如HTTP 500（内部服务器错误）)，请启用开发人员模式并诊断问题。 确保memcached正在运行，配置正确，`env.php`没有语法错误。

1. （可选。） 使用Telnet查看内存缓存存储。

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   结果显示类似以下内容：

   ```
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
