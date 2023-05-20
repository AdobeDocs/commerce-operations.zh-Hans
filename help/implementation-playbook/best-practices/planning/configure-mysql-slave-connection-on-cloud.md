---
title: 設定MySQL從屬連線的最佳實務
description: 瞭解如何為部署在雲端基礎結構上的Adobe Commerce站台設定MySQL從屬連線。
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: d65bc80a-c4ec-4ea4-aff1-110592838201
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# 設定MySQL從屬連線的最佳實務

>[!NOTE]
>
>本文包含業界標準的軟體術語，有些人可能會覺得這些術語帶有種族主義、性別歧視或壓迫性，並且可能會讓讀者感到傷害、創傷或不受歡迎。 Adobe正致力於從我們的程式碼、檔案和使用者體驗中移除這些詞語。

對於部署在雲端基礎結構Pro架構上的Adobe Commerce網站，Adobe建議預設為資料庫啟用MYSQL從屬連線。

Adobe Commerce可以非同步方式讀取多個資料庫。 當您啟用MYSQL從屬連線時，Adobe Commerce會使用資料庫的唯讀連線，在非主節點上接收唯讀流量。 當只有一個節點處理讀寫流量時，透過負載平衡來改善效能。

## 受影響的版本

雲端基礎結構上的Adobe Commerce， Pro架構

## 設定MySQL從屬連線

在雲端基礎結構上的Adobe Commerce中，您可以透過設定 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) 變數。 將此變數設為true可自動使用資料庫的唯讀連線。

**啟用MySQL從屬連線的方式**：

1. 在本機工作站上，變更至專案目錄。

1. 在 `.magento.env.yaml` 檔案，設定 `MYSQL_USE_SLAVE_CONNECTION` 為true。

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. 認可 `.magento.env.yaml` 檔案變更並推送到遠端環境。

   成功完成部署後，雲端環境便會啟用MySQL從屬連線。

進一步瞭解如何透過覆寫您現有的Commerce設定來自訂雲端環境 [環境變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) 在 _雲端基礎結構上的Adobe Commerce指南_.

## 其他資訊

- [雲端基礎結構上Adobe Commerce中的MySQL高負載瓶頸](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [雲端基礎結構上Adobe Commerce的資料庫最佳實務](database-on-cloud.md)
