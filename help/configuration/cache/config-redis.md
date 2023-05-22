---
title: 設定Redis
description: 取得Redis功能的概觀並開始您的Redis設定。
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# 設定Redis

Redis功能包括：

- PHP工作階段儲存
- 標籤型快取清理，不含 `foreach` 回圈
- 磁碟上儲存和主/從複製

## 安裝Redis

安裝和設定Redis軟體不屬於本指南的範圍。 請參閱下列資源：

- [下載Redis頁面](https://redis.io/download)
- [Redis快速入門](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Redis檔案頁面](https://redis.io/docs)

## 設定Redis設定

視您的安裝而定，您通常可以在下列其中一個檔案中找到Redis設定： `/etc/redis/redis.conf` 或 `/etc/redis/<port>.conf`

若要根據您的需求最佳化Redis執行個體，請為每個工作階段使用專用執行個體、Commerce快取和FPC，以獲得最佳結果。

對於工作階段，Adobe建議您啟用持續性，以使用下列任一持續性選項將Redis資料複製到磁碟：一般Redis資料庫備份(RDB)快照或僅附加檔案(AOF)持續性記錄。

- **Redis資料庫備份** (RDB)快照會在指定時間後（自上次儲存後最小金鑰數已變更），將完整的資料庫儲存在傾印檔案中。 使用 `save` 在內設定 `redis.conf` 檔案以設定此設定。

- **僅附加檔案** (AOF)會將傳送至Redis的每個寫入操作儲存在日誌檔案中。 Redis只會在重新啟動時讀取此檔案，並使用它來還原原始資料集。

您也可以同時啟用RDB和AOF選項。 如需其他詳細資訊，包括持續性選項的優點和缺點，請參閱 [Redis持續性檔案](https://redis.io/topics/persistence).

對於快取執行個體，請設定執行個體，使其足以儲存整個Commerce快取。 大小需求取決於不同因素，例如產品數量和商店檢視。 首先，您可以使用檔案系統上快取資料夾的大小。 例如，如果 `var/cache` 檔案系統上的資料夾為5 GB，請將您的Redis執行個體設定為至少5 GB才能開始。 快取執行個體不需要持續性，因為Commerce快取可以還原。 另請參閱 [Redis快取指南](https://redis.io/docs/manual/eviction/).

若要進行效能調整，您可以啟用下列非同步刪除的設定。 這些設定不會變更Redis的行為。

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

在Redis 6.x和更新版本上，您也可以新增以下值：

```ini
lazyfree-lazy-user-del yes
```
