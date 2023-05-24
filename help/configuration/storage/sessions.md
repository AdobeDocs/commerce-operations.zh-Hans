---
title: 会话存储位置
description: 了解会话文件的存储位置。
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# 会话存储位置

本主题讨论如何定位会话文件的存储位置。 系统使用以下逻辑来存储会话文件：

- 如果配置了memcached，则会话存储在RAM中；请参阅 [将内存缓存用于会话存储](memcached.md).
- 如果已配置Redis，则会话将存储在Redis服务器上；请参阅 [将Redis用于会话存储](../cache/redis-session.md).
- 如果您使用的是默认的基于文件的会话存储，则会按照显示的顺序将会话存储到以下位置：

   1. 中定义的目录 [`env.php`](#example-in-envphp)
   1. 中定义的目录 [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` 目录

## 中的示例 `env.php`

中的示例代码片段 `<magento_root>/app/etc/env.php` 如下所示：

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

上述示例将会话文件存储在 `/var/www/session`

## 中的示例 `php.ini`

作为用户，具有 `root` 权限，打开您的 `php.ini` 文件并搜索值 `session.save_path`. 这标识了会话的存储位置。

## 管理会话大小

请参阅 [会话管理](https://docs.magento.com/user-guide/stores/security-session-management.html) 在 _用户指南_.

## 垃圾收集配置

要清除过期的会话，系统会调用 `gc` (_垃圾收集_)处理程序随机选择的概率，该概率由 `gc_probability / gc_divisor` 指令。 例如，如果将这些指令设置为 `1/100` 分别表示 `1%` (_每100个请求一个垃圾收集调用的概率_)。

垃圾收集处理程序使用 `gc_maxlifetime` directive — 会话被视为的秒数 _垃圾桶_ 并可能清理干净。

在某些操作系统(Debian/Ubuntu)上，默认 `session.gc_probability` 指令为 `0`，可阻止垃圾收集处理程序运行。

您可以覆盖 `session.gc_` 指令来自 `php.ini` 中的文件 `<magento_root>/app/etc/env.php` 文件：

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

根据流量和商家网站的特定需求，配置会有所不同。
