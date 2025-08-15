---
title: 设置Ubuntu上的内存缓存
description: 在Ubuntu上安装和配置内存缓存。
feature: Configuration, Cache, Storage
exl-id: 831193d2-3e81-472c-9b87-78a8d52959b4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# 设置Ubuntu上的内存缓存

本节提供在Ubuntu上安装内存缓存的说明。

>[!INFO]
>
>Adobe建议使用memcached版本3.0.5或更高版本。

由于PHP对memcache没有本机支持，因此您必须安装扩展以便PHP使用它。 有两个可用的PHP扩展，请务必解码要使用哪个PHP扩展：

- `memcache` (_no d_) — 不是定期维护的较旧但常用的扩展。
当前`memcache`扩展&#x200B;_不适用于PHP 7。_&#x200B;请参阅有关memcache[的](https://www.php.net/manual/en/book.memcache.php)PHP文档。

  Ubuntu的确切名称为`php5-memcache`。

- `memcached` （_带`d`_） — 与PHP 7兼容的更新和维护的扩展。 请参阅有关memcached[的](https://www.php.net/manual/en/book.memcached.php)PHP文档。

  Ubuntu的确切名称为`php5-memcached`。

## 在Ubuntu上安装和配置内存缓存

**要在Ubuntu上安装和配置memcached**：

1. 作为具有`root`权限的用户，输入以下命令：

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. 更改`CACHESIZE`和`-l`的memcached配置设置：

   1. 在文本编辑器中打开`/etc/memcached.conf`。
   1. 找到`-m`参数。
   1. 将其值更改为至少`1GB`
   1. 找到`-l`参数。
   1. 将其值更改为`127.0.0.1`或`localhost`
   1. 将更改保存到`memcached.conf`并退出文本编辑器。
   1. 重新启动memcached。

      ```bash
      service memcached restart
      ```

1. 重新启动Web服务器。

   对于Apache，`service apache2 restart`

1. 继续下一部分。

## 在安装Magento之前验证memcached的工作原理

Adobe建议测试memcached，以确保它在安装Commerce之前正常工作。 执行此操作只需要几分钟的时间，并且以后可以简化故障排除。

### 验证Web服务器是否识别memcached

要验证Web服务器是否能够识别memcached：

1. 在Web服务器的docroot中创建`phpinfo.php`文件：

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. 转到Web浏览器中的该页面。 例如：

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. 确保memcached按如下方式显示：

   ![确认Web服务器可识别memcached](../../assets/configuration/memcache.png)

   验证您是否使用memcached版本3.0.5或更高版本。

   如果memcached未显示，请重新启动Web服务器并刷新浏览器页面。 如果仍然不显示，请验证是否已安装`php-pecl-memcached`扩展。

### 验证memcached是否可以缓存数据

此测试使用PHP脚本来验证memcached是否可以存储和检索缓存数据。

有关此测试的更多信息，请参阅[如何在Ubuntu上安装和使用Memcache教程](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04)。

在Web服务器的docroot中创建`cache-test.php`，内容如下：

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

其中`<memcached hostname or ip>`是`localhost`、`127.0.0.1`或memcache主机名或IP地址。 `<memcached port>`是侦听端口；默认情况下，`11211`。

在Web浏览器中转到该页面。 例如

```http
http://192.0.2.1/cache-test.php
```

第一次转到该页面时，会显示以下内容： `No matching key found. Refresh the browser to add it!`

刷新浏览器。 消息更改为`Successfully retrieved the data!`

最后，您可以使用Telnet查看memcache密钥：

```bash
telnet localhost <memcache port>
```

在提示下，输入

```shell
stats items
```

结果类似于以下内容：

```
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

刷新内存缓存存储并退出Telnet：

```shell
flush_all
```

```shell
quit
```

[有关Telnet测试的其他信息](https://darkcoding.net/software/memcached-list-all-keys/)
