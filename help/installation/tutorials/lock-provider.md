---
title: 設定鎖定提供者
description: 請按照以下步驟操作，以防止重複的cron工作和cron群組在您的Adobe Commerce或Magento Open Source部署上執行。
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# 設定鎖定提供者

在執行這個命令之前，您必須執行下列動作 *或* 您必須 [安裝應用程式](../advanced.md)：

* [建立或更新部署設定](deployment.md)
* [建立資料庫綱要](database.md)

## 安全安裝

{{$include /help/_includes/secure-install.md}}

## 設定鎖定

設定鎖定提供者，以防止啟動重複的cron作業和cron群組。 (需要Adobe Commerce或Magento Open Source 2.2.x、2.2.5及更高版本，以及2.3.3及更高版本。)

Adobe Commerce和Magento Open Source預設會使用資料庫儲存鎖定。 如果您的伺服器上有多個節點，建議您使用Zookeeper作為鎖定提供者。

如果您在雲端基礎結構上執行Adobe Commerce，則不需要設定鎖定提供者設定。 應用程式會在布建程式期間為Pro專案設定檔案鎖定提供者。 另請參閱 [雲端變數](https://devdocs.magento.com/cloud/env/variables-cloud.html).

### 命令使用方式

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### 引數說明

| 名稱 | 值 | 必填？ |
|--- |--- |--- |
| `--lock-provider` | 鎖定提供者名稱： `db`， `zookeeper`，或 `file`.<br><br>預設鎖定提供者： `db` | 否 |
| `--lock-db-prefix` | 使用時避免鎖定衝突的特定資料庫首碼 `db` 鎖定提供者。<br><br>預設值： `NULL` | 否 |
| `--lock-zookeeper-host` | 使用「 」時連線至Zookeeper叢集的主機與連線埠 `zookeeper` 鎖定提供者。<br><br>例如： `127.0.0.1:2181` | 是，如果您設定 `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper儲存鎖定的路徑。<br><br>預設路徑為： `/magento/locks` | 否 |
| `--lock-file-path` | 儲存檔案鎖定的路徑。 | 是，如果您設定 `--lock-provider=file` |
