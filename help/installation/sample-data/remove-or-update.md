---
title: 删除或更新示例数据模块
description: 按照以下步骤管理Adobe Commerce和Magento Open Source示例数据模块。
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# 删除或更新示例数据模块

本主题讨论如何：

* [删除示例数据模块](#remove-sample-data-modules) 从Adobe Commerce或Magento Open Source安装 `composer.json`. 此选项会 *非* 从数据库中删除示例数据。

* [准备更新示例数据](#prepare-to-update-sample-data) (例如，在更新Magento应用程序之前)。

## 删除示例数据模块

输入以下命令：

```bash
bin/magento sampledata:remove
```

下面是示例数据模块的完整列表：

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

仅限Adobe Commerce：

* `magento/module-customer-balance-sample-data`
* `magento/module-gift-card-sample-data`
* `magento/module-gift-registry-sample-data`
* `magento/module-multiple-wishlist-sample-data`
* `magento/module-target-rule-sample-data`

## 准备更新示例数据

此命令允许您在更新Adobe Commerce或Magento Open Source之前更新示例数据。

要准备样本数据以进行更新，请输入以下命令：

```bash
bin/magento sampledata:reset
```

之后， [更新应用程序](../tutorials/uninstall.md#update-the-application).
