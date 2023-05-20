---
title: 設定型別
description: 建立或擴充組態型別。
exl-id: 4390c310-b35a-431a-859f-3fd46d8ba6bf
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# 設定型別

## 擴充組態型別

若要擴充現有的組態型別，您只需在模組中建立組態檔即可。

例如，若要新增事件觀察者，您需建立 `app/code/{VendorName}/{ModuleName}/etc/events.xml` 並宣告新的觀察者。

由於事件設定型別存在於Commerce中，因此載入器和 `events.xsd` 驗證結構描述已存在且功能正常。

您的新 `events.xml` 會自動從您的模組收集並與其他 `events.xml` 其他模組的檔案。

## 建立設定型別

若要建立組態型別，您至少必須新增：

- 載入程式
- XSD驗證結構
- XML組態檔

例如，若要為新搜尋伺服器引入轉接器，讓擴充功能能夠設定如何在該伺服器中索引其實體，請建立：

- 載入程式
- XSD結構描述檔案
- 適當命名的組態檔。 例如， `search.xml`. 系統會根據您的結構描述讀取並驗證此檔案。
- 您工作所需的任何其他類別。

>[!INFO]
>
>如果新模組具有 `search.xml` 檔案載入時，它們會與您的檔案合併。

### 使用範例

若要建立組態型別，請執行下列動作：

1. 建立您的XSD檔案。
1. 建立您的XML檔案。
1. 在中定義您的設定物件 `di.xml`.

   以下範例來自Magento_Sales模組的 [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) 說明設定物件的外觀。

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

   - 第一個型別節點會設定Reader的檔案名稱，相關聯的 `Converter` 和 `SchemaLocator` 類別。
   - 然後 `pdfConfigDataStorage` 虛擬型別節點會將reader類別附加至 [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - 最後，最後一個型別節點會將該設定資料虛擬型別附加至 [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) 類別，用來實際讀取這些類別中的值 [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) 檔案。

1. 透過延伸定義讀取器 [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) 類別並重寫下列引數：

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**範例：**

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
>如果您偏好建立自己的讀者版本，您可以透過實作 `\Magento\Framework\Config\ReaderInterface`. 另請參閱 [Magento_Analytics設定讀取器](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

定義讀取器後，使用它來收集、合併、驗證組態檔，並將其轉換為內部陣列表示。

## 驗證設定型別

每個設定檔案都根據其設定型別特定的結構描述進行驗證。 範例：事件，在舊版Commerce中設定於 `config.xml`，現已設定於 `events.xml`.

可在影響相同設定型別的多個檔案合併之前（選用）和之後驗證設定檔案。 除非個別和合併檔案的驗證規則相同，否則您應該提供兩個結構描述來驗證組態檔案：

- 用於驗證個人的結構描述
- 用於驗證合併檔案的結構描述

新設定檔案必須附帶XSD驗證結構。 XML組態檔及其XSD驗證檔必須具有相同的名稱。

如果您必須為單一XML檔案使用兩個XSD檔案，則結構描述的名稱應該可識別，並與XML檔案相關聯。
如果您擁有 `events.xml` 檔案和第一個 `events.xsd` 檔案，合併的XSD檔案 `events.xml` 檔案可命名 `events_merged.xsd`.
若要確保透過適當的XSD檔案來驗證XML檔案，您必須將統一資源名稱(URN)加入XML檔案的XSD檔案中。 例如：

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

您的IDE可以在執行階段和開發期間驗證您的組態檔。
