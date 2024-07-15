---
title: 编辑器提示和技巧
description: 了解常见的编辑器开发任务和指南，以便快速解决问题。
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 5ead5fb1-3bb3-4e77-a4f1-8e10c4f91efb
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# 编辑器提示和技巧

使用编辑器开发Adobe Commerce模块时，您可能会遇到问题。 这些最佳实践描述了一些使开发更轻松并帮助您快速解决问题的常见任务。

>[!NOTE]
>
>这些准则主要适用于[全局参考体系结构(GRA)](../overview.md)项目。

## 加速编辑器

安装[https://github.com/hirak/prestissimo](https://github.com/hirak/prestissimo)以通过异步包下载来加快Composer的速度。

```bash
composer global require hirak/prestissimo
```

如果遇到问题，请卸载`prestissimo`：

```bash
composer global remove hirak/prestissimo
```

## 解决模糊的版本问题

编辑器有时因包版本而陷入死锁。 您可能会看到有关不兼容版本的消息，即使这些版本不兼容也是如此。 在调试兼容性问题之前，请尝试重置编辑器：

1. 清除编辑器缓存。

   ```bash
   composer clearcache
   ```

1. 删除所有包的`composer.lock`文件。

   ```bash
   rm -rf vendor/* composer.lock
   ```

1. 重新安装编辑器包。

   ```bash
   composer install
   ```

>[!TIP]
>
>这些步骤会将所有包更新到最新可用版本。 从Git还原`composer.lock`文件以撤消这些升级。

## 检查客户端包中可能的更新

1. 了解哪些包可能已过期。

   ```bash
   composer outdated
   ```

1. 使用通配符和/或`--minor-only`选项进行筛选，以跳过向后不兼容的升级：

   ```bash
   composer outdated 'magento/*'
   composer outdated --minor-only 'magento/*'
   ```

## 了解模块是否已安装

查看有关Git分支上所有已安装包的详细信息。

```bash
composer info
```

在切换Git分支后运行`composer install`并在运行`composer info`之前运行。 否则，Composer将显示有关您签出的上一个分支的详细信息。

>[!TIP]
>
>要筛选或搜索，请使用以下命令之一。
>
>```bash
>composer info '*magento*'
>composer info | grep magento
>```

## 了解安装（特定版本的）软件包的原因

有时，由于另一个包中存在严格的依赖关系，因此Composer会安装最新可用版本的包。

了解另一个包中是否存在严格的依赖关系。

```bash
composer why client/module-example
```

如果结果显示了一个包含中继（或其他非显式需要的包）的列表，请在该包上运行以下命令：

```bash
composer why example/metapackage
```

## 了解未安装软件包的原因

有时，Composer不会安装包，因为它与其他包冲突，或者由其他包替换它，或者您未将其定义为依赖关系。

了解未安装软件包的原因。

```bash
composer why-not client/module-example
```

## 托管专用编辑器存储库

如果需要专用编辑器存储库，请使用[专用包程序](https://packagist.com/)或[JFrog Artifactory](https://jfrog.com/integration/php-composer-repository/)。 不要使用[Satis](https://github.com/composer/satis)。

- **私有包管理器**&#x200B;是安全的，对于三个管理员用户每年大约花费600 USD，并且是托管的。

- **JFrog Artifactory**&#x200B;起始价格为每年1,176美元。 它并不像Packagist那样常用，但它支持的语言比PHP多。

- **Satis**&#x200B;没有内置的安全性，没有自动化功能，需要额外的托管。 只有你的时间也是免费的，才有自由。

## 版本控制包

按照Adobe Commerce [版本控制架构](https://developer.adobe.com/commerce/php/development/versioning/)中的说明使用[语义版本控制2.0.0](https://semver.org/spec/v2.0.0.html)。 不要重新发明轮子。

对于Adobe Commerce模块依赖项，请按照[模块版本依赖项](https://developer.adobe.com/commerce/php/development/versioning/dependencies/)文档操作。

请勿在`composer.json`文件内使用版本定义。 请改用Git标记进行版本。 请参阅[Composer版本和约束](https://getcomposer.org/doc/articles/versions.md#versions-and-constraints)。

## 将来自归档文件但不通过Composer的模块放在何处

在存档中为模块创建Git存储库并自行托管它们。 每个Adobe Commerce模块都有一个`composer.json`文件。 在Git中托管它并与专用包管理器同步后，即可使用Composer安装它。

当您收到包的新版本时，请将代码上传到Git并标记它，然后使用编辑器安装新版本。
