---
title: 模組組態檔
description: 瞭解如何使用設定型別來自訂模組。
exl-id: 87433c28-8e3d-43d0-b77e-3ff9a680af5f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2024'
ht-degree: 0%

---

# 模組組態檔概觀

的職責 `config.xml` 舊版Commerce中使用的設定檔案現在分為多個檔案，位於各種模組目錄中。 只有當模組請求特定設定型別時，Commerce才會隨選載入多個設定檔案。

您可以使用這些檔案，也稱為 _設定型別_ — 自訂模組行為的特定方面。

多個模組可宣告會影響相同組態型別（例如事件）的組態檔，然後合併這些多個組態檔。

以下是本主題中使用的常用辭彙：

- **設定物件** — 負責定義及驗證設定型別的Commerce程式庫或類別。 例如，的組態物件 `config.xml` 是 [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- **設定階段** — 階段定義為 _主要_， _全域_、和 _區域_. 每個階段會決定何時載入組態型別並與同名組態型別合併。 例如， `module.xml` 檔案會與其他檔案合併 `module.xml` 檔案。

- **設定範圍** — 作為組態階段的補充，範圍定義了組態型別模型。 例如， `adminhtml` 是在舞台與其他模組一起載入的區域範圍 `adminhtml` 設定。 如需詳細資訊，請參閱 [模組和區域](https://developer.adobe.com/commerce/php/architecture/modules/areas/).

## 設定載入和合併

本節將討論如何載入及合併組態檔。

### Commerce如何載入設定檔案

Commerce會依照以下順序載入設定檔（所有路徑都是相對於您的Commerce安裝目錄）：

- 主要設定([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml))。 此檔案用於啟動Commerce。
- 來自模組的全域設定(`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`)。 會從所有模組收集特定組態檔，並將它們合併在一起。
- 來自模組的區域特定設定(`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`)。 從所有模組收集設定檔案，並將其合併至全域設定。 某些區域特定設定可以覆寫或擴充全域設定。

位置

- `<your component base dir>` 是元件所在的基本目錄。 典型值為 `app/code` 或 `vendor` 相對於Commerce安裝目錄。
- `<vendorname>` 是元件的廠商名稱；例如，Commerce的廠商名稱是 `magento`.
- `<component-type>` 為下列其中一項：

   - `module-`：擴充功能或模組。
   - `theme-`：主題。
   - `language-`：語言套件。

>[!INFO]
>
>目前，主題位於 `<magento_root>/app/design/frontend` 或 `<magento_root>/app/design/adminhtml`.

- `<component-name>`：元件的名稱（如中所定義） [composer.json](https://github.com/magento/magento2/blob/2.4/composer.json).

### 設定檔案合併

組態檔中的節點會根據其完全合格的XPath進行合併，這在 `$idAttributes` 宣告為其識別碼的陣列。 此識別碼對於巢狀在相同父節點下的所有節點必須是唯一的。

商務應用程式合併演演算法：

- 如果節點識別碼相等（或如果未定義識別碼），則節點中的所有基礎內容（屬性、子節點和純量內容）會被覆寫。
- 如果節點識別碼不相等，則該節點是父節點的新子節點。
- 如果原始檔案有多個節點具有相同的識別碼，則會觸發錯誤，因為無法辨別識別碼。

合併組態檔案後，產生的檔案會包含原始檔案中的所有節點。

>[!INFO]
>
>您可以使用 [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) 用於偵錯和瞭解背後邏輯的類別 [組態檔載入程式](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) 和 [合併設定](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144) 程式。

## 組態型別、物件和介面

以下各節提供有關配置型別、其對應的配置物件以及可用於處理物件的介面的資訊：

### 組態型別和物件

下表顯示每個設定型別及其相關的Commerce設定物件。

| 組態檔 | 說明 | 階段 | 設定物件 |
| --- | --- | --- | --- |
| `address_formats.xml` | 位址格式宣告 | 主要、全域 | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [存取控制清單](https://developer.adobe.com/commerce/webapi/get-started/authentication/#relationship-between-aclxml-and-webapixml) | 全域 | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [進階報告](https://devdocs.magento.com/guides/v2.4/advanced-reporting/data-collection.html) | 主要、全域 | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | 快取型別宣告 | 主要、全域 | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | 目錄屬性設定 | 全域 | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` 和 `env.php` | [部署設定](../reference/deployment-files.md) | 這些檔案可由內部設定處理器讀取/寫入。 | 沒有物件，無法自訂 |
| `config.xml` | 系統設定 | 主要、全域 | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [定義訊息佇列系統的各個方面](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#communicationxml) | 全域 | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [設定cron群組](../cron/custom-cron-reference.md#configure-cron-groups) | 全域 | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [指定cron群組選項](../cron/custom-cron-reference.md) | 全域 | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [宣告式結構描述](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) | 全域 | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [相依性插入](https://developer.adobe.com/commerce/php/development/components/dependency-injection/) 設定 | 主要、全域、區域 | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | 提供EAV屬性設定 | 全域 | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | 電子郵件範本設定 | 全域 | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [搜尋引擎地區設定停用字詞設定](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | 全域 | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | 事件/觀察者設定 | 全域，區域 | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | 匯出實體設定 | 全域 | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [擴充功能屬性](https://developer.adobe.com/commerce/php/development/components/attributes/#extension-attributes) | 全域 | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | 定義欄位集 | 全域 | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [宣告索引子](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/) | 全域 | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | 宣告匯入實體 | 全域 | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | 定義管理員的功能表專案 | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | 定義模組設定資料和軟相依性 | 主要、全域 | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [MView設定](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/#mview-configuration) | 主要、全域 | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | 付款模組設定 | 主要、全域 | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [Magento持續](https://developer.adobe.com/commerce/php/module-reference/module-persistent/) 設定檔 | 全域 | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | PDF設定 | 全域 | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | 提供產品選項設定 | 全域 | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | 定義產品型別 | 全域 | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [定義現有佇列與其取用者之間的關係](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_consumerxml) | 全域 | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [定義發佈主題的Exchange。](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_publisherxml) | 全域 | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [定義訊息路由規則、宣告佇列和交換](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_topologyxml) | 全域 | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [進階報告](https://devdocs.magento.com/guides/v2.4/advanced-reporting/report-xml.html) | 全域 | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | 定義模組資源 | 全域 | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [路由](https://developer.adobe.com/commerce/php/development/components/routing/) 設定 | 區域 | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | 定義銷售總計設定 | 全域 | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | 提供搜尋引擎設定 | 全域 | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | 定義目錄搜尋設定 | 全域 | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | 定義會觸發私人內容區塊快取失效的動作 | 前端 | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | 定義系統組態頁面的選項 | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | 模組驗證設定檔 | 全域 | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | 定義Vendor_Module檢視設定值 | 全域 | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [設定Web API](https://developer.adobe.com/commerce/php/development/components/web-api/services/) | 全域 | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [定義REST自訂路由](https://developer.adobe.com/commerce/php/development/components/web-api/custom-routes/) | 全域 | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | 定義Widget | 全域 | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | 定義每個國家/地區的郵遞區號格式 | 全域 | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### 設定介面

您可以使用下方的介面與組態檔案互動 [Magento\框架\設定](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config).

若您符合下列條件，則可以使用這些介面： [建立設定型別](../reference/config-create-types.md#create-configuration-types).

`Magento\Framework\Config` 提供下列介面：

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php)，會將XML轉換為設定的記憶體陣列呈現。
- [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php)，會擷取指定範圍內的設定資料。
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php)，可識別要讀取的檔案位置 [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php)，會從儲存體讀取設定資料，並選取要讀取的儲存體。

亦即，檔案系統、資料庫、其他儲存體會根據合併規則合併組態檔，並使用驗證結構來驗證組態檔。

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php)，會找到XSD結構描述。
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php)，會傳回範圍清單。
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php)，會擷取驗證狀態。
