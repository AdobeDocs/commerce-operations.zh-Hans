---
title: 代码编译器
description: 了解如何从命令行运行代码编译器。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# 代码编译器

{{file-system-owner}}

代码编译包括以下内容（无特定顺序）：

- 应用程序代码生成（工厂、代理）
- 区域配置聚合（已优化） [依赖注入](https://glossary.magento.com/dependency-injection) 每区域配置)
- 拦截器生成（拦截器优化代码生成）
- 侦听缓存生成
- 存储库代码生成（为API生成的代码）
- 服务数据属性生成（生成） [扩展](https://glossary.magento.com/extension) 数据对象的类)

您可以在 [\Magento\Setup\Module\Di\App\Task\Operation][operation] 命名空间。

要运行单租户编译器，请执行以下操作：

```bash
bin/magento setup:di:compile
```

```terminal
Generated code and dependency injection configuration successfully.
```

要在安装商务应用程序之前编译代码，请执行以下操作：

在某些情况下，您可能需要先编译代码，然后再安装商务应用程序。

1. 启用模块。

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   使用 `[-c|--clear-static-content]` 选项清除 [静态内容](https://glossary.magento.com/static-content). 如果您之前已启用或已禁用模块，并且必须清除之前为这些模块生成的静态内容，则必须执行此操作。

   请参阅 [启用模块](../../installation/tutorials/manage-modules.md).

1. 编译代码。

   ```bash
   bin/magento setup:di:compile
   ```

   ```terminal
   Generated code and dependency injection configuration successfully.
   ```

要编译没有数据库的代码，请参阅 [部署静态视图文件，而无需安装Magento](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
