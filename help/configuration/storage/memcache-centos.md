---
title: 在CentOS上设置内存缓存
description: 了解如何在CentOS上安装和配置用于Adobe Commerce缓存的memcached。 了解设置说明和优化提示。
feature: Configuration, Cache, Storage
exl-id: fc4ad18b-7e99-496e-aebc-1d7640d8716c
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# 在CentOS上设置内存缓存

本节提供了在CentOS上安装内存缓存的说明。 有关详细信息，请参阅[memcached wiki](https://github.com/memcached/old-wiki)。

>[!INFO]
>
>Adobe建议使用最新的稳定memcached版本（当前为3.1.3 for memcached）。

由于PHP对memcache没有本机支持，因此您必须安装扩展以便PHP使用它。 有两个可用的PHP扩展，请务必解码要使用哪个PHP扩展：

- `memcache` (_no d_) — 不是定期维护的较旧但常用的扩展。
当前`memcache`扩展&#x200B;_不适用于PHP 7。_&#x200B;请参阅有关memcache[的](https://www.php.net/manual/en/book.memcache.php)PHP文档。

  对于CentOS，确切名称为`php-pecl-memcache`。

- `memcached` （_带`d`_） — 与PHP 7兼容的更新和维护的扩展。 请参阅有关memcached[的](https://www.php.net/manual/en/book.memcached.php)PHP文档。

  对于CentOS，确切名称为`php-pecl-memcached`。

## 在CentOS上安装和配置内存缓存

要在CentOS上安装memcached，请以具有`root`权限的用户身份执行以下任务：

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
   >上述命令的语法可能取决于您使用的程序包资料档案库。 例如，如果您使用webtatic和PHP 5.6，请输入`yum install -y php56w-pecl-memcache`。 使用`yum search memcache|grep php`查找相应的包名称。


1. 更改`CACHESIZE`和`OPTIONS`的memcached配置设置：

   1. 在文本编辑器中打开`/etc/sysconfig/memcached`。
   1. 找到`CACHESIZE`的值，并将其更改为至少1 GB。 例如：

      ```config
      CACHESIZE="1GB"
      ```

   1. 找到`OPTIONS`的值，并将其更改为`localhost`或`127.0.0.1`

1. 将更改保存到`memcached`并退出文本编辑器。
1. 重新启动memcached。

   ```bash
   service memcached restart
   ```

1. 重新启动Web服务器。

   对于Apache：

   ```bash
   service httpd restart
   ```

1. 继续下一部分。

## 在安装Commerce之前验证memcached的工作原理

Adobe建议测试memcached，以确保它在安装Commerce之前正常工作。 执行此操作只需要几分钟的时间，并且以后可以简化故障排除。

### 验证Web服务器是否识别memcached

要验证Web服务器是否能够识别memcached：

1. 在Web服务器的docroot中创建`phpinfo.php`文件：

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. 转到Web浏览器中的该页面。

   例如，`http://192.0.2.1/phpinfo.php`

1. 请确保memcache按以下方式显示：

![确认Web服务器识别了memcache](../../assets/configuration/memcache.png)

验证您是否使用memcached版本3.0.5或更高版本。

如果memcache未显示，请重新启动Web服务器并刷新浏览器页面。 如果仍然不显示，请验证是否已安装`php-pecl-memcache`扩展。

### 创建由MySQL数据库和PHP脚本组成的memcache测试

该测试使用MySQL数据库、表和数据来验证是否可以检索数据库数据并将其存储在memcache中。 PHP脚本首先搜索高速缓存。 如果结果不存在，脚本将查询数据库。 在原始数据库完成查询后，脚本使用`set`命令将结果存储在memcache中。

[有关此测试的更多详细信息](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

创建MySQL数据库：

```bash
mysql -u root -p
```

在`mysql`提示符下，输入以下命令：

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

在Web服务器的docroot中创建`cache-test.php`：

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

其中`<memcached hostname or ip>`是`localhost`、`127.0.0.1`或memcache主机名或IP地址。 `<memcached port>`是侦听端口；默认情况下，`11211`。

从命令行运行脚本。

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

第一个结果为`got result from mysql`。 这意味着memcached中不存在该键，但它是从MySQL中检索的。

第二个结果为`got result from memcached`，用于验证该值是否成功存储在memcached中。

最后，您可以使用Telnet查看memcache密钥：

```bash
telnet localhost <memcache port>
```

在提示下，输入

```bash
stats items
```

结果类似于以下内容：

```
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

刷新memcache存储并退出Telnet：

```bash
flush_all
```

```bash
quit
```

[有关Telnet测试的其他信息](https://darkcoding.net/software/memcached-list-all-keys/)
