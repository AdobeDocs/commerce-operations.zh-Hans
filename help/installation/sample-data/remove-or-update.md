---
title: 删除或更新示例数据模块
description: 按照以下步骤管理Adobe Commerce示例数据模块。
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# 删除或更新示例数据模块

本主题讨论如何：

* [删除示例数据模块](#remove-sample-data-modules) 从Adobe Commerce安装 `composer.json`. 此选项会 *非* 从数据库中删除示例数据。

* [准备更新示例数据](#prepare-to-update-sample-data) (例如，在更新Magento应用程序之前)。

## 删除示例数据模块

输入以下命令：

```bash
bin/magento sampledata:remove
```

下面是示例数据模块的完整列表：

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

## 准备更新示例数据

此命令允许您在更新Adobe Commerce之前更新示例数据。

要准备样本数据以进行更新，请输入以下命令：

```bash
bin/magento sampledata:reset
```

之后， [更新应用程序](../tutorials/uninstall.md#update-the-application).
