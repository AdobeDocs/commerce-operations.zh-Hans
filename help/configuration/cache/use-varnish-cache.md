---
title: 使用清漆清除缓存
description: 了解缓存清除如何与Riket配合使用，以及如何将其用作Adobe Commerce应用程序的Web缓存加速器。
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---


# 使用清漆清除缓存

本主题讨论了将Quiset用作Adobe Commerce和Magento Open Source的Web缓存加速器的基础知识。

## 清漆清洗

根据 [清漆文档](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;A *清除* 当你从 [缓存](https://glossary.magento.com/cache) 并随变体一起丢弃。” 清漆清除类似于缓存清除命令(或单击 **刷新Magento缓存** )。

事实上，当您清理、刷新或刷新商务缓存时，清漆也会清除。

安装并配置清漆以与Commerce一起使用后，以下操作可能会导致清漆清除：

- 维护 [网站](https://glossary.magento.com/website).

   例如，您在的“管理员”中执行的任何操作：

   - **商店** > **设置** > **配置** >常规> **常规**
   - **商店** > **设置** > **配置** >常规> **货币设置**
   - **商店** > **设置** > **配置** >常规> **存储电子邮件地址**

   当商务检测到此类更改时，将显示一条消息，通知您刷新缓存。

- 维护商店（例如，添加或编辑类别、价格、产品和促销定价规则）。

   在执行任何这些任务时，清漆会自动清除。

- 维护源代码。

   您应该刷新缓存，并定期删除 `generated/code` 和 `generated/metadata` 目录。 有关刷新缓存的信息，请参阅下一节。

## 配置商务以清除清漆

在使用配置清漆主机后，商务清除清漆主机 [`magento setup:config:set`](https://devdocs.magento.com/guides/2.4/install-gde/install/cli/install-cli-subcommands-deployment.html) 命令。

您可以使用可选参数 `--http-cache-hosts` 参数，指定以逗号分隔的清漆主机和侦听端口列表。 配置所有清漆主机，无论您有一个还是多个清漆主机。 （请勿将主机分隔为空格字符。）

参数格式必须为 `<hostname or ip>:<listen port>`，在这里 `<listen port>` 如果是端口80。

例如，

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

然后，在刷新商务缓存时，您可以清除清漆主机(也称为 *清洁* 缓存)或使用命令行。

要使用管理员刷新缓存，请单击 **[!UICONTROL SYSTEM]** >工具> **缓存管理**，然后单击 **刷新Magento缓存** 的双曲余切值。 （您还可以刷新单个缓存类型。）

要使用命令行刷新缓存，通常使用 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) 命令 [文件系统所有者](https://devdocs.magento.com/guides/2.4/install-gde/prereq/file-sys-perms-over.html).
