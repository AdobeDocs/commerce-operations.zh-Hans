---
title: 还原拆分数据库
description: 从已弃用的拆分数据库实施还原到单个数据库实施。
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# 从拆分数据库还原

{{ee-only}}

对于已实施的Adobe Commerce客户 [拆分数据库](multi-master.md)，以下主题介绍如何还原或迁移回单个数据库。 我们建议Adobe Commerce商家当前使用Split Database，并计划升级到2.4.2及更高版本，以及我们的 [公告](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) 计划弃用Split数据库。

从拆分数据库还原到单个数据库涉及创建 `magento_quote` 和 `magento_sales` 数据库，然后将它们加载到单个 `magento_main` 数据库。

在本例中，我们登录到所有三个数据库，它们安装在同一台主机上(`magento2-mysql`)作为“root”用户。 必须将这些值替换为数据库的相应值。

1. 创建备份 `magento_quote` 数据库：

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. 创建备份 `magento_sales` 数据库：

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. 加载 `magento_quote` 数据库 `magento_main` 数据库：

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. 加载 `magento_sales` 数据库 `magento_main` 数据库：

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. 删除 `magento_sales` 数据库：

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. 删除 `magento_quote` 数据库：

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. 删除的部署配置 `checkout` 和 `sales` 在 `connections` 和 `resources` 部分 `env.php` 文件。
1. 恢复外键：

   ```bash
   bin/magento setup:upgrade
   ```

## 验证您的工作

要验证您的单个数据库实施是否正常工作，请执行以下任务并验证数据是否已添加到 `magento_main` 使用数据库工具(如 [phpMyAdmin](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/optional.html#install-optional-phpmyadmin):

1. 验证外键是否已还原。 例如， `QUOTE_STORE_ID_STORE_STORE_ID` 键 `quote` 数据库表。
1. 确认客户可以从店面下订单。
1. 验证在将拆分数据库还原为单个数据库之前创建的订单在管理员中是否可用。
