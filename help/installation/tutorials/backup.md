---
title: 备份和回滚文件系统、介质和数据库
description: 按照以下步骤备份和恢复Adobe Commerce或Magento Open Source应用程序。
exl-id: b9925198-37b4-4456-aa82-7c55d060c9eb
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# 备份和回滚文件系统、介质和数据库

此命令允许您备份：

* 文件系统(不包括 `var` 和 `pub/static` 目录)
* 此 `pub/media` 目录
* 数据库

备份存储在 `var/backups` 目录，并可随时使用 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 命令。

备份后，您可以 [回滚](#rollback) 稍后。

>[!TIP]
>
>有关云基础架构项目的Adobe Commerce，请参阅 [快照和备份管理](https://devdocs.magento.com/cloud/project/project-webint-snap.html) 在 _云指南_.

## 启用备份

默认情况下，备份功能处于禁用状态。 要启用，请输入以下CLI命令：

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**弃用通知：**
>备份功能自2.1.16、2.2.7和2.3.0起已被弃用。我们建议调查其他备份技术和二进制备份工具（如Percona XtraBackup）。

## 设置打开文件限制

回滚到以前的备份可能会以静默方式失败，导致使用写入文件系统或数据库的数据不完整。 [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) 命令。

有时，较长的查询字符串会导致用户分配的内存空间因递归调用过多而耗尽内存。

## 如何设置打开的文件 `ulimit`

我们建议设置打开的文件 [`ulimit`](https://ss64.com/bash/ulimit.html) 文件系统用户的值 `65536` 或更多。

您可以在命令行上执行此操作，也可以通过编辑用户的shell脚本将其设置为用户的永久设置。

在继续之前，如果您尚未这样做，请切换到 [文件系统所有者](../prerequisites/file-system/overview.md).

命令：

```bash
ulimit -s 65536
```

如果需要，可以将其更改为更大的值。

>[!NOTE]
>
>打开文件的语法 `ulimit` 取决于您使用的UNIX shell。 前面的设置应适用于CentOS和Ubuntu以及Bash shell。 但是，对于macOS，正确的设置是 `ulimit -S 65532`. 有关更多信息，请参阅手册页或操作系统参考。

要在用户的Bash shell中设置值（可选），请执行以下操作：

1. 如果您尚未这样做，请切换到 [文件系统所有者](../prerequisites/file-system/overview.md).
1. 打开 `/home/<username>/.bashrc` 在文本编辑器中。
1. 添加以下行：

   ```bash
   ulimit -s 65536
   ```

1. 将更改保存到 `.bashrc` 并退出文本编辑器。

>[!WARNING]
>
>我们建议您避免为设置值 [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) 在 `php.ini` 文件，因为它可能会导致不完整的回滚，并且不会出现失败通知。

## 备份

命令用法：

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

该命令执行以下任务：

1. 将商店置于维护模式。
1. 执行以下命令选项之一。

   | Option | 含义 | 备份文件名和位置 |
   |--- |--- |--- |
   | `--code` | 备份文件系统（var和pub/static目录除外）。 | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | 备份pub/media目录 | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | 备份数据库。 | `var/backups/<timestamp>/_db.sql` |

1. 使存储退出维护模式。

例如，要备份文件系统和数据库，

```bash
bin/magento setup:backup --code --db
```

显示类似于以下内容的消息：

```terminal
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1434133011_filesystem.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1434133011_filesystem.tgz
[SUCCESS]: Code backup completed successfully.
DB backup is starting...
DB backup filename: 1434133011_db.sql
DB backup path: /var/www/html/magento2/var/backups/1434133011_db.sql
[SUCCESS]: DB backup completed successfully.
Disabling maintenance mode
```

## 回滚

本节讨论如何回滚到您之前创建的备份。 您必须知道要还原的备份文件的文件名。

要查找备份的名称，请输入：

```bash
bin/magento info:backups:list
```

备份文件名中的第一个字符串是时间戳。

要回滚到以前的备份，请输入：

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

例如，要恢复名为的媒体备份，请 `1440611839_filesystem_media.tgz`，输入

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

显示类似于以下内容的消息：

```terminal
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
