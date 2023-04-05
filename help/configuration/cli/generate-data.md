---
title: 生成数据以进行性能测试
description: 了解如何生成大量数据以用于性能测试。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 8%

---


# 性能测试数据

使用 [Performance Toolkit](https://github.com/magento/magento2/blob/2.4/setup/performance-toolkit) 或者使用其他工具进行性能测试时，您必须生成大量数据，如存储、类别和产品。

{{file-system-owner}}

## 用户档案

您可以使用 _用户档案_ （小、中、大和超大）。 用户档案位于 `<magento_root>/setup/performance-toolkit/profiles/<ce|ee>` 目录访问Advertising Cloud的帮助。

例如， `/var/www/html/magento2/setup/performance-toolkit/profiles/ce`

下图显示了如何使用 _小_ 用户档案：

![包含生成数据的样例存储](../../assets/configuration/generate-data.png)

下表提供了有关数据生成器配置文件的详细信息：小、中、大和超大。

| 参数 | 小型配置文件 | 中型配置文件 | 中型多站点用户档案 | 大型配置文件 | 超大型配置文件 |
| --- | --- | --- | --- | --- | --- |
| `websites` | 1 | 3 | 25 | 5 | 5 |
| `store_groups` | 1 | 3 | 25 | 5 | 5 |
| `store_views` | 1 | 3 | 50 | 5 | 5 |
| `simple_products` | 800 | 24,000 | 4,000 | 300,000 | 600,000 |
| `configurable_products` | 16个，24个选项 | 640，含24个选项 | 800（含24个选项）和79（含200个选项） | 8,000，含24个选项 | 16,000，含24个选项 |
| `product_images` | 每个产品100张图像/3张图像 | 每产品1000张图像/3张图像 | 每产品1000张图像/3张图像 | 2000年图片/每产品3张图片 | 2000年图片/每产品3张图片 |
| `categories` | 30 | 300 | 100 | 3,000 | 6,000 |
| `categories_nesting_level` | 3 | 3 | 3 | 5 | 5 |
| `catalog_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `catalog_target_rules` | 5 | 5 | 5 | 5 | 5 |
| `cart_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `cart_price_rules_floor` | 2 | 2 | 2 | 2 | 2 |
| `customers` | 200 | 2,000 | 2,000 | 5,000 | 10,000 |
| `tax rates` | 130 | 40,000 | 40,000 | 40,000 | 40,000 |
| `orders` | 80 | 50,000 | 50,000 | 100,000 | 150,000 |

### 运行数据生成器

>[!WARNING]
>
>运行数据生成器之前，请禁用服务器上运行的所有cron作业。 禁用cron作业会阻止数据生成器执行与活动cron作业冲突的操作，并避免不必要的错误。

按照本节所述运行命令。 命令运行后，您必须 [重新索引所有索引器](../cli/manage-indexers.md).

命令选项：

```bash
bin/magento setup:perf:generate-fixtures <path-to-profile>
```

其中 `<path-to-profile>` 指定配置文件的绝对文件系统路径和名称。

例如，

```bash
bin/magento setup:perf:generate-fixtures /var/www/html/magento2/setup/performance-toolkit/profiles/ce/small.xml
```

小型配置文件的示例输出：

```terminal
Generating profile with following params:
    |- Websites: 1
    |- Store Groups Count: 1
    |- Store Views Count: 1
    |- Categories: 30
    |- Attribute Sets (Default): 3
    |- Attribute Sets (Extra): 10
    |- Simple products: 800
    |- Configurable products: 0
    |--- 5 products for attribute set "Attribute Set 1"
    |--- 5 products for attribute set "Attribute Set 2"
    |--- 5 products for attribute set "Attribute Set 3"
    |--- 40 products for attribute set "Dynamic Attribute Set 1-24"
    |- Product images: 100, 3 per product
    |- Customers: 200
    |- Cart Price Rules: 20
    |- Catalog Price Rules: 20
    |- Catalog Target Rules: 5
    |- Orders: 80
Generating websites, stores and store views...  done in <time>
Generating categories...  done in <time>
Generating attribute sets...  done in <time>
Generating simple products...  done in <time>
... more ...
```

## 性能固定装置

### 管理员用户

生成管理员用户。 XML配置文件节点：

```xml
<!-- Number of admin users -->
<admin_users>{int}</admin_users>
```

### 属性集

生成具有指定配置的属性集。 XML配置文件节点：

```xml
<!-- Number of product attribute sets -->
<product_attribute_sets>{int}</product_attribute_sets>

<!-- Number of attributes per set -->
<product_attribute_sets_attributes>{int}</product_attribute_sets_attributes>

<!-- Number of values per attribute -->
<product_attribute_sets_attributes_values>{int}</product_attribute_sets_attributes_values>
```

### 捆绑产品

生成捆绑产品。 生成的束选择不会单独显示在目录中。 产品按类别和网站统一分发。 如果  `assign_entities_to_all_websites` 从配置文件设置为 `1`. 产品会分配给所有网站。

XML配置文件节点：

```xml
<!-- Number of products -->
<bundle_products>{int}</bundle_products>

<!-- Number of options per each product -->
<bundle_products_options>{int}</bundle_products_options>

<!-- Number of simple products per each option -->
<bundle_products_variation>{int}</bundle_products_variation>
```

### 购物车价格规则

生成购物车价格规则。 XML配置文件节点：

```xml
<!-- Number of cart price rules -->
<cart_price_rules>{int}</cart_price_rules>

<!-- Number of conditions per rule -->
<cart_price_rules_floor>{int}</cart_price_rules_floor>
```

### 目录价格规则

生成目录价格规则。 XML配置文件节点：

```xml
<!-- Number of catalog price rules -->
<catalog_price_rules>{int}</catalog_price_rules>
```

### 类别

生成类别。 如果 `assign_entities_to_all_websites` 设置为 `0`，所有类别按根类别统一分布；否则，所有类别都将分配给一个根类别。

XML配置文件节点：

```xml
<!-- Number of categories to generate -->
<categories>{int}</categories>

<!-- Nesting level of categories -->
<categories_nesting_level>{int}</categories_nesting_level>
```

### 配置

设置配置字段的值。 XML配置文件节点：

```xml
<!-- Config variables and values for change -->
<configs>
    <config>
        <path>{string}</path> <!-- e.g. admin/security/use_form_key -->
        <scope>{string}</scope> <!-- e.g. default -->
        <scopeId>{int}</scopeId>
        <value>{int|string}</value>
    </config>

    <!-- ... more entries ... -->
</configs>
```

### 可配置产品

生成可配置产品。 生成的可配置选项不会单独显示在目录中。 产品按类别和网站统一分发。 如果 `assign_entities_to_all_websites` 设置为 `1`，则会将产品分配到所有网站。

支持以下XML节点格式：

- 默认和预定义属性集的分布：

   ```xml
   <!-- Number of configurable products -->
   <configurable_products>{int}</configurable_products>
   ```

- 根据现有属性集生成产品：

   ```xml
   <configurable_products>
   
       <config>
               <!-- Existing attribute set name -->
               <attributeSet>{string}</attributeSet>
   
               <!-- Configurable sku pattern with %s -->
               <sku>{string}</sku>
   
               <!-- Number of configurable products -->
               <products>{int}</products>
   
               <!-- Category Name. Optional. By default category name from Categories fixture will be used -->
               <category>[{string}]</category>
   
               <!-- Type of Swatch attribute e.g. color|image -->
               <swatches>{string}</swatches>
       </config>
   
   <!-- ... more entries ... -->
   </configurable_products>
   ```

- 根据动态创建的具有指定数量的属性和选项的属性集生成产品：

   ```xml
   <configurable_products>
   
       <config>
           <!-- Number of attributes in configurable product -->
           <attributes>{int}</attributes>
   
           <!-- Number of options per attribute -->
           <options>{int}</options>
   
           <!-- Configurable sku pattern with %s -->
           <sku>{string}</sku>
   
           <!-- Number of configurable products -->
           <products>{int}</products>
   
           <!-- Category Name. Optional. By default category name from Categories fixture will be used -->
           <category>[{string}]</category>
   
           <!-- Type of Swatch attribute e.g. color|image -->
           <swatches>{string}</swatches>
       </config>
   
       <!-- ... more entries ... -->
   </configurable_products>
   ```

- 根据动态创建的属性集，为每个属性生成具有指定配置的产品：

   ```xml
   <configurable_products>
   
       <config>
           <attributes>
               <!-- Configuration for a first attribute -->
               <attribute>
                   <!-- Amount of options per attribute -->
                   <options>{int}</options>
   
                   <!-- Type of Swatch attribute -->
                   <swatches>{string}</swatches>
               </attribute>
   
               <!-- Configuration for a second attribute -->
               <attribute>
                   <!-- Amount of options per attribute -->
                   <options>{int}</options>
               </attribute>
           </attributes>
   
           <!-- Configurable sku pattern with %s -->
           <sku>{string}</sku>
   
           <!-- Number of configurable products -->
           <products>{int}</products>
   
           <!-- Category Name. Optional. By default, the category name from Categories fixture will be used -->
           <category>[{string}]</category>
       </config>
   
       <!-- ... more entries ... -->
   </configurable_products>
   ```

### 客户

生成客户。 客户在所有可用网站上均可正常分发。 除客户电子邮件、客户群组和客户地址之外，每个客户都具有相同的数据。

XML配置文件节点：

```xml
<!-- Number of customers to generate -->
<customers>{int}</customers>
```

您可以使用以下XML更改客户配置：

```xml
<customer-config>
    <!-- Number of addresses per each customer -->
    <addresses-count>{int}</addresses-count>
</customer-config>
```

### 产品图像

生成产品图像。 生成不包括调整大小。

XML配置文件节点：

```xml
<product-images>
    <!-- Number of images to generate -->
    <images-count>{int}</images-count>

    <!-- Number of images to be assigned per each product -->
    <images-per-product>{int}</images-per-product>
</product-images>
```

### 索引器状态

更新索引器的状态。 XML配置文件节点：

```xml
<indexer>
    <!-- Name of indexer (e.g. catalogrule_product) -->
    <id>{string}</id>
    <set_scheduled>{bool}</set_scheduled>
</indexer>
```

### 订单数

生成具有可配置数量的不同类型订单项的订单。 （可选）为生成的订单生成不活动的报价。

XML配置文件节点：

```xml
<!-- It is necessary to enable quotes for orders -->
<order_quotes_enable>{bool}</order_quotes_enable>

<!-- Min number of simple products per each order -->
<order_simple_product_count_from>{int}</order_simple_product_count_from>

<!-- Max number of simple products per each order -->
<order_simple_product_count_to>{int}</order_simple_product_count_to>

<!-- Min number of configurable products per each order -->
<order_configurable_product_count_from>{int}</order_configurable_product_count_from>

<!-- Max number of configurable products per each order -->
<order_configurable_product_count_to>{int}</order_configurable_product_count_to>

<!-- Min number of big configurable products (with big amount of options) per each order -->
<order_big_configurable_product_count_from>{int}</order_big_configurable_product_count_from>

<!-- Max number of big configurable products (with big amount of options) per each order -->
<order_big_configurable_product_count_to>{int}</order_big_configurable_product_count_to>

<!-- Number of orders to generate -->
<orders>{int}</orders>
```

### 简单产品

生成简单的产品。 产品按默认和预定义的属性集进行分发。 如果在配置文件中指定了额外的属性集，则为： `<product_attribute_sets>{int}</product_attribute_sets>`，则产品也会按其他属性集进行分发。

产品按类别和网站统一分发。 如果 `assign_entities_to_all_websites` 设置为 `1`，则会将产品分配到所有网站。

XML配置文件节点：

```xml
<!-- Number of simple products to generate -->
<simple_products>{int}</simple_products>
```

### 网站

生成网站。 XML配置文件节点：

```xml
<!-- Number of websites to be generated -->
<websites>{int}</websites>
```

### 存储组

生成存储组(在管理员中称为 _商店_)。 商店组在网站之间正常分发。

XML配置文件节点：

```xml
<!-- Number of store groups to be generated -->
<store_groups>{int}</store_groups>
```

### 存储视图

生成存储视图。 商店视图在商店组之间正常分发。 XML配置文件节点：

```xml
<!-- Number of store views to be generated -->
<store_views>{int}</store_views>

<!-- 1 means that all stores will have the same root category, 0 means that all stores will have unique root category -->
<assign_entities_to_all_websites>{0|1}<assign_entities_to_all_websites/>
```

### 税率

生成税率。 XML配置文件节点：

```xml
<!-- Accepts name of CSV file with tax rates (<path to Commerce folder>/setup/src/Magento/Setup/Fixtures/_files) -->
<tax_rates_file>{CSV file name}</tax_rates_file>
```

## 其他配置信息：

- `<Commerce root dir>/setup/performance-toolkit/config/attributeSets.xml` — 缺省属性集

- `<Commerce root dir>/setup/performance-toolkit/config/customerConfig.xml` — 客户配置

- `<Commerce root dir>/setup/performance-toolkit/config/description.xml` — 产品完整说明配置

- `<Commerce root dir>/setup/performance-toolkit/config/shortDescription.xml` — 产品简短说明配置

- `<Commerce root dir>/setup/performance-toolkit/config/searchConfig.xml` — 配置产品简短说明和完整说明。 为了向后兼容，提供了此旧的实施。

- `<Commerce root dir>/setup/performance-toolkit/config/searchTerms.xml` — 简短和完整描述中搜索词的数量较少

- `<Commerce root dir>/setup/performance-toolkit/config/searchTermsLarge.xml` — 在简短和完整描述中使用的搜索词数量较大。
