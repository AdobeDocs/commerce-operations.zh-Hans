---
title: 启用日志记录
description: 了解如何在Adobe Commerce中启用和禁用不同类型的日志记录。 了解日志记录配置和管理技术。
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: aff705cefcd4de38d17cad41628bc8dbd6d630cb
workflow-type: tm+mt
source-wordcount: '352'
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

### 查询日志记录存储位置

启用数据库日志记录后，Commerce会将查询日志存储在以下位置：

- **查询日志文件**： `<install-directory>/var/debug/db.log`
- **日志目录**： `<install-directory>/var/debug/`

查询日志包含：
- 应用程序执行的SQL查询
- 查询执行时间
- 查询参数和绑定
- 数据库连接信息

>[!NOTE]
>
>在高流量环境中，查询日志文件可能会快速增大。 监视磁盘空间，并考虑实施日志轮换或定期清理查询日志文件。

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

### 查看查询日志

您可以使用标准文件查看命令查看查询日志：

```bash
# View the entire query log
cat var/debug/db.log

# View the last 100 lines of the query log
tail -n 100 var/debug/db.log

# Monitor the query log in real-time
tail -f var/debug/db.log

# Search for specific queries
grep "SELECT" var/debug/db.log
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
