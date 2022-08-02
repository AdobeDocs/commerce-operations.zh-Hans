---
title: 会话存储位置
description: 了解会话文件的存储位置。
source-git-commit: 27c3914540a0574fa4ff58df50d5cd2c71fb6670
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# 会话存储位置

本主题讨论如何找到会话文件的存储位置。 系统使用以下逻辑存储会话文件：

- 如果配置了memcached，则会话会存储在RAM中；请参阅 [将memcached用于会话存储](memcached.md).
- 如果配置了Redis，则会话存储在Redis服务器上；请参阅 [将Redis用于会话存储](../cache/redis-session.md).
- 如果您使用默认的基于文件的会话存储，我们会按显示的顺序将会话存储在以下位置：

   1. 在中定义的目录 [`env.php`](#example-in-envphp)
   1. 在中定义的目录 [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` 目录

## 示例 `env.php`

示例代码片段 `<magento_root>/app/etc/env.php` 如下：

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

上面的示例将会话文件存储在 `/var/www/session`

## 示例 `php.ini`

作为用户， `root` 权限，打开 `php.ini` 文件并搜索 `session.save_path`. 这可标识会话的存储位置。

## 管理会话大小

请参阅 [会话管理](https://docs.magento.com/user-guide/stores/security-session-management.html) 在 _用户指南_.

## 垃圾收集配置

要清理过期的会话，系统会调用 `gc` (_垃圾收集_)处理程序 `gc_probability / gc_divisor` 指令。 例如，如果将这些指令设置为 `1/100` 分别表示 `1%` (_每100个请求一次调用垃圾收集的概率_)。

垃圾收集处理程序使用 `gc_maxlifetime` 指令 — 会话被视为的秒数 _垃圾_ 可能会被清理干净。

在某些操作系统(Debian/Ubuntu)上，默认 `session.gc_probability` 指令 `0`，以阻止垃圾收集处理程序运行。

您可以覆盖 `session.gc_` 指令 `php.ini` 文件 `<magento_root>/app/etc/env.php` 文件：

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

配置因商户网站的流量和特定需求而异。
