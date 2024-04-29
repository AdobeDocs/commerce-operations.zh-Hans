---
title: Composer项目结构
description: 了解如何设置和维护全局参考架构示例中所述的单独包选项。
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 8757d5b8-8309-452f-bfb3-1188a816d14f
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Composer项目结构

本指南介绍如何设置并维护 [单独的包选项](../examples.md#option-1-separate-packages) 在全球参考体系结构(GRA)示例中进行了说明。

## 先决条件

在开始之前，请验证以下各项：

- 您有一个Git存储库
- 您拥有Composer存储库（本主题重点介绍私有包程序）
- 您已将Composer存储库配置为镜像 `repo.magento.com` 和 `packagist.org` 存储库

## 主Git项目存储库

主Git项目存储库应仅包含编辑器项目。 您可以使用编辑器包管理其他所有内容。 主项目绝不应包含除以下文件结构之外的任何其他内容，因为Composer通过依赖项安装所有其他包：

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

将以下内容添加到 `.gitignore` 文件：

```tree
/*
!/composer.json
!/composer.lock
```

## 初始化主项目

1. 创建一个名为的Git存储库 `project-<region/country/brand>`.

1. 创建 `composer.json` 和 `composer.lock` 文件：

   ```bash
   composer create-project --no-install --repository-url=https://repo.magento.com/ magento/project-enterprise-edition project-<region/country/brand>
   cd <install-directory-name>
   printf '/*\n!/composer.json\n!/composer.lock\n!/.gitignore' > .gitignore
   composer config --unset version
   composer config name '<client>/project-<region/country/brand>'
   composer config description '<client> <region/country/brand> main composer project'
   composer config repositories.private-packagist composer https://repo.packagist.com/<client>/
   composer config repositories.packagist.org false
   composer config --unset repositories.0
   composer install
   git init
   git add --all
   git commit -m 'initialize project'
   git remote add origin git@bitbucket.org:<client>/project-<region/country/brand>.git
   git push -u origin master
   ```

## 保存非模块文件

1. 添加 `app/etc/config.xml` 文件到Git存储库。

   您可以使用将要创建的模块来安装其他区域或品牌特定的文件，例如 `.htaccess`、Google或Bing身份验证文本文件、可执行文件或其他不由Adobe Commerce模块管理的静态文件。

   使用 `magento2-component` 键入包以创建文件映射以将文件复制到主Git存储库中 `composer install` 和 `composer update` 操作。

1. 创建遵循命名惯例的Git存储库 `component-environment-<region/country/brand>`：

   ```bash
   bin/magento module:enable --all
   cd ../
   mkdir component-environment-<region/country/brand>
   cd component-environment-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/component-environment-<region/country/brand>' \
    --description='<client> <region/country/brand> environment files' \
    --type=magento2-component \
    --require="magento/magento-composer-installer:*"
   mkdir -p app/etc
   cp ../project-<region/country/brand>/app/etc/config.php app/etc/
   composer config -e
   ```

1. 添加 `app/etc/config.php` 文件作为映射 `extra.map` 属性 `composer.json` 文件：

   ```json
   {
       "name": "example-client/component-environment-emea",
       "description": "Example client EMEA environment files",
       "type": "magento2-component",
       "require": {
           "magento/magento-composer-installer": "*"
       },
       "extra": {
           "map": [
               [
                   "app/etc/config.php",
                   "app/etc/config.php"
               ]
           ]
       }
   }
   ```

1. 验证您的 `composer.json` 文件并将其提交到Git存储库：

   ```bash
   composer validate
   git init
   git add --all
   git commit -m 'initialize component'
   git remote add origin git@bitbucket.org:<client>/component-environment-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

## 设置中继

1. 创建以下Git存储库：

   - `meta-gra`
   - `meta-<region/country/brand>`

1. 设置以下依赖关系树：

   ```tree
   client/project-<region/country/brand>
   └─ requires -> client/meta-<region/country/brand>
                  ├─ requires -> client/component-environment-<region/country/brand>
                  └─ requires -> client/meta-gra
                                 └─ requires -> magento/product-enterprise-edition
   ```

1. 创建GRAmetapackage：

   ```bash
   cd ..
   mkdir meta-gra
   cd meta-gra
   composer init --no-interaction \
    --name='<client>/meta-gra' \
    --description='<client> GRA meta package' \
    --type=metapackage \
    --require="magento/product-enterprise-edition:<exact.required.version>"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-gra.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. 创建品牌隐喻：

   ```bash
   cd ..
   mkdir meta-<region/country/brand>
   cd meta-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/meta-<region/country/brand>' \
    --description='<client> <region/country/brand> meta package' \
    --type=metapackage \
    --require="<client>/component-environment-<region/country/brand>:~0.1" \
    --require="<client>/meta-gra:~0.1"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. 在主项目中通过依赖关系管理要求收集：

   ```bash
   cd ../project-<region/country/brand>
   rm app/etc/config.php
   composer remove --no-update magento/product-enterprise-edition
   composer require --no-update "<client>/meta-<region/country/brand>:~0.1"
   composer config minimum-stability alpha
   composer config prefer-stable true
   composer update
   git add --all
   git commit -m 'set up GRA dependency tree'
   git push origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. 验证编辑器是否复制了 `app/etc/config.php` 文件来源 `<client>/component-environment-<region/country/brand>`.

## 部署代码

在Web服务器上，您可以使用编辑器部署代码，但无法更新主项目。 在每次新部署时使用编辑器重新安装项目，这消除了生产和测试服务器访问Git的要求。

## 添加其他实例和包

每个实例(地区、品牌或其他独特的Adobe Commerce安装)都应拥有自己的 **主项目** 实例， **特定隐含**、和 **环境组件包**. 此 **GRA隐含** 应为 **共享** 跨所有实例。

以下任一方式均需要功能包(例如Adobe Commerce模块、主题、语言包和库)和第三方包：

- **GRA隐含** — 用于安装 _所有_ 实例
- **实例特定的中继** — 用于安装在单个品牌或区域上

>[!IMPORTANT]
>
>不需要主项目的包 `composer.json` 文件位于 `main` 或 `release` 分支。

## 准备开发

对于开发，请安装 `develop` 您所维护的所有模块的版本。

根据您的分支策略，您可能会 `develop`， `qa`， `uat`、和 `main` 分支。 Composer中存在每个分支，它们具有 `dev-` 前缀。 所以 `develop` 可通过Composer要求分支为版本 `dev-develop`.

1. 创建 `develop` 分支中的所有模块和项目存储库。

   ```bash
   cd ../component-environment-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../meta-<region/country/brand>
   git checkout master
   git checkout -b develop
   
   git push -u origin develop
   
   
   cd ../meta-gra
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../project-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   composer require \
   "magento-services/meta-fantasy-corp:dev-develop as 0.999" \
   "magento-services/meta-gra:dev-develop as 0.999" \
   "magento-services/component-environment-fantasy-corp:dev-develop as 0.999"
   ```

   上一步在 `composer.json` 文件：

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**不合并** 这些 `composer.json` 对您的生产分支进行了文件更改。 仅在上安装稳定版本的包 `release` 和 `main` 分支。 您可以定义这些依赖关系 `qa` 分支和其他非主分支。
