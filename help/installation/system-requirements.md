---
title: 系统要求
description: 了解Adobe Commerce的软件依赖项和系统要求。 发现经过测试的配置，以确保与部署环境兼容。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 107fac05f8e7bcbd66e07187f46a3ffa170a2001
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 0%

---

# 系统要求

下面总结了为Adobe Commerce测试的软件依赖项和服务。

在Commerce on Cloud的依赖项方面有一些差异。 Adobe Commerce on Cloud的服务版本和兼容性支持由测试并部署到托管云环境的服务决定，有时不同于Adobe Commerce内部部署支持的版本。 例如，内部部署支持Elasticsearch 7.17的Commerce 2.4.4，而Cloud上的Adobe Commerce 2.4.4支持OpenSearch 1。

>[!NOTE]
>
>系统要求表确定了涵盖的特定Adobe Commerce版本，包括任何明确标记的测试版或早期访问版。 请参阅[发行说明](../release/release-notes/overview.md)，详细了解Adobe Commerce的最新发布版本。
>
>与您的Commerce版本相关的服务版本不匹配可能会引入无法在支持的环境中重现的行为。 在这些情况下，支持部门可能会要求您将环境与支持的配置保持一致（例如，升级或降级服务版本），然后才能调查、排除故障或验证报告的行为。 在版本对齐后，支持人员可以继续调查。

下表显示了Adobe已在特定Adobe Commerce版本中测试的第三方软件依赖项版本。

Adobe仅支持下表所述的系统要求组合。 例如，2.4.5已通过MariaDB 10.4进行了全面测试。 Adobe建议您在升级到2.4.5之前升级到MariaDB 10.4。

为了确保顺利升级过程并防止部署失败，Adobe建议以增量方式升级RabbitMQ版本。 例如，从版本3.8升级到4.1时，您应该首先从3.8升级到3.9，然后从3.9升级到3.10，以此类推。 只有在到达版本3.13之后，您才应该继续升级到版本4.1。

>[!BEGINTABS]

>云端上的[!TAB Commerce]

[Commerce on Cloud模板](https://github.com/magento/magento-cloud)为与特定Commerce版本兼容的服务提供了默认配置。

{{$include /help/_includes/templated/cloud-requirements-table.md}}

在[文件`services.yaml`中定义了服务和版本](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)。 以下是云基础架构上Commerce 2.4.6的默认服务配置：

```yaml
mysql:
    type: mysql:10.6
    disk: 5120

redis:
    type: redis:7.0

opensearch:
    type: opensearch:2
    disk: 1024
```

请参阅&#x200B;*云基础架构上的Commerce*&#x200B;指南中的[配置服务](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)。

>[!TAB Commerce内部部署]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP设置

有特定的PHP配置设置，如`memory_limit`设置，可帮助您在使用Adobe Commerce时避免常见问题。 请参阅[必需的PHP设置](prerequisites/php-settings.md)。

有关云配置指南，请参阅&#x200B;*云基础架构上的Commerce*&#x200B;指南中的[PHP设置](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings)。

### PHP OPcache

Adobe建议您验证是否出于性能原因启用了[PHP OPcache](https://www.php.net/manual/en/book.opcache.php)。 OPcache在许多PHP分发中启用。
- **对于云基础架构部署上的Adobe Commerce**，默认情况下会安装`opcache`扩展。
- 对于Adobe Commerce内部部署：****
   - [验证是否已安装PHP OPcache扩展](prerequisites/php-settings.md#verify-php-is-installed)。
   - 有关性能设置的特定指导，请参阅&#x200B;*性能最佳实践*&#x200B;指南中的[PHP设置](../performance/software.md#php-settings)的软件建议。


如果必须单独安装OPcache，请参阅[PHP OPcache文档](https://www.php.net/manual/en/opcache.setup.php)。

### PHP进程控制

{{php-process-control}}

### PHPUnit

PHPUnit v9（作为命令行工具）。

### PHP扩展

[PHP安装说明](prerequisites/php-settings.md)包含安装这些扩展的步骤。

>[!TIP]
>
>有关云基础架构中的PHP扩展，请参阅&#x200B;_云基础架构上的Commerce_&#x200B;指南中的[启用PHP扩展](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions)。

>[!BEGINTABS]

>云端上的[!TAB Commerce]

下表显示了在Cloud平台上部署Adobe Commerce时支持的PHP扩展。

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce内部部署]

{{$include /help/_includes/templated/php-extensions.md}}

有关安装详细信息，请参阅[PHP官方文档](https://www.php.net/manual/en/extensions.php)。

>[!ENDTABS]

## 其他

本节介绍所有其他类型的必需软件和可选软件的支持和兼容性。

>[!NOTE]
>
>以下要求适用于Adobe Commerce的最新2.4.x修补程序版本。 在相关时，提供了有关云基础架构的Commerce指南。

### 浏览器

店面和管理员：

- Microsoft Edge（最新和以前的主要版本）
- Firefox（最新和以前的主要版本；任何操作系统）
- Chrome（最新和以前的主要版本；任何操作系统）
- Safari（最新和以前的主要版本；仅限macOS）
- 适用于iOS的Safari（适用于店面的最新和以前的主要版本）
- 适用于Android的Chrome（最新和以前的主要版本，适用于店面）

### 邮件服务器

邮件传输代理(MTA)或SMTP服务器。 云基础架构上的Commerce使用[SendGrid电子邮件服务](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/sendgrid)。

### 内存

升级从Commerce Marketplace和其他来源获得的应用程序和扩展最多可能需要2 GB的RAM。 如果您使用的系统RAM小于2 GB，请创建[交换文件](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)。 否则，升级可能会失败。

### 操作系统(Linux x86-64)

Linux发行版，如RedHat Enterprise Linux (RHEL)、CentOS、Ubuntu、Debian等。

Microsoft Windows和macOS **不支持**。

Adobe Commerce需要以下系统工具才能进行某些操作：

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gnu.org/software/gzip/manual/gzip.html)
- [[!DNL lsof]](https://lsof.readthedocs.io/en/stable/manpage/)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.4/en/mysqldump.html)
- [[!DNL nice]](https://www.gnu.org/s/coreutils/manual/html_node/nice-invocation.html)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://www.gnu.org/software/tar/manual/tar.html)

### SSL

- HTTPS需要有效的安全证书。
- 不支持自签名SSL证书。
- 传输层安全性(TLS)要求 — PayPal和`repo.magento.com`都需要TLS 1.2或更高版本。

有关云基础架构上的Commerce，请参阅&#x200B;*云基础架构上的Commerce*&#x200B;指南中的[Fastly配置](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)。

### Xdebug

对于Adobe Commerce，请使用[php_xdebug 2.5.x](https://xdebug.org/download)或更高版本（仅适用于开发环境；可能会对性能产生不利影响）。

有关云上的Adobe Commerce，请参阅&#x200B;*云基础架构上的Commerce*&#x200B;指南中的[配置Xdebug](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/debug)。

>[!NOTE]
>
>`xdebug`存在已知问题，该问题可能会影响Adobe Commerce安装或安装后对店面或管理员的访问。 在&#x200B;_Commerce支持知识库_&#x200B;中查看影响`xdebug`安装](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation)的[已知问题。


<!-- Last updated from includes: 2026-03-13 12:40:18 -->
