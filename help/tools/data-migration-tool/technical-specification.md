---
title: '"[!DNL Data Migration Tool] 技术规范”'
description: “了解 [!DNL Data Migration Tool] 以及在Magento1和Magento2之间传输数据时如何扩展。”
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# [!DNL Data Migration Tool] 技术规范

本节将介绍 [!DNL Data Migration Tool] 实施详细信息以及如何扩展其功能。

## 存储库

访问 [!DNL Data Migration Tool] 源代码，请参阅GitHub [存储库](https://github.com/magento/data-migration-tool).

## 系统要求

的 [系统要求](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) 对于 [!DNL Data Migration Tool] 与Magento2相同。

## 内部结构

### 目录结构

下图表示 [!DNL Data Migration Tool]:

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
│       ├── ResourceModel                   --- contains [adapter](https://glossary.magento.com/adapter) for connection to data storage and classes to work with structured data
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
│       ├── [Exception](https://glossary.magento.com/exception).php
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

运行迁移过程的脚本位于： `magento-root/bin/magento`.

## 配置

配置的架构 `config.xsd` 文件位于 `etc/` 目录访问Advertising Cloud的帮助。 默认配置文件(`config.xml.dist`)会为每个版本的Magento1.x创建。它位于 `etc/`.

默认配置文件可替换为自定义配置文件(请参阅 [命令语法](migrate-data/overview.md#command-syntax))。

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

* 步骤 — 描述迁移过程中处理的所有步骤

* 源 — 数据源配置。 可用源类型：数据库

* 目标 — 数据目标的配置。 可用目标类型：数据库

* options — 参数列表。 包含必选(map_file、settings_map_file、bulk_size)参数和可选(custom_option、resource_adapter_class_name、prefix_source、prefix_dest、log_file)参数

如果Magento在数据库表中安装了前缀，请更改前缀选项。 它可以为Magento1和Magento2数据库设置。 请相应地使用“source_prefix”和“dest_prefix”配置选项。

配置数据可通过 `\Migration\Config` 类。

## 可用操作的步骤

| 文档 | 字段 |
|---|---|
| `step` | 步骤节点内的二级节点。 必须在 `title` 属性。 |
| `integrity` | 指定负责完整性检查的PHP类。 比较表字段名称、类型和其他信息，以验证Magento1和2数据结构之间的兼容性。 |
| `data` | 指定负责数据检查的PHP类。 将数据（按表）从Magento1传输到Magento2。 |
| `volume` | 指定负责卷检查的PHP类。 比较表之间的记录数以验证传输是否成功。 |
| `delta` | 指定负责增量检查的PHP类。 在完全Magento迁移后，将增量从Magento1传输到客户2。 |

## 源数据库信息属性

| 文档 | 字段 | 必需？ |
|---|---|---|
| `name` | Magento1服务器的数据库名称。 | 是 |
| `host` | Magento1服务器的主机IP地址。 | 是 |
| `port` | Magento1服务器的端口号。 | 否 |
| `user` | Magento1数据库服务器的用户名。 | 是 |
| `password` | Magento1数据库服务器的密码。 | 是 |
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
| `password` | Magento2数据库服务器的密码。 | 是 |
| `ssl_ca` | SSL证书颁发机构文件的路径。 | 否 |
| `ssl_cert` | SSL证书文件的路径。 | 否 |
| `ssl_key` | SSL密钥文件的路径。 | 否 |

## 使用TLS协议进行连接

您还可以使用TLS协议（即，使用公共/专用加密密钥）连接到数据库。 将以下可选属性添加到 `database` 元素：

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

迁移过程由步骤组成。

步骤是一个单元，提供迁移某些分离数据所需的功能。 步骤可以包含一个或多个阶段（完整性检查、数据、卷检查和增量）。

默认情况下，需执行以下几个步骤([地图](#map-step), [EAV](#eav), [URL重写](#url-rewrite-step)，等等)。 您也可以选择添加自己的步骤。

与步骤相关的类位于src/Migration/Step目录中。

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

如果数据阶段支持回滚，则它应该实施 `RollbackInterface` 界面。

运行步骤的可视化由Symfony的ProgressBar组件提供(请参阅 [进度栏](http://symfony.com/doc/current/components/console/helpers/progressbar.html))。 以LogLevelProcessor的形式在步骤中访问此组件。

主要使用方法包括：

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## 步骤阶段

### 完整性检查

每个步骤都必须检查数据源结构(默认为Magento1)和数据目标结构(Magento2)是否兼容。 如果不兼容，则会显示一个错误，其中包含不兼容的实体。 当字段具有不同的数据类型(同一字段在Magento1中具有十进制数据类型，在Magento2中具有整数)时，将显示一条警告消息（在映射文件中涵盖该消息时除外）。

### 数据传输

如果通过完整性检查，则传输数据正在运行。 如果出现错误，则运行回滚以还原到Magento2的先前状态。 如果步骤类实现 `RollbackInterface` 接口，则在出错时执行回滚方法。

### 卷检查

迁移数据后，卷检查会提供额外的检查，以确认所有数据均正确传输。

### 增量交付

增量功能负责提供主迁移后添加的其余数据。

## 运行模式

该工具应以三种不同模式运行，具体顺序为：

1. 设置 — 迁移系统设置
1. 数据 — 主要迁移数据
1. 增量 — 迁移主迁移后添加的其余数据

每个模式都有其自己的待执行步骤列表。 请参阅config.xml

### 设置迁移模式

此工具的设置迁移模式用于传输以下实体：

1. 网站、商店、商店视图。
1. 存储配置（主要是M2中的Stores->Configuration或M1中的System->Configuration）

所有存储配置都将其数据保留在数据库的core_config_data表中。 settings.xml文件包含在迁移过程中应用的此表规则。 此文件介绍了应忽略、重命名或应更改其值的设置。 settings.xml文件具有以下结构：

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

在节点下 `<key>` 在 `core_config_data` 表。 `<ignore>` 规则会阻止工具传输某些设置。 此节点中可以使用通配符。 未在 `<ignore>` 节点已迁移。 如果Magento2中设置的路径发生更改，则应将其添加到 `//key/rename` 节点，旧路径指示在 `//key/rename/path` 节点和新路径指示于 `//key/rename/to` 节点。

在节点下 `<value>`，则中有一些规则与 `core_config_data` 表。 这些规则旨在由处理程序（实施的类）转换设置的值 `Migration\Handler\HandlerInterface`)并将其适用于Magento2。

### 数据迁移模式

在此模式下，大多数数据都会迁移。 在数据迁移之前，针对每个步骤运行完整性检查阶段。 如果完整性检查通过，则 [!DNL Data Migration Tool] 安装deltalog表（带前缀） `m2_cl_*`)和相应的触发器，并运行Magento1数据库的数据迁移阶段。 在迁移完成且未出现错误时，卷检查数据一致性。 如果迁移实时存储，则会显示警告消息。 不用担心，增量迁移会处理此增量数据。 最有价值的迁移步骤是映射、URL重写和EAV。

#### 映射步骤

映射步骤负责将大多数数据从Magento1传输到Magento2。 此步骤从map.xml文件(位于 `etc/` 目录)。 该文件描述了源(Magento1)和目标(Magento2)的数据结构之间的差异。 如果Magento1包含属于某些 [扩展](https://glossary.magento.com/extension) Magento2中不存在的实体，则可以将这些实体放置在此处，以通过映射步骤忽略它们。 否则，将显示一条错误消息。

映射文件具有下一种格式：

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

* *来源*  — 包含源数据库规则

* *目标*  — 包含目标数据库规则

选项：

* *忽略*  — 忽略使用此选项标记的文档、字段或数据类型

* *重命名*  — 描述具有不同名称的文档之间的名称关系。 如果目标文档名称与源文档名称不同，则可以使用重命名选项设置与目标表名称类似的源文档名称

* *移动*  — 设置规则，将指定字段从源文档移动到目标文档。 注意：目标文档名称应与源文档名称相同。 如果源文档和目标文档名称不同，则需要对包含已移动字段的文档使用重命名选项

* *转换*  — 是一个选项，允许用户根据处理程序中描述的行为迁移字段

* *处理程序*  — 描述字段的转换行为。 要调用处理程序，您需要在 `<handler>` 标记。 使用 `<param>` 标记，其中包含参数名称和值数据以将其传递到处理程序

**来源** 可用操作：

| 文档 | 字段 |
|--- |--- |
| 忽略重命名 | 忽略移动转换 |

**目标** 可用操作：

| 文档 | 字段 |
|--- |--- |
| 忽略 | 忽略转换 |

#### 通配符

忽略具有相似部分的文档(`document_name_1`, `document_name_2`)，则可以使用通配符功能。 Put `*` 符号而不是重复部分(`document_name_*`)，并且此掩码涵盖所有符合此掩码的源文档或目标文档。

#### URL重写步骤

此步骤非常复杂，因为Magento1中开发了许多与Magento2不兼容的算法。 对于Magento1的不同版本，可以使用不同的算法。 因此，在Step/UrlRewrite文件夹下，有一些类是为某些特定版本的Magento和Migration\Step\UrlRewrite\Version191to2000 is one of them开发的。 它可以将URL重写Magento1.9.1中的数据传输到Magento2。

#### EAV步骤

此步骤将所有属性（产品、客户、RMA）从Magento1转移到Magento2。 它使用map-eav.xml文件，该文件包含与map.xml文件中的规则类似的规则，以用于处理数据的特定情况。

在步骤中处理的一些表：

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### 增量迁移模式

在主迁移后，可以将附加数据添加到Magento1数据库（例如，由店面上的客户添加）。 要跟踪此数据，该工具会在迁移过程开始时为表设置数据库触发器。 有关更多信息，请参阅 [迁移由第三方扩展创建的数据](migrate-data/delta.md#migrate-data-created-by-third-party-extensions).

## 数据源

要访问Magento1和Magento2的数据源并使用其数据（选择、更新、插入、删除）进行操作，Resource文件夹中有许多类。 Migration\ResourceModel\Source和Migration\ResourceModel\Destination是主类。 所有迁移步骤都使用它来操作数据。 此数据包含在Migration\ResourceModel\Document、Migration\ResourceModel\Record、Migration\ResourceModel\Structure等类中。

以下是这些类的类图：

![迁移工具数据结构](../../assets/data-migration/MmigrationToolDataStructure.png)

## 记录

为了实现迁移过程的输出，并控制所有可能级别的PSR记录器，该记录器用于Magento中。 `\Migration\Logger\Logger` 类用于提供日志记录功能。 要使用该日志记录器，应通过构造函数将其注入 [依赖注入](https://glossary.magento.com/dependency-injection).

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

之后，您可以使用此类记录某些事件：

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

可以自定义日志信息应写入的位置。 为此，可以使用日志记录器的pushHandler()方法将处理程序添加到日志记录器。 每个处理程序都应实施 `\Monolog\Handler\HandlerInterface` 界面。 目前有两个处理程序：

* ConsoleHandler:将消息写入控制台

* FileHandler:将消息写入“log_file”配置选项中设置的日志文件

此外，还可以实施任何其他处理程序。 Magento框架中有一组处理程序。 将处理程序添加到日志记录器的示例：

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

要为日志记录器（当前模式、表名）设置其他数据，您可以使用日志记录器处理器。 现有处理器(MessageProcessor)。 它的创建目的是为日志消息添加“额外”数据，每次执行日志方法时都会调用。 MessageProcessor已保护$extra var，该变量包含“mode”、“stage”、“step”和“table”的空值。 额外数据可作为日志方法的第二个参数（上下文）传递给处理器。 AbstractStep->runStage（传递当前模式、阶段和步骤到处理器）方法中当前向处理器提供的附加数据集以及使用日志记录器 — >调试方法（传递迁移表名）的数据类。 向记录器添加处理器的示例：

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

可以设置详细程度。 至今，这里有三个级别：

* `ERROR` （仅将错误写入日志）
* `INFO` （只将重要信息写入日志，默认值）
* `DEBUG` （所有内容都写成）

可通过调用，分别为每个处理程序设置详细性日志级别 `setLevel()` 方法。 如果要通过命令行参数设置详细程度级别，则应在应用程序启动时更改“verbose”选项。

您可以使用专写格式化程序格式化日志消息。 要使格式设置程序功能正常工作，您必须使用 `setFormatter()` 方法。 目前，我们有一个格式化程序类(`MessageFormatter`)，以在消息处理(通过 `format()` 方法)。

在 `process()` 方法 `Migration\Logger\Manager` 类。 应用程序启动时调用方法。

## 自动测试

在 [!DNL Data Migration Tool]:

* 静态
* 单位
* 集成

它们位于工具的 `tests/` 目录，与测试类型相同(设备测试位于 `tests/unit` 目录)。 要启动测试，您应该安装了phpunit。 将当前目录更改为测试目录并启动phpunit。 例如：

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
