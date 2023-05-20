---
title: 進階內部部署安裝
description: 瞭解Adobe Commerce的進階安裝案例，或瞭解您所擁有的基礎架構Magento Open Source。
exl-id: e16e750a-e068-4a63-8ad9-62043e2a8231
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2406'
ht-degree: 0%

---

# 進階內部部署安裝

>[!TIP]
>
>遺失？ 需要協助嗎？ 嘗試我們的 [快速開始安裝](composer.md) 或 [投稿人安裝](https://developer.adobe.com/commerce/contributor/guides/install/) 指南。

>[!NOTE]
>
>如果您選擇啟用SELinux，請參閱 [SELinux和iptables](prerequisites/security.md).

## 命令列介面(CLI)

Adobe Commerce和Magento Open Source擁有單一命令列介面，用於安裝和設定工作： `<magento_root>/bin/magento`. 介面會執行多項工作，包括：

* 安裝（以及建立或更新資料庫架構、建立部署組態等相關工作）。
* 正在清除快取。
* 管理索引，包括重新索引。
* 建立翻譯字典和翻譯套件。
* 產生不存在類別（例如外掛程式的工廠和攔截器），產生物件管理員的相依性插入設定。
* 部署靜態檢視檔案。
* 從更少資源建立CSS。

其他優點：

* 單一命令(`<magento_root>/bin/magento list`)列出所有可用的安裝和設定命令。
* 根據Symfony提供一致的使用者介面。
* CLI可擴充，因此協力廠商開發人員可以「插入」至其中。 這還有另一個好處，就是消除了使用者的學習曲線。
* 已停用模組的命令不顯示。

本主題說明如何使用CLI安裝Adobe Commerce或Magento Open Source軟體。 如需有關設定的資訊，請參閱 [設定指南](../configuration/overview.md).

如有必要，安裝程式可以多次執行，因此您可以：

* 提供不同的值

   例如，在為Secure Sockets Layer (SSL)設定Web伺服器後，您可以執行安裝程式來設定SSL選項。

* 修正先前安裝中的錯誤
* 在其他資料庫執行個體中安裝Adobe Commerce或Magento Open Source

## 開始安裝之前

開始之前，請完成下列步驟：

* 確認您的系統符合中討論的需求 [系統需求](system-requirements.md).

* 全部完成 [必備條件](prerequisites/overview.md) 任務。

* 完成第一個安裝步驟。 另請參閱 [您的安裝或升級路徑](overview.md).

* 在您登入應用程式伺服器後， [切換到檔案系統擁有者](prerequisites/file-system/overview.md).

* 檢閱 [安裝快速入門](composer.md) 概述。

>[!NOTE]
>
>您必須從安裝Adobe Commerce或Magento Open Source `bin` 子目錄。

您可以使用不同的選項多次執行安裝程式，以完成如下的安裝工作：

* 分階段安裝 — 例如，在為Secure Sockets Layer (SSL)設定Web伺服器後，您可以再次執行安裝程式來設定SSL選項。

* 修正先前安裝中的錯誤。

* 在其他資料庫執行個體中安裝Adobe Commerce或Magento Open Source。

>[!NOTE]
>
>依照預設，如果您在相同資料庫執行個體中安裝軟體，安裝程式不會覆寫資料庫。 您可以使用選填的 `cleanup-database` 引數來變更此行為。

另請參閱 [更新、重新安裝、解除安裝](tutorials/uninstall.md).

### 安全安裝

{{$include /help/_includes/secure-install.md}}

## 安裝程式說明命令

您可以執行下列命令來尋找某些必要引數的值：

| 安裝程式引數 | 命令 |
| ------------------ | ------------------------------- |
| 語言 | bin/magento資訊:language:清單 |
| 貨幣 | bin/magento資訊:currency:清單 |
| 時區 | bin/magento資訊:timezone:清單 |

>[!NOTE]
>
>如果在執行這些命令時顯示錯誤，請確認已更新安裝相依性，如中所述 [更新安裝相依性](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## 從命令列安裝

install指令會使用以下格式：

```bash
bin/magento setup:install --<option>=<value> ... --<option>=<value>
```

下表說明安裝選項名稱和值。 如需安裝命令的範例，請參閱 [localhost安裝範例](#sample-localhost-installations).

>[!NOTE]
>
>包含空格或特殊字元的任何選項都必須用單引號或雙引號括住。

**管理員認證：**

下列選項會指定管理員使用者的使用者資訊和認證。

您可以在安裝期間或安裝後建立管理員使用者。 如果您在安裝期間建立使用者，則需要所有管理員認證變數。 另請參閱 [localhost安裝範例](#sample-localhost-installations).

下表提供許多但並非所有可用的安裝引數。 如需完整清單，請參閱 [命令列工具參考](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html).

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--admin-firstname` | 管理員使用者的名字。 | 是 |
| `--admin-lastname` | 管理員使用者的姓氏。 | 是 |
| `--admin-email` | 管理員使用者的電子郵件地址。 | 是 |
| `--admin-user` | 管理員使用者名稱。 | 是 |
| `--admin-password` | 管理員使用者密碼。 密碼長度必須至少為7個字元，且必須至少包含一個字母和數字字元。 我們建議使用更長、更複雜的密碼。 以單引號括住整個密碼字串。 例如， `--admin-password='A0b9%t3g'` | 是 |

**站台和資料庫組態選項：**

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--base-url` | 用於以下列任何格式存取管理員和店面的基本URL：<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**注意：** 配置(http://或https://)和結尾斜線都是必要的。<br><br>`<your install dir>` 是安裝Adobe Commerce或Magento Open Source軟體的docroot相對路徑。 根據您設定網頁伺服器和虛擬主機的方式，路徑可能是magento2或空白。<br><br>若要在localhost上存取Adobe Commerce或Magento Open Source，您可以使用 `http://127.0.0.1/<your install dir>/` 或 `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` 代表虛擬主機設定或虛擬化環境（如Docker）定義的基本URL。 例如，如果您以主機名稱設定虛擬主機 `magento.example.com`，您可以透過以下方式安裝軟體： `--base-url={{base_url}}` 和使用URL存取管理員，例如 `http://magento.example.com/admin`. | 是 |
| `--backend-frontname` | 用於存取管理員的統一資源識別碼(URI)。 您可以省略此引數，讓應用程式以下列模式為您產生隨機URI admin_jkhgdfq</code>.<br><br>基於安全考量，建議您使用隨機URI。 駭客或惡意軟體更難利用隨機URI。<br><br>URI會在安裝結束時顯示。 您稍後隨時可以使用 `bin/magento info:adminuri` 命令。<br><br>如果您選擇輸入值，建議您不要使用常見的字詞，例如admin、backend。 管理員URI可包含英數字元和底線字元(`_`)。 | 否 |
| `--db-host` | 使用下列任一：<br><br> — 資料庫伺服器的完整主機名稱或IP位址。<br><br>- `localhost` （預設）或 `127.0.0.1` 如果您的資料庫伺服器與web伺服器位於相同主機上。localhost表示MySQL使用者端程式庫使用UNIX通訊端來連線資料庫。 `127.0.0.1` 導致使用者端資料庫使用TCP通訊協定。 如需通訊端的詳細資訊，請參閱 [PHP PDO_MYSQL檔案](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**注意：** 您可以選擇在其主機名稱中指定資料庫伺服器連線埠，例如www.example.com:9000 | 是 |
| `--db-name` | 您要安裝資料庫表格的資料庫執行處理名稱。<br><br>預設為 `magento2`. | 是 |
| `--db-user` | 資料庫執行處理擁有者的使用者名稱。<br><br>預設為 `root`. | 是 |
| `--db-password` | 資料庫執行處理擁有者的密碼。 | 是 |
| `--db-prefix` | 只有在資料庫執行個體中已經有Adobe Commerce或Magento Open Source表格時，才使用。<br><br>在此情況下，請使用首碼來識別此安裝的表格。 有些客戶有一個以上的Adobe Commerce或Magento Open Source執行個體在伺服器上執行，且所有表格都在相同的資料庫中。<br><br>首碼的長度最多可為5個字元。 它必須以字母開頭，並且只能包含字母、數字和底線字元。<br><br>此選項可讓這些客戶與多個Adobe Commerce或Magento Open Source安裝共用資料庫伺服器。 | 否 |
| `--db-ssl-key` | 使用者端金鑰的路徑。 | 否 |
| `--db-ssl-cert` | 使用者端憑證的路徑。 | 否 |
| `--db-ssl-ca` | 伺服器憑證的路徑。 | 否 |
| `--language` | 用於管理員和店面的語言代碼。 (如果您尚未這樣做，您可以輸入來檢視語言代碼清單 `bin/magento info:language:list` 從bin目錄。) | 否 |
| `--currency` | 店面中使用的預設貨幣。 (如果尚未這樣做，您可以輸入以檢視貨幣清單 `bin/magento info:currency:list` 從bin目錄。) | 否 |
| `--timezone` | 在管理員和店面中使用的預設時區。 (如果尚未這樣做，您可以輸入 `bin/magento info:timezone:list` 從 `bin/` directory)。 | 否 |
| `--use-rewrites` | `1` 表示您對店面和管理程式中產生的連結使用網頁伺服器重寫。<br><br>`0` 停用使用web伺服器重寫。 這是預設值。 | 否 |
| `--use-secure` | `1` 允許在店面URL中使用安全通訊端層(SSL)。 在選取此選項之前，請確定您的網頁伺服器支援SSL。<br><br>`0` 停用SSL。 在此情況下，所有其他安全URL選項也假設為0。 這是預設值。 | 否 |
| `--base-url-secure` | 用於存取您的管理員和店面的安全基本URL，格式如下： `http[s]://<host or ip>/<your install dir>/` | 否 |
| `--use-secure-admin` | `1` 表示您使用SSL來存取管理員。 在選取此選項之前，請確定您的網頁伺服器支援SSL。<br><br>`0` 表示您未對管理員使用SSL。 這是預設值。 | 否 |
| `--admin-use-security-key` | 1讓應用程式使用隨機產生的索引鍵值來存取管理員和表單中的頁面。 這些金鑰值有助於防止跨網站指令碼偽造攻擊。 這是預設值。<br><br>`0` 停用金鑰。 | 否 |
| `--session-save` | 使用下列任一：<br><br>- `db` 將工作階段資料儲存在資料庫中。 如果您有叢集資料庫，請選擇資料庫儲存空間；否則，與檔案式儲存空間相比，可能不會有多大好處。<br><br>- `files` 將工作階段資料儲存在檔案系統中。 除非檔案系統存取緩慢、您有叢集資料庫，或您想要將工作階段資料儲存在Redis中，否則檔案式工作階段儲存體是適當的。<br><br>- `redis` 將工作階段資料儲存在Redis。 如果您使用Redis作為預設或頁面快取，則必須已安裝Redis。 如需設定Redis支援的其他資訊，請參閱將Redis用於工作階段儲存。 | 否 |
| `--key` | 如果您有金鑰，請指定金鑰來加密資料庫中的敏感資料。 如果您沒有，應用程式會為您產生一個。 | 是 |
| `--cleanup-database` | 若要在安裝Adobe Commerce或Magento Open Source之前刪除資料庫表格，請指定此引數（不含值）。 否則，資料庫將保持不變。 | 否 |
| `--db-init-statements` | 進階MySQL設定引數。 連線到MySQL資料庫時，使用資料庫初始化陳述式執行。 在設定任何值之前，請查閱與此類似的參考。<br><br>預設為 `SET NAMES utf8;`. | 否 |
| `--sales-order-increment-prefix` | 指定字串值，作為銷售訂單的前置詞。 通常，這用於保證付款處理者的唯一訂單編號。 | 否 |

**搜尋引擎設定選項：**

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--search-engine` | 用作搜尋引擎的Elasticsearch或OpenSearch版本。 預設值為 `elasticsearch7`. Elasticsearch5已過時，不建議使用。 | 否 |
| `--elasticsearch-host` | 執行Elasticsearch的主機名稱或IP位址。 預設值為 `localhost`. | 否 |
| `--elasticsearch-port` | 傳入HTTP請求的Elasticsearch連線埠。 預設值為 `9200`. | 否 |
| `--elasticsearch-index-prefix` | 識別Elasticsearch搜尋索引的前置詞。 預設值為 `magento2`. | 否 |
| `--elasticsearch-timeout` | 系統逾時前的秒數。 預設值為 `15`. | 否 |
| `--elasticsearch-enable-auth` | 啟用Elasticsearch伺服器上的驗證。 預設值為 `false`. | 否 |
| `--elasticsearch-username` | 向Elasticsearch伺服器驗證的使用者ID。 | 否，除非啟用驗證 |
| `--elasticsearch-password` | 用於向Elasticsearchserver進行驗證的密碼。 | 否，除非啟用驗證 |
| `--opensearch-host` | 執行OpenSearch的主機名稱或IP位址。 預設值為 `localhost`. | 否 |
| `--opensearch-port` | 傳入HTTP請求的OpenSearch連線埠。 預設值為 `9200`. | 否 |
| `--opensearch-index-prefix` | 識別OpenSearch搜尋索引的前置詞。 預設值為 `magento2`. | 否 |
| `--opensearch-timeout` | 系統逾時前的秒數。 預設值為 `15`. | 否 |
| `--opensearch-enable-auth` | 啟用OpenSearch伺服器上的驗證。 預設值為 `false`. | 否 |
| `--opensearch-username` | 用於向OpenSearch伺服器驗證的使用者ID。 | 否，除非啟用驗證 |
| `--opensearch-password` | 驗證OpenSearch伺服器的密碼。 | 否，除非啟用驗證 |

**[!DNL RabbitMQ]設定選項：**

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--amqp-host` | 請勿使用 `--amqp` 選項，除非您已設定 [!DNL RabbitMQ]. 另請參閱 [!DNL RabbitMQ] 安裝以取得關於安裝和設定的詳細資訊 [!DNL RabbitMQ].<br><br>主機名稱，其中 [!DNL RabbitMQ] 已安裝。 | 否 |
| `--amqp-port` | 用來連線的連線埠 [!DNL RabbitMQ]. 預設值為5672。 | 否 |
| `--amqp-user` | 用於連線到的使用者名稱 [!DNL RabbitMQ]. 不要使用預設使用者 `guest`. | 否 |
| `--amqp-password` | 用於連線的密碼 [!DNL RabbitMQ]. 不要使用預設密碼 `guest`. | 否 |
| `--amqp-virtualhost` | 用於連線的虛擬主機 [!DNL RabbitMQ]. 預設值為 `/`. | 否 |
| `--amqp-ssl` | 指示是否連線到 [!DNL RabbitMQ]. 預設值為 `false`. 另請參閱 [!DNL RabbitMQ] 瞭解設定SSL的相關資訊 [!DNL RabbitMQ]. | 否 |
| `--consumers-wait-for-messages` | 消費者是否應該等候佇列中的訊息？ 1 — 是，0 — 否 | 否 |

**鎖定組態選項：**

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--lock-provider` | 鎖定提供者名稱。<br><br>可用的鎖定提供者： `db`， `zookeeper`， `file`.<br><br>預設鎖定提供者： `db` | 否 |
| `--lock-db-prefix` | 使用時避免鎖定衝突的特定db首碼 `db` 鎖定提供者。<br><br>預設值： `NULL` | 否 |
| `--lock-zookeeper-host` | 使用時連線至Zookeeper叢集的主機與連線埠 `zookeeper` 鎖定提供者。<br><br>例如： `127.0.0.1:2181` | 是，如果您設定 `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper儲存鎖定的路徑。<br><br>預設路徑為： `/magento/locks` | 否 |
| `--lock-file-path` | 儲存檔案鎖定的路徑。 | 是，如果您設定 `--lock-provider=file` |

**消費者設定選項：**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>若要在安裝Adobe Commerce或Magento Open Source後啟用或停用模組，請參閱 [啟用和停用模組](tutorials/manage-modules.md).

**敏感資料：**

{{$include /help/_includes/sensitive-data.md}}

### localhost安裝範例

下列範例顯示使用各種選項在本機安裝Adobe Commerce的命令。

#### 範例1 — 使用管理員使用者帳戶進行基本安裝

下列範例會安裝包含下列選項的Adobe Commerce或Magento Open Source：

* 應用程式安裝在 `magento2` 與docroot開啟的網頁伺服器相關的目錄 `localhost` 而且管理員的路徑為 `admin`；因此：

   您的店面URL為 `http://127.0.0.1`

* 資料庫伺服器與Web伺服器位於相同的主機上。

   資料庫名稱為 `magento`，且使用者名稱和密碼都是 `magento`

* 使用伺服器重寫

* 管理員具有以下屬性：

   * 名字和姓氏為 `Magento User`
   * 使用者名稱為 `admin` 而且密碼是 `admin123`
   * 電子郵件地址為 `user@example.com`

* 預設語言為 `en_US` （美式英文）
* 預設貨幣為美元
* 預設時區為美國中部（美洲/芝加哥）
* OpenSearch 1.2安裝在 `os-host.example.com` 並在連線埠9200上連線

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

類似下列的訊息顯示指示安裝成功：

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### 範例2 — 無管理員使用者帳戶的基本安裝

您可以安裝Adobe Commerce或Magento Open Source，而不需要建立管理員使用者，如下列範例所示。

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

如果安裝成功，會顯示類似下列的訊息：

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

安裝後，您可以使用 `admin:user:create` 命令：
[建立或編輯管理員](tutorials/admin.md#create-or-edit-an-administrator)

#### 範例3 — 使用其他選項安裝

下列範例會安裝包含下列選項的Adobe Commerce或Magento Open Source：

* 應用程式安裝在 `magento2` 與docroot開啟的網頁伺服器相關的目錄 `localhost` 而且管理員的路徑為 `admin`；因此：

   您的店面URL為 `http://127.0.0.1`

* 資料庫伺服器與Web伺服器位於相同的主機上。

   資料庫名稱為 `magento`，且使用者名稱和密碼都是 `magento`

* 管理員具有以下屬性：

   * 名字和姓氏為 `Magento User`
   * 使用者名稱為 `admin` 而且密碼是 `admin123`
   * 電子郵件地址為 `user@example.com`

* 預設語言為 `en_US` （美式英文）
* 預設貨幣為美元
* 預設時區為美國中部（美洲/芝加哥）
* 安裝程式先清除資料庫，再安裝資料表和綱要
* 您可以使用銷售訂單增量前置詞 `ORD$` (因為它包含特殊字元 [`$`]，值必須括在雙引號中)
* 工作階段資料會儲存在資料庫中
* 使用伺服器重寫
* OpenSearch安裝在 `os-host.example.com` 並在連線埠9200上連線

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

>[!NOTE]
>
>您必須在單行上輸入指令，或如上例所示，使用 `\` 字元。

如果安裝成功，會顯示類似下列的訊息：

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```
