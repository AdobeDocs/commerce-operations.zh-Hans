---
title: 設定網站、商店和商店檢視的最佳實務
description: 瞭解設定網站、商店和商店檢視的最佳實務，以最大化網站效能。
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# 設定網站、商店和商店檢視的最佳實務

為獲得最佳網站效能，請在雲端基礎結構專案上為Adobe Commerce設定最多50個網站、50個商店和50個商店檢視。

>[!NOTE]
>
>針對雲端基礎結構上的Adobe Commerce，最佳實務尤其適用於生產環境（並可能適用於Staging on Pro架構，但受資源限制），其擁有的資源會比整合和開發環境多。 對於整合（Pro和Starter）和測試環境(Starter)，將商店檢視次數減少到5或10次以下（取決於技術審查）。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 改善效能的策略

如果您的專案需要許多網站、商店或商店檢視，您可以使用以下策略來改善效能：

- 將邏輯切換至類別以重新建構目錄
- 使用外部價格與價格管理系統(PMS)，將價目表與目錄資料分開。
- 使用替代noSQL資料儲存，例如Elasticsearch

## 對效能的潛在影響

網站和商店是目錄資料的倍數，因此擁有許多網站和商店可能會以下列方式負面影響網站效能：

- 較大的索引表格會增加完成索引作業所需的時間 [價格指數].
- 擷取應用程式設定的時間增加，會降低非快取目錄頁面的店面回應時間。
- 因為每個網站的資料會個別儲存，在管理員中完成「儲存」作業所需的時間會大幅增加。


## 其他資訊

- [瞭解網站、商店和商店檢視](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [設定多個網站或商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
