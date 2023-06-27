---
title: ‘[!DNL Data Migration Tool] 先决条件
description: 了解在开始使用之前需要做什么 [!DNL Data Migration Tool] 在Magento1和Magento2之间传输数据。
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# [!DNL Data Migration Tool] 先决条件

在开始迁移之前，请确保满足以下要求。

## Magento2系统

* 设置您的Magento2系统，使其符合 [系统要求](../../installation/system-requirements.md).

  使用至少与现有Magento1系统匹配的拓扑和设计。

* [安装Magento2](../../installation/overview.md).

## Cron

不要开始Magento2 cron作业。

## 数据库

* 安装后，备份或 [转储](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) 您的Magento2数据库。 这样，在迁移不成功时，可以恢复初始数据库状态。

* 验证 [!DNL Data Migration Tool] 具有连接Magento1和Magento2数据库的网络访问权限。

  打开防火墙中的端口，以便迁移工具可以与数据库通信。

* 确保您的MySQL帐户具有访问Magento数据库的所有必要权限。

如果为Magento1数据库启用了二进制日志记录，请设置全局 [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL系统变量 `1`，或授予 [SUPER权限](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) 到您的帐户。

* 我们不建议在迁移之前在Magento2存储区中创建新实体（产品、类别和属性），因为 [!DNL Data Migration Tool] 用Magento1中的旧实体覆盖此类新实体。

## 扩展

将Magento1扩展代码迁移到Magento2。

要查找最新的扩展版本，请访问 [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) 或与扩展提供商联系。

您还可以使用 [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
