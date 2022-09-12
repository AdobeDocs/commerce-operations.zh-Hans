---
title: 配置锁定提供程序
description: 请按照以下步骤操作，以防止重复的cron作业和cron组在Adobe Commerce或Magento Open Source部署中运行。
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 配置锁定提供程序

运行此命令之前，必须执行以下操作 *或* 您必须 [安装应用程序](../advanced.md):

* [创建或更新部署配置](deployment.md)
* [创建数据库模式](database.md)

## 安全安装

{{$include /help/_includes/secure-install.md}}

## 配置锁定

配置锁定提供程序以阻止启动重复的cron作业和cron组。 (需要Adobe Commerce或Magento Open Source2.2.x、2.2.5及更高版本，以及2.3.3及更高版本。)

Adobe Commerce和Magento Open Source默认使用数据库来保存锁。 如果您的服务器上有多个节点，我们建议使用Zookeeper作为锁定提供程序。

如果您在云基础架构上运行Adobe Commerce，则无需配置锁提供程序设置。 在设置过程中，应用程序会为Pro项目配置文件锁定提供程序。 请参阅 [云变量](https://devdocs.magento.com/cloud/env/variables-cloud.html).

### 使用命令

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### 参数描述

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--lock-provider` | 锁定提供程序名称： `db`, `zookeeper`或 `file`.<br><br>默认的锁定提供程序： `db` | 否 |
| `--lock-db-prefix` | 使用 `db` 锁定提供程序。<br><br>默认值： `NULL` | 否 |
| `--lock-zookeeper-host` | 在使用 `zookeeper` 锁定提供程序。<br><br>例如： `127.0.0.1:2181` | 是，如果您设置 `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper保存锁的路径。<br><br>默认路径为： `/magento/locks` | 否 |
| `--lock-file-path` | 保存文件锁定的路径。 | 是，如果您设置 `--lock-provider=file` |
