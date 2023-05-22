---
title: 靜態檢視檔案的部署策略
description: 閱讀Commerce應用程式的部署策略。
feature: Configuration, Deploy, Extensions
exl-id: 12ebbd36-f813-494f-9515-54ce697ca2e4
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# 靜態檢視檔案的部署策略

部署靜態檢視檔案時，您可以選擇三種可用策略之一。 其中每個選項都針對不同使用案例提供最佳部署結果：

- [標準](#standard-strategy)：一般部署程式。
- [快速](#quick-strategy) (_預設_)：在部署多個地區設定的檔案時，將部署所需的時間減到最少。
- [壓縮](#compact-strategy)：將發佈檢視檔案所佔用的空間減到最少。

以下各節說明每個策略的實作詳細資訊和功能。

## 標準策略

使用標準策略時，會部署所有套件的所有靜態檢視檔案，也就是由處理 [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php).

如需詳細資訊，請參閱 [部署靜態檢視檔案](../cli/static-view-file-deployment.md).

## 快速策略

快速策略會執行下列動作：

1. 對於每個主題，選擇一個任意語言環境，並部署此語言環境的所有檔案，例如在標準策略中。
1. 對於主題的所有其他區域設定：

   1. 會定義並部署覆寫已部署地區設定的檔案。
   1. 所有其他檔案在所有地區設定中都被視為類似，並從部署的地區設定中複製。

>[!INFO]
>
>作者： _相似_，是指與地區、主題或區域無關的檔案。 這些檔案可能包含CSS、影像和字型。

雖然有許多檔案重複，但此方法可將多個地區設定所需的部署時間減到最少。

## 壓縮策略

壓縮策略可藉由將類似檔案儲存在中來避免檔案重複 `base` 子目錄。

為獲得最佳化結果，已分配了三個可能相似性的範圍：區域、主題和地區。 此 `base` 系統會為這些範圍的所有組合建立子目錄。

檔案會根據下列模式部署至這些子目錄。

| 圖樣 | 說明 |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | 特定區域、佈景主題和區域設定的特定檔案 |
| `<area>/<theme>/default` | 特定區域特定主題的所有區域設定類似的檔案。 |
| `<area>/Magento/base/<locale>` | 特定區域和地區設定的特定檔案，但所有主題都類似。 |
| `<area>/Magento/base/default` | 特定區域的特定檔案，但所有主題和區域設定都類似。 |
| `base/Magento/base/<locale>` | 所有區域和主題都相似的檔案，但特定於特定地區設定。 |
| `base/Magento/base/default` | 所有區域、主題和區域設定都類似。 |

### 對應已部署的檔案

壓縮策略中使用的部署方法表示檔案繼承自基本主題和區域設定。 這些繼承關係會儲存在區域、主題和區域設定的每個組合的地圖檔案中。 PHP和JS有單獨的對應檔案：

- `map.php`
- `requirejs-map.js`

此 `map.php` 檔案使用者 [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) 以建置正確的URL。

此 `requirejs-map.js` 由使用 `baseUrlResolver` RequireJS的外掛程式。

範例： `map.php`：

```php?start_inline=1
return [
    'Magento_Checkout::cvv.png' => [
        'area' => 'frontend',
        'theme' => 'Magento/luma',
        'locale' => 'en_US',
    ],
    '...' => [
        'area' => '...',
        'theme' => '...',
        'locale' => '...'
    ]
];
```

範例： `requirejs-map.js`：

```js
require.config({
    "config": {
       "baseUrlInterceptor": {
            "jquery.js": "../../../../base/Magento/base/en_US/"
        }
    }
});
```

## 擴充功能開發人員的提示

若要建置靜態檢視檔案的URL，請使用 [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244).

請勿使用URL串連，以避免在頁面轉譯期間找不到靜態檔案且未顯示靜態檔案的問題。
