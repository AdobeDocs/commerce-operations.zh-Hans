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

一般来说， _停用词_ 是搜索引擎在处理文本后过滤掉的常用词。 最初，当磁盘空间和内存极其有限时，每保存1 KB就意味着显着提高了性能。 因此，搜索引擎通过忽略某些词语和保持较小的索引来实现性能提升。

尽管我们今天拥有更多存储，但性能仍然很重要。 与其他搜索引擎一样，Elasticsearch和OpenSearch仍使用停用词来提高性能。

您必须使用位于以下位置的CSV文件管理停用词： `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 目录或 `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` 目录，具体取决于您安装Commerce软件的方式。

有关Elasticsearch和OpenSearch如何使用停用词的更多信息，请参阅以下资源：

- [非索引词：性能对比精度](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [停用词的优劣](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [使用停用词](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [停用词和性能](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## 配置停用词

停用词位于 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 目录。 Adobe Commerce附带一个CSV文件，其中包含默认区域设置的停用词，以及另一个文件， `stopwords.csv`，其中包含用于表示任何区域设置的非其他CSV文件所代表的非停用词。

非索引字文件缓存的默认生命周期为15分钟。

### 编辑现有区域设置的停用词

**编辑非索引字**：

1. 登录到您的Commerce服务器，或切换到 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).
1. 使用文本编辑器在中打开停用词文件 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 目录。

   CSV文件使用命名约定 `stopwords_<locale_code>.csv`. 例如，德语停用词文件名为 `stopwords_de_DE.csv`.

1. 在文件中添加单词、删除单词或更改单词。

   （文件中的每个停用词都从新行开始。）

1. 保存更改并退出文本编辑器。
1. 清除配置缓存。

   - 管理员： **系统** >工具> **缓存管理**. 选择 **配置** 复选框，并从其上方的列表中，单击 **刷新**. 单击 **提交** 以完成操作。

   - 命令行：作为文件系统所有者，输入以下命令：

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. 在您的店面中搜索词语以检查结果。

### 为新区域设置创建非索引字

**为区域设置添加非索引字**：

1. 登录到您的Commerce服务器，或切换到 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).

1. 使用文本编辑器创建名为的停用词文件 `stopwords_<locale_code>.csv` 在 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 目录。

   例如，要为意大利语言环境创建非索引字，请命名文件 `stopwords_it_IT.csv`.

1. 在停用词文件中，确保每个停用词位于单独的一行上。
1. 保存更改并退出文本编辑器。
1. 在同一目录中，打开 `esconfig.xml` 在文本编辑器中。
1. 添加行到 `esconfig.xml` 如下所示：

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   例如，要添加意大利语非索引字文件，请添加以下行：

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. 将更改保存到 `esconfig.xml` 并退出文本编辑器。
1. 清除配置缓存。

   - 管理员： **系统** >工具> **缓存管理**. 选择 **配置** 复选框，并从其上方的列表中，单击 **刷新**. 单击 **提交** 以完成操作。

   - 命令行：作为文件系统所有者，输入以下命令：

     ```bash
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. 在您的店面中搜索词语以检查结果。

## 更改非索引字目录

本节讨论如何从下列选项之一更改默认非索引字目录（可选）：

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

此位置取决于您安装Commerce软件的方式。 如果您克隆了Magento2 GitHub存储库，则路径位于 `app/code`. 如果安装了压缩的归档文件或中继，则路径位于 `vendor`.

**更改目录**：

1. 以文件系统所有者的身份，打开Elasticsearch `di.xml` 在文本编辑器中。

   如果您克隆了存储库，则该存储库位于 `app/code/Magento/Elasticsearch/etc/di.xml`

   如果您有存档或中继，则它位于 `vendor/magento/module-elasticsearch/etc/di.xml`

1. 更改的值 `stopwordsDirectory` 到所需的目录：

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. 将更改保存到 `di.xml` 并退出文本编辑器。

## 从模块中更改目录

1. [创建模块](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. 在您的模块中 `etc/di.xml` 添加说明：

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. 在模块中，创建目录 `etc/stopwords`，以及相应的CSV文件。

1. 将更改保存到 `di.xml` 并退出文本编辑器。
