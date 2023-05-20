---
title: 技術細節
description: 閱讀有關管道部署的技術細節、設定型別和建議的工作流程。
exl-id: a396d241-f895-4414-92af-3abf3511e62a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 0%

---

# 技術細節

本主題討論Commerce 2.2及更高版本中管道部署的技術實作詳細資訊。 改進功能可分成下列幾個方面：

- [設定管理](#configuration-management)
- [管理員中的變更](#changes-in-the-admin)
- [安裝並移除cron](#install-and-remove-cron)

本主題也會討論 [建議的工作流程](#recommended-workflow) 用於管道部署，並提供一些範例來協助您瞭解其運作方式。

開始之前，請先檢閱 [您的開發、建置和生產系統的先決條件](../deployment/prerequisites.md).

## 設定管理

若要讓您同步化及維護開發及生產系統的組態，請使用下列覆寫配置。

![如何決定設定變數值](../../assets/configuration/override-flow-diagram.png)

如圖表所示，組態值會以下列順序使用：

1. 環境變數（如果存在）會覆寫所有其他值。
1. 從共用組態檔 `env.php` 和 `config.php`. 中的值 `env.php` 覆寫中的值 `config.php`.
1. 從儲存在資料庫中的值。
1. 如果這些來源中沒有任何值，則會使用預設值或NULL。

### 管理共用設定

共用設定儲存在 `app/etc/config.php`，這應該是在原始檔控制中。

在開發的管理員(或雲端基礎結構上的Adobe Commerce)中設定共用設定 _整合_)系統並將設定寫入 `config.php` 使用 [`magento app:config:dump` 命令](../cli/export-configuration.md).

### 管理系統特定設定

系統特定設定儲存在 `app/etc/env.php`，應 _not_ 在原始檔控制中。

在開發(或雲端基礎結構整合上的Adobe Commerce)系統的管理員中設定系統特定的設定，並將設定寫入 `env.php` 使用 [`magento app:config:dump` 命令](../cli/export-configuration.md).

此命令也會將敏感設定寫入 `env.php`.

### 管理敏感設定

敏感設定也會儲存在 `app/etc/env.php`.

您可以透過下列任何方式管理敏感設定：

- 環境變數
- 將敏感設定儲存在 `env.php` 在生產系統上使用 [`magento config:set:sensitive` 命令](../cli/set-configuration-values.md)

### 在Admin中鎖定的組態設定

中的任何組態設定 `config.php` 或 `env.php` 已在「管理員」中鎖定；也就是說，這些設定無法在「管理員」中變更。
使用 [`magento config:set` 或 `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) 命令來變更設定 `config.php` 或 `env.php` 檔案。

## 商務管理員

管理員在生產模式中會表現出以下行為：

- 您無法在「管理員」中啟用或停用快取型別
- 開發人員設定無法使用(**商店** >設定> **設定** >進階> **開發人員**)，包括：

   - 縮制CSS、JavaScript和HTML
   - 合併CSS和JavaScript
   - 伺服器端或使用者端LESS編譯
   - 內嵌翻譯
   - 如先前所述，任何組態設定 `config.php` 或 `env.php` 已鎖定，無法在管理員中編輯。
   - 您只能將管理員地區設定變更為已部署主題使用的語言

      下圖顯示 **帳戶設定** > **介面地區設定** 「管理員」中的清單，只顯示兩個已部署的區域設定：

      ![您只能將管理員地區設定變更為已部署地區設定](../../assets/configuration/split-deploy-admin-locale.png)

- 您無法使用Admin變更任何範圍的地區設定。

   建議您先進行這些變更，然後再切換至生產模式。

   您仍然可以使用環境變數或 `config:set` 包含路徑的CLI命令 `general/locale/code`.

## 安裝並移除cron

在2.2版中，我們首次提供 [`magento cron:install` 命令](../cli/configure-cron-jobs.md). 此命令會將crontab設定為執行命令的使用者。

此外，您可以使用 `magento cron:remove` 命令。

## 建議的管道部署工作流程

下圖顯示我們建議您如何使用管道部署來管理設定。

![建議的管道部署工作流程](../../assets/configuration/split-deploy-workflow.png)

### 開發系統

在您的開發系統上，您在「管理員」中進行設定變更，並產生共用設定， `app/etc/config.php` 以及系統特定組態， `app/etc/env.php`. 將Commerce程式碼和共用設定檢查到原始檔控制中，並將其推送到組建伺服器。

您還應在開發系統上安裝擴充功能並自訂Commerce程式碼。

在您的開發系統上：

1. 在「管理員」中設定設定。

1. 使用 `magento app:config:dump` 將組態寫入檔案系統的命令。

   - `app/etc/config.php` 是共用組態，包含所有設定 _例外_ 敏感和系統專屬設定。 此檔案應在原始檔控制中。
   - `app/etc/env.php` 是系統專屬的組態，其中包含特定系統專屬的設定（例如，主機名稱和連線埠號碼）。 此檔案應 _not_ 在原始檔控制中。

1. 將修改後的程式碼和共用設定新增至原始檔控制。

1. 若要在開發時移除產生的php程式碼和靜態資產檔案，請執行以下命令：

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

執行清除資產的命令後，Commerce會產生工作檔案。

>[!WARNING]
>
>請謹慎使用上述方法。 刪除 `.htacces`s檔案於 `generated` 或 `pub` 資料夾可能會導致問題。

### 建置系統

組建系統會編譯程式碼，並針對在Commerce中註冊的主題產生靜態檢視檔案。 它不需要連線至Commerce資料庫；只需要Commerce程式碼基底。

在您的建置系統上：

1. 從原始檔控制提取共用設定檔。
1. 使用 `magento setup:di:compile` 編譯程式碼的命令。
1. 使用 `magento setup:static-content:deploy -f` 更新靜態檔案檢視檔案的命令。
1. 將更新簽入原始檔控制中。

>[!INFO]
>
>另請參閱 [靜態檢視檔案的部署策略](../cli/static-view-file-strategy.md).

### 生產系統

在您的生產系統（即您的即時商店）上，您會從原始檔控制提取產生的資產和程式碼更新，並使用命令列或環境變數設定系統專屬和敏感的組態設定。

在您的生產系統上：

1. 啟動維護模式。
1. 從原始檔控制提取程式碼和設定更新。
1. 如果您使用Adobe Commerce，請停止佇列背景工作。
1. 使用 `magento app:config:import` 在生產系統中匯入組態變更的命令。
1. 如果您安裝的元件變更了資料庫綱要，請執行 `magento setup:upgrade --keep-generated` 更新資料庫架構和資料，保留產生的靜態檔案。
1. 若要設定系統特定的設定，請使用 `magento config:set` 命令或環境變數。
1. 若要設定敏感設定，請使用 `magento config:sensitive:set` 命令或環境變數。
1. 清理(也稱為 _排清_)快取。
1. 結束維護模式。

## 設定管理命令

我們提供下列指令來協助您管理設定：

- [`magento app:config:dump`](../cli/export-configuration.md) 將管理員組態設定寫入 `config.php` 和 `env.php` （敏感設定除外）
- [`magento config:set`](../cli/set-configuration-values.md) 在生產系統上設定系統特定設定的值。

   使用選填的 `--lock` 在Admin中鎖定選項的選項（也就是讓設定無法編輯）。 如果設定已鎖定，請使用 `--lock` 選項以變更設定。

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) 在生產系統上設定敏感設定的值。
- [`magento app:config:import`](../cli/import-configuration.md) 匯入組態變更來源： `config.php` 和 `env.php` 至生產系統。

## 設定管理範例

此段落顯示管理組態的範例，讓您瞭解變更的方式。 `config.php` 和 `env.php`.

### 變更預設地區設定

本區段顯示對所做的變更 `config.php` 當您使用管理員(**商店** >設定> **設定** >一般> **一般** > **地區設定選項**)。

在管理員中進行變更後，請執行 `bin/magento app:config:dump` 將值寫入 `config.php`. 此值會寫入 `general` 陣列位於 `locale` 做為下列的程式碼片段 `config.php` 顯示：

```php
'general' =>
    array (
        'locale' =>
        array (
            'code' => 'en_US',
            'timezone' => 'America/Chicago',
            'weight_unit' => 'kgs'
        )
    )
```

### 變更數個組態設定

本節討論如何進行下列設定變更：

- 新增網站、商店和商店檢視(**商店** >設定> **所有商店**)
- 變更預設電子郵件網域(**商店** >設定> **設定** >客戶> **客戶設定**)
- 設定PayPal API使用者名稱和API密碼(**商店** >設定> **設定** >銷售> **付款方法** > **PayPal** > **必要的PayPal設定**)

在管理員中進行變更後，請執行 `bin/magento app:config:dump` 在您的開發系統上。 這次，並非所有變更都會寫入 `config.php`；事實上，只有網站、商店和商店檢視會寫入該檔案，如下列程式碼片段所示。

### config.php

`config.php` 包含：

- 網站、商店和商店檢視的變更。
- 非系統特定搜尋引擎設定
- 不敏感的PayPal設定
- 通知您從中省略的敏感設定的註解 `config.php`

`websites` 陣列：

```php
      'new' =>
      array (
        'website_id' => '2',
        'code' => 'new',
        'name' => 'New website',
        'sort_order' => '0',
        'default_group_id' => '2',
        'is_default' => '0',
      ),
```

`groups` 陣列：

```php
      2 =>
      array (
        'group_id' => '2',
        'website_id' => '2',
        'code' => 'newstore',
        'name' => 'New store',
        'root_category_id' => '2',
        'default_store_id' => '2',
      ),
```

`stores` 陣列：

```php
     'newview' =>
      array (
        'store_id' => '2',
        'code' => 'newview',
        'website_id' => '2',
        'group_id' => '2',
        'name' => 'New store view',
        'sort_order' => '0',
        'is_active' => '1',
      ),
```

`payment` 陣列：

```php
      'payment' =>
      array (
        'paypal_express' =>
        array (
          'active' => '0',
          'in_context' => '0',
          'title' => 'PayPal Express Checkout',
          'sort_order' => NULL,
          'payment_action' => 'Authorization',
          'visible_on_product' => '1',
          'visible_on_cart' => '1',
          'allowspecific' => '0',
          'verify_peer' => '1',
          'line_items_enabled' => '1',
          'transfer_shipping_options' => '0',
          'solution_type' => 'Mark',
          'require_billing_address' => '0',
          'allow_ba_signup' => 'never',
          'skip_order_review_step' => '1',
        ),
```

### env.php

預設的電子郵件網域系統特定組態設定會寫入 `app/etc/env.php`.

兩者都不會寫入PayPal設定，因為 `bin/magento app:config:dump` 命令未寫入敏感設定。 您必須使用下列命令在生產系統上設定PayPal設定：

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
