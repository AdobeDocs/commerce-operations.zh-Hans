---
title: 启动消息队列使用者
description: 了解如何启动消息队列使用者。
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# 启动消息队列使用者

{{file-system-owner}}

您必须启动 [消息队列使用者](../queues/consumers.md) 启用异步操作，如Inventory management批量操作和REST批量操作以及异步端点。 要启用B2B功能，必须启动多个使用者。 第三方模块可能还要求您启动自定义消费者。

要查看所有使用者的列表，请执行以下操作：

```bash
bin/magento queue:consumers:list
```

要启动消息队列使用者，请执行以下操作：

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

使用所有可用消息后，该命令将终止。 您可以手动或使用cron作业再次运行该命令。 您还可以运行 `magento queue:consumers:start` 命令处理大型消息队列。 例如，您可以附加 `&` 命令在后台运行，返回提示符，然后继续运行命令：

```bash
bin/magento queue:consumers:start <consumer_name> &
```

请参阅 [队列:consumers:开始](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#queueconsumersstart) 在的Commerce部分中 _命令行工具引用_ 有关命令选项、参数和值的详细信息。

>[!INFO]
>
>此 `--multi-process` 选项存在于中 `queue:consumers:start` 命令，但若要使用并行进程运行使用者，请配置 [`multiple_processes`](../queues/manage-message-queues.md#configuration) 中的选项 `/app/etc/env.php`. 否则，如果 `queue:consumers:start` 调用时使用 `--multi-process` 选项，它仅在单个线程上工作。
