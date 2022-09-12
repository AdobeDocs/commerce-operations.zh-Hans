---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# 用于消息队列使用者的CLI选项

| 名称 | 描述 | 值 | 必需 |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | 确定用户是否将等待队列中的消息。 | 1 — 是，0 — 否 | 否 |

* `0`:用户处理队列中的可用消息，关闭TCP连接并终止。 即使已处理的消息数少于 `--max_messages` 值。

* `1`:用户将继续处理来自消息队列的消息，直到达到消息的最大数量(为 `--max_messages` 在 `queue:consumers:start` 命令)，然后关闭TCP连接并终止使用者进程。 如果队列在到达之前空了 `--max_messages` 消费者会等待更多消息到达。 如果您使用工作程序运行消费者，而不是使用cron作业，请将此变量设置为 `1`.

>[!WARNING]
>
>的 `--consumers-wait-for-messages` 选项是全局选项，不能为每个客户单独进行配置。
