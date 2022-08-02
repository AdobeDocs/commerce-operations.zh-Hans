---
title: 启用日志记录
description: 了解如何启用和禁用日志记录类型。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# 启用日志记录

{{file-system-owner}}

## 调试日志记录

默认情况下，商务会写入调试日志(`<install_directory>/var/log/debug.log`)，但在生产模式下则不会。 使用 `bin/magento setup:config:set --enable-debug-logging` 命令来更改默认值。

>[!INFO]
>
>自Commerce 2.3.1起，您将无法再使用 `bin/magento config:set dev/debug/debug_logging` 命令启用或禁用当前模式的调试日志记录。

### 启用调试日志记录

1. 使用 `setup:config:set` 命令启用当前模式的调试日志记录。

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. 刷新缓存。

   ```bash
   bin/magento cache:flush
   ```

### 禁用调试日志记录

1. 使用 `setup:config:set` 命令禁用当前模式的调试日志记录。

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. 刷新缓存。

   ```bash
   bin/magento cache:flush
   ```

## 数据库日志记录

默认情况下，商务会将数据库活动日志写入 `<install-dir>/var/debug/db.log` 文件。

### 启用数据库日志记录

1. 使用 `dev:query-log` 命令启用或禁用数据库日志记录。

   ```bash
   bin/magento dev:query-log:enable
   ```

   ```bash
   bin/magento dev:query-log:disable
   ```

1. 刷新缓存。

   ```bash
   bin/magento cache:flush
   ```

## Cron日志记录

现在，在版本2.3.1中，Commerce会创建一个单独的 `cron` 日志。 \
Commerce最近使cron日志记录更为详细，提供了更多信息，但将 `system.log` 相当大。
移动 `cron` 指向专用日志的信息使这两个日志更易于读取。

默认情况下，商务会写入 `cron` 信息 `<install-directory>/var/log/cron.log` 文件。

## Syslog日志记录

默认情况下，商务会写入 _syslog_ 登录到操作系统 `syslog` 文件。
自Commerce 2.3.1起，您必须使用 `magento` 命令启用或禁用syslog。
管理员中的设置已被删除。

### 启用系统日志记录

正在登录 `syslog` 默认情况下处于禁用状态。

1. 使用 `setup:config:set` 命令更改 `dev/syslog/syslog_logging` 数据库值到 `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. 刷新缓存。

   ```bash
   bin/magento cache:flush
   ```

### 禁用syslog日志记录

1. 使用 `setup:config:set` 命令更改 `dev/syslog/syslog_logging` 数据库值到 `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. 刷新缓存。

   ```bash
   bin/magento cache:flush
   ```
