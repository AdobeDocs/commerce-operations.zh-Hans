---
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---
# 代码片段

## 仅限Commerce {#commerce-only}

>[!NOTE]
>
>此 [!DNL Upgrade Compatibility Tool] 仅适用于Adobe Commerce实例。

<!-- Configuration guide snippets -->

## 文件系统所有者 {#file-system-owner}

>[!WARNING]
>
>所有MagentoCLI命令必须由 [文件系统所有者](/help/configuration/cli/config-cli.md#prerequisites).

## 备份命令 {#tip-backup-command}

>[!TIP]
>
>此 `support:backup` 命令为 _非_ 执行的相同代码备份 `setup:backup` 命令。 此 `support:backup` 命令用于备份代码以供Adobe Commerce支持部门检查。

## 仅限Adobe Commerce {#ee-only}

>[!NOTE]
>
>此功能仅适用于Adobe Commerce实例。

## 已弃用拆分数据库 {#deprecate-split-db}

>[!IMPORTANT]
>
>拆分数据库功能是 [已弃用](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) 在Adobe Commerce版本2.4.2中。 请参阅 [从拆分数据库还原到单个数据库](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## 向后不兼容的更改 {#bics}

>[!NOTE]
>
>Adobe Commerce版本可能包含向后不兼容的更改(BIC)。 要查看与向后不兼容的更改，请参阅 [BIC参考](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). 有关主要向后不兼容问题的说明，请参见 [BIC重点](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). 并非所有发行版本都引进了主要BIC。

## CVE通知 {#cve-notice}

>[!NOTE]
>
>从2.3.2版本开始，我们将分配并发布索引式常见漏洞和暴露(CVE)编号，其中会包含外部方报告给我们的每个安全错误。 这使用户能够更轻松地识别其部署中未解决的漏洞。 要了解有关CVE标识符的更多信息，请访问 [CVE](https://cve.mitre.org/).

## 其他发行信息 {#other-release-info}

>[!NOTE]
>
>虽然这些发行说明中描述的增强功能和错误修复代码与Adobe Commerce捆绑在一起，但其中几个项目(例如B2B、页面生成器和Progressive Web Application(PWA)Studio)也单独发布。 每个项目的文档中都提供了特定于项目的单独发行信息，其中记录了这些项目的错误修复。 请参阅 [产品版本概述](/help/release/release-notes/overview.md).

## PHP进程控制 {#php-process-control}

在并行模式下运行索引器之前，必须启用“进程控制”支持(`pcntl`)。 请参阅 [安装](https://www.php.net/manual/en/pcntl.installation.php) 在PHP文档中。
