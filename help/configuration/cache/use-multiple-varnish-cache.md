---
title: 使用多个Varnish实例清除缓存
description: 了解缓存清除如何与多个Varnish实例一起使用。
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 1%

---

# 缓存清除多个清漆实例

Adobe Commerce支持多个现成的Varnish实例。

本主题显示了使用Commerce配置多个Varnish实例的基础知识。

## 清除多个Varnish实例的配置

在使用配置Varnish主机后，Commerce会清除Varnish主机 [`magento setup:config:set`](../../installation/tutorials/deployment.md) 命令。

您应使用 `--http-cache-hosts` 用于指定清漆主机和监听端口的逗号分隔列表的参数。 （不要使用空格字符分隔主机。）

参数格式必须为 `<hostname or ip>:<listen port>`，可忽略 `<listen port>` 如果是端口80。

例如，

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

然后，您可以在刷新Commerce缓存时清除所有Varnish主机(也称为 _清理_ 缓存)，或使用命令行。

要使用“管理员”刷新缓存，请单击 **系统** >工具> **缓存管理**，然后单击 **刷新Magento缓存** 页面顶部的。 （也可以刷新单个缓存类型。）

要通过cli刷新多个Varnish实例的缓存，请使用 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) 命令作为 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).
