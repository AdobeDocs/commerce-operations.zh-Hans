---
title: 升级模块和扩展
description: 使用命令行界面和编辑器升级Adobe Commerce以及Magento Open Source模块和扩展。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# 升级模块和扩展

要更新或升级模块或扩展，请执行以下操作：

1. 从Marketplace或其他扩展开发人员下载更新的文件。 请注意模块名称和版本。

1. 将内容导出到Adobe Commerce或Magento Open Source根安装目录。

1. 如果模块存在编辑器包，请运行以下任一程序。

   每个模块名称的更新：

   ```bash
   composer update vendor/module-name
   ```

   每个版本更新：

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. 运行以下命令以升级、部署和清理缓存。

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```
