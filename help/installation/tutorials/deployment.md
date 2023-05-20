---
title: 建立或更新部署設定
description: 請依照下列步驟管理您的Adobe Commerce或Magento Open Source部署設定。
exl-id: 2cdde735-0c70-44e8-b2ee-ffb874c1c443
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# 建立或更新部署設定

使用此命令沒有先決條件。

## 建立或更新部署設定

[部署設定](../../configuration/reference/deployment-files.md) 提供應用程式初始化及啟動時所需的資訊。

在下列情況下，可以使用此命令：

* 您先前已安裝應用程式，且想要修改部署設定
* 您只要建立部署組態，並以其他方式繼續安裝
* 若要更新部署設定，而不影響其他任何專案

命令選項：

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

下表討論安裝引數和值的意義。

| 引數 | 值 | 必填？ |
|--- |--- |--- |
| `--backend-frontname` | 統一資源識別碼([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2))以存取Admin。<br><br>為避免利用漏洞，建議您不要使用常見的字詞，例如「管理員」、「後端」。 管理員URI可包含英數字元和底線字元(`_`)。 | 否 |
| `--db-host` | 使用下列任一：<br><br> — 資料庫伺服器的完整主機名稱或IP位址。<br><br>- `localhost` （預設）或 `127.0.0.1` 如果資料庫伺服器與Web伺服器位於相同主機上。 localhost表示MySQL使用者端程式庫使用UNIX通訊端連線到資料庫。 `127.0.0.1` 導致使用者端資料庫使用TCP通訊協定。 如需通訊端的詳細資訊，請參閱 [PHP PDO_MYSQL檔案](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**注意：** 您可以選擇在其主機名稱中指定資料庫伺服器連線埠，例如 `www.example.com:9000` | 否 |
| `--db-name` | 您要安裝資料庫表格的資料庫執行處理名稱。<br><br>預設為 `magento2`. | 否 |
| `--db-user` | 資料庫執行處理擁有者的使用者名稱。<br><br>預設為 `root`. | 否 |
| `--db-password` | 資料庫執行處理擁有者的密碼。 | 否 |
| `--db-prefix` | 只有在資料庫執行個體中已經有Adobe Commerce和Magento Open Source表格時，才使用這個選項。<br><br>在此情況下，請使用首碼來識別此安裝的表格。 有些客戶有一個以上的Adobe Commerce或Magento Open Source執行個體在伺服器上執行，且所有表格都在相同的資料庫中。<br><br>首碼的長度最多可為5個字元。 它必須以字母開頭，並且只能包含字母、數字和底線字元。<br><br>此選項可讓這些客戶與多個Adobe Commerce或Magento Open Source安裝共用資料庫伺服器。 | 否 |
| `--session-save` | 使用下列任一：<br><br>- `db` 若要將工作階段資料儲存在 [資料庫](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). 如果您有叢集資料庫，請選擇資料庫儲存空間；否則，與檔案式儲存空間相比，可能不會有多大好處。<br><br>- `files` 將工作階段資料儲存在檔案系統中。 除非檔案系統存取緩慢、您有叢集資料庫，或您想要將工作階段資料儲存在Redis中，否則檔案式工作階段儲存體是適當的。<br><br>- `redis` 將工作階段資料儲存在 [將Redis用於工作階段儲存](../../configuration/cache/config-redis.md). 如果您使用Redis作為預設或頁面快取，則必須已安裝Redis。 | 否 |
| `--key` | 如果您有金鑰，請指定要加密的金鑰 [敏感資料](#sensitive-data) 在資料庫中。 如果您沒有，應用程式會為您產生一個。 | 否 |
| `--db-init-statements` | 進階MySQL設定引數。 連線到MySQL資料庫時，使用資料庫初始化陳述式執行。<br><br>預設為 `SET NAMES utf8;`.<br><br>請參閱參考資料，類似於 [這個](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) 之後再設定任何值。 | 否 |
| `--http-cache-hosts` | 要向其傳送清除請求的HTTP快取閘道主機的逗號分隔清單。 （例如Varnish伺服器）。 使用此引數可指定要在相同請求中清除的一或多個主機。 （您只有一個主機或多個主機並不重要。）<br><br>格式必須為 `<hostname or ip>:<listen port>`，您可在此省略 `<listen port>` 如果是連線埠80。 例如， `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. 請勿以空格字元分隔主機。 | 否 |

## 匯入設定資料

設定生產系統時，最好從匯入組態設定 `config.php` 和 `env.php` 到資料庫中。
這些設定包括設定路徑和值、網站、商店、商店檢視和主題。

匯入網站、商店、商店檢視和主題後，您可以在生產系統上建立產品屬性，並將其套用至網站、商店和商店檢視。

在生產系統上，執行以下命令以從組態檔案匯入資料(`config.php` 和 `env.php`)至資料庫：

```bash
bin/magento app:config:import [-n, --no-interaction]
```

選填 `[-n, --no-interaction]` 旗標可讓命令在不進行其他確認的情況下執行。

如需其他資訊，請檢視 [從組態檔匯入資料](../../configuration/cli/import-configuration.md)

### 敏感資料

{{$include /help/_includes/sensitive-data.md}}
