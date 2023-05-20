---
title: 移除或更新範例資料模組
description: 請依照下列步驟管理Adobe Commerce和Magento Open Source範例資料模組。
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# 移除或更新範例資料模組

本主題說明如何：

* [移除範例資料模組](#remove-sample-data-modules) 從Adobe Commerce或Magento Open Source安裝 `composer.json`. 此選項會 *not* 從資料庫移除範例資料。

* [準備更新範例資料](#prepare-to-update-sample-data) (例如，在更新Magento應用程式之前)。

## 移除範例資料模組

輸入下列命令：

```bash
bin/magento sampledata:remove
```

範例資料模組的完整清單如下：

Adobe Commerce和Magento Open Source：

* `magento/module-bundle-sample-data`
* `magento/module-catalog-rule-sample-data`
* `magento/module-catalog-sample-data`
* `magento/module-cms-sample-data`
* `magento/module-configurable-sample-data`
* `magento/module-customer-sample-data`
* `magento/module-downloadable-sample-data`
* `magento/module-grouped-product-sample-data`
* `magento/module-msrp-sample-data`
* `magento/module-offline-shipping-sample-data`
* `magento/module-product-links-sample-data`
* `magento/module-review-sample-data`
* `magento/module-sales-rule-sample-data`
* `magento/module-sales-sample-data`
* `magento/module-sample-data`
* `magento/module-swatches-sample-data`
* `magento/module-tax-sample-data`
* `magento/module-theme-sample-data`
* `magento/module-widget-sample-data`
* `magento/module-wishlist-sample-data`
* `magento/sample-data-media`

僅限Adobe Commerce：

* `magento/module-customer-balance-sample-data`
* `magento/module-gift-card-sample-data`
* `magento/module-gift-registry-sample-data`
* `magento/module-multiple-wishlist-sample-data`
* `magento/module-target-rule-sample-data`

## 準備更新範例資料

此命令可讓您在更新Adobe Commerce或Magento Open Source之前更新範例資料。

若要準備要更新的範例資料，請輸入以下命令：

```bash
bin/magento sampledata:reset
```

之後， [更新應用程式](../tutorials/uninstall.md#update-the-application).
