---
title: 生成性能测试数据
description: 了解如何为Adobe Commerce性能测试生成大量数据。 了解数据生成用户档案和测试策略。
feature: Configuration, Orders
exl-id: 2f54701d-88c4-464a-b4dc-56db14d54160
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 9%

---

# 性能测试数据

## 轮廓

您可以调整使用&#x200B;_用户档案_（小、中、大和特大）创建的数据量。 配置文件位于`<magento_root>/setup/performance-toolkit/profiles/<ce|ee>`目录中。

例如，`/var/www/html/magento2/setup/performance-toolkit/profiles/ce`

下图显示了如何使用&#x200B;_小型_&#x200B;配置文件在店面中显示产品：

![具有生成数据的店面示例](../../assets/configuration/generate-data.png)

下表提供有关数据生成器配置文件的详细信息：小、中、大和特大。

| 参数 | 小型配置文件 | Medium配置文件 | Medium多站点配置文件 | 大型配置文件 | 超大配置文件 |
| --- | --- | --- | --- | --- | --- |
| `websites` | 1 | 3 | 25 | 5 | 5 |
| `store_groups` | 1 | 3 | 25 | 5 | 5 |
| `store_views` | 1 | 3 | 50 | 5 | 5 |
| `simple_products` | 800 | 24,000 | 4,000 | 300,000 | 600,000 |
| `configurable_products` | 16个，24个选项 | 640个，带24个选项 | 800（24个选项）和79（200个选项） | 8,000个，带24个选项 | 16,000个，带24个选项 |
| `product_images` | 100张图像/每个产品3张图像 | 1000张图像/每个产品3张图像 | 1000张图像/每个产品3张图像 | 2000张图像/每个产品3张图像 | 2000张图像/每个产品3张图像 |
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

{{file-system-owner}}

>[!WARNING]
>
>在运行数据生成器之前，请禁用服务器上运行的所有cron作业。 禁用cron作业会阻止数据生成器执行与活动cron作业冲突的操作，并避免不必要的错误。
>
>如果您打算在测试性能时使用[!DNL Adobe I/O Events for Adobe Commerce]实施事件，请在订阅[事件](https://developer.adobe.com/commerce/extensibility/events/)之前运行此命令。 先订阅事件可能会导致错误。

运行本节中介绍的命令。 运行该命令后，必须[重新索引所有索引器](../cli/manage-indexers.md)。

命令选项：

```bash
bin/magento setup:perf:generate-fixtures <path-to-profile>
```

其中`<path-to-profile>`指定配置文件的绝对文件系统路径和名称。

例如，

```bash
bin/magento setup:perf:generate-fixtures /var/www/html/magento2/setup/performance-toolkit/profiles/ce/small.xml
```

小配置文件的示例输出：

```
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

## 性能夹具

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

生成捆绑产品。 生成的束选取项不会在目录中单独显示。 产品按类别和网站统一分发。 如果配置文件中的`assign_entities_to_all_websites`设置为`1`。 产品会分配到所有网站。

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

生成类别。 如果将`assign_entities_to_all_websites`设置为`0`，则所有类别将按根类别均匀分布；否则，所有类别将分配给一个根类别。

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

### 可配置的产品

生成可配置产品。 生成的可配置选项不会单独显示在目录中。 产品按类别和网站统一分发。 如果`assign_entities_to_all_websites`设置为`1`，则产品将分配到所有网站。

支持以下XML节点格式：

- 按默认属性集和预定义属性集的分布：

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

- 根据动态创建的属性集生成具有指定数量的属性和选项的产品：

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

- 根据动态创建的属性集生成产品，每个属性均具有指定的配置：

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

生成客户。 客户在所有可用网站上均服从正态分布。 每个客户都有相同的数据，但客户电子邮件、客户组和客户地址除外。

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

生成产品图像。 生成时不包括调整大小。

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

### 订购

生成具有不同订单物料类型的可配置数量的订单。 （可选）为生成的订单生成无效报价。

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

生成简单产品。 产品按默认属性和预定义属性集分发。 如果在配置文件中指定了额外的属性集： `<product_attribute_sets>{int}</product_attribute_sets>`，则产品也会按额外的属性集进行分配。

产品按类别和网站统一分发。 如果`assign_entities_to_all_websites`设置为`1`，则产品将分配到所有网站。

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

### 商店组

生成商店组（在管理员中称为&#x200B;_商店_）。 商店组在网站之间正常分布。

XML配置文件节点：

```xml
<!-- Number of store groups to be generated -->
<store_groups>{int}</store_groups>
```

### 商店视图

生成商店视图。 存储视图在存储组之间正常分布。 XML配置文件节点：

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

- `<Commerce root dir>/setup/performance-toolkit/config/attributeSets.xml` — 默认属性集

- `<Commerce root dir>/setup/performance-toolkit/config/customerConfig.xml` — 客户配置

- `<Commerce root dir>/setup/performance-toolkit/config/description.xml` — 产品完整说明配置

- `<Commerce root dir>/setup/performance-toolkit/config/shortDescription.xml` — 产品简要说明配置

- `<Commerce root dir>/setup/performance-toolkit/config/searchConfig.xml` — 产品简短和完整说明的配置。 提供此旧版实施是为了向后兼容。

- `<Commerce root dir>/setup/performance-toolkit/config/searchTerms.xml` — 搜索词较少，仅提供简短和完整的描述

- `<Commerce root dir>/setup/performance-toolkit/config/searchTermsLarge.xml` — 要用于简短和完整描述的搜索词更多。
