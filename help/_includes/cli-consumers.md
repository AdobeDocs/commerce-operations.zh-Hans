---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---
# 消息队列使用者的CLI选项

| 名称 | 描述 | 值 | 必填 |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | 确定使用者是否将等待来自队列的消息。 | 1 — 是，0 — 否 | 否 |

* `0`：使用者处理队列中的可用消息，关闭TCP连接并终止。 即使已处理的消息数小于在启动使用者期间指定的`--max_messages`值，使用者也不会等待其他消息进入队列。

* `1`：使用者继续处理来自讯息伫列的讯息，直到达到讯息数目上限（在`queue:consumers:start`命令上为`--max_messages`指定的值）为止，然后关闭TCP连线并终止使用者处理序。 如果队列在到达`--max_messages`之前排空，则使用者将等待更多消息到达。 如果使用工作程序运行使用者而不是使用cron作业，则将此变量设置为`1`。

>[!WARNING]
>
>`--consumers-wait-for-messages`选项是全局选项，不能为每个使用者单独配置。
