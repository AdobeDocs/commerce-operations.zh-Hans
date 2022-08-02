---
title: 运行支持实用程序
description: 使用内置支持实用程序对您的商务项目进行故障诊断。
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---


# 运行支持实用程序

{{ee-only}}

{{file-system-owner}}

Adobe Commerce支持实用程序(也称为 [数据收集器](https://docs.magento.com/user-guide/system/support-data-collector.html) — 使用户能够收集有关系统的故障诊断信息，供我们的支持团队使用。

Adobe Commerce使用这些备份，也称为 _转储_，以分析需要访问您的代码的问题。 典型情况如下：

1. 您的Commerce商店遇到问题，请联系Adobe Commerce支持。
1. 支持人员确定他们需要查看您的代码或数据库才能重现问题。
1. 您将代码备份到 `.tar.gz` 文件。

   此备份(_E)排除您的媒体文件，以加快处理速度并生成更小的文件。

1. 将数据库备份到 `.tar.gz` 文件。

   默认情况下，进行备份时会对敏感数据进行哈希处理。

1. 将备份上载到文件共享服务。
1. 支持可在不影响开发或生产环境的情况下分析您的问题。

实用程序可能需要几分钟才能完成。

## 创建代码备份

此命令将代码备份并压缩为 `tar.gz` 格式。

{{tip-backup-command}}

命令选项：

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

其中：

- **`--name`** 指定转储文件名（可选）。 如果忽略此参数，则转储文件将加盖时间戳和日期戳。
- **`-o|--output=<path>`** 是用于存储备份的绝对文件系统路径（必需）。
- **`-l|--logs`** 包含日志文件（可选）。

例如，创建名为 `/var/www/html/magento2/var/log/mycodebackup.tar.gz`:

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

命令完成后，将代码备份提供给Adobe Commerce支持。

## 创建数据库备份

此命令将备份Commerce数据库并在 `tar.gz` 格式。

{{tip-backup-command}}

命令选项：

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

其中：

- **`--name`** 指定转储文件名（可选）。 如果忽略此参数，则转储文件将加盖时间戳和日期戳。
- **`-o|--output=<path>` 是用于存储备份的绝对文件系统路径（必需）。
- **`-l|--logs`** 包含日志文件（可选）。
- **`-i|--ignore-sanitize`** 表示数据被保留；在创建备份时，将标记忽略为对存储在数据库中的敏感数据进行哈希处理（可选）。

敏感数据包括来自以下数据库表的客户信息：

```terminal
'customer_entity',
'customer_entity_varchar',
'customer_address_entity',
'customer_address_entity_varchar',
'customer_grid_flat',
'quote',
'quote_address',
'sales_order',
'sales_order_address',
'sales_order_grid'
```

命令完成后，将数据库备份提供给Adobe Commerce支持。

## 疑难解答：显示实用程序和路径

我们提供命令，用于显示数据收集器和命令行所需实用工具的路径。 例如，如果Admin或命令行中出现如下错误，则可以使用这些命令：

```terminal
Utility lsof not found
```

按照显示的顺序运行以下命令，以显示支持实用程序和数据收集器使用的应用程序的路径：

1. 更改为Commerce安装目录。

   例如，`cd /var/www/magento2`

   >[!INFO]
   >
   >命令运行正确 _仅_ 从安装目录。

1. `bin/magento support:utility:paths` 创建 `<magento_root>/var/support/Paths.php`，其中列出了该实用程序使用的所有应用程序的路径。
1. `bin/magento support:utility:check` 显示文件系统路径。

示例如下：

```terminal
   gzip => /bin/gzip
   lsof => /usr/sbin/lsof
   mysqldump => /usr/bin/mysqldump
   nice => /bin/nice
   php => /usr/bin/php
   tar => /bin/tar
   sed => /bin/sed
   bash => /bin/bash
   mysql => /usr/bin/mysql
```

要解决运行工具时出现的问题，请确保这些应用程序已安装并位于Web服务器用户的 `$PATH` 环境变量。
