---
title: 消息队列概述
description: 阅读有关消息队列框架及其如何与Adobe Commerce应用程序配合使用的信息。
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 6f15a24e650a7138bae6d0b40f230e6970a943b0
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# 消息队列概述

Message Queue Framework (MQF)是一个允许模块将消息发布到队列的系统。 它还定义了将异步接收消息的[消费者](consumers.md)。 MQF支持多个报文传送代理：

- **[[!DNL RabbitMQ]](https://www.rabbitmq.com)** — 主要消息代理，它提供用于发送和接收消息的可伸缩平台。 它包括一个用于存储未投放消息的机制，并且基于高级消息队列协议(AMQP) 0.9.1规范。
- **[Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/)** — 使用STOMP（简单文本导向消息协议）进行可靠且可扩展消息传递的替代消息传递代理。 在Adobe Commerce 2.4.6及更高版本中引入。

## RabbitMQ (AMQP)

下图说明了Message Queue框架：

![消息队列框架](../../assets/configuration/mq-framework.png)

- 发布器是将消息发送到交换的组件。 它知道要发布到的交换以及它发送的报文的格式。

- Exchange接收来自发布者的消息并将消息发送到队列。 虽然[!DNL RabbitMQ]支持多种类型的交换，但Commerce仅使用主题交换。 主题中包含路由密钥，路由密钥包含以点分隔的文本字符串。 主题名称的格式为`string1.string2`：例如，`customer.created`或`customer.sent.email`。

  代理允许您在设置转发消息的规则时使用通配符。 您可以使用星号(`*`)替换&#x200B;_one_&#x200B;字符串，或使用井号(`#`)替换0个或多个字符串。 例如，`customer.*`将筛选`customer.create`和`customer.delete`，但不筛选`customer.sent.email`。 但是`customer.#`将筛选`customer.create`、`customer.delete`和`customer.sent.email`。

- 队列是存储消息的缓冲区。

- 消费者接收消息。 它知道要使用哪个队列。 它可以将消息的处理器映射到特定队列。

## Apache ActiveMQ Artemis (STOMP)

作为RabbitMQ的替代方案，Adobe Commerce还支持将[Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/)作为使用简单文本导向消息协议(STOMP)的消息代理。

>[!NOTE]
>
>ActiveMQ Artemis在Adobe Commerce 2.4.6及更高版本中引入。

下图说明了使用ActiveMQ Artemis的STOMP框架：

![STOMP框架](../../assets/configuration/stomp-framework.png)

### STOMP框架组件

- **发布者**&#x200B;是将消息发送到目标（队列或主题）的组件。 它知道要发布到的目标以及它发送的消息的格式。

- STOMP中的&#x200B;**目标**&#x200B;与AMQP中的交换角色类似，接收来自发布者的邮件并将其路由到其中。 STOMP使用直接目标寻址，并使用句点的分层命名模式：例如，`customer.created`或`inventory.updated`。

  Adobe Commerce对STOMP目标使用&#x200B;**ANYCAST**&#x200B;寻址模式，该模式提供点对点消息投放。 在ANYCAST模式中，消息仅从可用使用者池传送到一个使用者，从而实现多个使用者实例的负载平衡和工作分配。

- **队列**&#x200B;是存储消息的缓冲区。 通过ANYCAST寻址，队列可确保消息仅发送给一个使用者，即使有多个使用者连接到同一目的地也是如此。

- **消费者**&#x200B;接收来自目标的消息。 它知道要订阅哪个目的地，并且可以使用不同的确认模式（自动、客户端或单个客户端）处理消息。

## MySQL适配器（回退）

基本消息队列系统也可以在不使用外部消息代理的情况下进行设置。 在此系统中，MySQL适配器将消息存储在数据库中。 三个数据库表（`queue`、`queue_message`和`queue_message_status`）管理消息队列工作负载。 CRON工作能确保消费者能够接收信息。 此解决方案不是非常可扩展。 应尽可能将外部消息代理（如[!DNL RabbitMQ]或Apache ActiveMQ Artemis）用于生产环境。

## 相关信息

有关安装和配置说明：

- [安装和配置RabbitMQ](../../installation/prerequisites/rabbitmq.md)
- [安装和配置ActiveMQ Artemis](../../installation/prerequisites/activemq.md)
- [管理消息队列](manage-message-queues.md)
- [消息队列使用者](consumers.md)
