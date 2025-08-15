---
title: 配置搜索停用词
description: 了解如何使用CSV文件管理Adobe Commerce的停用词。
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# 配置搜索停用词

通常，_非索引字_&#x200B;是搜索引擎在处理文本后过滤掉的常用字。 最初，当磁盘空间和内存极其有限时，每保存1 KB就意味着显着提高了性能。 因此，搜索引擎通过忽略某些词语和保持较小的索引来实现性能提升。

尽管我们今天拥有更多存储，但性能仍然很重要。 与其他搜索引擎一样，Elasticsearch和OpenSearch仍使用停用词来提高性能。

您必须使用位于`<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`目录或`<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`目录中的CSV文件管理停用词，具体取决于您安装Commerce软件的方式。

有关Elasticsearch和OpenSearch如何使用停用词的更多信息，请参阅以下资源：

- [停止词：性能与Precision之比较](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [非索引字的优点和缺点](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [使用停用词](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [停用词和性能](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## 配置停用词

非索引字位于`<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`目录中。 Adobe Commerce随附一个CSV文件，其中包含默认区域设置的停用词，以及另一个文件`stopwords.csv`，其中包含其他CSV文件未表示的任何区域设置的停用词。

非索引字文件缓存的默认生命周期为15分钟。

### 编辑现有区域设置的停用词

**要编辑停用词**：

1. 登录到您的Commerce服务器或切换到[文件系统所有者](../../installation/prerequisites/file-system/overview.md)。
1. 使用文本编辑器在`<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`目录中打开停用词文件。

   CSV文件使用命名约定`stopwords_<locale_code>.csv`。 例如，德语非索引字文件名为`stopwords_de_DE.csv`。

1. 在文件中添加单词、删除单词或更改单词。

   （文件中的每个停用词都从新行开始。）

1. 保存更改并退出文本编辑器。
1. 清除配置缓存。

   - 管理员： **系统** >工具> **缓存管理**。 选中“**配置**”复选框，并从其上方的列表中单击“**刷新**”。 单击&#x200B;**提交**&#x200B;以完成操作。

   - 命令行：作为文件系统所有者，输入以下命令：

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. 在您的店面中搜索词语以检查结果。

### 为新区域设置创建非索引字

**要为区域设置**&#x200B;添加非索引字：

1. 登录到您的Commerce服务器或切换到[文件系统所有者](../../installation/prerequisites/file-system/overview.md)。

1. 使用文本编辑器在`stopwords_<locale_code>.csv`目录中创建名为`<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`的停用词文件。

   例如，要为意大利语言环境创建非索引字，请命名文件`stopwords_it_IT.csv`。

1. 在停用词文件中，确保每个停用词位于单独的一行上。
1. 保存更改并退出文本编辑器。
1. 在同一目录中，在文本编辑器中打开`esconfig.xml`。
1. 按如下方式向`esconfig.xml`添加一行：

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   例如，要添加意大利语非索引字文件，请添加以下行：

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. 将更改保存到`esconfig.xml`并退出文本编辑器。
1. 清除配置缓存。

   - 管理员： **系统** >工具> **缓存管理**。 选中“**配置**”复选框，并从其上方的列表中单击“**刷新**”。 单击&#x200B;**提交**&#x200B;以完成操作。

   - 命令行：作为文件系统所有者，输入以下命令：

     ```bash
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. 在您的店面中搜索词语以检查结果。

## 更改非索引字目录

本节讨论如何从下列选项之一更改默认非索引字目录（可选）：

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

此位置取决于您安装Commerce软件的方式。 如果您克隆了Magento 2 GitHub存储库，则路径位于`app/code`下。 如果您安装了压缩存档或中继，则路径位于`vendor`下。

**要更改目录**：

1. 作为文件系统所有者，在文本编辑器中打开Elasticsearch `di.xml`。

   如果您克隆了存储库，则该存储库位于`app/code/Magento/Elasticsearch/etc/di.xml`

   如果您有存档或中继，则它位于`vendor/magento/module-elasticsearch/etc/di.xml`

1. 将`stopwordsDirectory`的值更改为所需的目录：

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. 将更改保存到`di.xml`并退出文本编辑器。

## 从模块中更改目录

1. [创建模块](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. 在模块`etc/di.xml`中添加说明：

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. 在模块中，创建目录`etc/stopwords`以及相应的CSV文件。

1. 将更改保存到`di.xml`并退出文本编辑器。
