---
title: 使用多个清漆实例清除缓存
description: 了解缓存清除如何与多个清漆实例一起使用。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 1%

---


# 缓存清除多个清漆实例

Adobe Commerce和Magento Open Source支持多个开箱即用的清漆实例。

本主题显示了使用商务配置多个清漆实例的基础知识。

## 清除多个清漆实例的配置

在使用配置清漆主机后，商务清除清漆主机 [`magento setup:config:set`](../../installation/tutorials/deployment.md) 命令。

您应使用 `--http-cache-hosts` 参数，指定以逗号分隔的清漆主机和侦听端口列表。 （请勿将主机分隔为空格字符。）

参数格式必须为 `<hostname or ip>:<listen port>`，在这里 `<listen port>` 如果是端口80。

例如，

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

然后，在刷新商务缓存(也称为 _清洁_ 缓存)或使用命令行。

要使用管理员刷新缓存，请单击 **系统** >工具> **缓存管理**，然后单击 **刷新Magento缓存** 的双曲余切值。 （您还可以刷新单个缓存类型。）

要从cli刷新多个Rikest实例的缓存，请使用 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) 命令 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).
