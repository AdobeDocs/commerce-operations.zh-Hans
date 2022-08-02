---
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '97'
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
