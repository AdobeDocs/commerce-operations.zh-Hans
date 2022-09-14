---
title: “ [!UICONTROL RabbitMQ] 选项卡”
description: 了解 [!UICONTROL RabbitMQ] 选项卡 [!DNL Observation for Adobe Commerce].
source-git-commit: 3f2a401bb916fc04405f21ba2acfc42f7defdccb
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# 的 [!UICONTROL RabbitMQ] 选项卡

的 **[!UICONTROL RabbitMQ]** 选项卡中集中了以下信息 [!DNL RabbitMQ] 信号。

## [!UICONTROL RabbitMQ Infrastructure events]

![RabbitMQ基础架构事件](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

的 **[!UICONTROL RabbitMQ Infrastructure events]** 框架显示涉及的基础架构事件 [!DNL RabbitMQ] 在选定时间范围内发生的事件：

* %响应 [错误] 对于节点 [rabbit@host1]:意外的http响应来自%&#39;)作为“exempented_resp_node1”
* “%响应” [错误] 对于节点 [rabbit@host2]:意外的http响应（来自%&#39;）作为“exempent_resp_node2”
* “%响应” [错误] 对于节点 [rabbit@host3]:意外的http响应（来自%&#39;）作为“意外的resp_node3”
* “%响应” [错误] 对于节点 [rabbit@host3]:获取“http://localhost:15672/api/healthchecks/node/rabbit@host3”：上下文截止日期超过%”)作为“node3_timeout_exceeded”
* “%响应” [错误] 对于节点 [rabbit@host1]:获取“http://localhost:15672/api/healthchecks/node/rabbit@host1”：上下文截止时间超过%”)作为“node1_timeout_exceeded”
* “%响应” [错误] 对于节点 [rabbit@host2]:获取“http://localhost:15672/api/healthchecks/node/rabbit@host2”：上下文截止时间超过%”)作为“node2_timeout_exceeded”
* “%401未授权%”)作为“401_unauth”
* “%401未授权%”)作为“401_unauth”
* %服务已重新启动：rabbitmq-server%”)作为“rmq_service_restart”
* “%响应” [失败] 对于节点 [rabbit@host1]:nodedown%”)作为“rmq_node1_down”
* “%响应” [失败] 对于节点 [rabbit@host2]:nodedown%”)作为“rmq_node2_down”
* “%响应” [失败] 对于节点 [rabbit@host2]:nodedown%”)作为“rmq_node2_down”
* 已修改“%实体：exchange/bindings.destination%&#39;)作为&#39;rmq_entity_modified&#39;
* 已修改“%实体：exchange/bindings.destination%&#39;)作为&#39;rmq_entity_modified&#39;
* 已修改“%实体：queue/exclusive%&#39;)作为&#39;rmq_entity_created_q_exclusive&quot;%已修改实体：queue/auto_delete%”)作为“rmq_entity_q_delete”
* 已修改“%实体：queue/fuliber%”)作为“rmq_entity_modified_q-fuliber”
* 已修改“%实体：version/management%”)作为“rmq_entity_modified_ver_mgt”
* 已修改“%实体：version/management%”)作为“rmq_entity_modified_ver_mgt”

## [!UICONTROL RabbitMQ service start/stop signals]

![RabbitMQ服务启动/停止信号](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

此帧显示 [!DNL RabbitMQ] 在选定时间段内发生的服务启动/停止信号：

* 要求&#39;%RabbitMQ停止……%&#39;)作为“rabbitmq_stop”
* “%正在启动RabbitMQ%”)作为“rabbitmq_start”

## [!UICONTROL RabbitMQ errors]

![RabbitMQ错误](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

此帧显示 [!DNL RabbitMQ] 在选定的时间范围内发生的错误：

* “%exit，原因为{case_clause，timeout}和stacktrace {rabbit_mgmt_wm_healthchecks%&#39;}”为“exit_timeout”
* “%client意外关闭TCP连接%”)作为“client_closed_tcp_conn”
* “%at undefined exit，原因是在上下文shutdown_error%中关闭)为“undf exit”
* “%尝试从不允许的节点%”进行连接)为“disallowed_node”
* “%closing AMQP connection%”)作为“rmq_err_amqp_conn”

## [!UICONTROL RabbitMQ node status]

![RabbitMQ节点状态](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* “%rabbit on node rabbit@host1 down%”)作为“rmq_node1_down”
* “%rabbit on node rabbit@host2 down%”)作为“rmq_node2_down”
* “%rabbit on node rabbit@host3 down%”)作为“rmq_node3_down”
* “%rabbit on node rabbit@host1 up%”)作为“rmq_node1_up”
* “%rabbit on node rabbit@host2 up%”)作为“rmq_node2_up”
* “%rabbit on node rabbit@host3 up%”)作为“rmq_node3_up”

## [!UICONTROL RabbitMQ Message High-Level Summary status by Queue]

![RabbitMQ消息按队列的高级摘要状态](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

的 **[!UICONTROL RabbitMQ Message High-Level Summary status by Queue]** 图表显示 [!DNL RabbitMQ] 队列。

## [!UICONTROL RabbitMQ Message Detail Summary]

![RabbitMQ消息详细信息摘要](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* “%report.ERROR:Cron Job consumers_runner出现错误：NOT_FOUND - no queue%&#39;)作为“queue_err”
* “%report.ERROR:Cron Job consumers_runner出现错误：NOT_FOUND - no queue%&#39;)作为“queue_err”
* “%authenticated and agned access to vhost%”)作为“auth”
* “%closing AMQP connection%”)作为“close_conn”

## [!UICONTROL RabbitMQ Queue Consumption MB]

![RabbitMQ队列使用情况MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

的 **[!UICONTROL RabbitMQ Queue Consumption MB]** 图表显示每个 [!DNL RabbitMQ] 在选定的时间范围内排队。

## [!UICONTROL RabbitMQ Published Messages by Queue]

![RabbitMQ按队列发布的消息](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

的 **[!UICONTROL RabbitMQ Published Messages by Queue]** 图表显示每个 [!DNL RabbitMQ] 在选定的时间范围内排队。

## [!UICONTROL RabbitMQ Published Message Throughput by Queue]

![RabbitMQ按队列发布的消息吞吐量](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

的 **[!UICONTROL RabbitMQ Published Message Throughput by Queue]** 图表显示每秒发布的消息平均数 [!DNL RabbitMQ] 在选定的时间范围内排队。

## [!UICONTROL RabbitMQ Total Message Throughput by Queue]

![按队列划分的RabbitMQ消息总吞吐量](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

的 **[!UICONTROL RabbitMQ Total Message Throughput by Queue]** 图表显示每秒平均消息总数，按 [!DNL RabbitMQ] 在选定的时间范围内排队。

## [!UICONTROL RabbitMQ Consumers by Queue]

![按队列划分的RabbitMQ用户](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

的 **[!UICONTROL RabbitMQ Consumers by Queue]** 图表显示每个用户的平均总数 [!DNL RabbitMQ] 在选定的时间范围内排队。