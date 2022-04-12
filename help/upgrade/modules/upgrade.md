---
title: 升级模块和扩展
description: 使用命令行界面和编辑器升级Adobe Commerce以及Magento Open Source模块和扩展。
source-git-commit: 70f1bda91023526fbc0024b6a6fef93c7633ecc2
workflow-type: tm+mt
source-wordcount: '161'
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

## 供应商捆绑的扩展(VBE)

Adobe删除了所有 [VBE](https://devdocs.magento.com/extensions/vendor/) 在2.4.4中，供应商继续在Adobe Commerce Marketplace上支持这些扩展。

如果要继续将这些扩展与Adobe Commerce和Magento Open Source2.4.4及更高版本一起使用，则必须在 `composer.json` 文件 _之前_ 升级到2.4.4。请与供应商联系，获取要使用的包名称和版本。
