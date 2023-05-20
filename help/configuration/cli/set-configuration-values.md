---
title: 設定設定值
description: 瞭解如何設定設定值，以及變更在Admin中鎖定的值。
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 0%

---

# 設定設定值

{{file-system-owner}}

本主題討論可用來執行下列作業的進階組態命令：

- 從命令列設定任何組態選項
- 可選擇鎖定任何設定選項，使其值無法在Admin中變更
- 變更在管理員中鎖定的設定選項

您可以使用這些命令來手動或使用指令碼設定Commerce設定。 您使用 _設定路徑_，亦即 `/` — 分隔的字串，可唯一識別該組態選項。 您可以在下列參照中找到組態路徑：

- [敏感和系統專屬設定路徑參考](../reference/config-reference-sens.md)
- [付款設定路徑參考](../reference/config-reference-payment.md)
- [一般設定路徑參考](../reference/config-reference-general.md)
- [Commerce Enterprise B2B擴充功能設定路徑參考](../reference/config-reference-b2b.md)

您可以在下列時間設定值：

- 安裝Commerce之前，您只能設定預設範圍的設定值，因為它是唯一的有效範圍。

- 安裝Commerce後，您可以設定任何網站或商店檢視範圍的設定值。

使用下列命令：

- `bin/magento config:set` 依其設定路徑設定任何非敏感設定值
- `bin/magento config:sensitive:set` 依其設定路徑設定任何敏感設定值
- `bin/magento config:show` 顯示儲存的組態值；加密設定的值顯示為星號

## 必要條件

若要設定組態值，您必須至少知道下列其中一項：

- 設定路徑
- 若要設定特定範圍的組態值，您必須知道範圍代碼。

   若要設定預設範圍的設定值，您不需要執行任何動作。

### 尋找設定路徑

請參閱下列參考資料：

- [敏感和系統專屬設定路徑參考](../reference/config-reference-sens.md)
- [付款設定路徑參考](../reference/config-reference-payment.md)
- [其他設定路徑參考](../reference/config-reference-general.md)
- [Commerce Enterprise B2B擴充功能設定路徑參考](../reference/config-reference-b2b.md)

### 尋找範圍代碼

您可以在Commerce資料庫或Commerce管理員中找到範圍代碼。

**若要在管理員中尋找範圍代碼**：

1. 以可檢視網站和商店檢視的使用者身分登入管理員。
1. 按一下 **[!UICONTROL Stores]** >設定> **[!UICONTROL All Stores]**.
1. 在右窗格中，按一下網站或商店檢視的名稱以檢視其代碼。

   下圖顯示範例網站程式碼。

   ![從管理員取得網站或商店檢視代碼](../../assets/configuration/website-code.png)

