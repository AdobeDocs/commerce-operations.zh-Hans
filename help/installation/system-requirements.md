---
title: 系统要求
description: 了解Adobe Commerce的软件依赖项和系统要求。 查看经过测试的配置以了解与部署环境的兼容性。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: eacee993ec38cce7763d4c99b1bbb67a319d8c1a
workflow-type: tm+mt
source-wordcount: '1371'
ht-degree: 0%

---

# 系统要求

以下信息总结了为Adobe Commerce测试的软件依赖项和服务。

在Commerce on Cloud的依赖项方面有一些差异。 Adobe Commerce on Cloud的服务版本和兼容性支持由测试并部署到托管云环境的服务决定，有时不同于Adobe Commerce内部部署支持的版本。

>[!IMPORTANT]
>
>系统要求表列出了它们适用的Adobe Commerce版本，包括标记为测试版或抢先体验的版本。
>有关最新发布的Commerce版本，请参阅[发行说明](../release/release-notes/overview.md)。
>
>当您的服务版本与Commerce版本支持的配置不匹配时，行为可能与Adobe在测试中重现的行为不同。 Adobe支持部门可能会要求您在调查、故障排除或验证报告的行为之前，将环境与支持的配置保持一致。 调整环境后，Adobe支持部门可以继续调查。

下表显示了Adobe已在特定Adobe Commerce版本中测试的第三方软件依赖项版本。

Adobe仅支持下表列出的系统要求组合。 Adobe不验证或支持与列出的组合不匹配的配置。 例如，Adobe Commerce 2.4.9通过MariaDB 12.3进行测试。 在升级到2.4.9之前，请升级到MariaDB 12.3。

## 最新Commerce发行版本的系统要求

下表汇总了所有受支持的Commerce版本的最新版本的系统要求。 Adobe建议所有客户都升级到这些版本。

>[!BEGINTABS]

>[!TAB 云端上的 Commerce]

