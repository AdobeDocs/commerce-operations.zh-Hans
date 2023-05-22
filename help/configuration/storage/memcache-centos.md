---
title: 在CentOS上設定記憶體快取
description: 在CentOS上安裝並設定memcached。
feature: Configuration, Cache, Storage
exl-id: fc4ad18b-7e99-496e-aebc-1d7640d8716c
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# 在CentOS上設定記憶體快取

本節提供在CentOS上安裝memcached的說明。 如需詳細資訊，請參閱 [memcached wiki](https://github.com/memcached/old-wiki).

>[!INFO]
>
>Adobe建議使用最新的穩定memcached版本（目前memcached為3.1.3）。

由於PHP對memcache沒有原生支援，因此您必須安裝PHP擴充功能才能使用它。 有兩個可用的PHP擴充功能，請務必解碼要使用哪個：

- `memcache` (_否d_) — 舊版但常用的擴充功能，不會定期維護。
此 `memcache` 目前為擴充功能 _不會_ 使用PHP 7。 另請參閱 [memcache的PHP檔案](https://www.php.net/manual/en/book.memcache.php).

   確切的名稱為 `php-pecl-memcache` 適用於CentOS。

- `memcached` (_搭配`d`_) — 與PHP 7相容的更新和維護的擴充功能。 另請參閱 [memcached的PHP檔案](https://www.php.net/manual/en/book.memcached.php).

   確切的名稱為 `php-pecl-memcached` 適用於CentOS。

## 在CentOS上安裝並設定記憶體快取

若要在CentOS上安裝memcached，請以使用者身分執行以下工作 `root` 許可權：

1. 安裝memcached及其相依性：

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
   >上述命令的語法可能取決於您使用的套裝程式儲存區域。 例如，如果您使用網路和PHP 5.6，請輸入 `yum install -y php56w-pecl-memcache`. 使用 `yum search memcache|grep php` 以尋找適當的封裝名稱。


1. 變更的memcached組態設定 `CACHESIZE` 和 `OPTIONS`：

   1. 開啟 `/etc/sysconfig/memcached` 在文字編輯器中。
   1. 找到「 」的值 `CACHESIZE` 並將其變更為至少1 GB。 例如：

      ```config
      CACHESIZE="1GB"
      ```

   1. 找到「 」的值 `OPTIONS` 並將其變更為 `localhost` 或 `127.0.0.1`

1. 將變更儲存至 `memcached` 並退出文字編輯器。
1. 重新啟動memcached。

   ```bash
   service memcached restart
   ```

1. 重新啟動網頁伺服器。

   若為Apache：

   ```bash
   service httpd restart
   ```

1. 繼續下一節。

## 在安裝Commerce之前驗證memcached是否有效

Adobe建議先測試memcached以確保其可運作，然後再安裝Commerce。 只需幾分鐘即可完成，並可簡化後續的疑難排解。

### 確認網頁伺服器可辨識成員快取

若要確認網頁伺服器可辨識成員快取：

1. 建立 `phpinfo.php` 網頁伺服器docroot中的檔案：

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. 前往網頁瀏覽器中的該頁面。

   例如， `http://192.0.2.1/phpinfo.php`

1. 請確定memcache顯示如下：

![確認網頁伺服器可辨識成員快取](../../assets/configuration/memcache.png)

確認您使用的是memcached 3.0.5版或更新版本。

如果memcache未顯示，請重新啟動網頁伺服器並重新整理瀏覽器頁面。 如果仍然沒有顯示，請確認您已安裝 `php-pecl-memcache` 副檔名。

### 建立由MySQL資料庫和PHP指令碼組成的成員快取測試

此測試會使用MySQL資料庫、表格和資料，以確認您可以擷取資料庫資料並將其儲存在memcache中。 PHP指令碼會先搜尋快取。 如果結果不存在，指令碼會查詢資料庫。 原始資料庫完成查詢後，指令碼會使用 `set` 命令。

[此測試的更多詳細資料](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

建立MySQL資料庫：

```bash
mysql -u root -p
```

在 `mysql` 提示，輸入下列命令：

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

建立 `cache-test.php` 在網頁伺服器的docroot中：

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

位置 `<memcached hostname or ip>` 為 `localhost`， `127.0.0.1`，或成員快取主機名稱或IP位址。 此 `<memcached port>` 是監聽連線埠；依預設， `11211`.

從命令列執行指令碼。

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

第一個結果為 `got result from mysql`. 這表示該索引鍵不存在於memcached中，但它是從MySQL擷取的。

第二個結果為 `got result from memcached`，會驗證值是否已成功儲存在memcached中。

最後，您可以使用Telnet檢視memcache金鑰：

```bash
telnet localhost <memcache port>
```

出現提示時，輸入

```bash
stats items
```

結果類似下列：

```terminal
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

清除memcache儲存體並結束Telnet：

```bash
flush_all
```

```bash
quit
```

[Telnet測試的其他資訊](https://darkcoding.net/software/memcached-list-all-keys/)
