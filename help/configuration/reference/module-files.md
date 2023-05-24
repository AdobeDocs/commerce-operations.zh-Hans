---
title: 模块配置文件
description: 了解如何使用配置类型自定义模块。
exl-id: 87433c28-8e3d-43d0-b77e-3ff9a680af5f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2024'
ht-degree: 0%

---

# 模块配置文件概述

董事会之职责 `config.xml` 早期版本的Commerce中使用的配置文件现在分为多个文件，位于不同的模块目录中。 仅当模块请求特定配置类型时，Commerce才会按需加载多个配置文件。

您可以使用这些文件 — 也称为 _配置类型_ — 定制模块行为的特定方面。

多个模块可以声明影响同一配置类型的配置文件（例如，事件），并且合并这些多个配置文件。

以下是本主题中使用的常用术语：

- **配置对象** — 负责定义和验证配置类型的Commerce库或类。 例如，的配置对象 `config.xml` 是 [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- **配置阶段** — 阶段定义为 _主要_， _全局_、和 _区域_. 每个阶段确定何时加载配置类型并与同名配置类型合并。 例如， `module.xml` 文件与其他文件合并 `module.xml` 文件。

- **配置范围** — 作为配置阶段的补充，范围定义了配置类型模型。 例如， `adminhtml` 是一个区域范围，在阶段与其他模块一起加载&#39; `adminhtml` 配置。 有关更多信息，请参阅 [模块和区域](https://developer.adobe.com/commerce/php/architecture/modules/areas/).

## 配置加载和合并

本节讨论如何加载和合并配置文件。

### Commerce如何加载配置文件

Commerce按以下顺序加载配置文件（所有路径均相对于Commerce安装目录）：

- 主要配置([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml))。 此文件用于引导商务。
- 模块中的全局配置(`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`)。 从所有模块中收集特定配置文件并将它们合并在一起。
- 模块中的区域特定配置(`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`)。 从所有模块收集配置文件并将其合并到全局配置中。 某些区域特定的配置可以覆盖或扩展全局配置。

位置

- `<your component base dir>` 是组件所在的基本目录。 典型值为 `app/code` 或 `vendor` 相对于Commerce安装目录。
- `<vendorname>` 是组件的供应商名称；例如，Commerce的供应商名称为 `magento`.
- `<component-type>` 是以下项之一：

   - `module-`：扩展或模块。
   - `theme-`：主题。
   - `language-`：语言包。

>[!INFO]
>
>目前，主题位于 `<magento_root>/app/design/frontend` 或 `<magento_root>/app/design/adminhtml`.

- `<component-name>`：中定义的组件名称 [composer.json](https://github.com/magento/magento2/blob/2.4/composer.json).

### 配置文件合并

配置文件中的节点会根据其完全限定的XPath进行合并，后者具有在中定义的特殊属性 `$idAttributes` 声明为其标识符的数组。 对于嵌套在同一父节点下的所有节点，此标识符必须是唯一的。

商务应用程序合并算法：

- 如果节点标识符相等（或未定义标识符），则覆盖节点中的所有基础内容（属性、子节点和标量内容）。
- 如果节点标识符不相等，则该节点是父节点的新子节点。
- 如果原始文档具有多个具有相同标识符的节点，则会触发错误，因为无法区分标识符。

合并配置文件后，生成的文档将包含原始文件中的所有节点。

>[!INFO]
>
>您可以使用 [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) 类用于调试和了解背后的逻辑 [配置文件加载器](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) 和 [合并配置](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144) 进程。

## 配置类型、对象和界面

以下各节提供了有关配置类型、其相应的配置对象以及可用于处理这些对象的接口的信息：

### 配置类型和对象

下表显示了每个配置类型及其相关的Commerce配置对象。

| 配置文件 | 描述 | 暂存 | 配置对象 |
| --- | --- | --- | --- |
| `address_formats.xml` | 地址格式声明 | 主要，全局 | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [访问控制列表](https://developer.adobe.com/commerce/webapi/get-started/authentication/#relationship-between-aclxml-and-webapixml) | 全局 | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [高级报告](https://devdocs.magento.com/guides/v2.4/advanced-reporting/data-collection.html) | 主要，全局 | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | 缓存类型声明 | 主要，全局 | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | 目录属性配置 | 全局 | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` 和 `env.php` | [部署配置](../reference/deployment-files.md) | 这些文件可由内部配置处理器读取/写入。 | 没有对象，无法自定义 |
| `config.xml` | 系统配置 | 主要，全局 | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [定义消息队列系统的各个方面](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#communicationxml) | 全局 | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [配置cron组](../cron/custom-cron-reference.md#configure-cron-groups) | 全局 | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [指定cron组选项](../cron/custom-cron-reference.md) | 全局 | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [声明性模式](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) | 全局 | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [依赖项注入](https://developer.adobe.com/commerce/php/development/components/dependency-injection/) 配置 | 主要、全局、区域 | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | 提供EAV属性配置 | 全局 | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | 电子邮件模板配置 | 全局 | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [搜索引擎区域设置停用词配置](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | 全局 | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | 事件/观察者配置 | 全局，区域 | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | 导出实体配置 | 全局 | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [扩展属性](https://developer.adobe.com/commerce/php/development/components/attributes/#extension-attributes) | 全局 | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | 定义字段集 | 全局 | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [声明索引器](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/) | 全局 | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | 声明导入实体 | 全局 | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | 为管理员定义菜单项 | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | 定义模块配置数据和软依赖关系 | 主要，全局 | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [MView配置](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/#mview-configuration) | 主要，全局 | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | 支付模块配置 | 主要，全局 | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [Magento持续](https://developer.adobe.com/commerce/php/module-reference/module-persistent/) 配置文件 | 全局 | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | PDF设置 | 全局 | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | 提供产品选项配置 | 全局 | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | 定义产品类型 | 全局 | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [定义现有队列与其使用者之间的关系](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_consumerxml) | 全局 | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [定义发布主题的Exchange。](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_publisherxml) | 全局 | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [定义报文路由规则，声明队列和交换](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_topologyxml) | 全局 | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [高级报告](https://devdocs.magento.com/guides/v2.4/advanced-reporting/report-xml.html) | 全局 | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | 定义模块资源 | 全局 | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [路由](https://developer.adobe.com/commerce/php/development/components/routing/) 配置 | 区域 | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | 定义销售总额配置 | 全局 | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | 提供搜索引擎配置 | 全局 | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | 定义目录搜索配置 | 全局 | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | 定义触发专用内容块缓存失效的操作 | 前端 | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | 定义系统配置页面的选项 | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | 模块验证配置文件 | 全局 | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | 定义Vendor_Module视图配置值 | 全局 | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [配置Web API](https://developer.adobe.com/commerce/php/development/components/web-api/services/) | 全局 | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [定义REST自定义路由](https://developer.adobe.com/commerce/php/development/components/web-api/custom-routes/) | 全局 | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | 定义构件 | 全局 | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | 定义每个国家/地区的邮政编码格式 | 全局 | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### 配置界面

您可以使用下的界面与配置文件进行交互 [Magento\框架\配置](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config).

在以下情况下，您可以使用这些界面： [创建配置类型](../reference/config-create-types.md#create-configuration-types).

`Magento\Framework\Config` 提供了以下界面：

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php)，用于将XML转换为配置的内存数组内表示形式。
- [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php)，用于在指定的范围内检索配置数据。
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php)，标识要读取的文件的位置 [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php)，从存储中读取配置数据并选择从中读取的存储器。

即文件系统、数据库、其它存储根据合并规则对配置文件进行合并，并用验证模式对配置文件进行验证。

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php)，查找XSD架构。
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php)，这将返回范围列表。
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php)，以检索验证状态。
