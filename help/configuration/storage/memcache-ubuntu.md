---
title: 在Ubuntu上设置memcached
description: 在Ubuntu上安装和配置memcached。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---


# 在Ubuntu上设置memcached

本节提供了在Ubuntu上安装memcached的说明。

>[!INFO]
>
>Adobe建议使用memcached版本3.0.5或更高版本。

由于PHP不支持内存缓存，因此必须安装PHP的扩展才能使用它。 有两个PHP扩展可用，对要使用的进行解码很重要：

- `memcache` (_no d_) — 旧的常用扩展，不会定期维护。
的 `memcache` 当前扩展 _不_ 使用7菲律宾比索。 请参阅 [内存缓存的PHP文档](https://www.php.net/manual/en/book.memcache.php).

   确切的名称是 `php5-memcache` 为乌本图。

- `memcached` (_带有`d`_) — 与PHP 7兼容的较新且维护的扩展。 请参阅 [Memcached的PHP文档](https://www.php.net/manual/en/book.memcached.php).

   确切的名称是 `php5-memcached` 为乌本图。

## 在Ubuntu上安装和配置memcached

**在Ubuntu上安装和配置memcached**:

1. 作为用户， `root` 权限，输入以下命令：

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. 更改的memcached配置设置 `CACHESIZE` 和 `-l`:

   1. 打开 `/etc/memcached.conf` 在文本编辑器中。
   1. 找到 `-m` 参数。
   1. 至少将其值更改为 `1GB`
   1. 找到 `-l` 参数。
   1. 将其值更改为 `127.0.0.1` 或 `localhost`
   1. 将更改保存到 `memcached.conf` 并退出文本编辑器。
   1. 重新启动memcached。

      ```bash
      service memcached restart
      ```

1. 重新启动Web服务器。

   对于Apache， `service apache2 restart`

1. 继续下一节。

## 在安装Magento之前验证Memcached的工作

Adobe建议先测试memcached，以确保它在安装Commerce之前可正常工作。 这样做只需几分钟时间，并且以后可以简化故障排除。

### 验证Web服务器是否识别了memcached

要验证Web服务器是否识别Memcached，请执行以下操作：

1. 创建 `phpinfo.php` 文件：

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. 在Web浏览器中转到该页面。 例如：

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. 确保memcached显示如下：

   ![确认Web服务器识别了Memcached](../../assets/configuration/memcache.png)

   验证您使用的是Memcached 3.0.5或更高版本。

   如果未显示Memcached，请重新启动Web服务器并刷新浏览器页面。 如果仍未显示，请验证您是否安装了 `php-pecl-memcached` 扩展。

### 验证memcached是否可以缓存数据

此测试使用PHP脚本来验证memcached是否可以存储和检索缓存数据。

有关此测试的更多信息，请参阅 [如何在Ubuntu教程中安装和使用Memcache](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

创建 `cache-test.php` 在web服务器的docroot中，包含以下内容：

```php
$meminstance = new Memcached();

$meminstance->addServer("<memcached hostname or ip>", <memcached port>);

$result = $meminstance->get("test");

if ($result) {
    echo $result;
} else {
    echo "No matching key found. Refresh the browser to add it!";
    $meminstance->set("test", "Successfully retrieved the data!") or die("Could not save anything to memcached...");
}
```

其中 `<memcached hostname or ip>` 是 `localhost`, `127.0.0.1`，或memcache主机名或IP地址。 的 `<memcached port>` 是监听端口；默认情况下， `11211`.

在Web浏览器中转到该页面。 例如

```http
http://192.0.2.1/cache-test.php
```

首次转到页面时，将显示以下内容： `No matching key found. Refresh the browser to add it!`

刷新浏览器。 消息将更改为 `Successfully retrieved the data!`

最后，您可以使用Telnet查看内存缓存密钥：

```bash
telnet localhost <memcache port>
```

在提示时，输入

```shell
stats items
```

结果类似于以下内容：

```terminal
STAT items:2:number 1
STAT items:2:age 106
STAT items:2:evicted 0
STAT items:2:evicted_nonzero 0
STAT items:2:evicted_time 0
STAT items:2:outofmemory 0
STAT items:2:tailrepairs 0
STAT items:2:reclaimed 0
STAT items:2:expired_unfetched 0
STAT items:2:evicted_unfetched 0
```

刷新Memcached存储并退出Telnet:

```shell
flush_all
```

```shell
quit
```

[有关Telnet测试的其他信息](https://darkcoding.net/software/memcached-list-all-keys/)