1. 繼續使用 [設定值](#set-values).

**在資料庫中尋找範圍代碼**：

網站和商店檢視的範圍程式碼會儲存在的Commerce資料庫中 `store_website` 和 `store` 表格。

1. 連線至Commerce資料庫。

   ```bash
   mysql -u <Commerce database username> -p
   ```

1. 輸入下列命令：

   ```shell
   use <Commerce database name>;
   ```

   ```shell
   SELECT * FROM store;
   ```

   ```shell
   SELECT * FROM store_website;
   ```

   範例結果如下：

   ```terminal
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   使用中的值 `code` 欄。

1. 繼續下一節。

## 設定值

**設定系統特定組態值**：

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**設定敏感組態值**：

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

下表說明 `set` 命令引數：

| 引數 | 說明 |
| --- | --- |
| `--scope` | 設定的範圍。 可能的值包括 `default`， `website`，或 `store`. 預設值為 `default`. |
| `--scope-code` | 設定的範圍代碼（網站代碼或商店檢視代碼） |
| `-e or --lock-env` | 鎖定值，使其無法在管理員中編輯，或變更已在管理員中鎖定的設定。 命令會將值寫入 `<Commerce base dir>/app/etc/env.php` 檔案。 |
| `-c or --lock-config` | 鎖定值，使其無法在管理員中編輯，或變更已在管理員中鎖定的設定。 命令會將值寫入 `<Commerce base dir>/app/etc/config.php` 檔案。 此 `--lock-config` 選項覆寫 `--lock-env` 如果您同時指定兩個選項。 |
| `path` | _必填_. 設定路徑 |
| `value` | _必填_. 設定的值 |

>[!INFO]
>
>截至Commerce 2.2.4， `--lock-env` 和 `--lock-config` 選項會取代 `--lock` 選項。
>
>如果您使用 `--lock-env` 或 `--lock-config` 選項來設定或變更值，您必須使用 [`bin/magento app:config:import` 命令](../cli/import-configuration.md) 以在存取「管理員」或「店面」之前匯入設定。

如果您輸入不正確的設定路徑，此命令會傳回錯誤

```text
The "wrong/config/path" does not exist
```

如需詳細資訊，請參閱下列其中一節：

- [設定可在管理員中編輯的設定值](#set-configuration-values-that-can-be-edited-in-the-admin)
- [設定無法在管理員中編輯的設定值](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### 設定可在管理員中編輯的設定值

使用 `bin/magento config:set` _不含_ `--lock-env` 或 `--lock-config` 將值寫入資料庫。 您透過此方式設定的值可在Admin中編輯。

以下是設定存放區基底URL的一些範例：

設定預設範圍的基底URL：

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

設定基礎URL `base` 網站：

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

設定基礎URL `test` 存放區檢視：

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### 設定無法在管理員中編輯的設定值

如果您使用 `--lock-env`  選項如下所示，該命令會將組態值儲存在 `<Commerce base dir>/app/etc/env.php` 和會停用「管理員」中用於編輯此值的欄位。

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

您可以使用 `--lock-env` 在未安裝Commerce時用來設定設定值的選項。 不過，您只能設定預設範圍的值。

>[!INFO]
>
>此 `env.php` 檔案是系統專屬的。 您不應該將它轉移給其他系統。 您可以使用它來覆寫資料庫中的組態值。 例如，您可以從另一個系統取得資料庫傾印並覆寫 `base_url` 和其他值，因此您不必修改資料庫。

如果您使用 `--lock-config` 選項，組態值會儲存在 `<Commerce base dir>/app/etc/config.php`. 在管理員中編輯此值的欄位已停用。

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

您可以使用 `--lock-config` 以設定未安裝Commerce時的設定值。 不過，您只能設定預設範圍的值。

>[!INFO]
>
>您可以轉移 `config.php` 至另一個系統，以使用相同的組態值。 例如，如果您有測試系統，則使用相同的 `config.php` 表示您不必再次設定相同的設定值。

## 顯示組態設定的值

命令選項：

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

位置

- `--scope` 是設定的範圍（預設、網站、商店）。 預設值為 `default`
- `--scope-code` 是設定的範圍代碼（網站代碼或商店檢視代碼）
- `path` 是格式為first_part/second_part/third_part/etc (_必填_)

>[!INFO]
>
>此 `bin/magento config:show` 命令會顯示下列專案的值 [加密的值](../reference/config-reference-sens.md) 以一連串星號表示： `******`.

### 範例

**顯示所有儲存的組態**：

```bash
bin/magento config:show
```

結果：

```terminal
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**顯示「 」的所有已儲存組態 `base` 網站**：

```bash
bin/magento config:show --scope=websites --scope-code=base
```

結果：

```terminal
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**顯示預設範圍的基底URL**：

```bash
bin/magento config:show web/unsecure/base_url
```

結果：

```terminal
web/unsecure/base_url - http://example.com/
```

**若要顯示的基礎URL `base` 網站**：

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

結果：

```terminal
web/unsecure/base_url - http://example-for-website.com/
```

**若要顯示的基礎URL `default` 儲存**：

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

結果：

```terminal
web/unsecure/base_url - http://example-for-store.com/
```
