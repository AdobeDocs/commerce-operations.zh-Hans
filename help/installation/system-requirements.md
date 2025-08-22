---
title: 系统要求
description: 使用本参考可识别已在Adobe Commerce版本中测试的必需软件依赖项。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 0%

---

# 系统要求

下面总结了为Adobe Commerce测试的软件依赖项和服务。

在Commerce on Cloud的依赖项方面有一些差异。 Adobe Commerce on Cloud的服务版本和兼容性支持由测试并部署到托管云环境的服务决定，有时不同于Adobe Commerce内部部署支持的版本。 例如，内部部署支持Elasticsearch 7.17的Commerce 2.4.4，而Cloud上的Adobe Commerce 2.4.4支持OpenSearch 1。

>[!NOTE]
>
>系统要求仅适用于Adobe Commerce的发行版本。 不包括Beta或早期访问版本。 请参阅[发行说明](../release/release-notes/overview.md)以了解有关Adobe Commerce最新发行版本的更多信息。

下表显示了Adobe已在特定Adobe Commerce版本中测试的第三方软件依赖项版本。

Adobe仅支持下表所述的系统要求组合。 例如，2.4.5已通过MariaDB 10.4进行了全面测试。Adobe建议您在升级到2.4.5之前升级到MariaDB 10.4。

为了确保顺利升级过程并防止部署失败，Adobe建议以增量方式升级RabbitMQ版本。 例如，从版本3.8升级到4.1时，您应该首先从3.8升级到3.9，然后从3.9升级到3.10，以此类推。 只有在到达版本3.13之后，您才应该继续升级到版本4.1。

>[!BEGINTABS]
>[!TAB 云端上的 Commerce]

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

请参阅[云基础架构上的Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html)指南中的&#x200B;_配置服务_。

>[!TAB Commerce内部部署]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP设置

有特定的PHP配置设置，如`memory_limit`设置，可帮助您在使用Adobe Commerce时避免常见问题。 请参阅[必需的PHP设置](prerequisites/php-settings.md)。

有关云配置指南，请参阅[云基础架构上的Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html)指南中的&#x200B;_PHP设置_。

### PHP OPcache

建议您验证是否出于性能原因启用了[PHP OPcache](https://www.php.net/manual/en/intro.opcache.php)。 OPcache在许多PHP分发中启用。 默认情况下，`opcache`扩展安装在云基础架构上的Commerce中。

对于内部部署，验证是否已安装PHP OPcache，请参阅[PHP设置](prerequisites/php-settings.md)。 有关性能设置的特定指导，请参阅[性能最佳实践](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings)指南中的&#x200B;_PHP设置_&#x200B;的软件建议。

如果必须单独安装OPcache，请参阅[PHP OPcache文档](https://www.php.net/manual/en/opcache.setup.php)。

### PHP进程控制

{{php-process-control}}

### PHPUnit

PHPUnit v9（作为命令行工具）。

### PHP扩展

[PHP安装说明](prerequisites/php-settings.md)包含安装这些扩展的步骤。

>[!TIP]
>
>有关云基础架构中的PHP扩展，请参阅[云基础架构上的Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions)指南中的&#x200B;_启用PHP扩展_。

>[!BEGINTABS]
>[!TAB 云端上的 Commerce]

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
- Safari(最新和以前的主要版本；仅限macOS)
- 适用于iOS的Safari（适用于店面的最新和以前的主要版本）
- 适用于Android的Chrome（最新和以前的主要版本，适用于店面）

### 邮件服务器

邮件传输代理(MTA)或SMTP服务器。 云基础架构上的Commerce使用[SendGrid电子邮件服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html)。

### 内存

升级从Commerce Marketplace和其他来源获得的应用程序和扩展最多可能需要2 GB的RAM。 如果您使用的系统RAM小于2 GB，请创建[交换文件](https://support.magento.com/hc/en-us/articles/360032980432)；否则，升级可能会失败。

### 操作系统(Linux x86-64)

Linux发行版，如RedHat Enterprise Linux (RHEL)、CentOS、Ubuntu、Debian等。

Microsoft Windows和macOS **不支持**。

Adobe Commerce需要以下系统工具才能进行某些操作：

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gzip.org/)
- [[!DNL lsof]](https://linux.die.net/man/8/lsof)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [[!DNL nice]](https://linux.die.net/man/1/nice)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://linux.die.net/man/1/tar)

### SSL

- HTTPS需要有效的安全证书。
- 不支持自签名SSL证书。
- 传输层安全性(TLS)要求 — PayPal和`repo.magento.com`都需要TLS 1.2或更高版本。

有关云基础架构上的Commerce，请参阅[云基础架构上的Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)指南中的&#x200B;_Fastly配置_。

### Xdebug

对于Adobe Commerce，请使用[php_xdebug 2.5.x](https://xdebug.org/download)或更高版本（仅适用于开发环境；可能会对性能产生不利影响）。

有关云上的Adobe Commerce，请参阅[云基础架构上的Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html)指南中的&#x200B;_配置Xdebug_。

>[!NOTE]
>
>`xdebug`存在已知问题，该问题可能会影响Adobe Commerce安装或安装后对店面或管理员的访问。 在[Commerce支持知识库`xdebug`中查看影响](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html)安装&#x200B;_的_&#x200B;已知问题。


<!-- Last updated from includes: 2025-08-18 10:08:31 -->
