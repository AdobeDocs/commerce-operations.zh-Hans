---
title: 此 [!UICONTROL [!DNL RabbitMQ]]选项卡
description: 了解 [!UICONTROL [!DNL RabbitMQ]]选项卡，属于 [!DNL Observation for Adobe Commerce].
exl-id: c5370c30-fed8-4f45-89c3-ef0d6ad41a89
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# 此 [!UICONTROL [!DNL RabbitMQ]] 选项卡

此 **[!UICONTROL [!DNL RabbitMQ]]** 选项卡包含的信息重点在于 [!DNL RabbitMQ] 信号。

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] 基础架构事件](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

此 **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** 此框架显示了涉及以下内容的基础结构事件： [!DNL RabbitMQ] 在选定时间范围内发生的更改：

* `%Response [error] for node [rabbit@host1]: unexpected http response from%`)作为 `unexpected_resp_node1`
* `%Response [error] for node [rabbit@host2]: unexpected http response from%`)作为 `unexpected_resp_node2`
* `%Response [error] for node [rabbit@host3]: unexpected http response from%`)作为 `unexpected_resp_node3`
* `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`)作为 `node3_timeout_exceeded`
* `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`)作为 `node1_timeout_exceeded`
* `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`)作为 `node2_timeout_exceeded`
* `%401 Unauthorized%`)作为 `401_unauth`
* `%401 Unauthorized%`)作为 `401_unauth`
* `%Service restarted: rabbitmq-server%`)作为 `rmq_service_restart`
* `%Response [failed] for node [rabbit@host1]: nodedown%`)作为 `rmq_node1_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`)作为 `rmq_node2_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`)作为 `rmq_node2_down`
* `%Entity modified: exchange/bindings.destination%`)作为 `rmq_entity_modified`
* `%Entity modified: exchange/bindings.destination%`)作为 `rmq_entity_modified`
* `%Entity modified: queue/exclusive%`)作为 `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`)作为 `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`)作为 `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`)作为 `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`)作为 `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] 服务启动/停止信号](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

此框架显示 [!DNL RabbitMQ] 在选定的时间范围内发生的服务启动/停止信号：

* `%RabbitMQ is asked to stop...%`)作为 `rabbitmq_stop`
* `%Starting RabbitMQ%`)作为 `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] 错误](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

此框架显示 [!DNL RabbitMQ] 在选定的时间范围内发生的错误：

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}` 作为 `exit_timeout`
* `%client unexpectedly closed TCP connection%`)作为 `client_closed_tcp_conn`
* `%at undefined exit with reason shutdown in context shutdown_error%`)作为 `undef_exit`
* `%Connection attempt from disallowed node%`)作为 `disallowed_node`
* `%closing AMQP connection%`)作为 `rmq_err_amqp_conn`

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] 节点状态](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `%rabbit on node rabbit@host1 down%`)作为 `rmq_node1_down`
* `%rabbit on node rabbit@host2 down%`)作为 `rmq_node2_down`
* `%rabbit on node rabbit@host3 down%`)作为 `rmq_node3_down`
* `%rabbit on node rabbit@host1 up%`)作为 `rmq_node1_up`
* `%rabbit on node rabbit@host2 up%`)作为 `rmq_node2_up`
* `%rabbit on node rabbit@host3 up%`)作为 `rmq_node3_up`

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] 按队列显示的消息高级摘要状态](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

此 **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** 图表显示按以下方式发布的消息数： [!DNL RabbitMQ] 已选择时间范围的队列。

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] 消息详细信息摘要](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`)作为 `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`)作为 `queue_err`
* `%authenticated and granted access to vhost%`)作为 `auth`
* `%closing AMQP connection%`)作为 `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] 队列消耗MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

此 **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** 图形显示每个字节使用的字节数 [!DNL RabbitMQ] 在选定的时间范围内排队。

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] 按队列显示的已发布消息](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

此 **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** 图形显示每个字节使用的字节数 [!DNL RabbitMQ] 在选定的时间范围内排队。

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] 已发布的消息吞吐量（按队列）](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

此 **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** 图表显示每个报表每秒发布的消息的平均数 [!DNL RabbitMQ] 在选定的时间范围内排队。

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] 按队列的总消息吞吐量](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

此 **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** 图表显示每个报表的每秒平均消息总数 [!DNL RabbitMQ] 在选定的时间范围内排队。

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] 按队列列出的使用者](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

此 **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** 图表显示每个用户的平均总用户数 [!DNL RabbitMQ] 在选定的时间范围内排队。
