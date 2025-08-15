---
title: 启动消息队列使用者
description: 了解如何启动消息队列使用者。
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: cdd752532d17e1168e0aa7d354ec283089d98be3
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# 启动消息队列使用者

{{file-system-owner}}

必须启动[消息队列使用者](../queues/consumers.md)以启用异步操作，例如Inventory management批量操作以及REST批量操作和异步端点。 要启用B2B功能，必须启动多个使用者。 第三方模块可能还要求您启动自定义消费者。

要查看所有使用者的列表，请执行以下操作：

```bash
bin/magento queue:consumers:list
```

要启动消息队列使用者，请执行以下操作：

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

使用所有可用消息后，该命令将终止。 您可以手动或使用cron作业再次运行该命令。 您还可以运行`magento queue:consumers:start`命令的多个实例来处理大型消息队列。 例如，您可以将`&`附加到命令中，以便在后台运行该命令，返回提示符，然后继续运行命令：

```bash
bin/magento queue:consumers:start <consumer_name> &
```

有关命令选项、参数和值的详细信息，请参阅[`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart)命令行工具引用&#x200B;_的Commerce部分中的_。

>[!INFO]
>
>`--multi-process`选项存在于`queue:consumers:start`命令中，但若要使用并行进程运行使用者，请在[`multiple_processes`](../queues/manage-message-queues.md#configuration)中配置`/app/etc/env.php`选项。 否则，如果使用`queue:consumers:start`选项调用`--multi-process`，则它仅在单个线程上运行。
