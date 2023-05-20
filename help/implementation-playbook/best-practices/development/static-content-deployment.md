---
title: 靜態內容部署最佳實務
description: 瞭解如何避免靜態內容未出現在您的Adobe Commerce或Magento Open Source店面的問題。
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# 靜態內容部署最佳實務

本文介紹Adobe Commerce中的靜態內容部署(SCD)最佳實務，以協助避免靜態內容無法用於網站的問題。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

* 雲端基礎結構上的Adobe Commerce
* Adobe Commerce內部部署
* Magento Open Source

## 最佳實務

為避免靜態內容在您的網站上無法使用的問題，請遵循以下最佳實務，以確保您的靜態內容已正確設定和部署：

1. 請務必遵循部署准則：
   * 如需Adobe Commerce內部部署和Magento Open Source（所有版本）的相關資訊，請參閱 [部署概觀](../../../configuration/deployment/overview.md) （位於我們的開發人員檔案中）。
   * 如需雲端基礎結構上的Adobe Commerce （所有版本），請參閱 [雲端部署程式](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) 和 [靜態內容部署策略](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) （位於我們的開發人員檔案中）。

1. 針對雲端基礎結構上的Adobe Commerce （所有版本），請確保ece-tools使用的是最新版本。 請參閱： [更新ece-tools版本](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) （位於我們的開發人員檔案中）。
1. 對於雲端基礎結構上的Adobe Commerce （所有版本），請確定在建置階段而不是部署階段部署靜態內容。 請參閱： [存放區設定的組態管理 — 靜態內容部署效能](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) （位於我們的開發人員檔案中）。
1. 請確定您沒有長期執行的cron工作，並終止任何長期執行的cron程式。 長時間執行的cron工作可能會佔用CPU資源，並可能大幅增加部署時間。
1. 若為Adobe Commerce內部部署和Magento Open Source（所有版本），請檢查 `php` CLI中的程式可存取 `pub/static` 目錄。 否則，您可能會遇到靜態內容部署無法將檔案寫入該目錄的問題。 如需詳細資訊： [檔案系統存取許可權](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) （位於我們的開發人員檔案中）。
1. 確保 `generated` 目錄不是跨組建的共用目錄；否則，組建可能會隨機失敗。 如需詳細資訊：
   * Adobe Commerce內部部署和Magento Open Source（所有版本）： [技術細節](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) （位於我們的開發人員檔案中）。
   * 雲端基礎結構上的Adobe Commerce （所有版本）： [部署程式 — 第2階段：建置](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) （位於我們的開發人員檔案中）。

1. 檢查您的SCD策略。 此 *快速* 策略為預設值。 如需詳細資訊：
   * Adobe Commerce內部部署和Magento Open Source（所有版本）： [靜態檔案部署策略](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) （位於我們的開發人員檔案中）。
   * 雲端基礎結構上的Adobe Commerce （所有版本）： [部署變數 — SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) （位於我們的開發人員檔案中）。

## 其他資訊

在我們的開發人員檔案中：

* [靜態內容容器](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [靜態內容簽署](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [部署變數 — 靜態\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [部署流程](../../../performance/deployment-flow.md)
* [零停機部署](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [最佳化雲端部署](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)
