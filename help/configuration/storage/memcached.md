---
title: 使用内存缓存进行会话存储
description: 了解如何将Adobe Commerce配置为使用memcached在env.php中进行会话存储，以及何时选择Redis或Varnish进行其他缓存层。
feature: Configuration, Cache, Storage
exl-id: 24077929-e732-4579-8d7d-717a4902fc64
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '305'
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

   ```shell
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. 前往店面上的任何页面。

1. 登录到管理员并浏览多个页面。

   如果没有显示错误，恭喜您！ memcached正在工作！ 您可以选择查看内存缓存存储，如下一步骤中所述。

   如果显示错误(如HTTP 500（内部服务器错误）)，请启用开发人员模式并诊断问题。 确保memcached正在运行，配置正确，`env.php`没有语法错误。

1. （可选。） 使用Telnet查看内存缓存存储。

   ```shell
   telnet <memcached host or ip> <memcached port>
   ```

   ```shell
   stats items
   ```

   结果显示类似以下内容：

   ```text
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
