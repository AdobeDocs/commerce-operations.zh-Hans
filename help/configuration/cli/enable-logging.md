---
title: 启用日志记录
description: 了解如何在Adobe Commerce中启用和禁用不同类型的日志记录。 了解日志记录配置和管理技术。
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# 启用日志记录

{{file-system-owner}}

## 调试日志记录

默认情况下，Commerce在默认或开发模式下写入调试日志(`<install_directory>/var/log/debug.log`)，在生产模式下则不写入。 使用`bin/magento setup:config:set --enable-debug-logging`命令更改默认值。

>[!INFO]
>
>自Commerce 2.3.1起，您无法再使用`bin/magento config:set dev/debug/debug_logging`命令在当前模式下启用或禁用调试日志记录。

### 启用调试日志记录

1. 使用`setup:config:set`命令在当前模式下启用调试日志记录。

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. 刷新缓存。

   ```bash
   bin/magento cache:flush
   ```

### 禁用调试日志记录

1. 使用`setup:config:set`命令禁用当前模式的调试日志记录。

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. 刷新缓存。

   ```bash
   bin/magento cache:flush
   ```

## 数据库日志记录

默认情况下，Commerce将数据库活动日志写入`<install-dir>/var/debug/db.log`文件。

### 启用数据库日志记录

1. 使用`dev:query-log`命令启用或禁用数据库日志记录。

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

在版本2.3.1中，Commerce现在创建单独的`cron`日志。 \
Commerce最近使cron日志记录更详细，这提供了更多信息，但显着延长了`system.log`。
将`cron`信息移动到专用日志可使两个日志更易于读取。

默认情况下，Commerce将`cron`信息写入`<install-directory>/var/log/cron.log`文件。

## Syslog日志记录

默认情况下，Commerce将&#x200B;_syslog_&#x200B;日志写入操作系统`syslog`文件。
从Commerce 2.3.1开始，您必须使用`magento`命令启用或禁用syslog。
管理员中的设置已被删除。

### 启用syslog日志记录

默认情况下已禁用登录到`syslog`。

1. 使用`setup:config:set`命令将`dev/syslog/syslog_logging`数据库值更改为`true`。

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. 刷新缓存。

   ```bash
   bin/magento cache:flush
   ```

### 禁用syslog日志记录

1. 使用`setup:config:set`命令将`dev/syslog/syslog_logging`数据库值更改为`false`。

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. 刷新缓存。

   ```bash
   bin/magento cache:flush
   ```
