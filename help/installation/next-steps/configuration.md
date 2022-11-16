---
title: 配置应用程序
description: 了解Adobe Commerce和Magento Open Source内部部署所需的安装后配置。
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 0%

---


# 配置应用程序

现在，您已完成Adobe Commerce或Magento Open Source的安装，接下来需要对其进行配置。 本主题提供了一些推荐的配置设置。

## 设置Cron

UNIX任务调度程序cron对应用程序的日常操作至关重要。 它会计划一些事项，例如重新索引、新闻稿、电子邮件和Sitemap。 A *crontab* 是cron配置。

您必须在 *crontab*，或某些核心功能（以及某些第三方扩展）无法正常运行。

有关cron的更多信息（包括如何从命令行中删除crontab和运行cron），请参阅 [配置并运行cron](../../configuration/cli/configure-cron-jobs.md).

## 安全设置和建议

安装后，我们建议执行以下操作：

* 确保正确设置文件所有权和权限
* 我们强烈建议 [更改默认管理员URI](../tutorials/admin-uri.md) 从 `admin` 别的
* 确保 [`X-Frame-Option` HTTP头](../../configuration/security/xframe-options.md) 设置正确。
* 通过 [保护模板](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

如果安装者 [克隆GitHub存储库](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)，请确保在部署应用程序时，您仅包含生产环境所需的文件和文件夹。 不需要的文件和文件夹可能会暴露安全风险。

## 启用Apache服务器重写

如果您使用Apache Web服务器，则必须启用服务器重写才能正确显示页面。 否则，您会看到页面没有样式和其他问题。

[Apache服务器重写的部分](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## 多网络节点环境中的缓存

如果您有多个Web节点，则 *无法* 使用应用程序的默认文件缓存，因为web节点之间没有同步。 换句话说，一个Web节点上的活动仅被写入该Web节点的文件系统。 如果在其他Web节点上执行后续活动，则可能会写入不必要的文件，或导致错误。

请改为使用 [雷迪斯](../../configuration/cache/config-redis.md) （默认） [缓存](https://glossary.magento.com/cache) 和页面缓存。

## 服务器设置

本节简要讨论了我们建议您考虑的应用程序运行服务器的设置。 其中某些设置与应用程序无直接关系；这些仅作为建议提供。

### 日志旋转

UNIX `logrotate` 利用实用程序，可管理生成大量日志文件的系统。 它允许自动旋转、压缩、删除和邮寄日志文件。 每个日志文件可以每天、每周、每月或当日志文件超过指定大小时进行处理。

有关更多信息，请参阅以下内容之一：

* [操作方法：终极日志旋转命令教程，包含10个示例](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [堆栈交换](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` 手册页](https://linuxconfig.org/logrotate-8-manual-page)

### 设置可使各种服务进行通信的iptables规则

无论您有一台服务器还是多台服务器，都必须在防火墙中打开端口以使服务能够通信。 例如，如果将Solr搜索引擎与Adobe Commerce一起使用，则必须启用它以与Web服务器通信。 如果您有多个Web节点，则必须使它们能够相互通信。

更多信息：

* 乌本图： [Ubuntu文档页面](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [CentOS操作方法](https://wiki.centos.org/HowTos/Network/IPTables).

### 安全增强型Linux(SELinux)规则

对于您是否使用SELinux，我们没有推荐；但是，如果确实使用它，则必须将服务配置为彼此通信，类似于配置iptables。

更多信息：

* 乌本图： [Debian手册](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [CentOS维基](https://wiki.centos.org/HowTos/SELinux)

### 设置电子邮件服务器

Adobe Commerce和Magento Open Source需要电子邮件服务器。 我们不建议使用特定的服务器，但您可以尝试以下任一操作：

* 适用于CentOS的后缀([数字海洋教程](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [CentOS文档](https://www.centos.org))
* 适用于Ubuntu的修补程序([数字海洋教程](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Ubuntu文档](https://help.ubuntu.com/community/MailServer))

### 优化搜索引擎以提高性能：

自2.4.0起，所有安装都需要Elasticsearch或OpenSearch。

* [安装和配置搜索引擎](../../configuration/search/overview-search.md)

### 设置消息队列

自版本2.3.0起，Adobe Commerce和Magento Open Source包含消息队列功能。 在早期版本中，此插件仅可用于Adobe Commerce。

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## 仅Adobe Commerce的设置

仅当使用Adobe Commerce时，您才可以配置以下内容：

* [拆分用于结帐、订单管理和其他数据库表的数据库](../../configuration/storage/multi-master.md)
