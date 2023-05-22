---
title: 啟用記錄
description: 瞭解如何啟用和停用記錄型別。
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 啟用記錄

{{file-system-owner}}

## 偵錯記錄

依預設，Commerce會寫入除錯記錄(`<install_directory>/var/log/debug.log`)處於預設或開發模式時，但處於生產模式時則不會。 使用 `bin/magento setup:config:set --enable-debug-logging` 命令來變更預設值。

>[!INFO]
>
>自Commerce 2.3.1起，您無法再使用 `bin/magento config:set dev/debug/debug_logging` 命令來啟用或停用目前模式的偵錯記錄。

### 啟用偵錯記錄

1. 使用 `setup:config:set` 命令以啟用目前模式的偵錯記錄。

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. 清除快取。

   ```bash
   bin/magento cache:flush
   ```

### 停用偵錯記錄

1. 使用 `setup:config:set` 命令停用目前模式的偵錯記錄。

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. 清除快取。

   ```bash
   bin/magento cache:flush
   ```

## 資料庫記錄

根據預設，Commerce會將資料庫活動記錄檔寫入 `<install-dir>/var/debug/db.log` 檔案。

### 啟用資料庫記錄

1. 使用 `dev:query-log` 啟用或停用資料庫記錄的命令。

   ```bash
   bin/magento dev:query-log:enable
   ```

   ```bash
   bin/magento dev:query-log:disable
   ```

1. 清除快取。

   ```bash
   bin/magento cache:flush
   ```

## Cron記錄

在版本2.3.1中，Commerce現在會建立個別的 `cron` 記錄。 \
Commerce最近讓cron記錄更詳細，這提供了更多資訊，但延長了 `system.log` 相當大。
移動 `cron` 將資訊放入專用記錄檔可使兩個記錄檔更易於讀取。

依預設，Commerce會寫入 `cron` 的資訊 `<install-directory>/var/log/cron.log` 檔案。

## Syslog記錄

依預設，Commerce會寫入 _syslog_ 作業系統的記錄檔 `syslog` 檔案。
自Commerce 2.3.1起，您必須使用 `magento` 啟用或停用syslog的命令。
管理員中的設定已移除。

### 啟用syslog記錄

登入 `syslog` 預設為停用。

1. 使用 `setup:config:set` 命令以變更 `dev/syslog/syslog_logging` 資料庫值至 `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. 清除快取。

   ```bash
   bin/magento cache:flush
   ```

### 停用syslog記錄

1. 使用 `setup:config:set` 命令以變更 `dev/syslog/syslog_logging` 資料庫值至 `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. 清除快取。

   ```bash
   bin/magento cache:flush
   ```
