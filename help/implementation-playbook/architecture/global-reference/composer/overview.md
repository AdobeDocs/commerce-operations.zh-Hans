---
title: Composer开发
description: 了解如何在“vendor/”目录中就地开发编辑器模块。
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 7664ffb5-2e46-49c3-b2e6-c133c35d2f6b
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Composer开发

本主题介绍就地开发编辑器模块（作为`vendor/`目录中的Git存储库）并将这些模块添加到主Git项目的推荐方法。

>[!NOTE]
>
>这些准则主要适用于[全局参考体系结构(GRA)](../overview.md)项目。

## 准备开发分支

1. 在主Git存储库中创建或签出开发分支。
1. 需要您维护的每个模块的开发版本。

   在此示例中，主Git存储库中的每个分支都表示一个编辑器包版本。 此场景中推荐的编辑器版本的命名约定是`dev-`，后跟分支名称。 例如：

   - `dev-develop`
   - `dev-qa`

   ```bash
   composer require client/module-example:dev-develop
   ```

1. 如果另一个编辑器包需要特定版本的模块（例如，`client/module-example 1.0.12`），请用别名安装它：

   ```bash
   composer require 'client/module-example:dev-develop as 1.0.12'
   ```

   对于`qa`分支，将`dev-develop`替换为`dev-qa`。

## 将程序包转换为Git存储库

默认情况下，包不包含`.git/`目录。 Composer可以从Git中签出包，而不是使用预建的Composer包。 此方法的优势在于，您可以在开发期间轻松修改包。

1. 从`vendor/`目录中删除模块。

   ```bash
   rm -rf vendor/client/module-example
   ```

1. 使用[指定的Git源](#prepare-a-development-branch)重新安装模块。

   ```bash
   composer install --prefer-source
   ```

1. 验证编辑器包现在是否为Git存储库：

   ```bash
   cd vendor/client/module-example
   git remote -v
   ```

1. 要将多个模块批量转换为Git存储库（例如“客户端”模块），请执行以下操作：

   ```bash
   rm -rf vendor/client
   composer install --prefer-source
   ```

## 开始开发

1. 创建或检出特征/工作分支。 以下示例显示与Jira票证同名的分支。

   ```bash
   cd vendor/client/module-example
   git checkout master
   git checkout -b JIRA-1200
   ```

1. 在更改模块中的分支后，可通过刷新Adobe Commerce缓存和静态内容来查看这些更改。

   ```bash
   bin/magento cache:flush
   bin/magento module:enable --all --clear-static-content
   ```

## 使用您的开发更新主项目

通过修改`composer.lock`文件更新您的主Git存储库。 如果您的模块是新模块，请启用该模块。

```bash
# to update your packages and all dependencies of the package
composer update --with-all-dependencies client/module-example
# to update just your package
composer update client/module-example
 
bin/magento module:enable Client_ModuleExample
git add composer.lock app/etc/config.php
git commit
```
