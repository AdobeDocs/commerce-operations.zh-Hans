---
title: 配置 [!DNL Data Migration Tool]
description: 了解配置 [!DNL Data Migration Tool] 在Magento1和Magento2之间传输数据。
exl-id: 273be997-8085-4488-a455-f6005a85b406
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 0%

---

# 配置 [!DNL Data Migration Tool]

安装之后 [!DNL Data Migration Tool]，以下目录包含映射和配置文件：

* Magento Open Source：
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`：从Magento Open Source1迁移到Magento Open Source2的配置和脚本

* Adobe Commerce：
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`：从Magento Open Source1迁移到Adobe Commerce 2的配置和脚本
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`：从Adobe Commerce 1迁移到Adobe Commerce 2的配置和脚本

上述目录包含每个受支持版本的子目录。

## 配置迁移

有两种方法可配置 [!DNL Data Migration Tool]：

* 配置 [!DNL Data Migration Tool] 在单独的模块中（推荐）
* 更改 [!DNL Data Migration Tool] 中的配置 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/` 目录。

要使用源代码管理迁移配置并将其用于部署，您必须创建一个单独的模块。
如果您计划运行 [!DNL Data Migration Tool] 仅在本机中，您可以编辑文件 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/` 目录。

### 在单独的模块中配置迁移

在迁移任何数据之前，必须创建一个Magento2模块。

1. 创建Magento2模块。

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

1. 复制 `config.xml.dist` 配置文件从的相应目录 [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`)到 `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml` 文件。

   例如，如果您迁移 `Magento 1.9.3.6 Community Edition` 到 `Magento 2 Open Source`：

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. 在 `config.xml` 文件，必须设置M1和M2数据库的访问详细信息以及加密密钥。

1. 如果M1存储区有自定义更改，则应将其余配置文件映射到Magento1存储区自定义设置。 参见 [使用配置和映射文件](#migration-config).

### 在中配置迁移 `vendor` 文件夹

在迁移任何数据之前，必须创建 `config.xml` 配置文件。

要配置 [!DNL Data Migration Tool] 对于迁移：

1. 以或切换至以下身份登录到应用程序服务器： [文件系统所有者](../../installation/prerequisites/file-system/overview.md).

1. 切换到以下目录：

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. 输入以下命令以创建 `config.xml` 在提供的示例中：

   ```bash
   cp config.xml.dist config.xml
   ```

1. 打开 `config.xml` 在文本编辑器中。

1. config.xml文件至少必须包含对M1和M2数据库的访问详细信息以及加密密钥。

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

   此 &lt;crypt_key> 标记必须包含一个值。 您可以在 `<key>` 标签中，该文件位于Magento1实例上的app/etc/local.xml文件中。

   可选参数：

   * 数据库用户密码： `password=<password>`
   * 数据库自定义端口： `port=<port>`
   * 表前缀： `<source_prefix>`， `<dest_prefix>`

   例如，如果数据库所有者的用户名是 `root` 使用密码 `pass` 而你使用前缀 `magento1` 在Magento1数据库中，在下列位置使用 `config.xml`：

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

完成后，将更改保存到 `config.xml` 并退出文本编辑器。

### 使用TLS协议连接

您还可以使用TLS协议（即，使用公钥/私钥）连接到数据库。 将以下可选属性添加到 `database` 元素：

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

## 使用配置和映射文件

此 [!DNL Data Migration Tool] 用途 *映射文件* 用于在Magento1和Magento2数据库之间执行自定义数据库映射，包括：

* 更改表名

* 更改字段名称

* 忽略表或字段

* 将字段的传输数据调整为Magento2格式

支持的Magento版本的映射文件位于的子目录中 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

要使用映射文件，请执行以下操作：

1. 从以下来源复制它们 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` 到 `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` 并删除 `.dist` 扩展。

1. 更新中新复制文件的路径 `<options>` 节点 `config.xml`. 更新后的路径应为以下路径之一：

   1. 绝对文件路径，例如 `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. magento/data-migration-tool模块相对文件路径： `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. 根目录相对文件路径Magento： `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

此 `<Magento 2 dir>/vendor/magento/data-migration-tool/etc` 和 `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` 目录包含以下配置文件：

即使您正在使用 `map.xml.dist` 文件大多数情况下，下表讨论每个映射和其他文件。

| 映射文件名 | 描述 |
| --- | --- |
| `class-map.xml.dist` | Magento1和Magento2之间的类映射的字典 |
| `config.xml.dist` | 指定Magento1和Magento2数据库配置、步骤配置以及映射到文件的链接的主配置文件 |
| *仅限Adobe Commerce*. `customer-attr-document-groups.xml.dist` | 自定义客户属性步骤中使用的表的列表。 |
| *仅限Adobe Commerce*. `customer-attr-map.xml.dist` | 在自定义客户属性步骤中使用的映射文件。 |
| `deltalog.xml.dist` | 包含数据库例程设置所需的表列表。 |
| `eav-attribute-groups.xml.dist` | 包含在“简化步骤”中使用的属性列表。 |
| `eav-document-groups.xml.dist` | 包含在执行步骤中使用的表的列表。 |
| `log-document-groups.xml.dist` | 包含日志步骤中使用的表的列表。 |
| `map-eav.xml.dist` | EAV步骤中使用的映射文件。 |
| `map-log.xml.dist` | 日志映射文件。 |
| *仅限Adobe Commerce*. `map-sales.xml.dist` | SalesOrder Step中使用的映射文件。 |
| `map.xml.dist` | 映射步骤所需的映射文件。 |
| `settings.xml.dist` | 设置迁移配置文件，该文件指定迁移所需的规则 `core_config_data` 表格。 |
| `customer-attribute-groups.xml.dist` | 包含客户属性步骤中使用的属性列表。 |
| `customer-document-groups.xml.dist` | 包含客户属性步骤中使用的表的列表。 |
| `map-customer.xml.dist` | 在客户属性步骤中使用的映射文件。 |
| `order-grids-document-groups.xml.dist` | 包含在OrderGrid步骤中使用的表的列表。 |
| `map-document-groups.xml.dist` | 定义在数据插入时发生重复时更新的字段 |
| `map-stores.xml.dist` | 在存储步骤中使用的映射文件。 |
| `map-tier-price.xml.dist` | 在层价格步骤中使用的映射文件。 |
| *仅限Adobe Commerce*. `visual_merchandiser_map.xml.dist` | VisualMerchandiser步骤中使用的映射文件。 |
| *仅限Adobe Commerce*. `visual_merchandiser_attribute_groups.xml.dist` | 包含在VisualMerchandiser步骤中使用的属性列表。 |
| *仅限Adobe Commerce*. `visual_merchandiser_document_groups.xml.dist` | 包含在VisualMerchandiser步骤中使用的表的列表。 |

您可以引用 [[!DNL Data Migration Tool] 技术规范](technical-specification.md) 了解更多详细信息。
