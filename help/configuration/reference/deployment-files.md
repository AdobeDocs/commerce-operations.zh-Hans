---
title: 用於部署的組態檔
description: 瞭解設定檔案如何用於安裝Commerce應用程式。
feature: Configuration, Deploy
exl-id: 772a6814-6b18-4f8f-b31e-72faf790ff37
source-git-commit: b40d2bd4d466782ba5bc1b29ee8681756d9e85cc
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# 用於部署的組態檔

Adobe Commerce提供組態檔，可讓您輕鬆自訂元件及建立組態型別以擴充預設功能。 部署組態程式包含安裝的共用及系統特定組態。 Commerce的部署設定會分為 [`app/etc/config.php`](../reference/config-reference-configphp.md) 和 [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` 是 _已共用_ 設定檔。
此檔案包含已安裝模組、主題和語言套件的清單，以及共用組態設定。

   將此檔案簽入至原始檔控制，並將其用於您的開發、測試和生產系統。

- `app/etc/env.php` 包含安裝環境專屬的設定。

一起， `config.php` 和 `env.php` 稱為商務 _部署設定_ 因為檔案是在安裝期間建立的，且是啟動Commerce應用程式所需。

>[!INFO]
>
>此 [!DNL Commerce 2] 部署設定取代 `local.xml` 在 [!DNL Magento 1.x].

與其他不同 [模組組態檔](../reference/module-files.md)時，Commerce部署設定會在初始化期間載入記憶體、不會與任何其他檔案合併，且無法擴充。 (`config.php` 和 `env.php` 但會相互合併。)

## 有關部署設定的詳細資訊

`config.php` 和 `env.php` 是傳回 [多維度關聯陣列](https://www.w3schools.com:443/php/php_arrays.asp)，這基本上是設定引數和值的階層式排列。

在這個陣列的最上層有 _設定區段_. 區段具有由任意索引鍵區分的任意內容（純量值或巢狀陣列），其中索引鍵和值配對均由Commerce架構定義。

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) 僅提供這些區段的存取權，但不允許您延伸它們。

在下一個階層層級中，每個區段中的專案會根據模組順序定義排序，此定義是透過合併所有模組的組態檔案（已停用的模組除外）而取得。

以下各節討論部署設定的結構和內容：

- 管理已安裝的模組
- 系統特定設定

## 管理已安裝的模組

此 `config.php` 檔案包含已安裝模組的清單。 Adobe Commerce提供命令列和網頁型公用程式來管理模組（安裝、解除安裝、啟用、停用或升級）。

範例：

- 解除安裝元件： [`bin/magento setup:uninstall`](../../installation/tutorials/uninstall-modules.md)
- 檢查元件的狀態： [`bin/magento module:status`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#modulestatus)
- 啟用或停用元件： [`bin/magento module:disable`](../../installation/tutorials/manage-modules.md)， [`bin/magento module:enable`](../../installation/tutorials/manage-modules.md).

> _config.php_

```php
return array (
  'modules' =>
  array (
    'Magento_Core' => 1,
    'Magento_Store' => 1,
    'Magento_Theme' => 1,
    'Magento_Authorization' => 1,
    'Magento_Directory' => 1,
    'Magento_Backend' => 1,
    'Magento_Backup' => 1,
    'Magento_Eav' => 1,
    'Magento_Customer' => 1,
...
  ),
);
```

值 `1` 或 `0` 指示模組是啟用還是停用。

Commerce應用程式無法辨識已停用的模組；換言之，它們不會參與合併設定、相依性插入、事件、外掛程式等。 停用的模組不會修改店面或管理員，也不會影響路由。

已停用的模組與程式碼庫中缺少模組的唯一實際差異在於，自動載入器找到已停用的模組，且其類別和常數可用於在其他程式碼中重複使用。
