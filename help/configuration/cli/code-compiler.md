---
title: 代码编译器
description: 了解如何从命令行运行代码编译器。
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# 代码编译器

{{file-system-owner}}

代码编译包括以下内容（没有特定顺序）：

- 应用程序代码生成（工厂、代理）
- 区域配置聚合（优化了每区域的依赖项注入配置）
- 拦截器生成（优化拦截器代码生成）
- 拦截缓存生成
- 存储库代码生成（为API生成的代码）
- 服务数据属性生成（为数据对象生成的扩展类）

您可以在[\Magento\Setup\Module\Di\App\Task\Operation][operation]命名空间中找到代码编译类。

要运行单租户编译器，请执行以下操作：

```bash
bin/magento setup:di:compile
```

```
Generated code and dependency injection configuration successfully.
```

要在安装Commerce应用程序之前编译代码，请执行以下操作：

在某些情况下，您可能需要在安装Commerce应用程序之前编译代码。

1. 启用模块。

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   使用`[-c|--clear-static-content]`选项清除静态内容。 如果您之前已启用或禁用了模块，并且必须清除之前为其生成的静态内容，则必须执行此操作。

   请参阅[启用模块](../../installation/tutorials/manage-modules.md)。

1. 编译代码。

   ```bash
   bin/magento setup:di:compile
   ```

   ```
   Generated code and dependency injection configuration successfully.
   ```

要在没有数据库的情况下编译代码，请参阅[部署静态视图文件而不安装Magento](../cli/static-view-file-deployment.md)。

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
