---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# 消息队列使用者的CLI选项

| 名称 | 描述 | 值 | 必需 |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | 确定使用者是否将等待来自队列的消息。 | 1 — 是，0 — 否 | 否 |

* `0`：使用者处理队列中的可用消息，关闭TCP连接并终止。 即使已处理的消息数小于 `--max_messages` 在启动使用者期间指定的值。

* `1`：使用者继续处理来自消息队列的消息，直到达到消息数量上限（为指定的值） `--max_messages` 在 `queue:consumers:start` 命令)，然后关闭TCP连接并终止使用者进程。 如果队列在到达之前清空 `--max_messages` 消费者等待更多消息到达。 如果您使用工作程序运行消费者，而不是使用cron作业，则将此变量设置为 `1`.

>[!WARNING]
>
>此 `--consumers-wait-for-messages` 选项是一个全局选项，不能为每个使用者单独配置。
