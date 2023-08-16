---
title: 启用日志记录
description: 了解如何启用和禁用各种类型的日志记录。
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 启用日志记录

{{file-system-owner}}

## 调试日志记录

默认情况下，Commerce写入调试日志(`<install_directory>/var/log/debug.log`)处于默认或开发模式时，但不在生产模式时更新。 使用 `bin/magento setup:config:set --enable-debug-logging` 命令更改缺省值。

>[!INFO]
>
>自Commerce 2.3.1起，您将无法再使用 `bin/magento config:set dev/debug/debug_logging` 命令在当前模式下启用或禁用调试日志记录。

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

默认情况下，Commerce将数据库活动日志写入 `<install-dir>/var/debug/db.log` 文件。

### 启用数据库日志记录

1. 使用 `dev:query-log` 用于启用或禁用数据库日志记录的命令。

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

在版本2.3.1中，Commerce现在创建了一个单独的 `cron` 日志。 \
Commerce最近使cron日志记录更加冗长，这提供了更多信息，但延长了 `system.log` 相当大。
正在移动 `cron` 将信息保存到专用日志可使两个日志更易于读取。

默认情况下，Commerce会写入 `cron` 中的信息 `<install-directory>/var/log/cron.log` 文件。

## Syslog日志记录

默认情况下，Commerce会写入 _syslog_ 日志到操作系统 `syslog` 文件。
自Commerce 2.3.1起，您必须使用 `magento` 命令启用或禁用syslog。
管理员中的设置已被删除。

### 启用syslog日志记录

登录 `syslog` 默认情况下处于禁用状态。

1. 使用 `setup:config:set` 命令更改 `dev/syslog/syslog_logging` 数据库值至 `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. 刷新缓存。

   ```bash
   bin/magento cache:flush
   ```

### 禁用syslog日志记录

1. 使用 `setup:config:set` 命令更改 `dev/syslog/syslog_logging` 数据库值至 `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. 刷新缓存。

   ```bash
   bin/magento cache:flush
   ```
