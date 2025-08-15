---
title: 启用分析
description: 了解有关使MAGE Profiler能够与您的分析工具一起使用的更多信息。
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# 启用分析

通过Commerce分析，您可以：

- 启用内置探查器。

  您可以使用带有Commerce的内置探查器来执行分析性能等任务。 分析的性质取决于您使用的分析工具。 我们支持多种格式，包括HTML。 启用Profiler时，将生成一个`var/profiler.flag`文件，指示已启用Profiler并配置。 禁用后，将删除此文件。

- 在Commerce页面上显示依赖关系图。

  _依赖关系图_&#x200B;是对象依赖关系及其所有依赖关系，以及这些依赖关系的所有依赖关系等的列表。

  您应该特别关注&#x200B;_未使用的依赖项_&#x200B;的列表，这些依赖项是由于某些构造函数中请求但从未使用过而创建的对象（也就是说，未调用任何方法）。 因此，用于创建这些依赖项的处理器时间和内存被浪费了。

Commerce在[`Magento\Framework\Profiler`][profiler]中提供基本功能。

可以使用MAGE_PROFILER变量或命令行来启用和配置Profiler。

## 设置MAGE_PROFILER

您可以按照`MAGE_PROFILER`中讨论的任何方法来设置[的值。请设置引导参数值](../bootstrap/set-parameters.md)。

`MAGE_PROFILER`支持以下值：

- `1`以启用特定探查器的输出。

  您可以使用以下值之一来启用特定的Profiler：

   - 使用`csvfile`的[`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - 任何其他值（`2`除外），包括使用[`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html]的空值

- `2`以启用依赖关系图。

  依赖关系图通常显示在页面底部。 下图显示了输出的部分：

  ![依赖关系图](../../assets/configuration/depend-graphs.png)

## CLI命令

您可以使用CLI命令启用或禁用Profiler：

- `dev:profiler:enable <type>`通过`type`的`html`（默认）或`csvfile`启用探查器。 启用后，将创建标志文件`var/profiler.flag`。
- `dev:profiler:disable`禁用该探查器。 禁用后，将删除flagfile `var/profiler.flag`。

要启用依赖关系图，请使用变量选项。

**要启用或禁用Profiler**：

1. 登录到您的Commerce服务器。
1. 转到Commerce安装目录。
1. 作为文件系统所有者，启用探查器：

   要使用类型`html`启用探查器并创建flagfile，请执行以下操作：

   ```bash
   bin/magento dev:profiler:enable html
   ```

   要使用类型`csvfile`启用探查器并创建flagfile，请执行以下操作：

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   输出已保存到`<project-root>/var/log/profiler.csv`。 每次刷新页面时都会覆盖`profiler.csv`。

   要禁用Profiler并删除Flagfile，请执行以下操作：

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
