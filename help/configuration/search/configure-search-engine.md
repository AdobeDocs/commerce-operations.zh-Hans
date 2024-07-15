---
title: 搜索引擎配置
description: 为Adobe Commerce的内部部署配置搜索引擎。
feature: Configuration, Search
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# 搜索引擎配置

此部分讨论使用Adobe Commerce的内部部署测试Elasticsearch或OpenSearch时必须选择的最低设置。

>[!TIP]
>
>在版本2.4.4和2.4.3-p2中，标记为&#x200B;**Elasticsearch**的所有字段也适用于OpenSearch。
>当版本2.4.6中引入对Elasticsearch8.x的支持时，创建了新标签以区分Elasticsearch配置和OpenSearch配置。

有关配置搜索引擎的其他详细信息，请参阅[用户指南](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html)。

## 从管理员配置搜索引擎

>[!TIP]
>
>有关升级到新搜索引擎版本的说明，请参阅[升级先决条件](../../upgrade/prepare/prerequisites.md)。

要将系统配置为使用Elasticsearch或OpenSearch：

1. 以管理员身份登录到管理员。
1. 单击&#x200B;**[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**。
1. 从&#x200B;**[!UICONTROL Search Engine]**&#x200B;列表中，选择搜索引擎的相应版本。

   下表列出了配置和测试与Commerce的连接所需的选项。 除非您更改了搜索引擎的服务器设置，否则默认设置应该有效。 跳至下一步。

   | 选项 | 描述 |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | 输入运行Elasticsearch或OpenSearch的计算机的完全限定主机名或IP地址。云基础架构上的<br>Adobe Commerce：从集成系统中获取此值。 |
   | **[!UICONTROL Server Port]** | 输入Web服务器代理端口。 云基础架构上的默认值为9200<br>Adobe Commerce：从集成系统中获取此值。 |
   | **[!UICONTROL Index Prefix]** | 输入搜索引擎索引前缀。 如果您将单个实例用于多个Commerce安装（暂存环境和生产环境），则必须为每个安装指定一个唯一的前缀。 否则，您可以使用默认前缀magento2。 |
   | **[!UICONTROL Enable HTTP Auth]** | 仅当为搜索引擎服务器启用了身份验证时，才单击&#x200B;**[!UICONTROL Yes]**。 如果存在，请在提供的字段中提供用户名和密码。 |
   | **[!UICONTROL Server Timeout]** | 输入尝试建立与Elasticsearch或OpenSearch服务器的连接时等待的时间（以秒为单位）。 |

1. 单击&#x200B;**[!UICONTROL Test Connection]**。

   示例响应：

   ![成功](../../assets/configuration/elastic_test-success.png)

   继续：

   - [为搜索引擎配置Apache](../../installation/prerequisites/search-engine/configure-apache.md)
   - [为搜索引擎配置nginx](../../installation/prerequisites/search-engine/configure-nginx.md)

   或者您会看到：

   ![失败](../../assets/configuration/elastic_test-fail.png)

如果是这样，请尝试以下操作：

- 确保搜索引擎服务器正在运行。
- 如果服务器与Commerce不在同一台主机上，请登录到Commerce服务器，然后ping搜索引擎主机。 解决网络连接问题并再次测试连接。
- 检查启动Elasticsearch的命令窗口或OpenSearch以查找栈栈跟踪和异常。 您必须先解决这些问题，然后才能继续。 特别是，请确保您以具有`root`权限的用户身份启动搜索引擎。
- 请确保[UNIX防火墙和SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux)均已禁用，或设置规则以使您的搜索引擎和Commerce能够相互通信。
- 验证&#x200B;**[!UICONTROL Server Hostname]**&#x200B;字段的值。 确保服务器可用。 您可以改为尝试服务器的IP地址。
- 使用`netstat -an | grep <listen-port>`命令验证&#x200B;**[!UICONTROL Server Port]**&#x200B;字段中指定的端口是否未被其他进程使用。

  例如，要查看您的搜索引擎是否在其默认端口上运行，请使用以下命令：

  ```bash
  netstat -an | grep 9200
  ```

  如果它在端口9200上运行，则显示类似以下内容：

  ```terminal
  `tcp        0      0 :::9200            :::-         LISTEN`
  ```

## 重新索引目录搜索并刷新全页缓存

更改搜索引擎配置后，必须重新索引目录搜索索引，并使用管理或命令行刷新全页缓存。

使用Admin刷新缓存：

1. 在“管理员”中，单击&#x200B;**[!UICONTROL System]** > **[!UICONTROL Cache Management]**。
1. 选中&#x200B;**[!UICONTROL Page Cache]**&#x200B;旁边的复选框。
1. 从右上角的&#x200B;**[!UICONTROL Actions]**&#x200B;列表中，单击&#x200B;**刷新**。

   ![缓存管理](../../assets/configuration/refresh-cache.png)

要使用命令行清理缓存： [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

使用命令行重新索引：

1. 以[文件系统所有者](../../installation/prerequisites/file-system/overview.md)的身份登录或切换到Commerce服务器。
1. 输入以下任何命令：

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
   >与缓存不同，索引器由cron作业更新。 在开始使用搜索引擎之前，请确保已启用[cron](../cli/configure-cron-jobs.md)。
