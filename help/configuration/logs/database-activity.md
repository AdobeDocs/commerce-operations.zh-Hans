---
title: 记录数据库活动
description: 配置Commerce以使用Logger界面记录数据库活动。
feature: Configuration, Logs, Storage
exl-id: 2487c5ec-a01e-4d87-bc5e-c33643b032df
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# 记录数据库活动

以下示例显示如何使用[`Magento\Framework\DB\LoggerInterface`][interface]记录数据库活动，该应用程序有两种实现：

- 不记录任何内容（默认）： [`Magento\Framework\DB\Logger\Quiet`][quiet]
- `var/log`目录的日志： [`Magento\Framework\DB\Logger\File`][file]

>[!TIP]
>
>您可以使用Commerce CLI [启用和禁用数据库日志记录](../cli/enable-logging.md#database-logging)。

要更改`\Magento\Framework\DB\Logger\LoggerProxy`的默认配置，请编辑您的`app/etc/di.xml`。

首先，将`loggerAlias`和`logCallStack`参数的默认值更改为：

```xml
<type name="Magento\Framework\DB\Logger\LoggerProxy">
    <arguments>
        <argument name="loggerAlias" xsi:type="const">Magento\Framework\DB\Logger\LoggerProxy::LOGGER_ALIAS_FILE</argument>
        <argument name="logAllQueries" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_LOG_EVERYTHING</argument>
        <argument name="logQueryTime" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_QUERY_TIME_THRESHOLD</argument>
        <argument name="logCallStack" xsi:type="boolean">false</argument>
    </arguments>
</type>
```

之后，提供`Magento\Framework\DB\Logger\File`的文件路径：

```xml
<type name="Magento\Framework\DB\Logger\File">
    <arguments>
        <argument name="debugFile" xsi:type="string">log/db.log</argument>
    </arguments>
</type>
```

最后，使用编译代码：

```bash
bin/magento setup:di:compile
```

并通过以下方式清理缓存：

```bash
bin/magento cache:clean
```

<!-- link definitions -->

[file]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/File.php
[interface]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/LoggerInterface.php
[quiet]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/Quiet.php
