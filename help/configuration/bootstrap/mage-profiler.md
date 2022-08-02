---
title: 启用分析
description: 了解有关启用MAGE Profiler以与分析工具一起使用的更多信息。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# 启用分析

通过商务分析，您可以：

- 启用内置探查器。

   您可以使用带有商务的内置探查器执行分析性能等任务。 分析的性质取决于您使用的分析工具。 我们支持多种格式，包括HTML。 启用探查器时， `var/profiler.flag` 文件生成，指示探查器已启用并进行了配置。 禁用后，将删除此文件。

- 在“商务”页面上显示依赖关系图。

   A _依赖关系图_ 是对象依赖关系及其所有依赖关系的列表，以及这些依赖关系的所有依赖关系等。

   你应该对 _未使用的依赖项_，这些对象是之前创建的对象，因为它们是在某个构造函数中请求的，但从未使用过（即，未调用其任何方法）。 因此，浪费了用于创建这些依赖关系的处理器时间和内存。

商务在 [`Magento\Framework\Profiler`][profiler].

可以使用MAGE_PROFILER变量或命令行启用和配置Profiler。

## 设置MAGE_PROFILER

您可以设置 `MAGE_PROFILER` 以 [设置引导参数的值](../bootstrap/set-parameters.md).

`MAGE_PROFILER` 支持以下值：

- `1` 启用特定探查器的输出。

   您可以使用以下任一值来启用特定探查器：

   - `csvfile` 使用 [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - 任何其他值(除 `2`)，包括一个空值，该值使用 [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html]

- `2` 启用依赖关系图。

   依赖关系图通常显示在页面底部。 下图显示了输出的一部分：

   ![依赖关系图](../../assets/configuration/depend-graphs.png)

## CLI命令

可以使用CLI命令启用或禁用探查器：

- `dev:profiler:enable <type>` 启用profiler的 `type` of `html` （默认）或 `csvfile`. 启用后，将显示一个旗标文件 `var/profiler.flag` 创建时。
- `dev:profiler:disable` 禁用探查器。 禁用后，flagfile `var/profiler.flag` 删除。

要启用依赖关系图，请使用变量选项。

**启用或禁用探查器**:

1. 登录到您的商务服务器。
1. 更改为Commerce安装目录。
1. 作为文件系统所有者，请启用Profiler:

   使用类型启用探查器 `html` 并创建标记文件：

   ```bash
   bin/magento dev:profiler:enable html
   ```

   使用类型启用探查器 `csvfile` 并创建标记文件：

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   输出将保存到 `<project-root>/var/log/profiler.csv`. 的 `profiler.csv` 会在每次页面刷新时被覆盖。

   要禁用Profiler并删除flagfile，请执行以下操作：

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
