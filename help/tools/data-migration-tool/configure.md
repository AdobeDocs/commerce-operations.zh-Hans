---
title: 設定 [!DNL Data Migration Tool]
description: 瞭解設定 [!DNL Data Migration Tool] 以在Magento1和Magento2之間傳輸資料。
exl-id: 273be997-8085-4488-a455-f6005a85b406
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 0%

---

# 設定 [!DNL Data Migration Tool]

安裝之後 [!DNL Data Migration Tool]，下列目錄包含對應和組態檔：

* Magento Open Source：
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`：從Magento Open Source1移轉至Magento Open Source2的設定和指令碼

* Adobe Commerce：
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`：從Magento Open Source1移轉至Adobe Commerce 2的設定和指令碼
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`：從Adobe Commerce 1移轉至Adobe Commerce 2的設定和指令碼

上述目錄包含每個支援版本的子目錄。

## 設定移轉

有兩種方式可設定 [!DNL Data Migration Tool]：

* 設定 [!DNL Data Migration Tool] 在獨立的模組中（建議使用）
* 變更 [!DNL Data Migration Tool] 中的設定 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/` 目錄。

若要使用原始檔控制來管理您的移轉設定並用於部署，您必須建立個別的模組。
如果您計畫執行 [!DNL Data Migration Tool] 僅在本機中，您可以編輯以下位置的檔案： `<your Magento 2 install dir>/vendor/magento/data-migration-tool/` 目錄。

### 在個別模組中設定移轉

在移轉任何資料之前，您必須建立Magento2模組。

1. 建立Magento2模組。

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/composer.json`

   ```json
   {
       "name": "vendor/migration",
       "description": "Providing config for migration",
       "config": {
           "sort-packages": true
       },
       "require": {
           "magento/framework": "*",
           "magento/data-migration-tool": "*"
       },
       "type": "magento2-module",
       "autoload": {
           "files": [
               "registration.php"
           ],
           "psr-4": {
               "Vendor\\Migration\\": ""
           }
       },
       "version": "1.0.0"
   }
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/registration.php`

   ```php
   <?php
   
   \Magento\Framework\Component\ComponentRegistrar::register(
       \Magento\Framework\Component\ComponentRegistrar::MODULE,
       'Vendor_Migration',
       __DIR__
   );
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/module.xml`

   ```xml
   <?xml version="1.0"?>
   
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
       <module name="Vendor_Migration" setup_version="1.0.0">
           <sequence>
               <module name="Magento_DataMigrationTool"/>
           </sequence>
       </module>
   </config>
   ```

1. 複製 `config.xml.dist` 從的適當目錄中的組態檔 [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`)到 `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml` 檔案。

   例如，如果您移轉 `Magento 1.9.3.6 Community Edition` 至 `Magento 2 Open Source`：

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. 在 `config.xml` 檔案，您必須設定M1和M2資料庫的存取詳細資訊和加密金鑰。

