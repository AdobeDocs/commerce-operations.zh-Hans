---
title: 自定义 [!DNL Data Migration Tool]
description: 了解如何自定义 [!DNL Data Migration Tool] 在Magento1和Magento2之间传输扩展创建的数据。
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# 配置 [!DNL Data Migration Tool]

有时由创建的数据格式和结构 [扩展](https://marketplace.magento.com/extensions.html) 或自定义代码在Magento1和Magento2之间不同。 在中使用扩展点 [!DNL Data Migration Tool] 以迁移此数据。 如果数据格式和结构相同，则该工具可以自动迁移数据，而无需用户干预。

在迁移期间， [映射步骤](technical-specification.md#map-step) 扫描并比较所有Magento1和Magento2表，包括由扩展创建的表。 如果表相同，则该工具会自动迁移数据。 如果表不同，工具将终止并通知用户。

>[!NOTE]
>
>阅读 [技术规范](technical-specification.md) 在尝试扩展 [!DNL Data Migration Tool]. 另外，请查看 [迁移指南](../overview.md) 以了解有关使用迁移工具的一般信息。


## 较小的数据格式和结构更改

在大多数情况下， [映射步骤](technical-specification.md#map-step) 已使用中的以下方法充分解析少量数据格式和结构更改 `map.xml` 文件：

- 使用映射规则更改表或字段名称
- 使用现有处理程序或自定义处理程序转换数据格式

下面显示了同时使用映射规则和处理程序的示例。 此示例使用名为“GreatBlog”的假定Magento1扩展，该扩展已针对Magento2进行了改进。

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

- 不要从迁移不必要的数据 `great_blog_index` 索引表。
- 表 `great_blog_publication` 已重命名为 `great_blog_post` 在Magento2中，因此数据会迁移到新表中。
   - 此 `summary` 字段已重命名为 `title`，因此数据会迁移到新字段中。
   - 此 `priority` 字段已被删除并且不再存在于Magento2中。
   - 中的数据 `body` 字段已更改格式，应由自定义处理程序处理： `\Migration\Handler\GreatBlog\NewFormat`.
- 为Magento2中的“GreatBlog”扩展开发了一个新的评级功能。
   - 新 `great_blog_rating` 已创建表。
   - 新 `great_blog_post.rating` 字段已创建。

### 在其他步骤中扩展映射

其他步骤支持映射，例如 [EAV步骤](technical-specification.md#eav-step) 和客户属性步骤。 这些步骤将迁移预定义的Magento表列表。 例如，假设“GreatBlog”扩展在 `eav_attribute` 表和Magento2中更改的名称。 因为表格是由 [EAV步骤](technical-specification.md#eav-step)，应为编写映射规则 `map-eav.xml` 文件。 此 `map.xml` 和 `map-eav.xml` 文件使用相同的 `map.xsd` 架构，因此映射规则保持不变。

## 主要数据格式和结构更改

除了“映射步骤”之外， `config.xml` 文件，用于迁移具有主要格式和结构更改的数据，包括：

- [Url重写步骤](technical-specification.md#url-rewrite-step)
- OrderGrid步骤
- [EAV步骤](technical-specification.md#eav-step)

不像 [映射步骤](technical-specification.md#map-step)，则这些步骤扫描的是预定义的表列表，而不是所有表。

对于主要的数据格式和结构更改，请创建一个自定义步骤。

### 创建自定义步骤

使用相同的“GreatBlog”示例，假设扩展在Magento1中具有一个表，但经过重新设计以在Magento2中具有两个表。

在Magento1中，有一个 `greatblog_post` 表：

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

在Magento2中，为标签创建了新表 `greatblog_post_tags` 引入了：

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

MAGENTO2 `greatblog_post` 现在，表格将如下所示：

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

要将所有数据从旧表结构迁移到新表结构，您可以在中创建自定义步骤 `config.xml` 文件。 例如：

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

刀具根据步骤在 `config.xml` 文件；从上到下。 在我们的示例中， `GreatBlog Step` 最后运行。

步骤可以包含四种类型的类：

- 完整性检查
- 数据传送
- 音量检查
- 增量投放

>[!NOTE]
>
>请参阅 [配置](technical-specification.md#configuration)， [步骤内部](technical-specification.md#step-internals)， [暂存](technical-specification.md#step-stages)、和 [运行模式](technical-specification.md#running-modes) 以了解更多信息。


可以在这些类中组合复杂的SQL查询，以获取和迁移数据。 此外，这些表应在 [映射步骤](technical-specification.md#map-step) 因为它会扫描所有现有表并尝试迁移数据，除非数据位于 `<ignore>` 的标记 `map.xml` 文件。

对于完整性检查，在 `config.xml` 文件，以验证表结构是否符合预期。

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

映射文件 `map-greatblog.xml`：

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

完整性检查类 `Vendor\Migration\Step\GreatBlog\Integrity` 扩展 `Migration\App\Step\AbstractIntegrity` 并包含 `perform` 我们验证表结构的方法：

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

接下来，必须创建一个类来处理数据并将其保存到Magento2数据库中 `Vendor\Migration\Step\GreatBlog\Data`：

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

在Volume类中 `Vendor\Migration\Step\GreatBlog\Volume`，我们会检查数据是否已完全迁移：

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

要添加增量迁移功能，请将新组添加到 `deltalog.xml` 文件。 在 `group`，指定必须检查其更改的表名：

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

然后，创建 `Delta` 类 `Vendor\Migration\Step\GreatBlog\Delta` 扩展了 `Migration\App\Step\AbstractDelta`：

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

在示例中提供的自定义步骤实施之后，系统从单个Magento1表中获取数据，并使用对其进行处理 `Vendor\Migration\Step\GreatBlog\Data` 类并将数据存储在两个Magento2表中。 在增量迁移中使用提供新的和更改的记录 `Vendor\Migration\Step\GreatBlog\Delta` 类。

## 禁止的扩展方法

由于 [!DNL Data Migration Tool] 和Magento2在不断发展，现有步骤和处理程序可能会发生更改。 我们强烈建议不要覆盖 [映射步骤](technical-specification.md#map-step)， [URL重写步骤](technical-specification.md#url-rewrite-step)、和处理程序。

某些步骤不支持映射，因此不能在不更改代码的情况下更改这些步骤。 您可以编写一个额外的步骤以在迁移结束时更改数据，也可以创建 [GitHub问题](https://github.com/magento/data-migration-tool/issues) 并请求在现有步骤上添加新的扩展点。
