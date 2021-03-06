---
title: 部署流程
description: '了解在生产环境中部署Adobe Commerce或Magento Open Source所需的步骤。 '
source-git-commit: 9ab52374e031bd2b0a846dd5f47c89ff788dcafa
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---


# 部署流程

的 [!DNL Commerce] 生产部署流程有助于存储达到最高性能。

## 安装依赖项

的 `composer.json` 和 `composer.lock` 文件管理 [!DNL Commerce] 依赖项，并为每个包安装相应的版本。 必须先安装依赖项 [预处理依赖项注入指令](#preprocess-dependency-injection-instructions) 如果您计划更新 [自动加载器](#update-the-autoloader).

安装 [!DNL Commerce] 依赖关系：

```bash
composer install --no-dev
```

## 预处理依赖项注入指令

在预处理和编译依赖关系注入(ID)指令时，Magento:

* 读取并处理所有当前配置
* 分析类之间的依赖关系
* 创建自动生成的文件（包括代理、工厂等）
* 将编译的数据和配置存储在缓存中，在请求处理上可节省多达25%的时间

要预处理和编译DI指令，请执行以下操作：

```bash
bin/magento setup:di:compile
```

## 更新自动加载器

编译完成后，确认 [已启用APCu](https://devdocs.magento.com/guides/v2.4/performance-best-practices/software.html#php-settings) 和更新自动加载器：

要更新自动加载器，请执行以下操作：

>[!INFO]
>
>的 `-o` 选项会将PSR-0/4自动加载转换为classmap，以获得更快的自动加载器。 的 `--apcu` 选项使用APCu来缓存已找到/未找到的类。

```bash
composer dump-autoload -o --apcu
```

如果计划更新自动加载器，则必须按顺序运行以下命令：

```bash
composer install --no-dev
```

```bash
bin/magento setup:di:compile
```

```bash
composer dump-autoload -o
```

```bash
bin/magento setup:static-content:deploy
```

## 部署静态内容

部署静态内容原因 [!DNL Commerce] 要执行以下操作，请执行以下操作：

* 分析所有静态资源
* 执行内容合并、最小化和捆绑
* 读取和处理主题数据
* 分析主题回退
* 将所有已处理和实体化内容存储到特定文件夹，以便进一步使用

如果未部署静态内容， [!DNL Commerce] 即时执行所有列出的操作，从而显着增加响应时间。

您可以使用各种选项根据存储大小和履行需求自定义部署操作。 最常见的是紧凑部署策略。 请参阅 [静态文件部署策略](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-static-deploy-strategies.html)

要部署静态内容，请执行以下操作：

```bash
bin/magento setup:static-content:deploy
```

此命令允许编辑器重建到项目文件的映射，以便它们加载速度更快。

## 设置生产模式

>[!INFO]
>
>将模式设置为生产模式会自动运行 `setup:di:compile` 和 `setup:static-content:deploy`.

最后，您需要将存储置于生产模式。 生产模式已经过专门优化，可最大程度地提高存储的性能。 它还会停用所有特定于开发人员的功能。 此操作可以在 `.htaccess` 或 `nginx.conf` 文件：

`SetEnv MAGE_MODE production`

您还可以部署静态内容、编译内容，并在一个CLI命令中设置模式：

```bash
bin/magento deploy:mode:set production
```

该命令在后台运行，不允许您在每个特定步骤中设置其他选项。

## 其他启动前操作

建议执行这些步骤，但不是强制步骤。 您可以在以生产模式启动存储之前立即执行这些操作。 该列表包括：

* 重新编入数据索引，以避免索引中存在任何不一致的数据。
* 刷新缓存，以确保缓存中没有留下旧数据或错误数据。
* 预热缓存，该缓存会提前调用最受欢迎或最关键的存储页面，因此会生成并存储这些页面的缓存。 此操作可以通过任何Internet Crawler执行，也可以手动执行（如果您有小商店）。
