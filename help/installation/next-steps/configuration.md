---
title: 配置应用程序
description: 了解Adobe Commerce内部部署所需的安装后配置。
feature: Install, Configuration
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: a28dad04dac23075234a6ac3c2b362d125c9d981
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# 配置应用程序

现在您已安装Adobe Commerce，您需要对其进行配置。 本主题提供了一些推荐的配置设置。

## 设置cron

UNIX任务计划程序cron对应用程序的日常操作至关重要。 它计划重新索引、新闻稿、电子邮件和站点地图等内容。 *crontab*&#x200B;是cron配置。

您必须在&#x200B;*crontab*&#x200B;中安装Adobe Commerce服务，否则某些核心功能（以及某些第三方扩展）将无法正常运行。

有关cron的详细信息，包括如何删除crontab并从命令行运行cron，请参阅[配置和运行cron](../../configuration/cli/configure-cron-jobs.md)。

## 安全设置和推荐

安装后，我们建议执行以下操作：

* 确保正确设置文件所有权和权限
* 我们强烈建议[将默认管理员URI](../tutorials/admin-uri.md)从`admin`更改为其他内容
* 确保正确设置[`X-Frame-Option` HTTP标头](../../configuration/security/xframe-options.md)。
* 通过[保护您的模板](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)，采取防范措施以防止跨站点脚本(XSS)

如果通过[克隆GitHub存储库](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)进行安装，请确保在部署应用程序时仅包含生产环境所需的文件和文件夹。 不需要的文件和文件夹可能会暴露安全风险。

## 启用Apache服务器重写

如果使用Apache Web Server，则必须启用服务器重写以便正确显示页面。 否则，您会看到没有样式和其他问题的页面。

[关于Apache Server重写的部分](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## 多Webnode环境中的缓存

如果您有多个Web节点，则&#x200B;*不能*&#x200B;使用应用程序的默认文件缓存，因为Web节点之间没有同步。 换句话说，一个Web节点上的活动仅写入该Web节点的文件系统。 如果在另一个Web节点上执行后续活动，则可能会导致写入不必要的文件，也可能会导致出现错误。

请改用[Redis](../../configuration/cache/config-redis.md)作为默认缓存和页面缓存。

## 服务器设置

本节简要讨论了我们建议您考虑为运行应用程序的服务器进行的设置。 其中一些设置与应用程序没有直接关系；这些设置仅作为建议提供。

### 日志轮换

UNIX `logrotate`实用程序使您能够管理生成大量日志文件的系统。 它允许自动旋转、压缩、删除和邮寄日志文件。 每个日志文件都可以每日、每周、每月或当日志文件超过指定大小时进行处理。

有关更多信息，请参阅以下内容之一：

* [HowTo：包含十个示例的终极日志旋转命令教程](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [栈叠Exchange](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate`手册页](https://linuxconfig.org/logrotate-8-manual-page)

>[!AVAILABILITY]
>
>以下可用性信息适用于云基础架构项目上的Adobe Commerce：
>
>* 入门级环境没有日志轮换。
>
>* 无法在Pro集成环境中配置日志轮换。 您必须实施自定义解决方案/脚本，并[配置cron](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property)以根据需要运行脚本。

### 设置iptables规则以启用各种服务进行通信

无论您拥有一台服务器还是多台服务器，都必须在防火墙中打开端口以启用服务通信。 例如，如果将Solr搜索引擎与Adobe Commerce一起使用，则必须启用该搜索引擎以与Web服务器通信。 如果您有多个Web节点，则必须使它们能够相互通信。

更多信息：

* Ubuntu： [Ubuntu文档页面](https://help.ubuntu.com/community/IptablesHowTo)。
* CentOS： [CentOS操作方法](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)。

### Security Enhanced Linux (SELinux)规则

我们没有关于是否使用SELinux的建议；但是，如果确实使用它，则必须配置服务，使其像配置iptables一样相互通信。

更多信息：

* Ubuntu： [Debian手册](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS： [CentOS wiki](https://wiki.centos.org/HowTos/SELinux)

### 设置电子邮件服务器

Adobe Commerce需要电子邮件服务器。 我们不建议使用特定的服务器，但您可以尝试以下任一操作：

* CentOS的后缀（[Digital Ocean教程](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6)，[CentOS文档](https://www.centos.org)）
* Ubuntu的后缀（[数字海洋教程](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04)，[Ubuntu文档](https://help.ubuntu.com/community/MailServer)）

### 优化搜索引擎以提高性能：

从2.4.0开始的所有安装均需要Elasticsearch或OpenSearch。

* [安装和配置搜索引擎](../../configuration/search/overview-search.md)

### 设置消息队列

自版本2.3.0起，Adobe Commerce就包含消息队列功能。 在早期版本中，它仅适用于Adobe Commerce。

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## 仅适用于Adobe Commerce的设置

只有在使用Adobe Commerce时，才能配置以下内容：

* [拆分用于签出、订单管理和其他数据库表的数据库](../../configuration/storage/multi-master.md)
