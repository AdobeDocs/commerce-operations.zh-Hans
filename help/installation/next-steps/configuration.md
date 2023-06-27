---
title: 配置应用程序
description: 了解Adobe Commerce和Magento Open Source内部部署所需的安装后配置。
feature: Install, Configuration
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# 配置应用程序

现在您已安装Adobe Commerce或Magento Open Source，您需要对其进行配置。 本主题提供了一些推荐的配置设置。

## 设置cron

UNIX任务调度程序cron对应用程序的日常操作至关重要。 它安排重新索引、新闻稿、电子邮件和站点地图等内容。 A *crontab* 是cron配置。

您必须在中安装Adobe Commerce和Magento Open Source服务 *crontab*&#x200B;或某些核心功能（以及一些第三方扩展）无法正常运行。

有关cron的更多信息，包括如何删除crontab并从命令行运行cron，请参见 [配置和运行cron](../../configuration/cli/configure-cron-jobs.md).

## 安全设置和建议

安装后，我们建议执行以下操作：

* 确保正确设置了您的文件所有权和权限
* 我们强烈建议 [更改默认管理员URI](../tutorials/admin-uri.md) 起始日期 `admin` 到其他东西
* 确保 [`X-Frame-Option` HTTP标头](../../configuration/security/xframe-options.md) 设置正确。
* 针对跨站点脚本(XSS)采取预防措施，方法是 [保护模板](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

如果安装者 [克隆GitHub存储库](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)，确保在部署应用程序时，仅包含生产环境所需的文件和文件夹。 不需要的文件和文件夹可能会带来安全风险。

## 启用Apache Server重写

如果使用Apache Web Server，则必须启用服务器重写以便正确显示页面。 否则，您将看到没有样式和其他问题的页面。

[有关Apache Server重写的部分](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## 多webnode环境中的缓存

如果您有多个Web节点， *无法* 使用应用程序的默认文件缓存，因为Web节点之间没有同步。 换句话说，一个Web节点上的活动仅写入该Web节点的文件系统。 如果在另一个Web节点上执行后续活动，可能会导致写入不必要的文件，也可能会导致错误。

请改用 [Redis](../../configuration/cache/config-redis.md) 缺省高速缓存和页面高速缓存的缺省值。

## 服务器设置

本节简要讨论了我们建议您考虑为运行应用程序的服务器进行的设置。 其中一些设置与应用程序没有直接关系；这些设置仅作为建议提供。

### 日志轮换

UNIX `logrotate` 实用程序使您能够管理生成大量日志文件的系统。 它允许自动旋转、压缩、删除和邮寄日志文件。 每个日志文件都可以每日、每周、每月或当日志文件超过指定大小时进行处理。

有关更多信息，请参阅以下内容之一：

* [HowTo： Ultimate log rotate命令教程包含十个示例](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [栈栈交换](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` 手册页](https://linuxconfig.org/logrotate-8-manual-page)

### 设置iptables规则以启用各种服务进行通信

无论您拥有一台服务器还是多台服务器，都必须打开防火墙中的端口，以使服务能够通信。 例如，如果将Solr搜索引擎与Adobe Commerce一起使用，则必须启用该搜索引擎以与Web服务器通信。 如果您有多个Web节点，则必须启用它们来相互通信。

更多信息：

* Ubuntu： [Ubuntu文档页面](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS： [CentOS操作说明](https://wiki.centos.org/HowTos/Network/IPTables).

### Security Enhanced Linux (SELinux)规则

我们没有关于是否使用SELinux的建议；但是，如果确实使用它，则必须配置服务，以便与配置iptables类似，彼此通信。

更多信息：

* Ubuntu： [Debian手册](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS： [CentOS维客](https://wiki.centos.org/HowTos/SELinux)

### 设置电子邮件服务器

Adobe Commerce和Magento Open Source需要电子邮件服务器。 我们不建议使用特定的服务器，但您可以尝试以下任一操作：

* CentOS的后缀([数字海洋教程](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6)， [CentOS文档](https://www.centos.org))
* Ubuntu的后缀([数字海洋教程](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04)， [Ubuntu文档](https://help.ubuntu.com/community/MailServer))

### 优化搜索引擎以提高性能：

从2.4.0开始的所有安装都需要Elasticsearch或OpenSearch。

* [安装和配置搜索引擎](../../configuration/search/overview-search.md)

### 设置消息队列

从版本2.3.0开始，Adobe Commerce和Magento Open Source包含消息队列功能。 在早期版本中，它仅适用于Adobe Commerce。

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## 仅适用于Adobe Commerce的设置

只有在使用Adobe Commerce时，才能配置以下内容：

* [拆分数据库，用于结帐、订单管理和其他数据库表](../../configuration/storage/multi-master.md)
