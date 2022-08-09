---
title: 消息队列概述
description: 阅读有关消息队列框架及其如何与Adobe Commerce和Magento Open Source应用程序配合使用的信息。
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 消息队列概述

消息队列框架(MQF)是允许 [模块](https://glossary.magento.com/module) 将消息发布到队列。 它还定义将异步接收消息的用户。 MQF使用 [RabbitMQ](https://www.rabbitmq.com) 作为报文传送代理，它为发送和接收报文提供了一个可扩展的平台。 它还包括用于存储未传送消息的机构。 RabbitMQ基于高级消息队列协议(AMQP)0.9.1规范。

下图说明了消息队列框架：

![消息队列框架](../../assets/configuration/mq-framework.png)

- A [发布者](https://glossary.magento.com/publisher-subscriber-pattern) 是向exchange发送消息的组件。 它知道要发布到的交换机及其发送的消息格式。

- Exchange接收来自发布者的消息，并将其发送到队列。 虽然RabbitMQ支持多种类型的交换，但商务仅使用主题交换。 主题包括路由键，其中包含以点分隔的文本字符串。 主题名称的格式为 `string1.string2`:例如， `customer.created` 或 `customer.sent.email`.

   代理允许您在设置用于转发消息的规则时使用通配符。 您可以使用星号(`*`)替换 _one_ 字符串或井号(`#`)来替换0个或多个字符串。 例如， `customer.*` 过滤 `customer.create` 和 `customer.delete`，但不是 `customer.sent.email`. 但是 `customer.#` 过滤 `customer.create`,  `customer.delete`和 `customer.sent.email`.

- 队列是用于存储消息的缓冲区。

- 消费者接收消息。 它知道要消耗哪个队列。 它可以将消息的处理器映射到特定队列。

也可以不使用RabbitMQ来设置基本消息队列系统。 在此系统中， MySQL [适配器](https://glossary.magento.com/adapter) 将消息存储在数据库中。 三个数据库表(`queue`, `queue_message`和 `queue_message_status`)管理消息队列工作量。 Cron作业可确保用户能够接收消息。 此解决方案的扩展性不强。 应尽可能使用RabbitMQ。
