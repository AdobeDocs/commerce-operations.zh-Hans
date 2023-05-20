---
title: 最佳化CSS和JS資源檔案
description: 瞭解如何從管理員或命令列合併Adobe Commerce專案的CSS和JavaScript (JS)檔案，並加以縮制。
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# 最佳化資源檔案

若要獲得回應速度較快的Commerce網站，請最佳化CSS和JavaScript (JS)資源檔案，並消除轉譯器封鎖資源。

- **最佳化CSS和JS檔案** — 藉由設定Adobe Commerce將個別檔案合併、縮制及繫結至單一檔案，減少載入CSS和JavaScript (JS)檔案所需的時間。
- **消除轉譯器封鎖資源** — 考慮內聯提供關鍵JS和CSS功能，並延遲所有非關鍵JS/CSS樣式。 如需指引，請參閱 [消除轉譯器封鎖資源](https://web.dev/render-blocking-resources/).

## 受影響的產品和版本

[所有支援的版本，2.3和更新版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署
- Magento Open Source

## 合併或縮制CSS檔案

將CSS和JavaScript (JS)檔案合併、縮制和繫結為單一檔案，可以減少載入CSS和JS檔案所需的時間。

>[!IMPORTANT]
>
>雲端基礎結構上的Adobe Commerce一律會在生產模式中執行，否則無法進行設定，因此您必須使用命令列方法來啟用合併、縮制和捆綁。

### 使用管理員

若要啟用CSS合併或縮制，請前往 [!UICONTROL **管理員** > **商店** > **設定** > **設定** > **進階** > **開發人員** > **CSS設定**].

### 使用命令列

若要在雲端基礎結構的Adobe Commerce中啟用CSS合併：

1. 在本機執行此命令：

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. 將變更提交至 `app/etc/config.php` 檔案並重新部署。

若要在雲端基礎結構的Adobe Commerce中啟用CSS縮制：

1. 在本機執行此命令：

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. 將變更提交至 `app/etc/config.php` 檔案並重新部署。

## 最小化JS檔案

### 使用管理員

於 *管理員* 側欄，前往 **商店** > **設定** > **設定** > **進階** > **開發人員** > **JavaScript設定**.

### 使用命令列

若要在雲端基礎結構的Adobe Commerce中啟用JS縮制：

1. 在本機執行此命令：

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. 將變更提交至 `app/etc/config.php` 檔案並重新部署。

## 合併及捆綁JS檔案

您可以在Commerce管理員中開啟合併或繫結（合併和繫結無法同時啟用）： [!UICONTROL **商店** > **設定** > **設定** > **進階** > **開發人員** > **JavaScript設定**].

您也可以從命令列啟用Adobe Commerce內建組合（基本組合）：

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## 其他資訊

- [使用者端最佳化設定](../../../performance/configuration.md#client-side-optimization-settings)
- [使用手冊：最佳化資源檔案](https://docs.magento.com/user-guide/system/file-optimization.html)
- [前端開發人員指南：CSS合併、縮制和網站效能](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [進階JavaScript套裝](../../../performance/advanced-js-bundling.md)
