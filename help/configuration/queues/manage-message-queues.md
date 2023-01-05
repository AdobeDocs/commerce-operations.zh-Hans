---
title: 管理消息队列
description: 了解如何从命令行中管理消息队列，以用于Adobe Commerce。
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---


# 管理消息队列

您可以使用cron作业或外部进程管理器从命令行管理消息队列，以确保用户正在检索消息。

## 流程管理

Cron作业是重新启动消费者的默认机制。 启动的流程 `cron` 使用指定的消息数，然后终止。 重新运行 `cron` 重新启动用户。

以下示例显示了 `crontab` 运行用户的配置：

> /app/code/Magento/MessageQueue/etc/crontab.xml

```xml
...
<job name="consumers_runner" instance="Magento\MessageQueue\Model\Cron\ConsumersRunner" method="run">
    <schedule>* * * * *</schedule>
</job>
...
```

>[!INFO]
>
>您检查消息队列的频率取决于您的业务逻辑和可用系统资源。 通常，您可能希望检查新客户，并更频繁地发送欢迎电子邮件，而不是执行资源密集型流程，例如更新目录。 您应定义 `cron` 根据您的业务需要安排时间。
>
>可以在群组的管理员商店>设置>配置>高级>系统>开机配置选项中对其进行配置：消费者。
>
>请参阅 [配置并运行cron](../cli/configure-cron-jobs.md) 有关使用的更多信息 `cron` 和商务。

您还可以使用流程管理器，例如 [主管](http://supervisord.org/index.html) 来监视进程的状态。 管理器可以使用命令行根据需要重新启动进程。

## 配置

### 默认行为

- Cron作业 `consumers_runner` 已启用
- Cron作业 `consumers_runner` 运行所有已定义的用户
- 每个用户处理10000条消息，然后终止

>[!INFO]
>
>如果您的Adobe Commerce商店托管在云平台上，请使用 [`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) 配置 `consumers_runner` 创建作业。

### 特定配置

编辑 `/app/etc/env.php` 配置cron作业的文件 `consumers_runner`.

```php
...
    'cron_consumers_runner' => [
        'cron_run' => false,
        'max_messages' => 20000,
        'consumers' => [
            'consumer1',
            'consumer2',
        ],
        'multiple_processes' => [
            'consumer1' => 4
        ]
    ],
...
```

- `cron_run`  — 启用或禁用 `consumers_runner` cron作业(默认= `true`)。
- `max_messages`  — 每个用户在终止前必须处理的最大消息数(默认值= `10000`)。 尽管我们不建议使用，但您可以使用0来阻止消费者终止。 请参阅 [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) 配置用户处理来自消息队列的消息的方式。
- `consumers`  — 一个字符串数组，指定要运行的用户。 空数组运行 *全部* 消费者。
- `multiple_processes`  — 键值对数组，指定在多少个进程中运行哪个使用者。

   >[!INFO]
   >
   >不建议在MySQL操作的队列上运行多个使用者。 请参阅 [将消息队列从MySQL更改为AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) 以了解更多信息。

   >[!INFO]
   >
   >如果您的Adobe Commerce商店托管在云平台上，请使用 [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#consumers_wait_for_max_messages) 配置用户处理来自消息队列的消息的方式。

请参阅 [启动消息队列使用者](../cli/start-message-queues.md).
