---
title: 日志数据库活动
description: 配置商务以使用记录器界面记录数据库活动。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# 日志数据库活动

以下示例显示如何使用 [`Magento\Framework\DB\LoggerInterface`][interface]，其中具有两个实施：

- 未记录任何内容（默认）： [`Magento\Framework\DB\Logger\Quiet`][quiet]
- 登录到 `var/log` 目录： [`Magento\Framework\DB\Logger\File`][file]

>[!TIP]
>
>您可以使用Commerce CLI [启用和禁用数据库日志记录](../cli/enable-logging.md#database-logging).

更改的默认配置 `\Magento\Framework\DB\Logger\LoggerProxy`，编辑 `app/etc/di.xml`.

首先，更改 `loggerAlias` 和 `logCallStack` 参数为：

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

之后，提供 `Magento\Framework\DB\Logger\File`:

```xml
<type name="Magento\Framework\DB\Logger\File">
    <arguments>
        <argument name="debugFile" xsi:type="string">log/db.log</argument>
    </arguments>
</type>
```

最后，使用以下方法编译代码：

```bash
bin/magento setup:di:compile
```

然后，使用以下方法清理缓存：

```bash
bin/magento cache:clean
```

<!-- link definitions -->

[file]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/File.php
[interface]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/LoggerInterface.php
[quiet]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/Quiet.php
