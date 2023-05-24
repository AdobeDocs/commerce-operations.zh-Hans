---
title: 配置类型
description: 创建或扩展配置类型。
exl-id: 4390c310-b35a-431a-859f-3fd46d8ba6bf
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# 配置类型

## 扩展配置类型

要扩展现有的配置类型，您只需在模块中创建配置文件即可。

例如，要添加事件观察者，您需要创建 `app/code/{VendorName}/{ModuleName}/etc/events.xml` 并宣布为新的观察者

由于Commerce中存在事件配置类型，因此加载程序和 `events.xsd` 验证架构已存在且运行正常。

您的新 `events.xml` 自动从模块中收集并与其他 `events.xml` 其他模块的文件。

## 创建配置类型

要创建配置类型，您必须至少添加：

- 装载机
- XSD验证架构
- XML配置文件

例如，要为新搜索服务器引入适配器，以便扩展能够配置如何在该服务器中索引其实体，请创建：

- 装载机
- XSD架构文件
- 一个正确命名的配置文件。 例如， `search.xml`. 此文件将读取并根据您的架构进行验证。
- 您的工作所需的任何其他类。

>[!INFO]
>
>如果新模块具有 `search.xml` 文件，它们会在文件加载时与文件合并。

### 使用示例

要创建配置类型，请执行以下操作：

1. 创建您的XSD文件。
1. 创建XML文件。
1. 在中定义配置对象 `di.xml`.

   Magento_Sales模块的以下示例 [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) 说明了配置对象的外观。

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
   
       <type name="Magento\Sales\Model\Order\Pdf\Config\Reader">
           <arguments>
               <argument name="fileName" xsi:type="string">pdf.xml</argument>
               <argument name="converter" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Converter</argument>
               <argument name="schemaLocator" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\SchemaLocator</argument>
           </arguments>
       </type>
   
       <virtualType name="pdfConfigDataStorage" type="Magento\Framework\Config\Data">
           <arguments>
               <argument name="reader" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Reader</argument>
               <argument name="cacheId" xsi:type="string">sales_pdf_config</argument>
           </arguments>
       </virtualType>
   
       <type name="Magento\Sales\Model\Order\Pdf\Config">
           <arguments>
               <argument name="dataStorage" xsi:type="object">pdfConfigDataStorage</argument>
           </arguments>
       </type>
   </config>
   ```

   - 第一个类型节点设置Reader的文件名，与 `Converter` 和 `SchemaLocator` 类。
   - 然后， `pdfConfigDataStorage` 虚拟类型节点将reader类附加到实例 [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - 最后，最后一个类型节点将该配置数据虚拟类型附加到 [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) 类，用于实际读取来自这些 [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) 文件。

1. 通过扩展来定义读取器 [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) 类并重写以下参数：

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**示例：**

```php
<?php
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */

namespace Vendor\ModuleName\Model\Config;

use Magento\Framework\Config\Reader\Filesystem;

class Reader extends Filesystem
{
    /**
     * List of identifier attributes for merging
     *
     * @var array
     */
    protected $_idAttributes = [
         '</path/to/node_in_your_xml_file>'        => '<identifierAttributeName>',
         '</path/to/other/node_in_your_xml_file>'  => '<identifierAttributeName>',
    ];
}
```

>[!INFO]
>
>如果您希望创建自己的阅读器版本，可以通过实施 `\Magento\Framework\Config\ReaderInterface`. 参见 [Magento_Analytics配置读取器](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

定义读取器后，使用它来收集、合并、验证配置文件，并将其转换为内部数组表示形式。

## 验证配置类型

每个配置文件都根据特定于其配置类型的架构进行验证。 示例：在早期Commerce版本中配置的事件 `config.xml`，现在已在中配置 `events.xml`.

可以在影响同一配置类型的多个文件的任何合并之前（可选）和之后验证配置文件。 除非单个文件和合并文件的验证规则相同，否则应提供两个用于验证配置文件的架构：

- 用于验证个人的架构
- 用于验证合并文件的架构

新配置文件必须附带XSD验证架构。 XML配置文件及其XSD验证文件必须具有相同的名称。

如果必须为单个XML文件使用两个XSD文件，则架构的名称应可识别并与XML文件关联。
如果您拥有 `events.xml` 文件和第一个 `events.xsd` 文件，合并的 `events.xml` 文件可命名 `events_merged.xsd`.
要确保通过适当的XSD文件验证XML文件，必须将统一资源名称(URN)添加到XML文件的XSD文件中。 例如：

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

IDE可以在运行时和开发过程中验证配置文件。
