---
title: 在CentOS上设置memcached
description: 在CentOS上安装和配置memcached。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---


# 在CentOS上设置memcached

本节提供了在CentOS上安装Memcached的说明。 有关其他信息，请参阅 [memcachedwiki](https://github.com/memcached/old-wiki).

>[!INFO]
>
>Adobe建议使用最新的稳定memcached版本（目前为memcached 3.1.3）。

由于PHP不支持内存缓存，因此必须安装PHP的扩展才能使用它。 有两个PHP扩展可用，对要使用的进行解码很重要：

- `memcache` (_no d_) — 旧的常用扩展，不会定期维护。
的 `memcache` 当前扩展 _不_ 使用7菲律宾比索。 请参阅 [内存缓存的PHP文档](https://www.php.net/manual/en/book.memcache.php).

   确切的名称是 `php-pecl-memcache` 的URL。

- `memcached` (_带有`d`_) — 与PHP 7兼容的较新且维护的扩展。 请参阅 [Memcached的PHP文档](https://www.php.net/manual/en/book.memcached.php).

   确切的名称是 `php-pecl-memcached` 的URL。

## 在CentOS上安装和配置memcached

要在CentOS上安装Memcached，请以用户身份执行以下任务 `root` 权限：

1. 安装memcached及其依赖项：

   ```bash
   yum -y update
   ```

   ```bash
   yum install -y libevent libevent-devel
   ```

   ```bash
   yum install -y memcached
   ```

   ```bash
   yum install -y php-pecl-memcache
   ```

   >[!INFO]
   >
   >上述命令的语法可能取决于您使用的包存储库。 例如，如果您使用WebTatic和PHP 5.6，请输入 `yum install -y php56w-pecl-memcache`. 使用 `yum search memcache|grep php` 以查找相应的包名称。


1. 更改的memcached配置设置 `CACHESIZE` 和 `OPTIONS`:

   1. 打开 `/etc/sysconfig/memcached` 在文本编辑器中。
   1. 找到的值 `CACHESIZE` 并将其更改为至少1 GB。 例如：

      ```config
      CACHESIZE="1GB"
      ```

   1. 找到的值 `OPTIONS` 并将其更改为 `localhost` 或 `127.0.0.1`

1. 将更改保存到 `memcached` 并退出文本编辑器。
1. 重新启动memcached。

   ```bash
   service memcached restart
   ```

1. 重新启动Web服务器。

   对于Apache:

   ```bash
   service httpd restart
   ```

1. 继续下一节。

## 在安装Commerce之前验证Memcached的工作

Adobe建议先测试memcached，以确保它在安装Commerce之前可正常工作。 这样做只需几分钟时间，并且以后可以简化故障排除。

### 验证Web服务器是否识别了memcached

要验证Web服务器是否识别Memcached，请执行以下操作：

1. 创建 `phpinfo.php` 文件：

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. 在Web浏览器中转到该页面。

   例如， `http://192.0.2.1/phpinfo.php`

1. 确保memcache显示如下：

![确认Web服务器识别内存缓存](../../assets/configuration/memcache.png)

验证您使用的是Memcached 3.0.5或更高版本。

如果内存缓存未显示，请重新启动Web服务器并刷新浏览器页面。 如果仍未显示，请验证您是否安装了 `php-pecl-memcache` 扩展。

### 创建由MySQL数据库和PHP脚本组成的memcache测试

测试使用MySQL数据库、表和数据来验证是否可以检索数据库数据并将其存储在内存缓存中。 PHP脚本首先搜索缓存。 如果结果不存在，脚本将查询数据库。 在原始数据库完成查询后，脚本使用 `set` 命令。

[有关此测试的更多详细信息](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

创建MySQL数据库：

```bash
mysql -u root -p
```

在 `mysql` 提示，输入以下命令：

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

创建 `cache-test.php` 在web服务器的docroot中：

```php
$meminstance = new Memcached();

$meminstance->addServer('<memcached hostname or ip>', <memcached port>);

$query = "select id from example where name = 'new_data'";
$querykey = "KEY" . md5($query);

$result = $meminstance->get($querykey);

if (!$result) {
   try {
        $dbh = new PDO('mysql:host=localhost;dbname=memcache_test','memcache_test','memcache_test');
        $dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
        $result = $dbh->query("select id from example where name = 'new_data'")->fetch();
        $meminstance->set($querykey, $result, 0, 600);
        print "got result from mysql\n";
        return 0;
    } catch (PDOException $e) {
        die($e->getMessage());
    }
}
print "got result from memcached\n";
return 0;
```

其中 `<memcached hostname or ip>` 是 `localhost`, `127.0.0.1`，或memcache主机名或IP地址。 的 `<memcached port>` 是监听端口；默认情况下， `11211`.

从命令行中运行脚本。

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

第一个结果是 `got result from mysql`. 这意味着密钥在Memcached中不存在，但是从MySQL中检索。

第二个结果是 `got result from memcached`，用于验证值是否已成功存储在memcached中。

最后，您可以使用Telnet查看内存缓存密钥：

```bash
telnet localhost <memcache port>
```

在提示时，输入

```bash
stats items
```

结果类似于以下内容：

```terminal
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

刷新内存缓存并退出Telnet:

```bash
flush_all
```

```bash
quit
```

[有关Telnet测试的其他信息](https://darkcoding.net/software/memcached-list-all-keys/)
