---
title: 消息队列概述
description: 阅读有关消息队列框架及其如何与Adobe Commerce应用程序配合使用的信息。
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# 消息队列概述

Message Queue Framework (MQF)是一个允许模块将消息发布到队列的系统。 它还定义了 [消费者](consumers.md) 异步接收消息的服务器。 MQF使用 [[!DNL RabbitMQ]](https://www.rabbitmq.com) 作为报文传送代理，它提供用于发送和接收报文的可伸缩平台。 它还包括用于存储未传递消息的机制。 [!DNL RabbitMQ] 基于高级消息队列协议(AMQP) 0.9.1规范。

下图说明了Message Queue框架：

![消息队列框架](../../assets/configuration/mq-framework.png)

- 发布器是将消息发送到交换的组件。 它知道要发布到的交换以及它发送的报文的格式。

- Exchange接收来自发布者的消息并将消息发送到队列。 尽管 [!DNL RabbitMQ] 支持多种类型的交换，Commerce仅使用主题交换。 主题中包含路由密钥，路由密钥包含以点分隔的文本字符串。 主题名称的格式为 `string1.string2`：例如， `customer.created` 或 `customer.sent.email`.

  代理允许您在设置转发消息的规则时使用通配符。 您可以使用星号(`*`)以替换 _一_ 字符串或井号(`#`)以替换0个或更多字符串。 例如， `customer.*` 将过滤于 `customer.create` 和 `customer.delete`，但不匹配 `customer.sent.email`. 但是 `customer.#` 将过滤于 `customer.create`，  `customer.delete`、和 `customer.sent.email`.

- 队列是存储消息的缓冲区。

- 消费者接收消息。 它知道要使用哪个队列。 它可以将消息的处理器映射到特定队列。

也可以不使用设置基本消息队列系统 [!DNL RabbitMQ]. 在此系统中，MySQL适配器将消息存储在数据库中。 三个数据库表(`queue`， `queue_message`、和 `queue_message_status`)管理消息队列工作负载。 CRON工作能确保消费者能够接收信息。 此解决方案不是非常可扩展。 [!DNL RabbitMQ] 应尽可能使用。
