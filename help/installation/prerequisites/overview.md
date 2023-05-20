---
title: 內部部署安裝必備條件
description: 深入瞭解Adobe Commerce和Magento Open Source的內部安裝所需的軟體相依性。
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# 內部部署安裝必備條件

安裝Adobe Commerce或Magento Open Source之前，您必須先執行下列動作：

* 設定符合以下條件的一或多部主機： [系統需求](../system-requirements.md).
* 如果您要設定一個以上具有負載平衡的Web節點，請設定並測試系統的該部分 _早於_ 您安裝應用程式。
* 請務必在安裝期間於不同時間點備份整個系統，以便在發生問題時將其復原。

>[!NOTE]
>
>我們假設您要在以下位置安裝Adobe Commerce或Magento Open Source： **開發環境**，表示您擁有該電腦的根使用者存取權， **和** 電腦不需要高度安全。 如果您要設定較安全的機器，強烈建議您向網路管理員尋求其他協助。

強烈建議您更新並升級作業系統軟體。 這些升級可提供安全性與軟體修正，以防止未來發生問題。 不知道這代表什麼嗎？ 請檢視我們的 [安裝概觀頁面](../overview.md).

以使用者身分輸入以下命令，並附上 `root` 許可權：

* Ubuntu

   ```bash
   apt-get update
   ```

   ```bash
   apt-get upgrade
   ```

* CentOS

   ```bash
   yum -y update
   ```

   ```bash
   yum -y upgrade
   ```

## 先決條件檢查

若要檢查您的系統是否有先決條件，請輸入下列命令：

### Apache

CentOS： `httpd -v`

Ubuntu： `apache2 -v`

Adobe Commerce和Magento Open Source支援Apache版本2.4，因為以下結果指出：

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

若要安裝或升級Apache，請參閱 [Apache](web-server/apache.md).

### PHP

另請參閱 [系統需求](../system-requirements.md) PHP和的支援版本 [PHP] PHP要求。

### MySQL

```bash
mysql -u <database root user or database owner name> -p
```

例如：

```bash
mysql -u magento -p
```

檢查您是否有正確版本的MySQL，適用於您正在安裝的Adobe Commerce或Magento Open Source([檢視這裡以瞭解支援的版本](../system-requirements.md). 以下結果表示您正在執行的版本。)

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

型別 `help` 或 `\h` 以取得協助。 型別 `\c` 以清除目前的輸入陳述式。

輸入 `exit` 在 `mysql>` 提示以結束。

若要安裝或升級MySQL，請參閱 [MySQL](database/mysql.md).

### 搜尋引擎

若要驗證OpenSearch安裝：

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

若要驗證Elasticsearch安裝：

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

例如：

```bash
curl -XGET 'localhost:9200'
```

```terminal
{
  "name" : "Z0S2B05",
  "cluster_name" : "elasticsearch_myname",
  "cluster_uuid" : "V-kpikRJQHudN-Wzdt-IrQ",
  "version" : {
    "number" : "6.8.7",
    "build_flavor" : "oss",
    "build_type" : "tar",
    "build_hash" : "c63e621",
    "build_date" : "2020-02-26T14:38:01.193138Z",
    "build_snapshot" : false,
    "lucene_version" : "7.7.2",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
```
