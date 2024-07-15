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

本指南介绍如何设置和维护全局参考体系结构(GRA)示例中描述的[单独的包选项](../examples.md#option-1-separate-packages)。

## 先决条件

在开始之前，请验证以下各项：

- 您有一个Git存储库
- 您拥有Composer存储库（本主题重点介绍私有包程序）
- 您已配置编辑器存储库以镜像`repo.magento.com`和`packagist.org`存储库

## 主Git项目存储库

主Git项目存储库应仅包含编辑器项目。 您可以使用编辑器包管理其他所有内容。 主项目绝不应包含除以下文件结构之外的任何其他内容，因为Composer通过依赖项安装所有其他包：

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

将以下内容添加到`.gitignore`文件：

```tree
/*
!/composer.json
!/composer.lock
```

## 初始化主项目

1. 创建名为`project-<region/country/brand>`的Git存储库。

1. 创建`composer.json`和`composer.lock`文件：

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

1. 将`app/etc/config.xml`文件添加到Git存储库。

   您可以使用将要创建的模块安装其他区域或品牌特定文件，如`.htaccess`、Google或Bing身份验证文本文件、可执行文件或其他不由Adobe Commerce模块管理的静态文件。

   使用`magento2-component`类型包创建文件映射，以便在`composer install`和`composer update`操作期间将文件复制到主Git存储库中。

1. 创建遵循命名约定`component-environment-<region/country/brand>`的Git存储库：

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

1. 将`app/etc/config.php`文件添加为`composer.json`文件的`extra.map`属性中的映射：

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

1. 验证`composer.json`文件并将其提交到Git存储库：

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

1. 验证编辑器是否从`<client>/component-environment-<region/country/brand>`复制了`app/etc/config.php`文件。

## 部署代码

在Web服务器上，您可以使用编辑器部署代码，但无法更新主项目。 在每次新部署时使用编辑器重新安装项目，这消除了生产和测试服务器访问Git的要求。

## 添加其他实例和包

每个实例(地区、品牌或其他唯一的Adobe Commerce安装)都应获得自己的&#x200B;**主项目**&#x200B;实例、**特定中继**&#x200B;和&#x200B;**环境组件包**。 **GRA中继**&#x200B;应在所有实例中&#x200B;**共享**。

以下任一方式均需要功能包(例如Adobe Commerce模块、主题、语言包和库)和第三方包：

- **GRA中继** — 用于在&#x200B;_所有_&#x200B;实例上安装
- **特定于实例的中继包** — 用于安装在单个品牌或区域上

>[!IMPORTANT]
>
>在`main`或`release`分支上的主项目的`composer.json`文件中不需要包。

## 准备开发

对于开发，请安装您维护的所有模块的`develop`版本。

根据您的分支策略，您可能具有`develop`、`qa`、`uat`和`main`分支。 每个分支都存在于前缀为`dev-`的编辑器中。 因此，可以通过Composer以版本`dev-develop`的形式需要`develop`分支。

1. 在所有模块和项目存储库中创建`develop`分支。

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

   上一步在`composer.json`文件中生成以下行：

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**请勿将这`composer.json`个文件更改合并**&#x200B;到您的生产分支。 仅在`release`和`main`分支上安装稳定版本的包。 您可以为`qa`分支和其他非主分支定义这些依赖项。
