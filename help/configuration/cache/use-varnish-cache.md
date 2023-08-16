---
title: 使用清漆清除缓存
description: 了解缓存清除如何与Varnish配合使用以及如何将其用作Adobe Commerce应用程序的Web缓存加速器。
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# 使用清漆清除缓存

本主题讨论将Varnish用作Adobe Commerce和Magento Open Source的Web缓存加速器的基础知识。

## 清漆清除

根据 [涂漆文档](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html)， &quot;A *清除* 就是当您从缓存中选择对象并将其与其变体一起丢弃时，会出现的情况。” 清漆清除类似于缓存清除命令(或单击 **刷新Magento缓存** （在Admin中）。

事实上，当您清理、刷新或刷新Commerce缓存时，Varnish也会清除。

安装并配置Varnish以用于Commerce后，以下操作可能导致清空清空：

- 维护网站。

  例如，您在管理员中执行的任何操作：

   - **商店** > **设置** > **配置** >常规> **常规**
   - **商店** > **设置** > **配置** >常规> **货币设置**
   - **商店** > **设置** > **配置** >常规> **存储电子邮件地址**

  当Commerce检测到此类更改时，将显示一条消息，通知您刷新缓存。

- 维护商店（例如，添加或编辑类别、价格、产品和促销定价规则）。

  执行任何这些任务时，都会自动清除清漆。

- 维护源代码。

  您应该刷新缓存，并定期删除 `generated/code` 和 `generated/metadata` 目录。 有关刷新缓存的信息，请参阅下一部分。

## 配置Commerce清除清漆

使用配置清漆主机后，Commerce会清除清漆主机 [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#setupconfigset) 命令。

您可以使用可选参数 `--http-cache-hosts` 用于指定清漆主机和监听端口的逗号分隔列表的参数。 配置所有Varnish主机，无论您拥有一个还是多个。 （不要使用空格字符分隔主机。）

参数格式必须为 `<hostname or ip>:<listen port>`，可忽略 `<listen port>` 如果是端口80。

例如，

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

然后，您可以在刷新Commerce缓存时清除Varnish主机(也称为 *清理* 缓存)，或使用命令行。

要使用“管理员”刷新缓存，请单击 **[!UICONTROL SYSTEM]** >工具> **缓存管理**，然后单击 **刷新Magento缓存** 页面顶部的。 （也可以刷新单个缓存类型。）

要使用命令行刷新缓存，通常使用 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) 命令作为 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).
