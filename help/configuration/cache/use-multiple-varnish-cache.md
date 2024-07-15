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

在使用[`magento setup:config:set`](../../installation/tutorials/deployment.md)命令配置清漆主机后，Commerce会清除清漆主机。

您应该使用`--http-cache-hosts`参数指定以逗号分隔的Varnish主机和侦听端口列表。 （不要使用空格字符分隔主机。）

参数格式必须为`<hostname or ip>:<listen port>`，如果它是端口80，则可以省略`<listen port>`。

例如，

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

然后，当您在Admin中刷新Commerce缓存（也称为&#x200B;_清理_&#x200B;缓存）或使用命令行时，可以清除所有Varnish主机。

若要使用管理员刷新缓存，请单击&#x200B;**系统** >工具> **缓存管理**，然后单击页面顶部的&#x200B;**刷新Magento缓存**。 （也可以刷新单个缓存类型。）

要通过cli刷新多个Varnish实例的缓存，请使用[`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types)命令作为[文件系统所有者](../../installation/prerequisites/file-system/overview.md)。
