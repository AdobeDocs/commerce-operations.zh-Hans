---
title: 搜索引擎配置
description: 使用Adobe Commerce和Magento Open Source配置搜索引擎。
source-git-commit: 66681f06c15907a5d25e71005c27785f0745ed63
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---


# 搜索引擎配置

本节讨论在测试Elasticsearch或使用Adobe Commerce和Magento Open Source进行OpenSearch时必须选择的最低设置。 从版本2.4.4和2.4.3-p2开始，所有字段均标记为 **Elasticsearch** 也适用于OpenSearch。

有关配置搜索引擎的其他详细信息，请参阅 [用户指南](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html).

## 从管理员配置搜索引擎

要将系统配置为使用Elasticsearch或OpenSearch，请执行以下操作：

1. 以管理员身份登录。
1. 单击 **商店** >设置> **配置** > **目录** > **目录** > **目录搜索**.
1. 从 **搜索引擎** 列表，选择搜索引擎的相应版本。如果您使用OpenSearch，则必须选择Elasticsearch7。

   下表列出了配置和测试与Commerce的连接所需的配置选项。
除非您更改了搜索引擎的服务器设置，否则默认值应该有效。 跳到下一步。

   | 选项 | 描述 |
   |--- |--- |
   | **Elasticsearch服务器主机名** | 输入运行Elasticsearch或OpenSearch的计算机的完全限定的主机名或IP地址。<br>Adobe Commerce云基础架构：从集成系统中获取此值。 |
   | **Elasticsearch服务器端口** | 输入Web服务器代理端口。 默认为9200<br>Adobe Commerce云基础架构：从集成系统中获取此值。 |
   | **Elasticsearch索引前缀** | 输入搜索引擎索引前缀。 如果对多个Commerce安装（暂存和生产环境）使用单个实例，则必须为每个安装指定唯一的前缀。 否则，您可以使用默认前缀magento2。 |
   | **启用ElasticsearchHTTP身份验证** | 单击 **是** 仅当您为搜索引擎服务器启用了身份验证时。 如果是，请在提供的字段中提供用户名和密码。 |

1. 单击 **测试连接**.

   示例响应：

   ![成功](../../assets/configuration/elastic_test-success.png)

   继续：

   - [为搜索引擎配置Apache](../../installation/prerequisites/search-engine/configure-apache.md)
   - [为搜索引擎配置nginx](../../installation/prerequisites/search-engine/configure-nginx.md)

   或者您看到：

   ![失败](../../assets/configuration/elastic_test-fail.png)

如果是，请尝试以下操作：

- 确保搜索引擎服务器正在运行。
- 如果服务器位于与Commerce不同的主机上，请登录到Commerce服务器，并对搜索引擎主机执行Ping操作。 解决网络连接问题并再次测试连接。
- 检查在其中启动Elasticsearch的命令窗口或OpenSearch查找堆栈跟踪和异常。 您必须先解决这些问题，然后才能继续。 特别是，请确保您以用户身份使用 `root` 权限。
- 确保 [UNIX防火墙和SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) 都被禁用，或设置规则以使搜索引擎和商务能够相互通信。
- 验证 **Elasticsearch服务器主机名** 字段。 确保服务器可用。 您可以尝试使用服务器的IP地址。
- 使用 `netstat -an | grep <listen-port>` 命令来验证 **Elasticsearch服务器端口** 字段，而不会将其他进程使用。

   例如，要查看搜索引擎是否在其默认端口上运行，请使用以下命令：

   ```bash
   netstat -an | grep 9200
   ```

   如果它在端口9200上运行，则显示如下所示：

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## 重新索引目录搜索并刷新完整页面缓存

更改搜索引擎配置后，必须重新编入目录搜索索引索引，然后使用管理或命令行刷新全页缓存。

要使用管理员刷新缓存，请执行以下操作：

1. 在管理员中，单击 **系统** > **缓存管理**.
1. 选中旁边的复选框 **页面缓存**.
1. 从 **操作** 列表，单击 **刷新**.

   ![缓存管理](../../assets/configuration/refresh-cache.png)

要使用命令行清除缓存，请执行以下操作： [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

要使用命令行重新编入索引，请执行以下操作：

1. 作为或切换到 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).
1. 输入以下任意命令：

   输入以下命令以仅重新索引目录搜索索引：

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   输入以下命令以重新索引所有索引器：

   ```bash
   bin/magento indexer:reindex
   ```

1. 等待重新索引完成。

   >[!INFO]
   >
   >与缓存不同，索引器由cron作业更新。 确保 [启用cron](../cli/configure-cron-jobs.md) 开始使用搜索引擎之前。

