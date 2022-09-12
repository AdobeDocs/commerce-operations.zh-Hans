---
title: 配置搜索秒词
description: 了解如何使用CSV文件管理Adobe Commerce的秒数。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---


# 配置搜索秒词

总的来说， _秒词_ 是搜索引擎在处理文本后过滤掉的常用词。 最初，当磁盘空间和内存极其有限时，每节省一千字节就意味着性能显着提高。 因此，搜索引擎通过忽略某些词语和保持索引较小来获得性能提升。

尽管我们现在有更多的存储，但性能仍然很重要。 Elasticsearch和OpenSearch与其他搜索引擎一样，仍使用秒词来提高性能。

您必须使用位于 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 目录或 `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` 目录，具体取决于您安装商务软件的方式。

有关Elasticsearch和OpenSearch如何使用秒词的更多信息，请参阅以下资源：

- [秒数：性能与精度比较](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [词的利弊](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [使用秒数](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [秒数和性能](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## 配置秒数

停止字位于 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 目录访问Advertising Cloud的帮助。 Adobe Commerce和Magento Open Source附带一个CSV文件，其中包含默认区域设置的停止语言，并且还附加一个文件： `stopwords.csv`，该字段包含任何不由其他CSV文件表示的区域设置的秒数。

秒词文件的默认生命周期 [缓存](https://glossary.magento.com/cache) 15分钟。

### 编辑现有区域设置的秒数

**编辑秒数**:

1. 登录到您的Commerce服务器，或切换到 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).
1. 使用文本编辑器在 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 目录访问Advertising Cloud的帮助。

   CSV文件使用命名约定 `stopwords_<locale_code>.csv`. 例如，德语秒词文件名为 `stopwords_de_DE.csv`.

1. 在文件中添加词语、删除词语或更改词语。

   （文件中的每个停止词都从新行开始。）

1. 保存更改并退出文本编辑器。
1. 清除配置缓存。

   - 管理员： **系统** >工具> **缓存管理**. 选择 **配置** 复选框，然后在其上方的列表中单击 **刷新**. 单击 **提交** 以完成操作。

   - 命令行：作为文件系统所有者，输入以下命令：

      ```bash
      php <magento_root>/bin/magento cache:clean config
      ```

1. 通过在 [店面](https://glossary.magento.com/storefront).

### 为新区域设置创建秒数

**为区域设置添加秒数**:

1. 登录到您的Commerce服务器，或切换到 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).

1. 使用文本编辑器创建名为的秒数文件 `stopwords_<locale_code>.csv` 在 `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` 目录访问Advertising Cloud的帮助。

   例如，要为意大利语区域设置创建秒数，请将文件命名为 `stopwords_it_IT.csv`.

1. 在您的秒数文件中，确保每个秒数位于单独的行中。
1. 保存更改并退出文本编辑器。
1. 在同一目录中，打开 `esconfig.xml` 在文本编辑器中。
1. 将行添加到 `esconfig.xml` 如下所示：

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   例如，要添加意大利语的秒数文件，请添加以下行：

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. 将更改保存到 `esconfig.xml` 并退出文本编辑器。
1. 清除配置缓存。

   - 管理员： **系统** >工具> **缓存管理**. 选择 **配置** 复选框，然后在其上方的列表中单击 **刷新**. 单击 **提交** 以完成操作。

   - 命令行：作为文件系统所有者，输入以下命令：

      ```bash
      php <magento_root>/bin/magento magento cache:clean config
      ```

1. 通过在店面上搜索词来检查结果。

## 更改秒表目录

本节将讨论如何选择从以下内容之一更改默认的停止字目录：

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

位置取决于您安装商务软件的方式。 如果您克隆了Magento2 GitHub存储库，则路径位于 `app/code`. 如果安装了压缩存档或元数据包，则路径将在 `vendor`.

**更改目录**:

1. 作为文件系统所有者，打开Elasticsearch `di.xml` 在文本编辑器中。

   如果克隆了存储库，则它位于 `app/code/Magento/Elasticsearch/etc/di.xml`

   如果你有档案或元数据库，它位于 `vendor/magento/module-elasticsearch/etc/di.xml`

1. 更改 `stopwordsDirectory` 到所需目录：

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. 将更改保存到 `di.xml` 并退出文本编辑器。

## 从模块更改目录

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

1. 在您的模块中，创建目录 `etc/stopwords`，且包含相应的CSV文件。

1. 将更改保存到 `di.xml` 并退出文本编辑器。
