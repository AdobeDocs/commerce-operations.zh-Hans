---
title: 快速入門內部部署
description: 請依照下列步驟，在您擁有的基礎架構上安裝Adobe Commerce或Magento Open Source。
exl-id: a93476e8-2b30-461a-91df-e73eb1a14d3c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 0%

---

# 快速入門內部部署

我們使用 [Composer](https://getcomposer.org/) 管理Adobe Commerce和Magento Open Source元件及其相依性。 使用Composer來取得Adobe Commerce和Magento Open Source中繼，可提供下列優點：

- 重複使用協力廠商程式庫，而不用與原始程式碼捆綁
- 使用元件式架構搭配強大的相依性管理，減少擴充功能衝突和相容性問題
- 遵守 [PHP-Framework互通性群組(FIG)](https://www.php-fig.org/) 標準
- 使用其他元件重新封裝Magento Open Source
- 在生產環境中使用Adobe Commerce或Magento Open Source軟體

>[!NOTE]
>
>參與Magento Open Source的開發人員應使用 [git型](https://developer.adobe.com/commerce/contributor/guides/install/) 安裝方法。

## 必要條件

在繼續之前，您必須執行下列動作：

- 全部完成 [必要條件任務](system-requirements.md).
- [安裝撰寫器](https://getcomposer.org/download/).
- 取得 [驗證金鑰](prerequisites/authentication-keys.md) 前往Adobe Commerce和Magento Open Source撰寫器存放庫。

## 以檔案系統擁有者的身分登入

瞭解所有權、許可權和檔案系統擁有者，請參閱 [所有權和許可權主題概觀](prerequisites/file-system/overview.md).

若要切換至檔案系統擁有者：

1. 以具有寫入檔案系統許可權的使用者身分登入應用程式伺服器，或切換至該使用者。

   如果您使用bash shell，則可以使用以下語法切換到檔案系統擁有者並同時輸入命令：

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   如果檔案系統擁有者不允許登入，您可以執行下列動作：

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. 若要從任何目錄執行CLI命令，請新增 `<app_root>/bin` 至您的系統 `PATH`.

   由於shell的語法不同，請參考參考如 [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   CentOS的bash shell範例：

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   您可以選擇以下列方式執行命令：

   - `cd <app_root>/bin` 並以下列身分執行 `./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>` 是網頁伺服器docroot的子目錄

## 取得中繼資料

若要取得Adobe Commerce或Magento Open Source中繼資料：

1. 以或切換至以下身分登入應用程式伺服器： [檔案系統擁有者](prerequisites/file-system/overview.md).
1. 變更至Web伺服器docroot目錄，或您設定為虛擬主機docroot的目錄。
1. 使用Adobe Commerce或Magento Open Source中繼資料建立撰寫器專案。

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   出現提示時，輸入您的驗證金鑰。 公開金鑰和私密金鑰會在以下位置建立和設定： [Commerce Marketplace](https://marketplace.magento.com/customer/account/login/).

   如果您遇到錯誤，例如 `Could not find package...` 或 `...no matching package found`，請確定您的命令中沒有拼字錯誤。 如果您仍然遇到錯誤，則可能未獲授權下載Adobe Commerce。 連絡人 [Adobe Commerce支援](https://support.magento.com/hc/en-us) 以取得協助。

   另請參閱 [疑難排除](https://support.magento.com/hc/en-us/articles/360033818091) 以取得更多錯誤的說明。

   >[!NOTE]
   >
   >Adobe Commerce客戶可在正式發行(GA)日期前兩週存取修補程式。 搶鮮版套件只能透過Composer取得。 在GA之前，您無法存取開發人員入口網站或GitHub上的發行前版本。 如果您在Composer中找不到這些套件，請聯絡Adobe Commerce支援。

### 範例 — 次要版本

次要發行包含新功能、品質修正和安全性修正。 使用Composer指定次要版本。 例如，若要指定Adobe Commerce 2.4.5中繼套件：

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5 <install-directory-name>
```

### 範例 — 品質修補程式

品質修補程式主要包含功能性 _和_ 安全性修正。 不過，它們有時也可能包含向後相容的新功能。 使用Composer下載品質修補程式。 例如，若要指定Adobe Commerce 2.4.5中繼套件：

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5 <install-directory-name>
```

### 範例 — 安全性修補程式

安全性修補程式僅包含安全性修正。 其設計可讓升級程式更快、更輕鬆。

安全性修補程式使用撰寫器命名慣例 `2.4.5-px`. 使用Composer指定修補程式。 例如，若要下載Adobe Commerce 2.4.5-p1中繼資料：

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5-p1 <install-directory-name>
```

## 設定檔案許可權

您必須先設定網頁伺服器群組的讀寫許可權，才能安裝Adobe Commerce或Magento Open Source。 這是必要的，以便命令列可以將檔案寫入檔案系統。

```terminal
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## 安裝應用程式

您必須使用命令列安裝Adobe Commerce或Magento Open Source。

此範例假設安裝目錄名為 `magento2ee`，則 `db-host` 在同一部電腦上(`localhost`)，且 `db-name`， `db-user`、和 `db-password` 全部 `magento`：

```bash
bin/magento setup:install \
--base-url=http://localhost/magento2ee \
--db-host=localhost \
--db-name=magento \
--db-user=magento \
--db-password=magento \
--admin-firstname=admin \
--admin-lastname=admin \
--admin-email=admin@admin.com \
--admin-user=admin \
--admin-password=admin123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1 \
--search-engine=opensearch \
--opensearch-host=os-host.example.com \
--opensearch-port=9200 \
--opensearch-index-prefix=magento2 \
--opensearch-timeout=15
```

>[!TIP]
>
>您可以使用自訂管理員URI `--backend-frontname` 選項。 但是，我們建議省略此選項，並允許安裝命令自動產生隨機URI。 駭客或惡意軟體更難利用隨機URI。 安裝完成時，URI會顯示在主控台中。

>[!TIP]
>
>如需CLI安裝選項的完整說明，請參閱 [從命令列安裝應用程式](advanced.md).

## 命令摘要

若要顯示完整的命令清單，請輸入：

```bash
bin/magento list
```

若要取得特定命令的說明，請輸入：

```bash
bin/magento help <command>
```

例如：

```bash
bin/magento help setup:install
```

```bash
bin/magento help cache:enable
```

下表總結了可用的命令。 命令僅以摘要形式顯示。 如需命令的詳細資訊，請按一下「命令」欄中的連結。

| 命令 | 說明 | 必要條件 |
|--- |--- |--- |
| `magento setup:install` | 安裝應用程式 | 無 |
| `magento setup:uninstall` | 移除應用程式。 | 已安裝應用程式 |
| `magento setup:upgrade` | 更新應用程式。 | 部署設定 |
| `magento maintenance:{enable/disable}` | 啟用或停用維護模式（在維護模式中，只有劐免IP地址可以存取管理員或店面）。 | 已安裝應用程式 |
| `magento setup:config:set` | 建立或更新部署設定。 | 無 |
| `magento module:{enable/disable}` | 啟用或停用模組。 | 無 |
| `magento setup:store-config:set` | 設定店面相關選項，例如基本URL、語言、時區。 | 部署設定 |
| `magento setup:db-schema:upgrade` | 更新資料庫結構。 | 部署設定 |
| `magento setup:db-data:upgrade` | 更新資料庫資料。 | 部署設定 |
| `magento setup:db:status` | 檢查資料庫是否為程式碼的最新版本。 | 部署設定 |
| `magento admin:user:create` | 建立管理員使用者。 | 您可以建立下列專案的使用者：<br><br>部署設定<br><br>至少啟用 `Magento_User` 和 `Magento_Authorization` 模組<br><br>資料庫(最簡單的方式是使用 `bin/magento setup:upgrade`) |
| `magento list` | 列出所有可用的指令。 | 無 |
| `magento help` | 提供指定命令的說明。 | 無 |

### 通用引數

以下引數是所有命令通用的引數。 這些命令可以在應用程式安裝之前或之後執行：

| 詳細版本 | 簡短版本 | 含義 |
|--- |--- |--- |
| `--help` | `-h` | 取得任何命令的說明。 例如， `./magento help setup:install` 或 `./magento help setup:config:set`. |
| `--quiet` | `-q` | 安靜模式；無輸出。 |
| `--no-interaction` | `-n` | 無互動式問題。 |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 詳細程度。 例如， `--verbose=3` 或 `-vvv` 顯示除錯詳細資訊，這是最詳細的輸出。 預設為 `--verbose=1` 或 `-v`. |
| `--version` | `-V` | 顯示此應用程式版本 |
| `--ansi` | 不適用 | 強制ANSI輸出 |
| `--no-ansi` | 不適用 | 停用ANSI輸出 |

>[!NOTE]
>
>恭喜！ 您已完成快速安裝。 需要更進階的說明嗎？ 請檢視我們的 [進階安裝](advanced.md) 指南。
