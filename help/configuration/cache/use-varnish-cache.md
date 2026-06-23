---
title: 清漆缓存清除
description: 了解缓存清除如何与Adobe Commerce的Varnish Web缓存加速器配合使用。 了解缓存管理和优化技术。
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
badgePaas: label="内部部署" type="Informative" url="https://experienceleague.adobe.com/zh-hans/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce本地项目。"
autotag-review: '2026-06-22T22:18:33.462Z'
TQID: 'https://experienceleague.adobe.com/ePhbVWjx-hX99p8OKiKqzT-w2KZu-XjS1XieuStKqc4'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 405
ht-degree: 0%

---

# 使用清漆清除缓存

本主题讨论将Varnish用作Adobe Commerce的Web缓存加速器的基础知识。

{{varnish-config-cloud}}

## 清漆清除

根据[Varnish文档](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html)，“当您从缓存中挑选对象并将其随其变体一起丢弃时，将发生&#x200B;*清除*。” 清漆清除类似于缓存清除命令（或单击管理员中的&#x200B;**刷新Magento缓存**）。

事实上，当您清理、刷新或刷新Commerce缓存时，“清漆”也会清除。

安装并配置Varnish以用于Commerce后，以下操作可能会导致清空清空：

- 维护网站。

  例如，您在管理员中执行的任何操作：

   - **存储** > **设置** > **配置** >常规> **常规**
   - **存储** > **设置** > **配置** >常规> **货币设置**
   - **存储** > **设置** > **配置** >常规> **存储电子邮件地址**

  当Commerce检测到此类更改时，将显示一条消息，通知您刷新缓存。

- 维护商店（例如，添加或编辑类别、价格、产品和促销定价规则）。

  执行任何这些任务时，都会自动清除清漆。

- 维护源代码。

  您应刷新缓存，并定期删除`generated/code`和`generated/metadata`目录中的所有内容。 有关刷新缓存的信息，请参阅下一部分。

## 配置Commerce以清除清漆

在使用[`magento setup:config:set`](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/cli-reference/commerce-on-premises#setupconfigset)命令配置清漆主机后，Commerce会清除清漆主机。

您可以使用可选参数`--http-cache-hosts`参数指定以逗号分隔的Varnish主机和侦听端口列表。 配置所有Varnish主机，无论您拥有一个还是多个。 （不要使用空格字符分隔主机。）

参数格式必须为`<hostname or ip>:<listen port>`，如果它是端口80，则可以省略`<listen port>`。

例如，

```shell
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

然后，当您在Admin中刷新Commerce缓存（也称为&#x200B;*清理*&#x200B;缓存）或使用命令行时，可以清除Varnish主机。

要使用管理员刷新缓存，请单击&#x200B;**[!UICONTROL SYSTEM]** >工具> **缓存管理**，然后单击页面顶部的&#x200B;**刷新Magento缓存**。 （也可以刷新单个缓存类型。）

要使用命令行刷新缓存，通常使用[`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types)命令作为[文件系统所有者](../../installation/prerequisites/file-system/overview.md)。
