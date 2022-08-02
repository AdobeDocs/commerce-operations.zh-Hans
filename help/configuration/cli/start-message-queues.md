---
title: 启动消息队列使用者
description: 了解如何启动消息队列消费者。
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# 启动消息队列使用者

{{file-system-owner}}

必须启动消息队列使用者才能启用异步操作，如Inventory management批量操作以及REST批量和异步端点。 要启用B2B功能，您必须启动多个用户。 第三方模块可能还要求您启动自定义消费者。

要查看所有用户的列表，请执行以下操作：

```bash
bin/magento queue:consumers:list
```

要启动消息队列使用者，请执行以下操作：

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

在消耗所有可用消息后，命令将终止。 您可以再次手动或通过cron作业运行命令。 您还可以运行 `magento queue:consumers:start` 命令处理大消息队列。 例如，您可以附加 `&` 命令在后台运行它，返回到提示符，然后继续运行命令：

```bash
bin/magento queue:consumers:start <consumer_name> &
```

请参阅 [队列:consumers:开始](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#queueconsumersstart) (在 _命令行工具引用_ 有关命令选项、参数和值的详细信息。

>[!INFO]
>
>的 `--multi-process` 选项在 `queue:consumers:start` 命令，但要使用并行进程运行使用者，请配置 [`multiple_processes`](../queues/manage-message-queues.md#configuration) 选项 `/app/etc/env.php`. 否则，如果 `queue:consumers:start` 使用 `--multi-process` 选项，则它仅在单个线程上工作。
