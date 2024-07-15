---
title: 自定义日志记录
description: 了解如何使用自定义日志记录调查错误。
feature: Configuration, Logs
exl-id: 6c94ebcf-70df-4818-a17b-32512eba516d
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# 自定义日志记录概述

日志可提供系统进程的可见性；例如，调试信息可帮助您了解何时发生错误或导致错误的原因。

本主题侧重于基于文件的日志记录，尽管Commerce还提供了在数据库中存储日志的灵活性。

Adobe建议使用集中式应用程序日志记录，原因如下：

- 它允许在除应用程序服务器之外的服务器上存储日志，并减少磁盘I/O操作，从而简化对应用程序服务器的支持。

- 它通过使用特殊工具（如[Logstash]、[Logplex]或[fluentd]）使日志数据的处理更加有效，而不会影响生产服务器。

  >[!INFO]
  >
  >Adobe不建议或认可任何特定的日志记录解决方案。

## PSR-3合规性

[PSR-3标准][laminas]为日志记录库定义了公用PHP接口。 PSR-3的主要目标是允许库以简单且通用的方式接收`Psr\Log\LoggerInterface`对象并向其写入日志。

这让您能够轻松替换实施，而无需担心此类替换可能会破坏应用程序代码。 它还确保即使将来系统的版本中更改了日志实施，自定义组件也能正常工作。

## 独白

Commerce 2符合PSR-3标准。 默认情况下，Commerce使用[独白]。 在Commerce应用程序[`di.xml`][di]中作为`Psr\Log\LoggerInterface`的首选项实现的单一日志。

Monolog是一种常用的PHP日志记录解决方案，具有多种使您能够构建高级日志记录策略的处理程序。 以下是Monolog的工作原理摘要。

Monolog _logger_&#x200B;是拥有自己的&#x200B;_处理程序_&#x200B;集的通道。 Monolog有许多处理程序，包括：

- 记录到文件和syslog
- 发送警报和电子邮件
- 记录特定的服务器和网络日志记录
- 登录开发(与FireBug和Chrome Logger等集成)
- 登录到数据库

每个处理程序可以处理输入消息并停止传播，也可以将控件传递到链中的下一个处理程序。

可以通过多种不同的方式处理日志消息。 例如，可以将所有调试信息存储在磁盘上的文件中，将日志级别较高的消息放入数据库中，最后通过电子邮件发送日志级别为“严重”的消息。

其他渠道可以具有一组不同的处理程序和逻辑。

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[已流化]: https://www.fluentd.org/
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[独白]: https://github.com/Seldaek/monolog
