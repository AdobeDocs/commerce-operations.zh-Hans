---
title: 工作階段儲存位置
description: 瞭解工作階段檔案儲存的位置。
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# 工作階段儲存位置

本主題說明如何找出工作階段檔案的儲存位置。 系統會使用以下邏輯來儲存工作階段檔案：

- 如果您已設定memcached，工作階段會儲存在RAM中；請參閱 [將記憶體快取用於工作階段儲存](memcached.md).
- 如果您已設定Redis，工作階段會儲存在Redis伺服器上；請參閱 [將Redis用於工作階段儲存](../cache/redis-session.md).
- 如果您使用預設的檔案式工作階段儲存，我們會依照顯示的順序將工作階段儲存在下列位置：

   1. 在中定義的目錄 [`env.php`](#example-in-envphp)
   1. 在中定義的目錄 [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` 目錄

## 中的範例 `env.php`

中的範常式式碼片段 `<magento_root>/app/etc/env.php` 如下：

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

上述範例會將工作階段檔案儲存在 `/var/www/session`

## 中的範例 `php.ini`

作為使用者，具有 `root` 許可權，開啟您的 `php.ini` 檔案並搜尋 `session.save_path`. 這會識別工作階段的儲存位置。

## 管理工作階段大小

請參閱 [工作階段管理](https://docs.magento.com/user-guide/stores/security-session-management.html) 在 _使用手冊_.

## 垃圾收集設定

若要清除過期的工作階段，系統會呼叫 `gc` (_垃圾收集_)處理常式，根據以下計算出的機率隨機進行： `gc_probability / gc_divisor` 指令。 例如，如果您將這些指示詞設為 `1/100` 分別表示下列兩種情況的機率： `1%` (_每100個請求一個垃圾收集呼叫的機率_)。

垃圾收集處理常式會使用 `gc_maxlifetime` directive — 工作階段被視為的秒數 _垃圾桶_ 並可能清除。

在某些作業系統上(Debian/Ubuntu)，預設值為 `session.gc_probability` 指示詞是 `0`，可防止垃圾收集處理常式執行。

您可以覆寫 `session.gc_` 指令來自 `php.ini` 中的檔案 `<magento_root>/app/etc/env.php` 檔案：

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

此設定會依流量和商家網站的特定需求而有所不同。
