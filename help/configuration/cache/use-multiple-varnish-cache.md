---
title: 使用多个清漆实例进行缓存清除
description: 了解缓存清除如何与Adobe Commerce中的多个清漆实例配合使用。 了解配置和管理最佳实践。
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
badgePaas: label="内部部署" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce本地项目。"
autotag-review: '2026-06-22T22:16:50.500Z'
TQID: 'https://experienceleague.adobe.com/GeX8wkpM1rLLWM7jMhP2r-SJ8uV-x7fLXC8WEazZQDo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 206
ht-degree: 0%

---

# 使用多个Varnish实例清除缓存

Adobe Commerce支持多个现成的Varnish实例。

本主题显示了使用Commerce配置多个Varnish实例的基础知识。

{{varnish-config-cloud}}

## 清除多个Varnish实例的配置

在使用[`magento setup:config:set`](../../installation/tutorials/deployment.md)命令配置清漆主机后，Commerce会清除清漆主机。

您应该使用`--http-cache-hosts`参数指定以逗号分隔的Varnish主机和侦听端口列表。 （不要使用空格字符分隔主机。）

参数格式必须为`<hostname or ip>:<listen port>`，如果它是端口80，则可以省略`<listen port>`。

例如，

```shell
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

然后，当您在Admin中刷新Commerce缓存（也称为&#x200B;_清理_&#x200B;缓存）或使用命令行时，可以清除所有Varnish主机。

若要使用管理员刷新缓存，请单击&#x200B;**系统** >工具> **缓存管理**，然后单击页面顶部的&#x200B;**刷新Magento缓存**。 （也可以刷新单个缓存类型。）

要通过cli刷新多个Varnish实例的缓存，请使用[`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types)命令作为[文件系统所有者](../../installation/prerequisites/file-system/overview.md)。
