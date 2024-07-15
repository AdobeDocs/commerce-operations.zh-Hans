---
title: 全局参考架构示例
description: 请参阅管理大型Adobe Commerce项目的代码示例。
role: Developer, Architect
level: Experienced
hide: true
hidefromtoc: true
exl-id: 2a85b9bf-e547-4a2a-9234-210865f55609
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---

# 全局参考架构示例

本主题介绍组织[全局参考体系结构(GRA)](overview.md)代码库的常用方法。 虽然首选使用[单独的包](#option-1-separate-packages)选项，但在某些情况下，需要下面描述的其他选项之一。

## 定义

{{$include /help/_includes/gra-definitions.md}}

## 选项1：单独的包

请参阅[Composer项目结构](composer/project-structure.md)设置此方法的最佳实践。

![全局参考体系结构的单独包选项示意图](../../../assets/playbooks/gra-separate-packages.png)

管理GRA Composer包的最灵活方式是通过中继。 元包仅包含`composer.json`文件，该文件定义了其他包依赖关系。 使用[专用包](https://packagist.com/)存储库创建中包。

### 主项目`composer.json`

```json
{
    "name": "example-client/region-1",
    "description": "Example Client Region 1",
    "type": "project",
    "require": {
        "magento/product-enterprise-edition": "2.3.5",
        "example-client/meta-region-1": "~1.0"
    },
    "minimum-stability": "dev",
    "prefer-stable": true,
    "repositories": [
        {"type": "composer", "url": "https://repo.packagist.com/example-client/"},
        {"packagist.org": false}
    ]
}
```

### `example-client/meta-region-1 composer.json`

```json
{
    "name": "example-client/meta-region-1",
    "description": "Region 1 meta package",
    "type": "metapackage",
    "require": {
        "example-client/meta-gra": "~1.0",
        "example-client/theme-frontend-region1",
        "example-client/language-es-es",
        "ingenico/ogone-client"
    }
}
```

### `example-client/meta-gra composer.json`

```json
{
    "name": "example-client/meta-gra",
    "description": "GRA meta package",
    "type": "metapackage",
    "require": {
        "geoip2/geoip2": "~2.0",
        "magento-services/module-stackify-logger": "~1.1",
        "example-client/sap-connector",
        "example-client/service-chat",
        "example-client/store-locator"
    }
}
```

每个模块、语言包、主题和库都有自己的Git存储库。 每个Git存储库都会自动同步到专用包存储库，并在该处生成包，前提是Git存储库的根中存在`composer.json`文件。

## 选项2：批量包

以下是单个Composer包中多个模块的示例。

批量包只能包含相同类型的包。 例如，如果您有Adobe Commerce模块、主题、语言包和库的多个包，则必须为每个类型创建单独的批量包。

供应商目录中的文件结构应类似于以下示例。 但是，请检查您的项目以查看Git存储库中应包含的内容)：

```tree
.
└── example-client/
    └── gra/
        └── src/
            ├── SapConnector/
            │   ├── etc/
            │   └── registration.php
            ├── ServiceChat/
            │   ├── etc/
            │   └── registration.php
            ├── StoreLocator/
            │   ├── etc/
            │   └── registration.php
            └── composer.json
```

`composer.json`文件应如下所示：

```json
{
    "name": "example-client/gra",
    "description": "GRA Modules",
    "require": {
        "magento/magento-composer-installer": "*"
    },
    "type": "magento2-module",
    "autoload": {
        "files": [
            "src/SapConnector/registration.php",
            "src/ServiceChat/registration.php",
            "src/StoreLocator/registration.php"
        ],
        "psr-4": {
            "ExampleClient\\SapConnector\\": "src/SapConnector",
            "ExampleClient\\ServiceChat\\": "src/ServiceChat",
            "ExampleClient\\StoreLocator\\": "src/StoreLocator"
        }
    }
}
```

## 选项3：拆分Git

此架构使用四个Git存储库来存储代码：

- `core`：包含Adobe Commerce核心安装。 用于升级Adobe Commerce版本。
- `GRA`：包含GRA代码。 所有GRA模块、语言包、白色标签主题和库。
- `brand/region`：每个品牌或地区都有自己的存储库，其中仅包含特定于品牌或地区的代码。
- `release`：以上所有内容都已合并到此Git存储库中。 此处仅允许合并提交。

![示意图说明了全局参考体系结构的拆分Git选项](../../../assets/playbooks/gra-split-git.png)

要设置此选项，请执行以下操作：

1. 在Git中创建四种存储库类型。 仅创建`core`和`GRA`存储库一次。 为每个品牌创建一个`brand/region`和一个`release`存储库。

   建议的存储库名称：

   - `m2-core`
   - `m2-gra`
   - `m2-region-x`/`m2-brand-x` （例如，`m2-emea`/`m2-adobe`）
   - `m2-release-region-x`/`m2-release-brand-x` （例如，`m2-release-emea`/`m2-release-adobe`）

1. 创建`release/`目录并运行以下命令，为所有存储库创建共享Git历史记录。

   ```bash
   git init
   git remote add origin git@github.com:example-client/m2-release-brand-x.git
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   touch .gitkeep
   git add .gitkeep
   git commit -m 'initialize repository'
   git push -u origin master
   git push core master
   git push gra master
   git push region-x master
   ```

1. 将每个存储库（`core`除外）克隆到计算机上的其他目录中。

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   git clone git@github.com:example-client/m2-region-x.git
   git clone git@github.com:example-client/m2-gra.git
   ```

1. [安装Adobe Commerce和编辑器](../../../installation/composer.md)。 删除`.gitignore`文件，添加`core`远程文件，添加并提交代码以及推送。

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition m2-core
   cd m2-core
   git init
   rm .gitignore
   git remote add origin git@github.com:example-client/m2-core.git
   git fetch
   git checkout .gitkeep
   git add --all
   git commit -m 'install Adobe Commerce'
   git push
   ```

1. 在`GRA`存储库中，创建以下目录：

   - `app/code/`
   - `app/design/`
   - `app/i18n/`
   - `lib/`

1. 添加代码。 删除`.gitignore`文件，添加并提交代码，添加远程数据库，然后推送。

1. 在`brand/region`存储库中。 执行与`GRA`存储库中相同的操作，并牢记文件必须是唯一的。 您不能同时在此存储库和`GRA`存储库中包含同一文件。

1. 在`release`存储库中，应用合并。

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   cd m2-release-brand-x
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

1. 删除`.gitkeep`文件。

1. 将`release`存储库部署到生产、测试、QA和开发服务器。 升级`core`、`GRA`和`brand`代码同样可以轻松运行以下命令：

   ```bash
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

## 选项4：莫诺雷波（推荐）

此策略非常模拟Magento Open SourceGit存储库的工作方式。

所有代码都在单个存储库中进行开发和测试。 自动化从此单一存储库中提取包，可使用编辑器将其安装在UAT和生产环境中。

![示意图说明了全局参考体系结构的monorepo选项](../../../assets/playbooks/gra-monorepo1.png)

使用monorepo选项，您可以轻松地在单个存储库中工作，同时还可以灵活地使用包组合实例。

版本控制和包蒸馏通过使用GitHub操作或GitLab操作通过自动化来完成。

![示意图说明了全局参考体系结构的monorepo选项](../../../assets/playbooks/gra-monorepo2.png)

有关此自动化的更多信息，请参阅以下资源：

- [https://github.com/symplify/monorepo-builder](https://github.com/symplify/monorepo-builder)
- [https://github.com/danharrin/monorepo-split-github-action](https://github.com/danharrin/monorepo-split-github-action)

>[!TIP]
>
>设置monorepo是先进的，但以最低的间接成本提供了最大的灵活性。

## 不要混合策略

不建议对GRA包使用组合方法，对品牌或区域包使用组合方法。`app/`

您不仅获得了两种方法的&#x200B;_所有优点_，还获得了它们的&#x200B;_缺点_。 您应该选择其中一个（Git或编辑器）以优化工作。

## 要避免的解决方案

- **表示GRA或品牌的模块命名约定**

  命名模块以表示GRA或品牌会导致缺乏灵活性。 相反，请使用编辑器中继信息来确定模块属于哪个组。 例如，对于客户VF，包`vf/meta-gra`包含对所有GRA包的引用，可以使用`composer require vf/meta-gra`命令进行安装。 包`vf/meta-kipling`包含对所有吉卜林特定包和`vf/meta-gra`包的引用。 例如，模块名为`vf/module-sales`和`vf/module-sap`。 此命名约定允许您在品牌状态与GRA状态之间移动包，但具有较低的影响。

- **每个实例的Adobe Commerce核心升级**

  为不同品牌或地区安排Adobe Commerce核心升级（包括修补程序升级），以尽可能紧密地共同执行。 由于兼容性限制，为共享模块支持多个Adobe Commerce版本会导致模块分叉，并将维护工作增加一倍。 在继续常规开发之前，请确保所有实例都在同一Adobe Commerce版本上运行，以防止这种工作量的增加。
