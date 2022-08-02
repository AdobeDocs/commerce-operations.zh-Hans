---
title: 自定义日志记录
description: 了解如何使用自定义日志记录来调查错误。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# 自定义日志记录概述

日志可提供系统进程的可见性；例如，调试信息可帮助您了解何时发生错误或导致错误的原因。

本主题重点介绍基于文件的日志记录，不过商务也提供了在数据库中存储日志的灵活性。

Adobe建议使用集中式应用程序日志记录，原因如下：

- 它允许将日志存储在应用程序服务器以外的服务器上，并减少磁盘I/O操作，从而简化了对应用程序服务器的支持。

- 它通过使用特殊工具(例如 [Logstash], [Logplex]或 [流量] — 不影响生产服务器。

   >[!INFO]
   >
   >Adobe不建议或认可任何特定的日志记录解决方案。

## PSR-3合规性

的 [PSR-3标准][laminas] 为日志库定义通用的PHP界面。 PSR-3的主要目标是允许库接收 `Psr\Log\LoggerInterface` 对象，并以简单且通用的方式将日志写入该对象。

这样，实施就可以轻松替换，而不必担心这种替换可能会破坏应用程序代码。 它还保证，即使在将来版本的系统中更改日志实施，自定义组件也能正常工作。

## 独白

商务2遵循PSR-3标准。 默认情况下，商务使用 [独白]. 作为优先项实施的独白 `Psr\Log\LoggerInterface` 在商务应用程序中 [`di.xml`][di].

Monolog是一种流行的PHP日志记录解决方案，具有多种处理程序，使您能够构建高级日志记录策略。 以下是Monolog的工作原理的摘要。

独白 _logger_ 是一个有其自己 _处理程序_. Monolog有许多处理程序，包括：

- 日志到文件和syslog
- 发送警报和电子邮件
- 特定于日志的服务器和网络日志记录
- 登录开发（与FireBug和Chrome Logger等集成）
- 登录数据库

每个处理程序可以处理输入消息和停止传播或将控制传递给链中的下一个处理程序。

日志消息可以采用多种不同的方式进行处理。 例如，您可以将所有调试信息存储到磁盘上的文件中，将日志级别较高的消息放入数据库中，最后通过电子邮件发送日志级别为“关键”的消息。

其他渠道可以具有不同的处理程序和逻辑集。

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[流量]: http://www.fluentd.org
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[独白]: https://github.com/Seldaek/monolog
