---
title: 自定义 [!DNL Data Migration Tool]
description: 了解如何自定义 [!DNL Data Migration Tool] 用于在Magento1和Magento2之间传输由扩展创建的数据。
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 配置 [!DNL Data Migration Tool]

有时，创建的数据格式和结构 [扩展](https://marketplace.magento.com/extensions.html) 或者，自定义代码在Magento1和Magento2中不同。 在 [!DNL Data Migration Tool] 迁移此数据。 如果数据格式和结构相同，则该工具可以自动迁移数据，而无需用户干预。

在迁移期间， [映射步骤](technical-specification.md#map-step) 扫描并比较所有Magento1和Magento2表，包括由扩展创建的表。 如果表相同，则该工具会自动迁移数据。 如果表不同，该工具将终止并通知用户。

>[!NOTE]
>
>阅读 [技术规范](technical-specification.md) 在尝试扩展 [!DNL Data Migration Tool]. 另外，请查看 [迁移指南](../overview.md) 以了解有关使用迁移工具的常规信息。


## 次要数据格式和结构更改

在大多数情况下， [映射步骤](technical-specification.md#map-step) 使用 `map.xml` 文件：

- 使用映射规则更改表或字段名称
- 使用现有处理程序或自定义处理程序转换数据格式

以下示例显示了如何同时使用映射规则和处理程序。 此示例使用一个名为“GreatBlog”的假设Magento1扩展，该扩展已对Magento2进行了改进。

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

- 请勿从 `great_blog_index` 索引表。
- 表格 `great_blog_publication` 已重命名为 `great_blog_post` 在Magento2中，因此数据会迁移到新表。
   - 的 `summary` 字段已重命名为 `title`，因此数据将迁移到新字段。
   - 的 `priority` 字段，且该字段在Magento2中不再存在。
   - 中的数据 `body` 字段的格式已更改，且应由自定义处理程序处理： `\Migration\Handler\GreatBlog\NewFormat`.
- 在Magento2中为“GreatBlog”扩展开发了新的评级功能。
   - 新 `great_blog_rating` 表。
   - 新 `great_blog_post.rating` 字段。

### 在其他步骤中扩展映射

其他步骤支持映射，例如 [EAV步骤](technical-specification.md#eav-step) 和客户属性步骤。 这些步骤可迁移预定义的Magento表列表。 例如，假定“GreatBlog”扩展在 `eav_attribute` 表和Magento2中更改的名称。 由于表由 [EAV步骤](technical-specification.md#eav-step)，则应为 `map-eav.xml` 文件。 的 `map.xml` 和 `map-eav.xml` 文件使用相同的 `map.xsd` 架构，因此映射规则保持不变。

## 主要数据格式和结构更改

除了映射步骤之外， `config.xml` 数据迁移的文件，主要格式和结构变化包括：

- [Url重写步骤](technical-specification.md#url-rewrite-step)
- 顺序网格步骤
- [EAV步骤](technical-specification.md#eav-step)

与 [映射步骤](technical-specification.md#map-step)，这些步骤将扫描预定义的表列表，而不是所有表。

对于主要数据格式和结构更改，请创建自定义步骤。

### 创建自定义步骤

使用相同的“GreatBlog”示例，假设扩展在Magento1中有一个表，但经过重新设计，在Magento2中有两个表。

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

在Magento2中，新增了标记表 `greatblog_post_tags` 引入：

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

Magento2 `greatblog_post` 表格现在如下所示：

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

要将所有数据从旧表结构迁移到新表结构，您可以在 `config.xml` 文件。 例如：

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

该工具根据步骤在 `config.xml` 文件；从上到下。 在本例中， `GreatBlog Step` 最后运行。

步骤可以包括四种类型的类：

- 完整性检查
- 数据传送
- 卷检查
- 增量传送

>[!NOTE]
>
>请参阅 [配置](technical-specification.md#configuration), [步骤内部](technical-specification.md#step-internals), [阶段](technical-specification.md#step-stages)和 [运行模式](technical-specification.md#running-modes) 以了解更多信息。


复杂的SQL查询可以组合在这些类中以获取和迁移数据。 此外，在 [映射步骤](technical-specification.md#map-step) 因为它会扫描所有现有表并尝试迁移数据，除非它位于 `<ignore>` 标记 `map.xml` 文件。

对于完整性检查，请在 `config.xml` 文件来验证表结构是否与预期一致。

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

映射文件 `map-greatblog.xml`:

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

完整性检查类 `Vendor\Migration\Step\GreatBlog\Integrity` 扩展 `Migration\App\Step\AbstractIntegrity` 和包含 `perform` 验证表结构的方法：

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

接下来，必须创建一个类以处理数据并将其保存到Magento2数据库 `Vendor\Migration\Step\GreatBlog\Data`:

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

在卷类中 `Vendor\Migration\Step\GreatBlog\Volume`，我们会检查数据是否已完全迁移：

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

要添加增量迁移功能，请在 `deltalog.xml` 文件。 在 `group`，指定必须检查以进行更改的表的名称：

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

然后，创建 `Delta` 类 `Vendor\Migration\Step\GreatBlog\Delta` 延伸 `Migration\App\Step\AbstractDelta`:

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

在示例中提供的自定义步骤实施之后，系统会从单个Magento1表中获取数据，并使用 `Vendor\Migration\Step\GreatBlog\Data` 类并将数据存储在两个Magento2表中。 在增量迁移中，使用 `Vendor\Migration\Step\GreatBlog\Delta` 类。

## 禁止的扩展方法

自 [!DNL Data Migration Tool] 而Magento2不断演变，现有步骤和处理程序都会发生更改。 我们强烈建议不要覆盖诸如 [映射步骤](technical-specification.md#map-step), [URL重写步骤](technical-specification.md#url-rewrite-step)、和处理程序之间的映射。

某些步骤不支持映射，因此不更改代码便无法更改。 您可以编写一个额外的步骤来在迁移结束时更改数据，也可以创建 [GitHub问题](https://github.com/magento/data-migration-tool/issues) 并在现有步骤中请求新的扩展点。
