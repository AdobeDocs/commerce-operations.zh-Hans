---
title: 会话存储位置
description: 了解会话文件的存储位置。
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# 会话存储位置

本主题讨论如何定位会话文件的存储位置。 系统使用以下逻辑来存储会话文件：

- 如果配置了memcached，则会话存储在RAM中；请参阅[将memcached用于会话存储](memcached.md)。
- 如果配置了Redis，则会话存储在Redis服务器上；请参阅[将Redis用于会话存储](../cache/redis-session.md)。
- 如果您使用的是默认的基于文件的会话存储，则会按照显示的顺序将会话存储在以下位置：

   1. 在[`env.php`](#example-in-envphp)中定义的目录
   1. 在[`php.ini`](#example-in-phpini)中定义的目录
   1. `<magento_root>/var/session`目录

## `env.php`中的示例

`<magento_root>/app/etc/env.php`中的示例代码片段如下所示：

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

上述示例将会话文件存储在`/var/www/session`中

## `php.ini`中的示例

作为具有`root`权限的用户，打开您的`php.ini`文件并搜索`session.save_path`的值。 这标识了会话的存储位置。

## 管理会话大小

请参阅&#x200B;_用户指南_&#x200B;中的[会话管理](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/security/security-session-management)。

## 垃圾收集配置

为了清理过期的会话，系统根据`gc_probability / gc_divisor`指令计算的概率随机调用`gc` （_垃圾回收_）处理程序。 例如，如果分别将这些指令设置为`1/100`，则表示`1%`的概率（每100个请求一个垃圾收集调用的概率&#x200B;__）。

垃圾收集处理程序使用`gc_maxlifetime`指令，即会话被视为&#x200B;_垃圾桶_&#x200B;并可能被清理的秒数。

在某些操作系统(Debian/Ubuntu)上，默认`session.gc_probability`指令为`0`，该指令可阻止垃圾收集处理程序运行。

您可以覆盖`<magento_root>/app/etc/env.php`文件中`php.ini`文件中的`session.gc_`指令：

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

根据流量和商户网站的特定需求，配置会有所不同。
