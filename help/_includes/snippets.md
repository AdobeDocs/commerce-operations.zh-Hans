---
source-git-commit: 74cb55f4552bc1b2dace37d9a6f7e68939d1c262
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---
# 代码片段

## 仅限商务 {#commerce-only}

>[!NOTE]
>
>的 [!DNL Upgrade Compatibility Tool] 仅适用于Adobe Commerce实例。

<!-- Configuration guide snippets -->

## 文件系统所有者 {#file-system-owner}

>[!WARNING]
>
>所有MagentoCLI命令都必须由 [文件系统所有者](/help/configuration/cli/config-cli.md#prerequisites).

## 备份命令 {#tip-backup-command}

>[!TIP]
>
>的 `support:backup` 命令为 _not_ 执行的相同代码备份 `setup:backup` 命令。 的 `support:backup` 命令用于备份代码以供Adobe Commerce支持部门检查。

## 仅Adobe Commerce {#ee-only}

>[!NOTE]
>
>此功能仅适用于Adobe Commerce实例。

## 已弃用拆分数据库 {#deprecate-split-db}

>[!IMPORTANT]
>
>拆分数据库功能是 [已弃用](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) 在版本2.4.2的Adobe Commerce中。 请参阅 [从拆分数据库还原到单个数据库](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## 后向不兼容的更改 {#bics}

>[!NOTE]
>
>Adobe Commerce和Magento Open Source版本可能包含不兼容的后向更改(BIC)。 要查看向后不兼容的更改，请参阅 [BIC引用](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). 有关主要的不兼容后向问题，请参见 [BIC亮点](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). 并非所有版本都引入了主要的BIC。

## CVE通知 {#cve-notice}

>[!NOTE]
>
>从2.3.2版本开始，我们将分配并发布已编入索引的常见漏洞和暴露(CVE)编号，其中每个安全错误都由外部方向我们报告。 这允许用户更轻松地识别其部署中的未寻址漏洞。 您可以在 [CVE](https://cve.mitre.org/).
