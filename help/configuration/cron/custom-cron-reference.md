---
title: 自定义cron作业和cron组引用
description: 了解如何使用cron组自定义cron。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---


# 自定义转码参考

本主题可帮助您为自定义模块设置crontab和（可选）cron组。 如果您的自定义模块需要定期计划任务，则必须为该模块设置crontab。 A _crontab_ 是cron作业配置。

（可选）您可以设置一个自定义组，该组可让您独立于其他cron作业运行该组中定义的cron作业。

有关分步教程，请参阅 [配置自定义cron作业和cron组（教程）](custom-cron-tutorial.md).

有关cron作业的概述，请参阅 [配置cron作业](../cli/configure-cron-jobs.md).

## 配置Cron组

本节将讨论如何（可选）为自定义模块创建cron组。 如果您不需要执行此操作，请继续下一节。

A _cron组_ 是一个逻辑组，通过它可以一次轻松地为多个进程运行cron。 大多数商务模块都使用 `default` 康隆集团；某些模块使用 `index` 群组。

如果要为自定义模块实施cron，则可以选择使用 `default` 组或其他组。

**为模块配置CRON组**:

创建 `crontab.xml` 文件：

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

对于一个组，文件应具有以下内容：

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
| `group_name` | cron组的名称。 组名称不必唯一。 您一次可以为一个组运行cron。 |
| `job_name` | 此Cron作业的唯一ID。 |
| `classpath` | 要实例化的类（类路径）。 |
| `method` | 方法 `classpath` 呼叫。 |
| `time` | 以cron格式计划。 如果在Commerce数据库或其他存储中定义了计划，请忽略此参数。 |

结果 `crontab.xml` 两个组可能如下所示：

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

例如，请参阅 [Magento_Customer crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### 指定Cron组选项

您可以声明一个新组，并通过 `cron_groups.xml` 文件，位于：

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

| 选项 | 描述 |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | 将计划写入的频率（以分钟为单位） `cron_schedule` 表。 |
| `schedule_ahead_for` | 将计划写入 `cron_schedule` 表。 |
| `schedule_lifetime` | 必须启动cron作业或认为cron作业已错过（“太晚”，无法运行）的时间范围（以分钟为单位）。 |
| `history_cleanup_every` | 在数据库中保留该cron历史记录的时间（以分钟为单位）。 |
| `history_success_lifetime` | 成功完成的cron作业记录保留在数据库中的时间（以分钟为单位）。 |
| `history_failure_lifetime` | 在数据库中保留失败cron作业记录的时间（以分钟为单位）。 |
| `use_separate_process` | 在单独的php流程中运行此cron组的作业 |

## 禁用cron作业

Cron作业没有 `disable` 功能 [观察](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). 但是，可以使用以下技术来禁用cron作业： `schedule` 包含永远不会发生的日期的时间。

例如，禁用 `visitor_clean` cron作业在 `Magento_Customer` 模块：

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

禁用 `visitor_clean` cron作业，创建自定义模块并重写 `visitor_clean` cron作业 `schedule`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

现在， `visitor_clean` cron作业已设置为在2月30日00:00运行，该日期永远不会发生。
