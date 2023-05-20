---
title: 自訂 [!DNL Data Migration Tool]
description: 瞭解如何自訂 [!DNL Data Migration Tool] 以在Magento1和Magento2之間傳輸擴充功能建立的資料。
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# 設定 [!DNL Data Migration Tool]

有時建立的資料格式和結構 [擴充功能](https://marketplace.magento.com/extensions.html) 或自訂程式碼在Magento1和Magento2之間不同。 使用內的擴充點 [!DNL Data Migration Tool] 以移轉此資料。 如果資料格式和結構相同，工具可以自動移轉資料，無需使用者介入。

在移轉期間， [地圖步驟](technical-specification.md#map-step) 會掃描並比較所有Magento1和Magento2表格，包括由擴充功能建立的表格。 如果表格相同，工具會自動移轉資料。 如果表格不同，工具會終止並通知使用者。

>[!NOTE]
>
>閱讀 [技術規格](technical-specification.md) 在嘗試延伸 [!DNL Data Migration Tool]. 此外，請檢閱 [移轉指南](../overview.md) 以取得使用移轉工具的一般資訊。


## 微幅資料格式和結構變更

在大多數情況下， [地圖步驟](technical-specification.md#map-step) 使用下列方法，足以解析細微的資料格式和結構變更： `map.xml` 檔案：

- 使用對應規則變更表格或欄位名稱
- 使用現有處理常式或自訂處理常式轉換資料格式

以下同時使用對應規則和處理常式的範例。 此範例使用名為「GreatBlog」的假設Magento1擴充功能，此擴充功能已針對Magento2進行改善。

```xml
<source>
    <document_rules>
        <ignore>
            <document>great_blog_index</document>
        </ignore>
        <rename>
            <document>great_blog_publication</document>
            <to>great_blog_post</to>
        </rename>
    </document_rules>
    <field_rules>
        <move>
            <field>great_blog_publication.summary</field>
            <to>great_blog_post.title</to>
        </move>
        <ignore>
            <field>great_blog_publication.priority</field>
        </ignore>
        <transform>
            <field>great_blog_publication.body</field>
            <handler class="\Migration\Handler\GreatBlog\NewFormat">
                <param name="switch" value="yes" />
            </handler>
        </transform>
    </field_rules>
</source>
<destination>
    <document_rules>
        <ignore>
            <document>great_blog_rating</document>
        </ignore>
    </document_rules>
    <field_rules>
        <ignore>
            <field>great_blog_post.rating</field>
        </ignore>
    </field_rules>
</destination>
```

- 請勿從移轉不必要的資料 `great_blog_index` 索引資料表。
- 表格 `great_blog_publication` 已重新命名為 `great_blog_post` 在Magento2中，因此資料會移轉至新表格。
   - 此 `summary` 欄位已重新命名為 `title`，因此資料會移轉至新欄位。
   - 此 `priority` 欄位已移除，不再存在於Magento2中。
   - 中的資料 `body` 欄位已變更格式，應由自訂處理常式處理： `\Migration\Handler\GreatBlog\NewFormat`.
- Magento2已為「GreatBlog」擴充功能開發新的評等功能。
   - 新 `great_blog_rating` 已建立表格。
   - 新 `great_blog_post.rating` 欄位已建立。

### 在其他步驟中擴充對應

其他步驟支援對應，例如 [EAV步驟](technical-specification.md#eav-step) 以及客戶屬性步驟。 這些步驟會移轉預先定義的Magento表格清單。 例如，假設「GreatBlog」擴充功能在 `eav_attribute` 表格和名稱在Magento2中變更。 因為表格是由 [EAV步驟](technical-specification.md#eav-step)，對應規則應該針對 `map-eav.xml` 檔案。 此 `map.xml` 和 `map-eav.xml` 檔案使用相同的 `map.xsd` 結構描述，因此對應規則會維持不變。

## 重大資料格式和結構變更

除了「地圖步驟」，還有其他步驟 `config.xml` 以主要格式和結構變更移轉資料的檔案，包括：

- [Url重寫步驟](technical-specification.md#url-rewrite-step)
- OrderGrid步驟
- [EAV步驟](technical-specification.md#eav-step)

不喜歡 [地圖步驟](technical-specification.md#map-step)，這些步驟會掃描預先定義的表格清單，而非所有表格。

如需重大資料格式和結構變更，請建立自訂步驟。

### 建立自訂步驟

使用相同的「GreatBlog」範例，假設擴充功能在Magento1中有一個表格，但重新設計後在Magento2中有兩個表格。

在Magento1中，有一個 `greatblog_post` 表格：

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

在Magento2中，為標籤新增了表格 `greatblog_post_tags` 推出了：

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

MAGENTO2 `greatblog_post` 表格現在看起來像這樣：

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

若要將所有資料從舊表格結構移轉到新表格結構，您可以在 `config.xml` 檔案。 例如：

```xml
<steps mode="data">
    ...
    <step title="GreatBlog Step">
        <integrity>Vendor\Migration\Step\GreatBlog\Integrity</integrity>
        <data>Vendor\Migration\Step\GreatBlog\Data</data>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
<steps mode="delta">
    ...
    <step title="GreatBlog Step">
        <delta>Vendor\Migration\Step\GreatBlog\Delta</delta>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
```

此工具會根據步驟在中的位置執行步驟 `config.xml` 檔案；從上到下。 在我們的範例中， `GreatBlog Step` 最後執行。

步驟可包含四種類別：

- 完整性檢查
- 資料傳遞
- 音量檢查
- Delta傳遞

>[!NOTE]
>
>請參閱 [設定](technical-specification.md#configuration)， [步驟內部](technical-specification.md#step-internals)， [階段](technical-specification.md#step-stages)、和 [執行模式](technical-specification.md#running-modes) 以取得詳細資訊。


可以在這些類別中組合複雜的SQL查詢，以擷取和移轉資料。 此外，這些表格在下列位置中應被「忽略」： [地圖步驟](technical-specification.md#map-step) 因為它會掃描所有現有表格並嘗試移轉資料，除非資料位於 `<ignore>` 的標籤 `map.xml` 檔案。

對於完整性檢查，請在 `config.xml` 檔案來驗證資料表結構是否如我們所預期。

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
        xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/config.xsd">
    ...
    <options>
        ...
        <greatblog_map_file>app/code/Vendor/Migration/etc/opensource-to-opensource/map-greatblog.xml</greatblog_map_file>
        ...
    </options>
</config>
```

對應檔案 `map-greatblog.xml`：

```xml
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
     xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/map.xsd">
    <source>
        <field_rules>
            <ignore>
                <field>greatblog_post.tags</field>
            </ignore>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>greatblog_post_tags</document>
            </ignore>
        </document_rules>
    </destination>
</map>
```

完整性檢查類別 `Vendor\Migration\Step\GreatBlog\Integrity` 延伸 `Migration\App\Step\AbstractIntegrity` 並包含 `perform` 我們驗證表格結構的方法：

```php
class Integrity extends \Migration\App\Step\AbstractIntegrity
{
    ...
    /**
     * Integrity constructor.
     * @param ProgressBar\LogLevelProcessor $progress
     * @param Logger $logger
     * @param Config $config
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param MapFactory $mapFactory
     * @param string $mapConfigOption
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        Logger $logger,
        Config $config,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        MapFactory $mapFactory,
        $mapConfigOption = 'greatblog_map_file'
    ) {
        parent::__construct($progress, $logger, $config, $source, $destination, $mapFactory, $mapConfigOption);
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $this->progress->start($this->getIterationsCount());
        $this->check(['greatblog_post'], MapInterface::TYPE_SOURCE);
        $this->check(['greatblog_post', 'greatblog_post_tags'], MapInterface::TYPE_DEST);
        $this->progress->finish();
        return $this->checkForErrors();
    }
    ...
}
```

接下來，您必須建立一個類別，以便處理和儲存資料至Magento2資料庫 `Vendor\Migration\Step\GreatBlog\Data`：

```php
class Data implements \Migration\App\Step\StageInterface
{
    ...
    /**
     * Data constructor.
     *
     * @param ProgressBar\LogLevelProcessor $progress
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param ResourceModel\RecordFactory $recordFactory
     * @param RecordTransformerFactory $recordTransformerFactory
     * @param MapFactory $mapFactory
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        ResourceModel\RecordFactory $recordFactory,
        RecordTransformerFactory $recordTransformerFactory,
        MapFactory $mapFactory
    ) {
        $this->progress = $progress;
        $this->destination = $destination;
        $this->recordFactory = $recordFactory;
        $this->source = $source;
        $this->recordTransformerFactory = $recordTransformerFactory;
        $this->map = $mapFactory->create('greatblog_map_file');
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocName = 'greatblog_post';
        $sourceDocument = $this->source->getDocument($sourceDocName);
        $destinationDocName = 'greatblog_post';
        $destinationDocument = $this->destination->getDocument($destinationDocName);
        /** @var \Migration\RecordTransformer $recordTransformer */
        $recordTransformer = $this->recordTransformerFactory->create(
            [
                'sourceDocument' => $sourceDocument,
                'destDocument'   => $destinationDocument,
                'mapReader'      => $this->map
            ]
        );
        $recordTransformer->init();

        $this->progress->start($this->source->getRecordsCount($sourceDocName));
        $pageNumber = 0;
        while (!empty($items = $this->source->getRecords($sourceDocName, $pageNumber))) {
            $pageNumber++;
            $recordsToSave = $destinationDocument->getRecords();
            foreach ($items as $item) {
                $sourceRecord = $this->recordFactory->create(
                    ['document' => $sourceDocument, 'data' => $item]
                );
                $destinationRecord = $this->recordFactory->create(['document' => $destinationDocument]);
                $recordTransformer->transform($sourceRecord, $destinationRecord);
                $recordsToSave->addRecord($destinationRecord);
            }
            $this->destination->saveRecords($destinationDocName, $recordsToSave);

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
            $this->progress->advance();
        }

        $this->progress->finish();
        return true;
    }
    ...
}
```

在磁碟區類別中 `Vendor\Migration\Step\GreatBlog\Volume`，我們會檢查資料是否已完全移轉：

```php
class Volume extends \Migration\App\Step\AbstractVolume
{
    ...
    /**
     * @inheritdoc
     */
    public function perform()
    {
        $documentName = 'greatblog_post';
        $sourceCount = $this->source->getRecordsCount($documentName);
        $destinationCount = $this->destination->getRecordsCount($documentName);
        if ($sourceCount != $destinationCount) {
            $this->errors[] = sprintf(
                'Mismatch of entities in the document: %s Source: %s Destination: %s',
                $documentName,
                $sourceCount,
                $destinationCount
            );
        }

        return $this->checkForErrors(Logger::ERROR);
    }
    ...
}
```

若要新增差異移轉功能，請將新群組新增至 `deltalog.xml` 檔案。 在 `group`，指定必須檢查變更的資料表名稱：

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

然後，建立 `Delta` 類別 `Vendor\Migration\Step\GreatBlog\Delta` 延伸功能 `Migration\App\Step\AbstractDelta`：

```php
class Delta extends \Migration\App\Step\AbstractDelta
{
    /**
     * @var string
     */
    protected $mapConfigOption = 'greatblog_map_file';

    /**
     * @var string
     */
    protected $groupName = 'delta_greatblog';

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocumentName = 'greatblog_post';
        $idKeys = ['post_id'];
        $page = 0;
        while (!empty($items = $this->source->getChangedRecords($sourceDocumentName, $idKeys, $page++))) {
            $this->destination->deleteRecords(
                'greatblog_post_tags',
                $idKeys,
                $items
            );

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
        }

        //parent class takes care of greatblog_post records automatically
        return parent::perform();
    }
}
```

在範例中提供的自訂步驟實作後，系統會從單一Magento1表格中取得資料，並使用進行處理 `Vendor\Migration\Step\GreatBlog\Data` 將資料分類並儲存在兩個Magento2表格中。 新記錄和變更記錄會在差異遷移時使用 `Vendor\Migration\Step\GreatBlog\Delta` 類別。

## 禁止的擴充功能方法

由於 [!DNL Data Migration Tool] 和Magento2不斷演化，現有步驟和處理常式可能會有所變更。 我們強烈建議您不要覆寫此類步驟的行為 [地圖步驟](technical-specification.md#map-step)， [URL重寫步驟](technical-specification.md#url-rewrite-step)、和處理程式。

某些步驟不支援對應，且無法在未變更程式碼的情況下變更。 您可以撰寫在移轉結束時變更資料的額外步驟，或建立 [GitHub問題](https://github.com/magento/data-migration-tool/issues) 並詢問現有步驟上的新擴充點。
