---
title: 自定义cron作业和cron组引用
description: 了解如何使用cron组自定义cron。
exl-id: 16e342ff-aa94-4e31-8c75-dfea1ef02706
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# 自定义crons引用

本主题可帮助您为自定义模块设置crontab和（可选）cron组。 如果您的自定义模块需要定期计划任务，则必须为该模块设置crontab。 A _crontab_ 是cron作业配置。

（可选）您可以设置自定义组，通过自定义组可以独立于其他cron作业运行该组中定义的cron作业。

有关分步教程，请参阅 [配置自定义cron作业和cron组（教程）](custom-cron-tutorial.md).

有关cron作业的概述，请参见 [配置cron作业](../cli/configure-cron-jobs.md).

## 配置cron组

本节讨论如何为自定义模块选择性地创建cron组。 如果您不需要执行此操作，请继续下一部分。

A _cron组_ 是一个逻辑组，它使您能够一次为多个进程轻松运行cron。 大多数Commerce模块使用 `default` cron组；某些模块使用 `index` 组。

如果您要为自定义模块实施cron，则可以选择使用 `default` 组或其他组。

**为模块配置cron组**：

创建 `crontab.xml` 模块目录中的文件：

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

对于一个组，该文件应具有以下内容：

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="<group_name>">
        <job name="<job_name>" instance="<classpath>" method="<method>">
            <schedule><time></schedule>
        </job>
    </group>
</config>
```

其中：

| 值 | 描述 |
|---|---|
| `group_name` | cron组的名称。 组名称不必是唯一的。 您可以一次为一个组运行cron。 |
| `job_name` | 此cron作业的唯一ID。 |
| `classpath` | 要实例化的类（类路径）。 |
| `method` | 中的方法 `classpath` 来打电话。 |
| `time` | 以cron格式计划。 如果在Commerce数据库或其他存储中定义了计划，则忽略此参数。 |

结果 `crontab.xml` 对于两个组，可能如下所示：

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="<job_1_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_2_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
    <group id="index">
        <job name="<job_3_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_4_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

例如，请参阅 [Magento_客户crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### 指定Cron组选项

您可以声明新组并指定其配置选项（所有选项都在存储视图范围中运行），方法是 `cron_groups.xml` 文件，位于：

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

以下是 `cron_groups.xml` 文件：

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
    <group id="<group_name>">
        <schedule_generate_every>1</schedule_generate_every>
        <schedule_ahead_for>4</schedule_ahead_for>
        <schedule_lifetime>2</schedule_lifetime>
        <history_cleanup_every>10</history_cleanup_every>
        <history_success_lifetime>60</history_success_lifetime>
        <history_failure_lifetime>600</history_failure_lifetime>
        <use_separate_process>1</use_separate_process>
    </group>
</config>
```

其中：

| Option | 描述 |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | 将计划写入的频率（以分钟为单位） `cron_schedule` 表格。 |
| `schedule_ahead_for` | 将计划写入的时间（以分钟为单位） `cron_schedule` 表格。 |
| `schedule_lifetime` | 必须启动cron作业或将cron作业视为已错过（“太晚”而无法运行）的时间窗口（以分钟为单位）。 |
| `history_cleanup_every` | cron历史记录保留在数据库中的时间（以分钟为单位）。 |
| `history_success_lifetime` | 成功完成的cron作业的记录保留在数据库中的时间（以分钟为单位）。 |
| `history_failure_lifetime` | 失败的cron作业记录保留在数据库中的时间（以分钟为单位）。 |
| `use_separate_process` | 在单独的php进程中运行此cron组的作业 |

## 禁用cron作业

Cron作业没有 `disable` 功能与我们的相同 [观察者](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). 但是，可以使用以下技术禁用cron作业： `schedule` 包含永远不会发生的日期的时间。

例如，禁用 `visitor_clean` 在中定义的cron作业 `Magento_Customer` 模块：

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

要禁用 `visitor_clean` cron作业，创建自定义模块并重写 `visitor_clean` cron作业 `schedule`：

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

现在， `visitor_clean` cron作业已设置为在2月30日00:00运行 — 该日期永远不会发生。
