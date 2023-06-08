---
title: 管理消息队列
description: 了解如何通过Adobe Commerce的命令行管理消息队列。
exl-id: 619e5df1-39cb-49b6-b636-618b12682d32
source-git-commit: 8dce1f1e961ec02d7783a7423a51a7d4567dce79
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 管理消息队列

您可以使用cron作业或外部进程管理器从命令行管理消息队列，以确保使用者正在检索消息。

## 流程管理

Cron作业是重新启动使用者的默认机制。 进程启动者 `cron` 使用指定数量的消息，然后终止。 重新运行 `cron` 重新启动消费者。

以下示例显示了 `crontab` 运行使用者的配置：

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
>检查消息队列的频率取决于您的业务逻辑和可用的系统资源。 通常，您可能希望检查新客户，并发送欢迎电子邮件，而不是执行更占用资源的过程（如更新目录）。 您应该定义 `cron` 根据您的业务需求进行计划。
>
>可以在管理员商店>设置>配置>高级>系统> Cron配置选项中配置组：使用者。
>
>参见 [配置和运行cron](../cli/configure-cron-jobs.md) 有关使用的更多信息 `cron` 使用Commerce。

也可以使用进程管理器，例如 [主管](https://supervisord.readthedocs.io/en/latest/) 以监视进程状态。 管理员可以使用命令行根据需要重新启动进程。

## 配置

### 默认行为

- Cron作业 `consumers_runner` 已启用
- Cron作业 `consumers_runner` 运行所有已定义的使用者
- 每个使用者处理消息10000然后终止

>[!INFO]
>
>如果您的Adobe Commerce商店托管在Cloud平台上，请使用 [`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) 配置 `consumers_runner` cron job（CRON作业）。

### 特定配置

编辑 `/app/etc/env.php` 用于配置cron作业的文件 `consumers_runner`.

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

- `cron_run`  — 一个布尔值，用于启用或禁用 `consumers_runner` cron作业(默认= `true`)。
- `max_messages`  — 终止前每个使用者必须处理的最大消息数(默认值= `10000`)。 虽然我们不建议这样做，但您可以使用0来阻止消费者终止。 参见 [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) 配置使用者处理消息队列中消息的方式。
- `consumers`  — 一个字符串数组，指定要运行的使用者。 空数组运行 *所有* 消费者。
- `multiple_processes`  — 一个键值对数组，指定要在多少个进程中运行的使用者。 在Commerce 2.4.4或更高版本中支持。

  >[!INFO]
  >
  >不建议在MySQL操作的队列上运行多个使用者。 参见 [将消息队列从MySQL更改为AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) 了解更多信息。

  >[!INFO]
  >
  >如果您的Adobe Commerce商店托管在Cloud平台上，请使用 [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#consumers_wait_for_max_messages) 配置使用者处理消息队列中消息的方式。

参见 [启动消息队列使用者](../cli/start-message-queues.md).
