---
title: 配置锁定提供程序
description: 执行以下步骤，防止重复的cron作业和cron组在Adobe Commerce部署上运行。
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# 配置锁定提供程序

运行此命令之前，必须执行以下&#x200B;*或*&#x200B;操作，必须[安装应用程序](../advanced.md)：

* [创建或更新部署配置](deployment.md)
* [创建数据库模式](database.md)

## 安全安装

{{$include /help/_includes/secure-install.md}}

## 配置锁定

配置锁定提供程序以防止启动重复的cron作业和cron组。 (需要Adobe Commerce 2.2.x、2.2.5及更高版本以及2.3.3及更高版本。)

默认情况下，Adobe Commerce使用数据库保存锁定。 如果您的服务器上有多个节点，我们建议使用Zookeeper作为锁定提供程序。

如果您在云基础架构上运行Adobe Commerce，则无需配置锁定提供程序设置。 应用程序在预配过程中为Pro项目配置文件锁定提供程序。 查看[云变量](https://devdocs.magento.com/cloud/env/variables-cloud.html)。

### 命令用法

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### 参数描述

| 名称 | 值 | 必需？ |
|--- |--- |--- |
| `--lock-provider` | 锁定提供程序名称： `db`、`zookeeper`或`file`。<br><br>默认锁定提供程序： `db` | 否 |
| `--lock-db-prefix` | 使用`db`锁定提供程序时为避免锁定冲突而使用的特定数据库前缀。<br><br>默认值： `NULL` | 否 |
| `--lock-zookeeper-host` | 使用`zookeeper`锁定提供程序时用于连接到Zookeeper群集的主机和端口。<br><br>例如： `127.0.0.1:2181` | 是，如果您设置`--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Zookeeper保存锁的路径。<br><br>默认路径为： `/magento/locks` | 否 |
| `--lock-file-path` | 保存文件锁定的路径。 | 是，如果您设置`--lock-provider=file` |
