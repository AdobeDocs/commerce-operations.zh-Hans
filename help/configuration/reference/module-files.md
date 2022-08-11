---
title: 模块配置文件
description: 了解如何使用配置类型自定义模块。
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '2019'
ht-degree: 0%

---


# 模块配置文件概述

的责任 `config.xml` 在Commerce早期版本中使用的配置文件现在分为多个文件，它们位于各种模块目录中。 仅当模块请求特定配置类型时，商务的多个配置文件才会按需加载。

您可以使用这些文件，也称为 _配置类型_ — 自定义模块行为的特定方面。

多个模块可以声明影响相同配置类型（例如事件）的配置文件，并且这些多个配置文件会被合并。

以下是本主题中使用的常用术语：

- **配置对象** — 负责定义和验证配置类型的商务库或类。 例如， `config.xml` is [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- **配置阶段** — 阶段定义为 _主要_, _全球_&#x200B;和 _面积_. 每个阶段都确定何时加载配置类型并将其与同名配置类型合并。 例如， `module.xml` 文件与其他文件合并 `module.xml` 文件。

- **配置范围** — 作为配置阶段的补充，范围定义配置类型模型。 例如， `adminhtml` 是与其他模块一起加载的阶段区域范围。 `adminhtml` 配置。 有关更多信息，请参阅 [模块和区域](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_and_areas.html).

## 配置加载和合并

本节讨论如何加载和合并配置文件。

### Commerce如何加载配置文件

Commerce按以下顺序加载配置文件（所有路径都相对于您的Commerce安装目录）：

- 主配置([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml))。 此文件用于引导Commerce。
- 模块的全局配置(`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`)。 从所有模块收集特定配置文件并将它们合并在一起。
- 模块中特定于区域的配置(`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`)。 从所有模块收集配置文件，并将它们合并到全局配置中。 某些特定于区域的配置可以覆盖或扩展全局配置。

where

- `<your component base dir>` 是组件所在的基目录。 典型值包括 `app/code` 或 `vendor` 相对于Commerce安装目录。
- `<vendorname>` 是组件的供应商名称；例如，商务的供应商名称为 `magento`.
- `<component-type>` 是以下任一项：

   - `module-`:扩展或模块。
   - `theme-`:主题。
   - `language-`:语言包。

>[!INFO]
>
>目前，主题位于 `<magento_root>/app/design/frontend` 或 `<magento_root>/app/design/adminhtml`.

- `<component-name>`:组件的名称(在 [composer.json](https://github.com/magento/magento2/blob/2.4/composer.json).

### 配置文件合并

配置文件中的节点会根据其完全限定的XPath进行合并，XPath在 `$idAttributes` 数组声明为其标识符。 对于嵌套在同一父节点下的所有节点，此标识符必须是唯一的。

商务应用程序合并算法：

- 如果节点标识符相等（或者如果未定义标识符），则会覆盖节点中的所有基础内容（属性、子节点和标量内容）。
- 如果节点标识符不相等，则该节点是父节点的新子节点。
- 如果原始文档具有多个具有相同标识符的节点，则会触发错误，因为无法区分标识符。

合并配置文件后，生成的文档包含原始文件中的所有节点。

>[!INFO]
>
>您可以使用 [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) 用于调试和了解逻辑的类 [配置文件加载器](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) 和 [合并配置](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144) 进程。

## 配置类型、对象和接口

以下各节提供了有关配置类型、其相应配置对象以及可用于处理这些对象的接口的信息：

- [配置类型和对象](#config-files-classes-objects)
- [配置界面](#config-files-classes-int)

### 配置类型和对象

下表显示了每种配置类型及其与之相关的商务配置对象。

| 配置文件 | 描述 | 阶段 | 配置对象 |
| --- | --- | --- | --- |
| `address_formats.xml` | 地址格式声明 | 主要，全局 | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [访问控制列表](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication.html#relationship-between-aclxml-and-webapixml) | 全球 | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [高级报表](https://devdocs.magento.com/guides/v2.4/advanced-reporting/data-collection.html) | 主要，全局 | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | 缓存类型声明 | 主要，全局 | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | 目录属性配置 | 全球 | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` 和 `env.php` | [部署配置](../reference/deployment-files.md) | 这些文件可由内部配置处理器读取/写入。 | 没有对象，无法自定义 |
| `config.xml` | 系统配置 | 主要，全局 | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [定义消息队列系统的方面](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#communicationxml) | 全球 | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [配置CRON组](../cron/custom-cron-reference.md#configure-cron-groups) | 全球 | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [指定开关组选项](../cron/custom-cron-reference.md) | 全球 | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [声明性模式](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/declarative-schema/db-schema.html) | 全球 | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [依赖注入](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/depend-inj.html) 配置 | 主要，全球，地区 | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | 提供EAV属性配置 | 全球 | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | 电子邮件模板配置 | 全球 | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [搜索引擎区域设置秒词配置](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | 全球 | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | 事件/观察者配置 | 全球，区域 | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | 导出实体配置 | 全球 | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [扩展属性](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/attributes.html#extension) | 全球 | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | 定义字段集 | 全球 | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [声明的索引器](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/indexing-custom.html) | 全球 | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | 声明导入实体 | 全球 | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | 为管理员定义菜单项 | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | 定义模块配置数据和软依赖项 | 主要，全局 | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [MView配置](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/indexing-custom.html#mview-configuration) | 主要，全局 | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | 付款模块配置 | 主要，全局 | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [Magento(_P)](https://devdocs.magento.com/guides/v2.4/mrg/module-persistent.html) 配置文件 | 全球 | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | PDF设置 | 全球 | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | 提供产品选项配置 | 全球 | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | 定义产品类型 | 全球 | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [定义现有队列与其使用者之间的关系](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#queueconsumerxml) | 全球 | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [定义发布主题的交换。](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#queuepublisherxml) | 全球 | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [定义消息路由规则、声明队列和交换](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#queuetopologyxml) | 全球 | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [高级报表](https://devdocs.magento.com/guides/v2.4/advanced-reporting/report-xml.html) | 全球 | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | 定义模块资源 | 全球 | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [路线](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/routing.html) 配置 | 面积 | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | 定义销售总额配置 | 全球 | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | 提供搜索引擎配置 | 全球 | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | 定义目录搜索配置 | 全球 | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | 定义触发专用内容块缓存失效的操作 | 前端 | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | 为系统配置页定义选项 | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | 模块验证配置文件 | 全球 | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | 定义Vendor_Module视图配置值 | 全球 | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [配置Web API](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/service-contracts/service-to-web-service.html) | 全球 | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [定义REST自定义路由](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/webapi/custom-routes.html) | 全球 | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | 定义小组件 | 全球 | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | 为每个国家/地区定义邮政编码格式 | 全球 | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### 配置界面

您可以使用 [Magento\框架\配置](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config).

如果您 [创建配置类型](../reference/config-create-types.md#create-configuration-types).

`Magento\Framework\Config` 提供了以下界面：

- [框架\配置\转换器界面](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php)，可将XML转换为内存中配置的数组表示形式。
- [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php)，用于检索指定作用域中的配置数据。
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php)，用于标识要读取的文件的位置 [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php)，从存储中读取配置数据并选择从中读取的存储。

即文件系统、数据库、其他存储按照合并规则合并配置文件，并用验证模式验证配置文件。

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php)，用于查找XSD架构。
- [框架\配置\范围列表界面](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php)，返回作用域列表。
- [框架\配置\验证状态界面](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php)，用于检索验证状态。