[Commerce on Cloud模板](https://github.com/magento/magento-cloud)为与每个版本行的最新Commerce版本兼容的服务提供了默认配置。

{{$include /help/_includes/templated/cloud-requirements-table.md}}

**<sup>1</sup>MariaDB 12.3与Adobe Commerce 2.4.9之间的兼容性**
MariaDB 12.3正式发布后，MariaDB 12.3与Adobe Commerce 2.4.9之间的兼容性将得到确认，预计将在5-6月时间范围内发布。

对于默认配置，服务和版本定义在[的`services.yaml`文件](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)中。
有关更多详细信息，请参阅*云基础架构上的Commerce*&#x200B;指南中的[配置服务](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)。

>[!TAB Commerce内部部署]

{{$include /help/_includes/templated/system-requirements-table.md}}

**MySQL 8.0于2026年4月30日停止支持(EOS)。**
在此日期之后，Adobe Commerce 2.4.7、2.4.6、2.4.5和2.4.4将不再提供兼容性或
支持在MySQL 8.0之后发布的任何MySQL版本。Adobe不会
在此Adobe上验证或提供对较新MySQL主要版本的支持
Commerce版本行。
运行版本2.4.7、2.4.6、2.4.5、2.4.4的所有Adobe Commerce内部部署客户都非常强
建议将其数据库服务器迁移到兼容的MariaDB版本。

云上的Adobe Commerce客户必须在支持的版本上保持平台依赖性。 请参阅生命周期策略中的[平台依赖项](../release/lifecycle-policy.md#platform-dependencies)。

**Elasticsearch 7.17于2026年1月15日停止支持(EOS)。**
在此日期之后，Adobe Commerce 2.4.6、2.4.5和2.4.4将不提供兼容性或
支持在Elasticsearch 7之后发布的任何Elasticsearch版本。Adobe不会
在此Adobe上验证或提供对较新Elasticsearch主要版本的支持
Commerce版本行。
运行版本2.4.6、2.4.5、2.4.4的所有Adobe Commerce本地客户都属于强客户
建议将其搜索基础结构迁移到兼容的OpenSearch版本。

>[!ENDTABS]

## 早期Commerce版本的系统要求

下表列出了Adobe Commerce版本的系统要求，包括扩展支持中的要求。 提供这些表仅供参考。 Adobe不建议使用不支持的软件依赖项版本，支持团队要求您将环境与支持的配置相协调，然后才能调查、排除或验证报告的行为。

>[!NOTE]
>
>Adobe Commerce 2.4.6处于[扩展支持](../release/lifecycle-policy.md#extended-support)到&#x200B;**2027年8月30日**&#x200B;的过渡期，其后是[仅限安全的过渡期](../release/lifecycle-policy.md#security-only-transitional-period)到&#x200B;**2028年5月31日**。 这些规定仅适用于Adobe Commerce客户。 它们不扩展对第三方依赖项（如MySQL）的支持。
>
>如果您在云上运行Adobe Commerce，则必须在&#x200B;**2028年6月1日** [版本升级实施日期](../release/version-upgrade-enforcement-policy.md)之前升级到支持的版本或迁移到[!DNL Adobe Commerce as a Cloud Service]。 有关完整生命周期日期，请参阅[支持结束日期](../release/lifecycle-policy.md#end-of-support-dates)表。
>
>该表将折叠以最小化此文章的长度。 选择标题可将其展开。

+++早期版本的要求

>[!BEGINTABS]

>[!TAB 云端上的 Commerce]

[Commerce on Cloud模板](https://github.com/magento/magento-cloud)为与特定Commerce版本兼容的服务提供了默认配置。

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

对于默认配置，服务和版本定义在[的`services.yaml`文件](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)中。
有关更多详细信息，请参阅*云基础架构上的Commerce*&#x200B;指南中的[配置服务](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)。

>[!TAB Commerce内部部署]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**MySQL 8.0于2026年4月30日停止支持(EOS)。**
在此日期之后，Adobe Commerce 2.4.7、2.4.6、2.4.5和2.4.4将不再提供兼容性或
支持在MySQL 8.0之后发布的任何MySQL版本。Adobe不会
在此Adobe上验证或提供对较新MySQL主要版本的支持
Commerce版本行。
运行版本2.4.7、2.4.6、2.4.5、2.4.4的所有Adobe Commerce内部部署客户都非常强
建议将其数据库服务器迁移到兼容的MariaDB版本。

云上的Adobe Commerce客户必须在支持的版本上保持平台依赖性。 请参阅生命周期策略中的[平台依赖项](../release/lifecycle-policy.md#platform-dependencies)。

**Elasticsearch 7.17于2026年1月15日停止支持(EOS)。**
在此日期之后，Adobe Commerce 2.4.6、2.4.5和2.4.4将不提供兼容性或
支持在Elasticsearch 7之后发布的任何Elasticsearch版本。Adobe不会
在此Adobe上验证或提供对较新Elasticsearch主要版本的支持
Commerce版本行。
运行版本2.4.6、2.4.5、2.4.4的所有Adobe Commerce本地客户都属于强客户
建议将其搜索基础结构迁移到兼容的OpenSearch版本。

>[!ENDTABS]

+++

## PHP设置

有特定的PHP配置设置，如`memory_limit`设置，可帮助您在使用Adobe Commerce时避免常见问题。 请参阅[必需的PHP设置](prerequisites/php-settings.md)。

有关云配置指南，请参阅&#x200B;*云基础架构上的Commerce*&#x200B;指南中的[PHP设置](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/configure/app/php-settings)。

### PHP OPcache

Adobe建议您验证是否出于性能原因启用了[PHP OPcache](https://www.php.net/manual/en/book.opcache.php)。 OPcache在许多PHP分发中启用。

- **对于云基础架构部署上的Adobe Commerce**，默认情况下会安装`opcache`扩展。
- 对于Adobe Commerce内部部署：**&#x200B;**
   - [验证是否已安装PHP OPcache扩展](prerequisites/php-settings.md#verify-php-is-installed)。
   - 有关性能设置的特定指导，请参阅&#x200B;*性能最佳实践*&#x200B;指南中的[PHP设置](../performance/software.md#php-settings)的软件建议。


如果必须单独安装OPcache，请参阅[PHP OPcache文档](https://www.php.net/manual/en/opcache.setup.php)。

### PHP进程控制

{{php-process-control}}

### PHPUnit

支持的PHPUnit主版本取决于Adobe Commerce版本。 Adobe使用PHPUnit 12测试2.4.9，使用PHPUnit 10测试2.4.8-p5，使用PHPUnit 9测试2.4.7-p10到2.4.4-p18。 在主要版本中安装PHPUnit作为命令行工具，该版本与针对您的发行版测试的Adobe配置相匹配。

### PHP扩展

[PHP安装说明](prerequisites/php-settings.md)包含安装这些扩展的步骤。

>[!TIP]
>
>有关云基础架构中的PHP扩展，请参阅&#x200B;_云基础架构上的Commerce_&#x200B;指南中的[启用PHP扩展](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions)。

>[!BEGINTABS]

>[!TAB 云端上的 Commerce]

下表显示了在Cloud平台上部署Adobe Commerce时支持的PHP扩展。

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce内部部署]

{{$include /help/_includes/templated/php-extensions.md}}

有关安装详细信息，请参阅[PHP官方文档](https://www.php.net/manual/en/extensions.php)。

>[!ENDTABS]

## 其他软件要求

本节介绍所有其他类型的必需软件和可选软件的支持和兼容性。

>[!NOTE]
>
>以下要求适用于Adobe Commerce的最新2.4.x修补程序版本。 在相关时，提供了有关云基础架构的Commerce指南。

### 浏览器

店面和管理员：

- Microsoft Edge（最新和以前的主要版本）
- Firefox（任何操作系统上的最新和以前的主要版本）
- Chrome（任何操作系统上的最新和以前的主要版本）
- Safari（仅限macOS上的最新和以前的主要版本）
- 适用于iOS的Safari（店面的最新和以前的主要版本）
- Chrome for Android（店面的最新和以前的主要版本）

### 邮件服务器

邮件传输代理(MTA)或SMTP服务器。 云基础架构上的Commerce使用[SendGrid电子邮件服务](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/project/sendgrid)。

### 内存

升级从Commerce Marketplace和其他来源获得的应用程序和扩展最多可能需要2 GB的RAM。 如果您使用的系统RAM小于2 GB，请创建[交换文件](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)。 否则，升级可能会失败。

### 操作系统(Linux x86-64)

Linux发行版，如Red Hat Enterprise Linux (RHEL)、CentOS、Ubuntu、Debian等。

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

有关云基础架构上的Commerce，请参阅&#x200B;*云基础架构上的Commerce*&#x200B;指南中的[Fastly配置](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)。

### Xdebug

对于Adobe Commerce，请使用[php_xdebug 2.5.x](https://xdebug.org/download)或更高版本（仅适用于开发环境；可能会对性能产生不利影响）。

有关云上的Adobe Commerce，请参阅&#x200B;*云基础架构上的Commerce*&#x200B;指南中的[配置Xdebug](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/test/debug)。

>[!NOTE]
>
>`xdebug`存在已知问题，该问题可能会影响Adobe Commerce安装或安装后对店面或管理员的访问。 在&#x200B;_Commerce支持知识库_&#x200B;中查看影响`xdebug`安装[&#128279;](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation)的已知问题。

<!-- Last updated from includes: 2026-06-01 15:26:19 -->
