---
title: 升级基于Git的安装
description: 升级您从git存储库克隆的Adobe Commerce或Magento Open Source安装。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# 升级基于git的安装

本主题讨论内容贡献开发人员如何在不重新安装的情况下更新Adobe Commerce或Magento Open Source。 如果您不是参与开发人员，请参阅 [执行升级](../implementation/perform-upgrade.md).

要升级（如果您是参与开发人员），请执行以下操作：

1. 登录到您的服务器。

1. 切换到 [文件系统所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. 更改为您克隆应用程序的目录。 例如，

   ```bash
   cd /var/www/magento2
   ```

1. 保存您对 `composer.json` 文件，因为后续步骤会覆盖该文件。

1. 创建备份 `composer.json` 文件。

   ```bash
   cp composer.json composer.json.old
   ```

1. 更新本地存储库以获取最新代码：

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >如果 `git pull origin develop` 失败，请参阅 [疑难解答](https://support.magento.com/hc/en-us/articles/360034229872).

1. 比较并合并 `composer.json.old` 文件 `composer.json` 文件。

1. 解决依赖关系，并将确切的版本写入 `composer.lock` 文件。

   ```bash
   composer update
   ```

1. 更新数据库：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除缓存：

   ```bash
   bin/magento cache:clean
   ```
