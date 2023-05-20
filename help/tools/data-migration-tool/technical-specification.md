---
title: '''[!DNL Data Migration Tool] 技術規格'
description: 瞭解的實作詳細資料 [!DNL Data Migration Tool] 以及在Magento1和Magento2之間傳輸資料時如何擴充。
exl-id: fec3ac3a-dd67-4533-a29f-db917f54d606
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2079'
ht-degree: 0%

---

# [!DNL Data Migration Tool] 技術規格

本節將說明 [!DNL Data Migration Tool] 實作詳細資料，以及如何擴充其功能。

## 存放庫

若要存取 [!DNL Data Migration Tool] 原始碼，請參閱GitHub [存放庫](https://github.com/magento/data-migration-tool).

## 系統需求

此 [系統需求](../../installation/system-requirements.md) 的 [!DNL Data Migration Tool] 與Magento2相同。

## 內部結構

### 目錄結構

下圖代表目錄結構 [!DNL Data Migration Tool]：

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

## 進入點

執行移轉程式的指令碼位於： `magento-root/bin/magento`.

## 設定

設定的結構描述 `config.xsd` 檔案位於 `etc/` 目錄。 預設組態檔(`config.xml.dist`)會針對Magento1.x的每個版本建立。它位在 `etc/`.

預設設定檔案可由自訂設定檔案取代(請參閱 [命令語法](migrate-data/overview.md#command-syntax))。

組態檔案具有下列結構：

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

* 步驟 — 說明移轉期間處理的所有步驟

* source — 資料來源的設定。 可用的來源型別：資料庫

* destination — 資料目的地的設定。 可用的目的地型別：資料庫

* options — 引數清單。 包含必要(map_file、settings_map_file、bulk_size)和選用(custom_option、resource_adapter_class_name、prefix_source、prefix_dest、log_file)引數

變更前置詞選項，以備在資料庫表格中安裝了帶有前置詞的Magento時使用。 可以為Magento1和Magento2資料庫設定它。 請相應地使用「source_prefix」和「dest_prefix」組態選項。

設定資料可透過以下方式存取： `\Migration\Config` 類別。

## 可用的步驟作業

| 檔案 | 欄位 |
|---|---|
| `step` | 「步驟」節點內的第二層節點。 相關步驟的說明必須指定於 `title` 屬性。 |
| `integrity` | 指定負責完整性檢查的PHP類別。 比較表格欄位名稱、型別和其他資訊，以驗證Magento1和2資料結構之間的相容性。 |
| `data` | 指定負責資料檢查的PHP類別。 將資料、表格從Magento1傳輸至Magento2。 |
| `volume` | 指定負責體積塊檢查的PHP類別。 比較表格之間的記錄數，以驗證傳輸是否成功。 |
| `delta` | 指定負責增量檢查的PHP類別。 完整資料移轉後，將差異從Magento1傳輸至Magento2。 |

## 來源資料庫資訊屬性

| 檔案 | 欄位 | 必填？ |
|---|---|---|
| `name` | Magento1伺服器的資料庫名稱。 | 是 |
| `host` | Magento1伺服器的主機IP位址。 | 是 |
| `port` | Magento1伺服器的連線埠號碼。 | 否 |
| `user` | Magento1資料庫伺服器的使用者名稱。 | 是 |
| `password` | Magento1資料庫伺服器的密碼。 | 是 |
| `ssl_ca` | SSL憑證授權單位檔案的路徑。 | 否 |
| `ssl_cert` | SSL憑證檔案的路徑。 | 否 |
| `ssl_key` | SSL金鑰檔案的路徑。 | 否 |

## 目的地資料庫資訊屬性

| 檔案 | 欄位 | 必填？ |
|---|---|---|
| `name` | Magento2伺服器的資料庫名稱。 | 是 |
| `host` | Magento2伺服器的主機IP位址。 | 是 |
| `port` | Magento2伺服器的連線埠號碼。 | 否 |
| `user` | Magento2資料庫伺服器的使用者名稱。 | 是 |
| `password` | Magento2資料庫伺服器的密碼。 | 是 |
| `ssl_ca` | SSL憑證授權單位檔案的路徑。 | 否 |
| `ssl_cert` | SSL憑證檔案的路徑。 | 否 |
| `ssl_key` | SSL金鑰檔案的路徑。 | 否 |

## 使用TLS通訊協定連線

您也可以使用TLS通訊協定（亦即使用公開/私用密碼編譯金鑰）連線到資料庫。 將下列選擇性屬性新增至 `database` 元素：

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

## 步驟內部

移轉程式包含多個步驟。

步驟是一個單位，提供移轉一些分隔資料所需的功能。 步驟可以包含一個或多個階段（完整性檢查、資料、磁碟區檢查以及差異）。

依預設，有幾個步驟([地圖](#map-step)， [EAV](#eav)， [URL重寫](#url-rewrite-step)、等等)。 您也可以選擇新增自己的步驟。

步驟相關類別位於src/Migration/Step目錄中。

若要執行Step類別，必須在config.xml檔案中定義類別。

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

每個階段類別都必須實作StageInterface。

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

如果資料階段支援回覆，則應實作 `RollbackInterface` 介面。

執行步驟的視覺效果由Symfony的ProgressBar元件提供(請參閱 [進度列](https://symfony.com/doc/current/components/console/helpers/progressbar.html))。 在步驟中以LogLevelProcessor存取此元件。

主要使用方法如下：

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## 步驟階段

### 完整性檢查

每個步驟都必須檢查資料來源的結構(預設為Magento1)和資料目的地的結構(Magento2)是否相容。 如果沒有 — 發生不相容的實體時會顯示錯誤。 如果欄位有不同的資料型別(相同的欄位在Magento1有十進位資料型別，在Magento2有整數)，則會顯示警告訊息（除非該訊息涵蓋在Map檔案中）。

### 資料傳輸

如果完整性檢查通過，則傳輸資料正在執行。 如果出現錯誤，則復原執行以恢復Magento2的上一個狀態。 如果步驟類別實作 `RollbackInterface` 介面，然後在發生錯誤時執行復原方法。

### 磁碟區檢查

資料移轉後，「磁碟區檢查」會額外檢查所有資料是否已正確傳輸。

### 差異傳遞

Delta功能負責傳遞主要移轉後新增的其餘資料。

## 執行模式

工具應依特定順序以三種不同的模式執行：

1. 設定 — 移轉系統設定
1. 資料 — 主要資料移轉
1. delta — 移轉主要移轉後新增的其餘資料

每個模式都有各自要執行的步驟清單。 請參閱config.xml

### 設定移轉模式

此工具的設定移轉模式用於轉移以下實體：

1. 網站、商店、商店檢視。
1. 存放區組態（主要是在M2中儲存 — >組態或在M1中系統 — >組態）

所有存放區設定都會將其資料儲存在資料庫的core_config_data表格中。 settings.xml檔案包含此資料表的規則，這些規則會在移轉程式期間套用。 此檔案說明應該忽略、重新命名或應該變更其值的設定。 settings.xml檔案具有以下結構：

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

在節點下 `<key>` 有一些規則可搭配中的「path」欄使用 `core_config_data` 表格。 `<ignore>` 規則會阻止工具傳輸某些設定。 此節點中可以使用萬用字元。 所有其他設定未列於 `<ignore>` 節點已移轉。 如果設定的路徑在Magento2中變更，則應將其新增至 `//key/rename` 節點，其中舊路徑為 `//key/rename/path` 節點和新路徑指示於 `//key/rename/to` 節點。

在節點下 `<value>`中，有些規則可搭配「value」欄使用 `core_config_data` 表格。 這些規則旨在透過處理常式（實作的類別）轉換設定的值 `Migration\Handler\HandlerInterface`)並根據Magento2進行調整。

### 資料移轉模式

在此模式中，大部分資料都會移轉。 在資料移轉之前，系統會針對每個步驟執行完整性檢查階段。 如果完整性檢查通過， [!DNL Data Migration Tool] 安裝deltalog表格（含前置詞） `m2_cl_*`)和對應觸發器至Magento1資料庫，並執行資料移轉階段的步驟。 移轉完成且無錯誤時，磁碟區檢查會檢查資料的一致性。 如果您移轉即時存放區，它會顯示警告訊息。 別擔心，增量移轉會處理這些增量資料。 最有價值的移轉步驟包括地圖、URL重寫和EAV。

#### 地圖步驟

對應步驟負責將大部分資料從Magento1傳輸到Magento2。 此步驟會從map.xml檔案(位於 `etc/` 目錄)。 此檔案說明來源(Magento1)和目的地(Magento2)的資料結構之間的差異。 如果Magento1包含屬於Magento2中不存在之某些擴充功能的表格或欄位，則可以將這些實體放置在此處，以透過「對應步驟」忽略它們。 否則，它會顯示錯誤訊息。

對應檔案的格式如下：

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

區域：

* *source*  — 包含來源資料庫的規則

* *目的地*  — 包含目的地資料庫的規則

選項：

* *忽略*  — 略過標示為此選項的檔案、欄位或資料型別

* *重新命名*  — 說明不同名稱的檔案之間的名稱關係。 如果目的地檔名稱與來原始檔不同，您可以使用重新命名選項來設定與目的地表格名稱相似的來源檔名稱

* *移動*  — 設定將指定欄位從來原始檔移動到目的地檔案的規則。 附註：目的檔名稱應與來源檔名稱相同。 如果來源和目的地檔名稱不同 — 您需要對包含移動欄位的檔案使用重新命名選項

* *轉換*  — 是一個選項，可讓使用者根據處理常式中所述的行為遷移欄位

* *處理常式*  — 說明欄位的轉換行為。 若要呼叫處理常式，您必須在 `<handler>` 標籤之間。 使用 `<param>` 標籤以傳遞引數名稱和值資料給處理常式

**來源** 可用操作：

| 檔案 | 欄位 |
|--- |--- |
| 忽略重新命名 | 忽略移動轉換 |

**目的地** 可用操作：

| 檔案 | 欄位 |
|--- |--- |
| 忽略 | 忽略轉換 |

#### 萬用字元

忽略具有類似零件的檔案(`document_name_1`， `document_name_2`)，則可以使用萬用字元功能。 Put `*` 符號而非重複部分(`document_name_*`)，此遮罩涵蓋符合此遮罩的所有來源或目的地檔案。

#### URL重寫步驟

此步驟很複雜，因為在Magento1中開發的許多不同演演算法與Magento2不相容。 對於Magento1的不同版本，可能有不同的演演算法。 因此，在Step/UrlRewrite資料夾下，有一些針對某些特定Magento版本開發的類別，Migration\Step\UrlRewrite\Version191to2000就是其中之一。 它可以將URL重寫資料從Magento1.9.1傳輸至Magento2。

#### EAV步驟

此步驟會將所有屬性（產品、客戶、RMA）從Magento1移轉至Magento2。 它使用map-eav.xml檔案，其中包含處理資料的特定案例，與map.xml檔案中的規則相似的規則。

在步驟中處理的一些表格：

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### 差異移轉模式

主要移轉後，其他資料可能已新增至Magento1資料庫（例如店面的客戶）。 若要追蹤此資料，工具會在移轉程式開始時設定資料表的資料庫觸發程式。 如需詳細資訊，請參閱 [移轉由協力廠商擴充功能建立的資料](migrate-data/delta.md#migrate-data-created-by-third-party-extensions).

## 資料來源

若要存取Magento1和Magento2的資料來源，並運用其資料（選取、更新、插入、刪除），Resource資料夾中有許多類別。 Migration\ResourceModel\Source和Migration\ResourceModel\Destination是主要類別。 所有移轉步驟都會使用它來操作資料。 這些資料包含在Migration\ResourceModel\Document、Migration\ResourceModel\Record、Migration\ResourceModel\Structure等類別中。

以下是這些類別的類別圖表：

![移轉工具資料結構](../../assets/data-migration/MmigrationToolDataStructure.png)

## 記錄

為了實作移轉程式的輸出並控制所有可能的層級，套用了Magento中使用的PSR記錄器。 `\Migration\Logger\Logger` 類別已實作以提供記錄功能。 若要使用記錄器，您應透過建構函式相依性插入來插入記錄器。

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

之後，您可以使用此類別來記錄某些事件：

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

可以自訂記錄資訊的寫入位置。 您可以透過使用記錄器的pushHandler()方法將處理常式新增到記錄器來執行此操作。 每個處理常式都應該實作 `\Monolog\Handler\HandlerInterface` 介面。 目前有兩個處理常式：

* ConsoleHandler：將訊息寫入主控台

* FileHandler：將訊息寫入已在「log_file」組態選項中設定的記錄檔

您也可以實作任何其他處理常式。 Magento架構中有一組處理常式。 將處理常式新增至記錄器的範例：

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

若要為記錄器設定其他資料（目前模式、表格名稱），您可以使用記錄器處理器。 有一個現有的處理器(MessageProcessor)。 建立它是為了新增記錄訊息的「額外」資料，並在每次執行記錄方法時呼叫。 MessageProcessor已保護$extra var，其中包含&#39;mode&#39;、&#39;stage&#39;、&#39;step&#39;和&#39;table&#39;的空白值。 額外的資料可作為記錄方法的第二個引數（內容）傳遞給處理器。 目前在AbstractStep->runStage （傳遞目前模式、階段和步驟到處理器）方法和資料類別中使用了記錄器 — >偵錯方法（傳遞移轉表格名稱）的處理器中會有額外的資料集。 將處理器新增至記錄器的範例：

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

您可以設定詳細程度的等級。 目前分為三個層級：

* `ERROR` （只將錯誤寫入記錄檔）
* `INFO` （只有重要資訊會寫入記錄檔，預設值）
* `DEBUG` （所有內容都會寫入）

您可以呼叫，個別為每個處理常式設定詳細記錄層級 `setLevel()` 方法。 如果您想要透過命令列引數設定詳細等級，您應在應用程式啟動時變更「詳細」選項。

您可以使用單色格式化程式來格式化記錄訊息。 若要讓格式化程式功能發揮作用，您必須使用 `setFormatter()` 方法。 目前，我們有一個格式化程式類別(`MessageFormatter`)在訊息處理期間設定特定格式（取決於詳細程度等級） (透過 `format()` 方法)。

在詳細模式中操作記錄器（新增處理常式與處理器）與處理是在下列專案中執行： `process()` 方法 `Migration\Logger\Manager` 類別。 當應用程式啟動時，就會呼叫方法。

## 自動測試

中有三種型別的測試 [!DNL Data Migration Tool]：

* 靜態
* 單位
* 整合

它們位於工具的 `tests/` 目錄，與測試型別相同(單元測試位於 `tests/unit` 目錄)。 若要啟動測試，您應該已安裝phpunit。 將目前目錄切換到測試目錄並啟動phpunit。 例如：

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
