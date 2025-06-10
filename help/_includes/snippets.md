---
source-git-commit: 102fee9672c75c94c7d18d47562338f8eff97f11
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---
# 代码片段

## 仅限Commerce {#commerce-only}

>[!NOTE]
>
>[!DNL Upgrade Compatibility Tool]仅适用于Adobe Commerce实例。

<!-- Configuration guide snippets -->

## 文件系统所有者 {#file-system-owner}

>[!WARNING]
>
>所有Magento CLI命令都必须由[文件系统所有者](/help/configuration/cli/config-cli.md#prerequisites)运行。

## 备份命令 {#tip-backup-command}

>[!TIP]
>
>`support:backup`命令是&#x200B;_而不是_&#x200B;由`setup:backup`命令执行的相同代码备份。 `support:backup`命令用于备份代码以供Adobe Commerce支持部门检查。

## B2B修补程序 {#b2b-patches}

>[!NOTE]
>
>安装此安全修补程序后，Adobe Commerce B2B商家还必须更新到最新的兼容B2B安全修补程序版本。 请参阅[B2B发行说明](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes)。

## 仅限Adobe Commerce {#ee-only}

>[!NOTE]
>
>此功能仅适用于Adobe Commerce实例。

## 已弃用拆分数据库 {#deprecate-split-db}

>[!IMPORTANT]
>
>在Adobe Commerce版本2.4.2中，拆分数据库功能[已弃用](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157)。 请参阅[从拆分数据库还原到单个数据库](/help/configuration/storage/revert-split-database.md)。

<!-- End of Configuration guide snippets -->

## 向后不兼容的更改 {#bics}

>[!NOTE]
>
>Adobe Commerce版本可能包含向后不兼容的更改(BIC)。 要查看与向后不兼容的更改，请参阅[BIC参考](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/)。 在[BIC亮点](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/)中描述了严重的向后不兼容问题。 并非所有发行版本都引进了主要BIC。

## Alpha免责声明 {#alpha}

>[!IMPORTANT]
>
>[Alpha](/help/release/versioning-policy.md#alpha-patch-release)版本可能不完整，并且可能包含缺陷。 它们按“原样”提供，不提供任何形式的担保。 Adobe没有义务维护、更正、更新、更改、修改或以其他方式支持(通过Adobe支持服务或其他方式)Alpha版本。 客户不应依赖Alpha版本或任何随附文档或材料的正确功能或性能。 使用Alpha版本完全由客户自行承担风险。

## Beta免责声明 {#beta}

>[!IMPORTANT]
>
>Beta版本可能包含缺陷，并“按原样”提供，无任何类型的担保。 Adobe没有义务维护、更正、更新、更改、修改或以其他方式支持(从Adobe支持服务或任何其他服务)Beta版。 客户应谨慎使用，切勿依赖测试版和/或任何随附的文档或材料的正确功能或性能。 因此，使用测试版完全由客户自行承担风险。

## CVE通知 {#cve-notice}

>[!NOTE]
>
>从2.3.2版本开始，我们将分配并发布索引式常见漏洞和暴露(CVE)编号，其中会包含外部方报告给我们的每个安全错误。 这使用户能够更轻松地识别其部署中未解决的漏洞。 您可以在[CVE](https://cve.mitre.org/)了解有关CVE标识符的更多信息。

## 其他发行信息 {#other-release-info}

>[!NOTE]
>
>虽然这些发行说明中描述的增强功能和错误修复代码与Adobe Commerce捆绑在一起，但其中几个项目(例如B2B、Page Builder和Progressive Web Applications (PWA) Studio)也独立发布。 每个项目的文档中都提供了特定于项目的单独发行信息，其中记录了这些项目的错误修复。 请参阅[产品版本概述](/help/release/release-notes/overview.md)。

## PHP进程控制 {#php-process-control}

在并行模式下运行索引器之前，必须在PHP中启用进程控制支持(`pcntl`)。 请参阅PHP文档中的[安装](https://www.php.net/manual/en/pcntl.installation.php)。
