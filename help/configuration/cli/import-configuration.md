---
title: 從組態檔匯入資料
description: 從組態檔匯入Adobe Commerce組態設定。
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# 匯入組態設定

{{file-system-owner}}

當您使用Commerce 2.2設定生產系統時 [管道部署模型](../deployment/technical-details.md)，您必須 _匯入_ 組態設定來自 `config.php` 和 `env.php` 到資料庫中。
這些設定包括設定路徑和值、網站、商店、商店檢視和主題。

匯入網站、商店、商店檢視和主題後，您可以在生產系統上建立產品屬性，並將其套用至網站、商店和商店檢視。

>[!INFO]
>
>此 `bin/magento app:config:import` 命令不會處理儲存在環境變數中的設定。

## 匯入命令

在您的生產系統上，執行下列命令以從組態檔案匯入資料(`config.php` 和 `env.php`)至資料庫：

```bash
bin/magento app:config:import [-n, --no-interaction]
```

使用選填的 `[-n, --no-interaction]` 標幟以匯入資料而不進行任何互動。

如果您輸入 `bin/magento app:config:import` 若沒有選用標幟，您必須確認變更。

例如，如果設定檔案包含一個新網站和一個新商店，則會顯示以下訊息：

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

若要繼續匯入，請輸入 `yes`.

如果部署組態檔包含要匯入的一些資料，則會顯示類似下列的訊息：

```terminal
Start import:
Some information about importing
```

如果部署組態檔不包含任何要匯入的資料，則會顯示類似下列的訊息：

```terminal
Start import:
Nothing to import
```

## 我們匯入的內容

以下各節將詳細討論我們匯入的資料。

### 系統設定

Commerce直接使用中的值 `system` 中的陣列 `config.php` 或 `env.php` 檔案，而非匯入資料庫中，因為它們需要一些前置和後置處理動作。

例如，設定路徑的值 `web/secure/base_url` 必須透過後端模型驗證。

#### 後端模型

後端模型是處理系統組態變更的機制。
您在中定義後端模組 `<module_name>/adminhtml/system.xml`.

所有後端模型都必須擴充 [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) 類別。

當我們匯入後端模型時，不會儲存設定值。

### 網站、商店和商店群組設定

我們匯入下列型別的設定。
(這些設定位於 `scopes` 中的陣列 `config.php`.)

- `websites`：網站相關設定
- `groups`：儲存相關設定
- `stores`：存放區檢視相關設定

上述設定可透過下列模式匯入：

- `create`： `config.php` 包含新實體(`websites`， `groups`， `stores`)中不存在的URL。
- `update`： `config.php` 包含實體(`websites`， `groups`， `stores`)與生產環境不同的
- `delete`： `config.php` 會 _not_ 包含實體(`websites`， `groups`， `stores`)時，才會變更生產環境

>[!INFO]
>
>我們不會匯入與存放區相關聯的根類別。 您必須使用Commerce管理員將根類別與商店相關聯。

### 主題設定

主題設定包含您在Commerce系統中註冊的所有主題；資料直接來自 `theme` 資料庫表格。 (主題設定位於 `themes` 中的陣列 `config.php`.)

#### 主題資料的結構

陣列索引鍵是完整主題路徑： `area` + `theme path`

例如， `frontend/Magento/luma`.
`frontend` 為區域和 `Magento/luma` 是主題路徑。

陣列的值是有關佈景主題的資料：程式碼、標題、路徑、父系ID

完整範例：

```php?start_inline=1
'frontend/Magento/luma' =>
   array (
      'parent_id' => 'Magento/blank',
      'theme_path' => 'Magento/luma',
      'theme_title' => 'Magento Luma',
      'is_featured' => '0',
      'area' => 'frontend',
      'type' => '0',
      'code' => 'Magento/luma',
),
```

>[!INFO]
>
>- _主題註冊_. 如果主題資料定義於 `config.php` 但佈景主題的原始程式碼不存在於檔案系統中，佈景主題會遭忽略（亦即，未註冊）。
>- _主題移除_. 如果主題不存在於 `config.php` 但原始程式碼存在於檔案系統上，主題並未移除。

