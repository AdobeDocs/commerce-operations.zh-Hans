---
title: 快取型別
description: 將快取前端與快取型別建立關聯。
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# 快取型別

下列步驟會逐步說明將快取前端與快取型別建立關聯的步驟。

## 步驟1：定義快取前端

商務應用程式具有 `default` 您可以用於任何快取前端 [快取型別](../cli/manage-cache.md#clean-and-flush-cache-types). 本節探討如何選擇性定義具有不同名稱的快取前端，如果您希望自訂前端，這會比較好。

>[!INFO]
>
>若要使用 `default` 快取型別，您不需要修改 `env.php` 完全；您會修改Commerce的全域 `di.xml`. 另請參閱 [低階快取選項](cache-options.md).

您必須指定自訂快取前端 `app/etc/env.php` 或Commerce的全域 `app/etc/di.xml`.

以下範例說明如何在 `env.php` 檔案，會覆寫 `di.xml` 檔案：

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<unique frontend id>' => [
             <cache options>
        ],
    ],
    'type' => [
         <cache type 1> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
    'type' => [
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

位置 `<unique frontend id>` 是用於識別您的前端和檔案的唯一名稱 `<cache options>` 是各種快取型別（資料庫、Redis等）專屬主題中討論的選項。

## 步驟2：設定快取

您可以在中指定前端和後端快取設定選項 `env.php` 或 `di.xml`. 此為選擇性工作。

`env.php` 範例：

```php?start_inline=1
'frontend' => <frontend_type>,
'frontend_options' => [
    <frontend_option> => <frontend_option_value>,
    ...
],
'backend' => <backend_type>,
'backend_options' => [
    <backend_option> => <backend_option_value>,
    ...
],
```

位置

- `<frontend_type>` 是低階前端快取型別。 指定與相容的類別名稱 `Zend\Cache\Core`.
若您省略 `<frontend_type>`， [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) 已使用。

- `<frontend_option>`， `<frontend_option_value>` 是Commerce架構在建立前端快取時以關聯陣列形式傳遞至前端快取的選項名稱和值。
- `<backend_type>` 是低階後端快取型別。 指定與相容的類別名稱 `Zend_Cache_Backend` 以及實作 `Zend_Cache_Backend_Interface`.
- `<backend_option>` 和 `<backend_option_value>` 是Commerce框架在建立後端Cache時，作為關聯陣列傳遞至後端快取的選項名稱和值。

請參閱 [Laminas檔案](https://docs.laminas.dev/) 以取得最新的Zend資訊。
