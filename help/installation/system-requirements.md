---
title: 系统要求
description: 了解Adobe Commerce的软件依赖项和系统要求。 查看经过测试的配置以了解与部署环境的兼容性。
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
last-update: 2026-09-18
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 2456f0e28fa24e23eb7692a905c708007a00bd96
workflow-type: tm+mt
source-wordcount: '1614'
ht-degree: 0%
---
# 系统要求

以下信息总结了为Adobe Commerce测试的软件依赖项和服务。

云基础架构上Adobe Commerce的软件依赖项与内部部署的软件依赖项不同。 Adobe根据在托管云环境中测试和部署的服务，确定支持的服务版本和兼容性。 这些版本有时与内部部署支持的版本不同。

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

>云端上的[!TAB Commerce]

[Commerce on Cloud模板](https://github.com/magento/magento-cloud)为与每个版本行的最新Commerce版本兼容的服务提供了默认配置。

{{$include /help/_includes/templated/cloud-requirements-table.md}}

[`services.yaml`文件](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)定义了默认服务和版本。
请参阅*云基础架构上的Commerce*&#x200B;指南中的[配置服务](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)。

>[!TAB Commerce内部部署]

{{$include /help/_includes/templated/system-requirements-table.md}}

**MySQL 8.0于2026年4月30日停止支持(EOS)。**
在此日期之后，Adobe Commerce 2.4.7、2.4.6、2.4.5和2.4.4不提供对MySQL 8.0之后发布的MySQL版本的兼容性或支持。
Adobe不验证或支持这些Commerce发行版的较新MySQL主要版本。
如果您运行Adobe Commerce本地版本2.4.7、2.4.6、2.4.5或2.4.4，Adobe强烈建议将数据库服务器迁移到兼容的MariaDB版本。

云上的Adobe Commerce客户必须在支持的版本上保持平台依赖性。 请参阅生命周期策略中的[平台依赖项](../release/lifecycle-policy.md#platform-dependencies)。

**Elasticsearch 7.17于2026年1月15日停止支持(EOS)。**
在此日期之后，Adobe Commerce 2.4.6、2.4.5和2.4.4不提供对Elasticsearch 7之后发布的Elasticsearch版本的兼容性或支持。
Adobe不验证或支持这些Commerce版本的较新Elasticsearch主要版本。
如果您运行Adobe Commerce本地版本2.4.6、2.4.5或2.4.4，Adobe强烈建议将您的搜索基础架构迁移到兼容的OpenSearch版本。

>[!ENDTABS]

## 2.4.10-alpha Commerce发行版本的系统要求

>[!BEGINTABS]

>云端上的[!TAB Commerce]

{{$include /help/_includes/templated/cloud-requirements-table-alpha.md}}

>[!TAB Commerce内部部署]

{{$include /help/_includes/templated/system-requirements-table-alpha.md}}

>[!ENDTABS]

## 早期Commerce版本的系统要求

下表列出了Adobe Commerce版本的系统要求，包括扩展支持中的要求。 这些表仅供参考。 Adobe不建议使用不支持的软件依赖项版本。 在Adobe支持部门调查、故障排除或验证报告的行为之前，您必须使环境与支持的配置保持一致。

>[!NOTE]
>
>Adobe Commerce 2.4.6处于[扩展支持](../release/lifecycle-policy.md#extended-support)到&#x200B;**2027年8月30日**&#x200B;的过渡期，其后是[仅限安全的过渡期](../release/lifecycle-policy.md#security-only-transitional-period)到&#x200B;**2028年5月31日**。 这些规定仅适用于Adobe Commerce客户。 它们不扩展对第三方依赖项（如MySQL）的支持。
>
>如果您在云上运行Adobe Commerce，则必须在&#x200B;**2028年6月1日** [安全要求和截止日期](../release/security-enforcement-policy.md)之前升级到支持的版本或迁移到[!DNL Adobe Commerce as a Cloud Service]。 有关完整生命周期日期，请参阅[支持结束日期](../release/lifecycle-policy.md#end-of-support-dates)表。
>
>该表将折叠以最小化此文章的长度。 选择标题可将其展开。

+++早期版本的要求

>[!BEGINTABS]

>云端上的[!TAB Commerce]

[Commerce on Cloud模板](https://github.com/magento/magento-cloud)为与特定Commerce版本兼容的服务提供了默认配置。

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

[`services.yaml`文件](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml)定义了默认服务和版本。
请参阅*云基础架构上的Commerce*&#x200B;指南中的[配置服务](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)。

>[!TAB Commerce内部部署]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**MySQL 8.0于2026年4月30日停止支持(EOS)。**
在此日期之后，Adobe Commerce 2.4.7、2.4.6、2.4.5和2.4.4不提供对MySQL 8.0之后发布的MySQL版本的兼容性或支持。
Adobe不验证或支持这些Commerce发行版的较新MySQL主要版本。
如果您运行Adobe Commerce本地版本2.4.7、2.4.6、2.4.5或2.4.4，Adobe强烈建议将数据库服务器迁移到兼容的MariaDB版本。

云上的Adobe Commerce客户必须在支持的版本上保持平台依赖性。 请参阅生命周期策略中的[平台依赖项](../release/lifecycle-policy.md#platform-dependencies)。

**Elasticsearch 7.17于2026年1月15日停止支持(EOS)。**
在此日期之后，Adobe Commerce 2.4.6、2.4.5和2.4.4不提供对Elasticsearch 7之后发布的Elasticsearch版本的兼容性或支持。
Adobe不验证或支持这些Commerce版本的较新Elasticsearch主要版本。
如果您运行Adobe Commerce本地版本2.4.6、2.4.5或2.4.4，Adobe强烈建议将您的搜索基础架构迁移到兼容的OpenSearch版本。

>[!ENDTABS]

+++

## PHP设置

配置PHP设置（如`memory_limit`），以帮助避免在使用Adobe Commerce时常见的问题。 请参阅[必需的PHP设置](prerequisites/php-settings.md)。

有关云配置指南，请参阅&#x200B;*云基础架构上的Commerce*&#x200B;指南中的[PHP设置](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings)。

### PHP OPcache

Adobe建议验证是否已启用[PHP OPcache](https://www.php.net/manual/en/book.opcache.php)以提高性能。 许多PHP分发都启用OPcache。

- **对于云基础架构部署上的Adobe Commerce**，默认情况下会安装`opcache`扩展。
- 对于Adobe Commerce内部部署：****
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
>有关云基础架构中的PHP扩展，请参阅&#x200B;_云基础架构上的Commerce_&#x200B;指南中的[启用PHP扩展](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions)。

>[!BEGINTABS]

>云端上的[!TAB Commerce]

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

Adobe Commerce支持以下店面和管理员浏览器的最新和先前主要版本，但以下说明除外：

- Microsoft Edge
- Firefox（任何操作系统）
- Chrome（任何操作系统）
- Safari（仅限macOS）
- 适用于iOS的Safari（仅限店面）
- Chrome for Android（仅限店面）

### 邮件服务器

邮件传输代理(MTA)或SMTP服务器。 云基础架构上的Commerce使用[SendGrid电子邮件服务](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/sendgrid)。

### 内存

从Commerce Marketplace和其他源升级应用程序和扩展最多可能需要2 GB的RAM。 如果系统的RAM小于2 GB，请创建[交换文件](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade)。 如果没有交换文件，升级可能会失败。

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

有关云基础架构上的Commerce，请参阅&#x200B;*云基础架构上的Commerce*&#x200B;指南中的[Fastly配置](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)。

### Xdebug

仅对于Adobe Commerce开发环境，请使用[php_xdebug 2.5.x](https://xdebug.org/download)或更高版本。 Xdebug可能会对性能产生负面影响。

有关云上的Adobe Commerce，请参阅&#x200B;*云基础架构上的Commerce*&#x200B;指南中的[配置Xdebug](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/debug)。

>[!NOTE]
>
>Xdebug存在的已知问题可能会影响Adobe Commerce的安装或者对店面或管理员的安装访问权限。 在&#x200B;_Commerce支持知识库_&#x200B;中查看影响`xdebug`安装](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation)的[已知问题。

<!-- Last updated from includes: 2026-10-13 09:11:06 -->
