---
title: “[!DNL Data Migration Tool]技术规范”
description: 了解 [!DNL Data Migration Tool] 的实现详细信息以及在Magento1和Magento2之间传输数据时如何扩展。
exl-id: fec3ac3a-dd67-4533-a29f-db917f54d606
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '2098'
ht-degree: 0%

---

# [!DNL Data Migration Tool]技术规范

本节介绍[!DNL Data Migration Tool]实现详细信息以及如何扩展其功能。

## 存储库

要访问[!DNL Data Migration Tool]源代码，请参阅GitHub [存储库](https://github.com/magento/data-migration-tool)。

## 系统要求

[!DNL Data Migration Tool]的[系统要求](../../installation/system-requirements.md)与Magento2相同。

## 内部结构

### 目录结构

下图表示[!DNL Data Migration Tool]的目录结构：

```terminal
├── etc                                    --- all configuration files
│   ├── opensource-to-opensource            --- configuration files for migration from Magento Open Source 1 to Magento Open Source 2
│   │   ├── 1.9.1.1
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── 1.9.2.0
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── ........
│   │   ├── class-map.xml.dist
│   │   ├── deltalog.xml.dist
│   │   └── settings.xml.dist
│   │   ├── ........
│   ├── opensource-to-commerce              --- configuration files for migration from Magento Open Source 1 to Adobe Commerce 2
│   ├── commerce-to-commerce                --- configuration files for migration from Adobe Commerce 1 to Adobe Commerce 2
│   ├── class-map.xsd
│   ├── config.xsd
│   ├── map.xsd
│   └── settings.xsd
├── src
│   └── Migration
│       ├── App                             --- application framework
│       ├── Console
│       ├── Handler                         --- handlers are used by map files
│       │   ├── AbstractHandler.php
│       │   ├── AddPrefix.php
│       │   ├── ConvertIp.php
│       │   ├── ........
│       ├── Logger
│       ├── Reader
│       ├── Mode
│       │   ├── AbstractMode.php
│       │   ├── Data.php
│       │   ├── Delta.php
│       │   └── Settings.php
│       ├── ResourceModel                   --- contains adapter for connection to data storage and classes to work with structured data
│       │   ├── Adapter
│       │   │   └── Mysql.php
│       │   ├── AbstractCollection.php
│       │   ├── AbstractResource.php
│       │   ├── AdapterInterface.php
│       │   ├── Destination.php
│       │   ├── Document.php
│       │   ├── Record.php
│       │   ├── Source.php
│       │   └── Structure.php
│       ├── Config.php
│       ├── Exception.php
│       └── Step                            --- functionality for migrating specific data
│           ├── Eav
│           │   ├── Data.php
│           │   ├── Helper.php
│           │   ├── InitialData.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── Map
│           │   ├── Data.php
│           │   ├── Delta.php
│           │   ├── Helper.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── UrlRewrite
│           │   ├── Version11300to2000.php
│           │   ├── Version11410to2000.php
│           │   └── Version191to2000.php
│           ├── ..........
└── tests
    ├── integration
    ├── static
    └── unit
```

## 入口点

运行迁移进程的脚本位于： `magento-root/bin/magento`。

## 配置

配置`config.xsd`文件的架构位于`etc/`目录中。 为Magento1.x的每个版本创建默认配置文件(`config.xml.dist`)。它位于`etc/`下的单独目录中。

默认配置文件可由自定义配置文件替换（请参阅[命令语法](migrate-data/overview.md#command-syntax)）。

配置文件具有以下结构：

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="settings">
        <step title="Settings step">
            <integrity>Migration\Step\Settings</integrity>
            <data>Migration\Step\Settings</data>
        </step>
    </steps>
    <steps mode="data">
        <step title="Map step">
            <integrity>Migration\Step\Map\Integrity</integrity>
            <data>Migration\Step\Map\Data</data>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <steps mode="delta">
        <step title="Map step">
            <delta>Migration\Step\Map\Delta</delta>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <source>
        <database host="localhost" name="magento1" user="root" password=""/>
    </source>
    <destination>
        <database host="localhost" name="magento2" user="root" password=""/>
    </destination>
    <options>
        <map_file>map-file.xml</map_file>
        <settings_map_file>settings-map-file.xml</settings_map_file>
        <bulk_size>100</bulk_size>
        <custom_option>custom_option_value</custom_option>
        <source_prefix />
        <dest_prefix />
        ...
    </options>
</config>
```

* 步骤 — 描述迁移期间处理的所有步骤

* 源 — 数据源的配置。 可用的源类型：数据库

* 目标 — 数据目标的配置。 可用的目标类型：数据库

* 选项 — 参数列表。 包含必需(map_file、settings_map_file、bulk_size)和可选(custom_option、resource_adapter_class_name、prefix_source、prefix_dest、log_file)参数

在数据库表中安装了带有前缀的Magento时更改前缀选项。 可以为Magento1和Magento2数据库设置此值。 请相应地使用“source_prefix”和“dest_prefix”配置选项。

可使用`\Migration\Config`类访问配置数据。

## 步骤可用操作

| 文档 | 字段 |
|---|---|
| `step` | Steps节点中的第二级节点。 必须在`title`属性中指定相关步骤的描述。 |
| `integrity` | 指定负责完整性检查的PHP类。 比较表字段名称、类型和其他信息，以验证Magento1和2数据结构之间的兼容性。 |
| `data` | 指定负责数据检查的PHP类。 将数据逐表从Magento1传输到Magento2。 |
| `volume` | 指定负责卷检查的PHP类。 比较表之间的记录数以验证传输是否成功。 |
| `delta` | 指定负责增量检查的PHP类。 完全数据迁移后，将增量从Magento1传输到Magento2。 |

## Source数据库信息属性

| 文档 | 字段 | 必需？ |
|---|---|---|
| `name` | Magento1服务器的数据库名称。 | 是 |
| `host` | 主机1服务器的MagentoIP地址。 | 是 |
| `port` | Magento1服务器的端口号。 | 否 |
| `user` | Magento1数据库服务器的用户名。 | 是 |
| `password` | Magento1数据库服务器的口令。 | 是 |
| `ssl_ca` | SSL证书颁发机构文件的路径。 | 否 |
| `ssl_cert` | SSL证书文件的路径。 | 否 |
| `ssl_key` | SSL密钥文件的路径。 | 否 |

## 目标数据库信息属性

| 文档 | 字段 | 必需？ |
|---|---|---|
| `name` | Magento2服务器的数据库名称。 | 是 |
| `host` | Magento2服务器的主机IP地址。 | 是 |
| `port` | Magento2服务器的端口号。 | 否 |
| `user` | Magento2数据库服务器的用户名。 | 是 |
| `password` | Magento2数据库服务器的口令。 | 是 |
| `ssl_ca` | SSL证书颁发机构文件的路径。 | 否 |
| `ssl_cert` | SSL证书文件的路径。 | 否 |
| `ssl_key` | SSL密钥文件的路径。 | 否 |

## 使用TLS协议连接

您还可以使用TLS协议（即使用公共/专用加密密钥）连接到数据库。 将以下可选属性添加到`database`元素：

* `ssl_ca`
* `ssl_cert`
* `ssl_key`

例如：

```xml
<source>
    <database host="localhost" name="magento1" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</source>
<destination>
    <database host="localhost" name="magento2" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</destination>
```

## 步骤内部

迁移过程包括几个步骤。

步骤是一个单元，它提供迁移某些分隔数据所需的功能。 步骤可以包含一个或多个阶段（完整性检查、数据、卷检查和增量）。

默认情况下，有几个步骤（[映射](#map-step)、[EAV](#eav)、[URL重写](#url-rewrite-step)等）。 您也可以选择添加自己的步骤。

步骤相关类位于src/Migration/Step目录中。

要执行Step类，必须在config.xml文件中定义该类。

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="mode_name">
        <step title="Step Name">
            <integrity>Migration\Step\StepName\Integrity</integrity>  <!-- integrity check stage of the step -->
            <data>Migration\Step\StepName\Data</data>
            <volume>Migration\Step\StepName\Volume</volume>
        </step>
        ...
    </steps>
    ...
</config>
```

每个阶段类都必须实现StageInterface。

```php
class StageClass implements StageInterface
{
  /**
   * Perform the stage
   *
   * @return bool
   */
  public function perform()
  {
  }
}
```

如果数据阶段支持回滚，则它应该实现`RollbackInterface`接口。

运行步骤的可视化图表由Symfony的ProgressBar组件提供（请参阅[进度条](https://symfony.com/doc/current/components/console/helpers/progressbar.html)）。 以LogLevelProcessor的身份在步骤中访问此组件。

主要使用方法有：

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## 步骤阶段

### 完整性检查

每个步骤都必须检查数据源的结构(默认为Magento1)和数据目标(Magento2)的结构是否兼容。 如果不兼容 — 对于不兼容的实体会显示错误。 如果字段具有不同的数据类型(同一字段在Magento1中具有十进制数据类型，在Magento2中具有整数)，则会显示警告消息（除非该字段包含在映射文件中）。

### 数据传输

如果完整性检查通过，则正在传输数据。 如果出现错误，则回滚运行以恢复Magento2的上一个状态。 如果步骤类实现`RollbackInterface`接口，则在出现错误时执行回滚方法。

### 音量检查

在迁移数据之后，“卷检查”会提供附加检查，以检查是否正确传输了所有数据。

### 增量投放

增量功能负责交付主迁移后添加的其余数据。

## 运行模式

该工具应按特定顺序以三种不同的模式运行：

1. 设置 — 迁移系统设置
1. 数据 — 主要数据迁移
1. delta — 迁移主迁移后添加的其余数据

每种模式都有各自要执行的步骤列表。 请参阅config.xml

### 设置迁移模式

此工具的设置迁移模式用于传输以下实体：

1. 网站、商店、商店视图。
1. 存储配置（主要是在M2中存储 — >配置，或在M1中存储 — >配置）

所有存储配置将其数据保存在数据库的core_config_data表中。 settings.xml文件包含适用于此表的规则，这些规则在迁移过程中应用。 此文件描述应忽略、重命名或更改其值的设置。 settings.xml文件具有以下结构：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="settings.xsd">
    <key>
        <ignore>
            <path>path/to/ignore*</path>
        </ignore>
        <rename>
            <path>path/to/rename</path>
            <to>new/path/renamed</to>
        </rename>
    <key>
    <value>
        <transform>
            <path>some/key/to/change</path>
            <handler class="Some\Handler\Class"/>
        </transform>
    </value>
</settings>
```

在节点`<key>`下，有一些规则可与`core_config_data`表中的“path”列一起使用。 `<ignore>`规则阻止工具传输某些设置。 可在此节点中使用通配符。 `<ignore>`节点中未列出的所有其他设置都将迁移。 如果设置的路径在Magento2中发生更改，则应将其添加到`//key/rename`节点，其中旧路径在`//key/rename/path`节点中指示，新路径在`//key/rename/to`节点中指示。

在节点`<value>`下，有一些规则可与`core_config_data`表中的“value”列一起使用。 这些规则旨在通过处理程序（实现`Migration\Handler\HandlerInterface`的类）转换设置的值，并将其调整为Magento2。

### 数据迁移模式

在此模式下，将迁移大部分数据。 在数据迁移之前，将为每个步骤运行完整性检查阶段。 如果完整性检查通过，[!DNL Data Migration Tool]将向Magento1数据库安装deltalog表（前缀为`m2_cl_*`）和相应的触发器，并运行步骤的数据迁移阶段。 当迁移完成且无错误时，卷检查将检查数据一致性。 如果迁移实时存储，则可能会显示警告消息。 不用担心，增量迁移会处理这些增量数据。 最有价值的迁移步骤是映射、URL重写和EAV。

#### 映射步骤

映射步骤负责将大部分数据从Magento1传输到Magento2。 此步骤从map.xml文件（位于`etc/`目录）中读取说明。 该文件描述了源(Magento1)和目标(Magento2)的数据结构之间的差异。 如果Magento1包含属于Magento2中不存在的某个扩展的表或字段，则可以将这些实体放置在此处，以按映射步骤忽略它们。 否则，它将显示错误消息。

映射文件的格式如下：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="map.xsd">
    <source>
        <document_rules>
            <ignore>
                <document>some_document2</document>
            </ignore>
            <rename>
                <document>some_document</document>
                <to>some_dest_document</to>
            </rename>
            <log_changes>
                <document key="primary_key">some_dest_document</document>
            </log_changes>
        </document_rules>

        <field_rules>
            <move>
                <field>some_document1.field1</field>
                <to>some_document1.field2</to>
            </move>
            <ignore>
                <field>some_document3.field8</field>
            </ignore>
            <transform>
                <field>some_document1.field1</field>
                <handler class="\Migration\Handler\Convert">
                    <param name="map" value="[value1:value2;value3:value4;value5:value6;]" />
                </handler>
            </transform>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>some_document8</document>
            </ignore>
        </document_rules>

        <field_rules>
            <transform>
                <field>some_document5.field3</field>
                <handler class="\Migration\Handler\SetValue">
                    <param name="value" value="10" />
                </handler>
            </transform>
        </field_rules>
    </destination>
</map>
```

区域：

* *源* — 包含源数据库的规则

* *目标* — 包含目标数据库的规则

选项：

* *忽略* — 忽略使用此选项标记的文档、字段或数据类型

* *重命名* — 描述具有不同名称的文档之间的名称关系。 如果目标文档名称与源文档名称不同，您可以使用重命名选项来设置与目标表名称类似的源文档名称

* *移动* — 设置将指定字段从源文档移动到目标文档的规则。 注意：目标文档名称应与源文档名称相同。 如果源文档名称与目标文档名称不同 — 需要对包含已移动字段的文档使用重命名选项

* *转换* — 是一个允许用户根据处理程序中描述的行为迁移字段的选项

* *处理程序* — 描述字段的转换行为。 要调用处理程序，您需要在`<handler>`标记中指定处理程序类名称。 将`<param>`标记与参数名称和值数据一起使用，以将其传递给处理程序

**Source**&#x200B;可用操作：

| 文档 | 字段 |
|--- |--- |
| 忽略重命名 | 忽略移动转换 |

**目标**&#x200B;可用操作：

| 文档 | 字段 |
|--- |--- |
| 忽略 | 忽略转换 |

#### 通配符

若要忽略具有相似部件(`document_name_1`， `document_name_2`)的文档，您可以使用通配符功能。 放入`*`符号而不是重复部分(`document_name_*`)，此掩码覆盖符合此掩码的所有源文档或目标文档。

#### URL重写步骤

此步骤比较复杂，因为在Magento1中开发的许多算法与Magento2不兼容。 对于Magento1的不同版本，可以有不同的算法。 因此，在Step/UrlRewrite文件夹下，有一些为某些特定版本的Magento开发的类，Migration\Step\UrlRewrite\Version191to2000就是其中之一。 它可以将URL重写数据从Magento1.9.1传输到Magento2。

#### EAV步骤

此步骤会将所有属性（产品、客户、RMA）从Magento1转移到Magento2。 它使用map-eav.xml文件，其中包含与map.xml文件中的规则相似的规则，用于特定情况下处理数据。

在此步骤中处理的一些表：

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### 增量迁移模式

主迁移后，其他数据可能已添加到Magento1数据库中（例如，由店面的客户添加）。 为了跟踪此数据，工具会在迁移过程的开始阶段为表设置数据库触发器。 有关详细信息，请参阅[迁移由第三方扩展创建的数据](migrate-data/delta.md#migrate-data-created-by-third-party-extensions)。

## 数据源

要访问Magento1和Magento2的数据源并操作其数据（选择、更新、插入、删除），资源文件夹中有许多类。 Migration\ResourceModel\Source和Migration\ResourceModel\Destination是主类。 所有迁移步骤都使用它来操作数据。 此数据包含在Migration\ResourceModel\Document、Migration\ResourceModel\Record、Migration\ResourceModel\Structure等类中。

以下是这些类的类图：

![迁移工具数据结构](../../assets/data-migration/MmigrationToolDataStructure.png)

## 记录

为了实现迁移过程的输出并控制所有可能的级别，在Magento中使用了PSR记录器。 已实现`\Migration\Logger\Logger`类以提供日志记录功能。 要使用记录器，应通过构造函数依赖项注入来注入记录器。

```php
class SomeClass
{
    ...
    protected $logger;

    public function __construct(\Migration\Logger\Logger $logger)
    {
        $this->logger = $logger;
    }
    ...
}
```

之后，您可以使用此类来记录某些事件：

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

可以自定义日志信息的写入位置。 为此，您可以使用记录器的pushHandler()方法将处理程序添加到记录器。 每个处理程序都应实现`\Monolog\Handler\HandlerInterface`接口。 就目前而言，有两个处理程序：

* ConsoleHandler：将消息写入控制台

* FileHandler：将消息写入已在“log_file”配置选项中设置的日志文件

此外，还可以实施任何其他处理程序。 Magento框架中有一组处理程序。 向记录器添加处理程序的示例：

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

要为记录器设置附加数据（当前模式、表名称），您可以使用记录器处理器。 有一个现有的处理器(MessageProcessor)。 创建该插件是为了添加用于记录消息的“额外”数据，并在每次执行log方法时调用。 MessageProcessor已保护$extra var，其中包含空的“mode”、“stage”、“step”和“table”值。 额外数据可以作为log方法的第二个参数（上下文）传递给处理器。 当前以AbstractStep->runStage（将当前模式、阶段和步骤传递到处理器）方法向处理器发送的数据集以及使用logger->debug方法（传递迁移表名称）的数据类。 将处理器添加到记录器的示例：

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

可以设置详细级别。 就目前而言，有三个层次：

* `ERROR` （仅将错误写入日志）
* `INFO` （只将重要信息写入日志，默认值）
* `DEBUG` （已写入所有内容）

可以通过调用`setLevel()`方法为每个处理程序分别设置详细日志级别。 如果要通过命令行参数设置详细级别，则应该在应用程序启动时更改“verbose”选项。

您可以使用单色格式化程序格式化日志消息。 要使格式化程序功能正常工作，必须使用`setFormatter()`方法指定日志处理程序。 目前，我们有一个格式化程序类(`MessageFormatter`)，它在消息处理期间（通过从处理程序执行的`format()`方法）设置特定格式（取决于详细程度级别）。

在`Migration\Logger\Manager`类的`process()`方法中执行操作记录器（添加处理程序和处理器）和详细模式处理。 方法是在应用程序启动时调用的。

## 自动测试

[!DNL Data Migration Tool]中有三种类型的测试：

* 静态
* 单位
* 集成

它们位于工具的`tests/`目录中，这与测试类型相同（单元测试位于`tests/unit`目录中）。 要启动测试，应安装phpunit。 将当前目录更改为测试目录并启动phpunit。 例如：

```bash
[10:32 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool]-[git master]
$ cd tests/unit
```

```bash
[10:33 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool/tests/unit]-[git master]
$ phpunit
PHPUnit 8.1.0 by Sebastian Bergmann.
....
```
