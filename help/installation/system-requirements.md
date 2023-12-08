---
title: 系统要求
description: 使用本参考可识别已在Adobe Commerce和Magento Open Source版本中测试的必需软件依赖项。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 8b9e4de2799532e4654fce63d856c2d301025f09
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 0%

---

# 系统要求

下面总结了针对Adobe Commerce和Magento Open Source测试的软件依赖项和服务。

Commerce对云基础架构的依赖性存在一些差异。 云基础架构上Adobe Commerce的服务版本和兼容性支持取决于测试和部署到托管云环境的服务，有时不同于Adobe Commerce内部部署支持的版本。 例如，内部部署支持Elasticsearch7.17的Commerce 2.4.4，而云基础架构上的Commerce 2.4.4支持OpenSearch 1.2。

下表显示了Adobe使用特定Adobe Commerce和Magento Open Source版本测试的第三方软件依赖项版本。

Adobe仅支持下表中描述的系统要求组合。 例如，2.4.5已通过MariaDB 10.4进行了全面测试。Adobe建议您在升级到2.4.5之前升级到MariaDB 10.4。

>[!BEGINTABS]

>[!TAB 云端商务]

此 [云模板上的Commerce](https://github.com/magento/magento-cloud) 提供与特定Commerce版本兼容的服务的默认配置。

{{$include /help/_includes/templated/cloud-requirements-table.md}}

服务和版本在中定义 [该 `services.yaml` 文件](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). 以下是云基础架构上Commerce 2.4.6的默认服务配置：

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

请参阅 [配置服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) 在 _云基础架构上的Commerce_ 指南。

>[!TAB Commerce内部部署]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP设置

有特定的PHP配置设置，如 `memory_limit` 设置，这有助于您在使用Adobe Commerce和Magento Open Source时避免出现常见问题。 请参阅 [必需的PHP设置](prerequisites/php-settings.md).

有关云配置指南，请参阅 [PHP设置](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) 在 _云基础架构上的Commerce_ 指南。

### PHP OPcache

建议您确认 [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) 出于性能原因而启用。 OPcache在许多PHP分发中启用。 此 `opcache` 默认情况下，扩展安装在云基础架构上的Commerce中。

对于内部部署，验证是否已安装PHP OPcache，请参见 [PHP设置](prerequisites/php-settings.md). 有关性能设置的特定指导，请参阅软件建议 [PHP设置](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) 在 _性能最佳实践_ 指南。

如果必须单独安装OPcache，请参见 [PHP OPcache文档](https://www.php.net/manual/en/opcache.setup.php).

### PHP进程控制

{{php-process-control}}

### PHPUnit

PHPUnit（作为命令行工具）9.0.0

### PHP扩展

此 [PHP安装说明](prerequisites/php-settings.md) 包括安装这些扩展步骤。

>[!TIP]
>
>有关云基础架构中的PHP扩展，请参见 [启用PHP扩展](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) 在 _云基础架构上的Commerce_ 指南。

>[!BEGINTABS]

>[!TAB 云端商务]

下表显示了在Cloud平台上部署Adobe Commerce时支持的PHP扩展。

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce内部部署]

{{$include /help/_includes/templated/php-extensions.md}}

请参阅 [PHP官方文档](https://www.php.net/manual/en/extensions.php) 了解安装详细信息。

>[!ENDTABS]

## 其他

本节介绍所有其他类型的必需软件和可选软件的支持和兼容性。

>[!NOTE]
>
>以下要求适用于Adobe Commerce和Magento Open Source的最新2.4.x修补程序版本。 在相关时，提供云基础架构上的Commerce指导。

### 浏览器

店面和管理员：

- Microsoft Edge（最新和以前的主要版本）
- Firefox（最新和以前的主要版本；任何操作系统）
- Chrome（最新和以前的主要版本；任何操作系统）
- Safari(最新和以前的主要版本；仅限macOS)
- 适用于iPad 2的Safari Mobile、iPad Mini、带有Retina Display的iPad(iOS 12或更高版本)、桌面店面
- 适用于iPhone 6或更高版本的Safari Mobile；适用于iOS 12或更高版本的移动店面
- 适用于移动设备的Chrome（最新和以前的主要版本） [Android™ 4或更高版本] 适用于移动店面)

### 邮件服务器

邮件传输代理(MTA)或SMTP服务器。 云基础架构上的Commerce使用 [SendGrid电子邮件服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### 内存

升级从Commerce Marketplace和其他来源获得的应用程序和扩展最多可能需要2 GB的RAM。 如果您使用的系统RAM小于2 GB，请创建 [交换文件](https://support.magento.com/hc/en-us/articles/360032980432)；否则，升级可能会失败。

### 操作系统(Linux x86-64)

Linux发行版，如RedHat Enterprise Linux (RHEL)、CentOS、Ubuntu、Debian等。 不支持Microsoft Windows和macOS。

Adobe Commerce和Magento Open Source需要以下系统工具才能进行某些操作：

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
- 传输层安全性(TLS)要求 — PayPal和 `repo.magento.com` 这两种方法都需要TLS 1.2或更高版本。

有关云基础架构上的Commerce，请参阅 [Fastly配置](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) 在 _云基础架构上的Commerce_ 指南。

### Xdebug

对于Adobe Commerce和Magento Open Source，请使用 [php_xdebug 2.5.x](https://xdebug.org/download) 或更高版本（仅限开发环境；可能会对性能产生不利影响）。

有关云上的Adobe Commerce，请参阅 [配置Xdebug](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) 在 _云基础架构上的Commerce_ 指南。

>[!NOTE]
>
>存在已知问题 `xdebug` 会影响Adobe Commerce或Magento Open Source安装或安装后对店面或Admin的访问的其他资源。 请参阅 [已知问题，影响 `xdebug` 安装](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) 在 _Commerce支持知识库_.
