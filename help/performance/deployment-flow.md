---
title: 部署流程
description: 了解在生产环境中部署Adobe Commerce或Magento Open Source所需的步骤。
feature: Best Practices, Deploy
exl-id: 88da0b1b-5aa7-4f1c-9d01-ae58324b2754
source-git-commit: 012cba58b336b032b1c911539008c1fb961c2e07
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# 部署流程

此 [!DNL Commerce] 生产部署流程可帮助存储实现最佳性能。

## 安装依赖项

此 `composer.json` 和 `composer.lock` 文件管理 [!DNL Commerce] 依赖关系，并为每个包安装适当的版本。 必须先安装依赖项，然后才能安装 [预处理依赖项注入指令](#preprocess-dependency-injection-instructions) 如果您计划更新 [自动加载机](#update-the-autoloader).

安装 [!DNL Commerce] 依赖关系：

```bash
composer install --no-dev
```

## 预处理依赖项注入指令

在预处理和编译依赖项注入(DI)指令时，请Magento：

* 读取和处理所有当前配置
* 分析类之间的依赖关系
* 创建自动生成的文件（包括代理、工厂等）
* 将编译后的数据和配置存储在缓存中，最多可节省25%的请求处理时间

要预处理和编译DI指令，请执行以下操作：

```bash
bin/magento setup:di:compile
```

## 更新自动加载程序

编译完成后，请确认 [APCu已启用](../performance/software.md#php-settings) 并更新自动加载程序：

要更新自动加载程序，请执行以下操作：

>[!INFO]
>
>此 `-o` 选项将PSR-0/4自动加载转换为类映射，以获得更快的自动加载程序。 此 `--apcu` 选项使用APCu缓存已找到/未找到类。

```bash
composer dump-autoload -o --apcu
```

如果计划更新自动加载程序，则必须按顺序运行以下命令：

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

部署静态内容原因 [!DNL Commerce] 要执行以下操作：

* 分析所有静态资源
* 执行内容合并、最小化和捆绑
* 读取和处理主题数据
* 分析主题回退
* 将所有已处理和实例化内容存储到特定文件夹以供进一步使用

如果未部署静态内容， [!DNL Commerce] 会动态执行所有列出的操作，从而显着增加响应时间。

您可以使用多种选项，根据存储大小和履行需求自定义部署操作。 最常见的是紧凑部署策略。 请参阅 [静态文件部署策略](../configuration/cli/static-view-file-strategy.md)

要部署静态内容，请执行以下操作：

```bash
bin/magento setup:static-content:deploy
```

此命令允许Composer重新生成到项目文件的映射，以便更快地加载这些文件。

## 设置生产模式

>[!INFO]
>
>将模式设置为生产模式会自动运行 `setup:di:compile` 和 `setup:static-content:deploy`.

最后，您需要将商店置于生产模式。 生产模式经过专门优化，可提供存储的最大性能。 它还停用了所有特定于开发人员的功能。 这可以在以下位置完成： `.htaccess` 或 `nginx.conf` 文件：

`SetEnv MAGE_MODE production`

您还可以在一个CLI命令中部署静态内容、编译内容并设置模式：

```bash
bin/magento deploy:mode:set production
```

命令在后台运行，不允许在每个特定步骤上设置其他选项。

## 其他启动前操作

建议执行这些步骤，但并非强制性的。 您可以在以生产模式启动存储之前立即执行这些操作。 该列表包括：

* 重新编入数据索引，以避免索引中出现任何不一致的数据。
* 刷新缓存以确保缓存中没有留下旧的或不正确的数据。
* 预热缓存，提前调出最受欢迎或最关键的存储页面，以便生成并存储这些页面的缓存。 此操作可以使用任何Internet Crawler执行，或者手动执行（如果存储空间较小）。