1. 如果您的M1存放區有自訂變更，您應將其餘的設定檔案對應至您的Magento1存放區自訂。 另請參閱 [使用設定和對應檔案](#migration-config).

### 在中設定移轉 `vendor` 資料夾

在移轉任何資料之前，您必須建立 `config.xml` 設定檔案（來自提供的範例）。

若要設定 [!DNL Data Migration Tool] 移轉：

1. 以或切換至以下身分登入應用程式伺服器： [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).

1. 切換到下列目錄：

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. 輸入下列命令以建立 `config.xml` 從提供的範例中：

   ```bash
   cp config.xml.dist config.xml
   ```

1. 開啟 `config.xml` 在文字編輯器中。

1. config.xml檔案至少必須包含M1和M2資料庫的存取詳細資訊以及加密金鑰。

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root"/>
   </destination>
   <options>
      <crypt_key />
   </options>
   ```

   此 &lt;crypt_key> 標籤必須包含值。 您可以在下列位置找到它： `<key>` 標籤中，此標籤位於Magento1執行個體上的app/etc/local.xml檔案中。

   選擇性引數：

   * 資料庫使用者密碼： `password=<password>`
   * 資料庫自訂連線埠： `port=<port>`
   * 表格首碼： `<source_prefix>`， `<dest_prefix>`

   例如，如果資料庫擁有者的使用者名稱為 `root` 使用密碼 `pass` 而且您會使用前置詞 `magento1` 在Magento1資料庫中，使用下列專案： `config.xml`：

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root" password="pass"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root" password="pass"/>
   </destination>
   <options>
      <source_prefix>magento1</source_prefix>
      <crypt_key>f3e25abe619dae2387df9fs594f01985</crypt_key>
   </options>
   ```

完成後，將變更儲存至 `config.xml` 並退出文字編輯器。

### 使用TLS通訊協定連線

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

## 使用設定和對應檔案

此 [!DNL Data Migration Tool] 使用 *對應檔案* 可讓您執行Magento1與Magento2資料庫之間的自訂資料庫對應，包括：

* 變更表格名稱

* 變更欄位名稱

* 忽略表格或欄位

* 將欄位的傳輸資料調整為Magento2格式

支援Magento版本的對應檔案位於的子目錄中 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

若要使用對應檔案：

1. 複製來源 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` 至 `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` 並移除 `.dist` 副檔名。

1. 更新中新複製檔案的路徑 `<options>` 節點： `config.xml`. 更新的路徑應為下列其中一項：

   1. 絕對檔案路徑，例如 `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. magento/data-migration-tool模組相對檔案路徑： `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. 根目錄相對檔案路徑Magento： `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

此 `<Magento 2 dir>/vendor/magento/data-migration-tool/etc` 和 `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` 目錄包含下列組態檔：

即使您使用 `map.xml.dist` 檔案大多數情況下，下表討論每個對應和其他檔案。

| 對應檔案名稱 | 說明 |
| --- | --- |
| `class-map.xml.dist` | Magento1和Magento2之間類別對應的字典 |
| `config.xml.dist` | 指定Magento1和Magento2資料庫組態、步驟組態和對應檔案連結的主要組態檔 |
| *僅限Adobe Commerce*. `customer-attr-document-groups.xml.dist` | 自訂客戶屬性步驟中使用的表格清單。 |
| *僅限Adobe Commerce*. `customer-attr-map.xml.dist` | 對應自訂客戶屬性步驟中使用的檔案。 |
| `deltalog.xml.dist` | 包含設定資料庫常式所需的表格清單。 |
| `eav-attribute-groups.xml.dist` | 包含執行步驟中使用的屬性清單。 |
| `eav-document-groups.xml.dist` | 包含執行步驟中使用的表格清單。 |
| `log-document-groups.xml.dist` | 包含記錄步驟中使用的表格清單。 |
| `map-eav.xml.dist` | EAV步驟中使用的對應檔案。 |
| `map-log.xml.dist` | 記錄對應檔案。 |
| *僅限Adobe Commerce*. `map-sales.xml.dist` | SalesOrder Step中使用的對應檔案。 |
| `map.xml.dist` | 對應步驟所需的對應檔案。 |
| `settings.xml.dist` | 設定移轉組態檔，指定移轉所需的規則 `core_config_data` 表格。 |
| `customer-attribute-groups.xml.dist` | 包含用於客戶屬性步驟的屬性清單。 |
| `customer-document-groups.xml.dist` | 包含用於客戶屬性步驟的表格清單。 |
| `map-customer.xml.dist` | 對應客戶屬性步驟中使用的檔案。 |
| `order-grids-document-groups.xml.dist` | 包含用於OrderGrids步驟的表格清單。 |
| `map-document-groups.xml.dist` | 定義資料插入時發生重複時更新的欄位 |
| `map-stores.xml.dist` | 對應用於商店步驟的檔案。 |
| `map-tier-price.xml.dist` | 用於層級價格步驟的對映檔案。 |
| *僅限Adobe Commerce*. `visual_merchandiser_map.xml.dist` | VisualMerchandiser步驟中使用的對應檔案。 |
| *僅限Adobe Commerce*. `visual_merchandiser_attribute_groups.xml.dist` | 包含用於VisualMerchandiser步驟的屬性清單。 |
| *僅限Adobe Commerce*. `visual_merchandiser_document_groups.xml.dist` | 包含用於VisualMerchandiser步驟的表格清單。 |

您可參閱 [[!DNL Data Migration Tool] 技術規格](technical-specification.md) 以取得更多詳細資料。
