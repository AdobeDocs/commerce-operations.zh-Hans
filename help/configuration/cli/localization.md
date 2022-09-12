---
title: 翻译字典和语言包
description: 了解如何生成翻译字典和构建语言包。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '1509'
ht-degree: 0%

---


# 本地化

{{file-system-owner}}

商务翻译允许您通过生成以下内容为多个地区和市场自定义您的商店并将其本地化：

- **翻译字典**，这是自定义或翻译的便捷方式 _部分_ 单词和短语，例如自定义模块或主题的单词和短语。
- **语言包** 能让你翻译 _任意或全部_ 商务应用程序中的单词和短语。

请参阅 [翻译概述].

## 生成翻译字典

您可以生成 [翻译词典] 要自定义现有字符串、在自定义模块中翻译单词和短语、将主题本地化或创建 [语言包](https://glossary.magento.com/language-package).

要开始翻译，请使用命令生成一个包含所有现有短语和单词的收集列表的字典CSV文件。

要生成字典并开始翻译，请执行以下操作：

1. 使用翻译收集命令从已启用的组件中提取可翻译的单词和短语。 内容提取到CSV文件中。
1. 翻译现有单词和短语。 您可以根据需要添加其他自定义术语。

   您可以选择使用翻译的词典：

1. 您可以将翻译字典打包到语言包中，并将包提供给商务商店管理员。

1. 在管理员中，存储管理员 [配置翻译].

命令选项：

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

下表说明了参数和值：

| 参数 | 值 | 必需？ |
|--- |--- |--- |
| `<path to directory to translate>` | 具有可翻译代码的目录的路径；换言之，即包含要翻译短语的PHP、PHTML或XML文件。<br><br>该工具会开始搜索您输入的路径，并搜索包含的所有文件和子目录。<br><br>如果使用 `-m --magento`. | 是（字典），否（包）。 |
| `-m --magento` | 从此翻译词典创建语言包时需要。 如果使用，则搜索包含bin/magento的目录。 此选项会向词典中的每一行添加主题或模块。<br><br>示例如下：<br><br>&quot;No Items Found&quot;,&quot;No Items Found&quot;,module，Magento_Wishlist | 否 |
| `-o --output="<path>"` | 指定要创建的翻译字典CSV文件的绝对文件系统路径和文件名。 您输入的值区分大小写。 CSV文件的名称必须与区域设置名称完全匹配，包括字符的大小写。<br><br>如果忽略此参数，则输出将定向到stdout。 | 否 |

>[!INFO]
>
>要从翻译词典创建语言包，您需要 _必须_ 使用 `-m|--magento` 选项。

### 翻译准则

翻译单词和短语时请遵循以下准则：

- 仅更改第二列的内容。 从英语中翻译短语(`US`)到所需的语言。
- 在为区域设置创建字典时，使用默认的商务字符串。
- 在翻译时，请注意占位符： `%1`, `%2`

商务使用占位符插入上下文值；它们 _not_ 用于翻译。 例如：

```text
Product '%1' has been added to shopping cart.
```

使用一个值填充：

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

生成的短语必须至少包含每个占位符中的一个。 例如，假定 `%1` to `%3` 在原始短语中。 翻译可以按任意顺序包含任意数量的这些占位符，但必须至少存在一个 `%1`, `%2`和 `%3`. 转换不能包含原始值中不存在的占位符值(例如， `%4`, `%5`，等等)。

翻译短语的示例：

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## 创建语言包

与翻译词典不同，您可以使用语言包翻译商务应用程序中的任何或所有单词和短语。 您可以使用翻译字典来翻译特定组件（如模块或主题）。 [了解有关语言包的更多信息].

本节将讨论如何创建将CSV文件写入模块和主题的语言包。 要创建语言包，必须执行以下部分中讨论的任务：

1. [收集和翻译单词和短语](#generate-a-translation-dictionary). ( `--magento` 参数是必需的。)
1. [运行语言包命令](#run-the-language-package-command).
1. [创建目录和文件](#create-directories-and-files).
1. （可选。） [为语言配置多个包](#configure-multiple-packages-for-a-language).

### 运行语言包命令

命令用法：

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

下表说明语言包命令的参数和值：

| 参数 | 值 | 必需？ |
|--- |--- |--- |
| `<source>` | CSV文件的绝对文件系统路径和文件名，其中包含要划分到语言包中所需的组合翻译字典和元信息。<br><br>使用 [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) 要创建CSV文件，请按照 [创建目录和文件](#m2devgde-xlate-files). | 是 |
| `<locale>` | [ISO 639-1] （语言）和 [ISO 3166] （国家/地区）语言的标识符，用作所有生成的CSV文件的文件名。 示例： `de_DE`, `pt_PT`, `pt_BR`. | 是 |
| `-m --mode` | 如果目标文件存在，则指定是替换现有语言包还是与新语言包合并。 合并会覆盖任何存在的短语并添加新短语。<br><br>值：合并或替换（默认）。 | 否 |
| `-d --allow-duplicates` | 包含此选项可在语言包中允许重复项。 否则，如果命令在具有不同翻译的多个条目中遇到相同的短语，则该命令将失败并出现错误。 | 否 |

### 创建目录和文件

语言包位于 `app/i18n/<VendorName>` 在商务文件系统中，包含以下内容：

- 所需的许可证文件
- `composer.json`
- `registration.php` the [寄存器] 语言包
- [`language.xml`](#language-package-languagexml) 元信息文件

>[!INFO]
>
>您必须将整个路径小写。 例如，请参阅 [`de_de`].

要创建这些文件，请执行以下操作：

1. 在下创建目录 `app/i18n`.

   例如，商务语言包位于 `app/i18n/magento`

1. 添加所需的许可证文件。
1. 添加 [`composer.json`] 指定语言包的依赖项。
1. 使用注册语言包 [`registration.php`]
1. 添加 `language.xml` 元信息文件，在下一节中讨论。

#### 语言包language.xml

在 `language.xml` 配置文件中，必须指定此包的语言继承顺序。

语言继承允许您创建名为 _孩子_ 基于称为 _父项_. 子翻译将覆盖父翻译。 但是，如果子翻译无法上传或显示，或者缺少短语或单词，则Commerce会使用父翻译 [语言](https://glossary.magento.com/locale). [语言包继承示例](#example-of-language-inheritance).

要声明资源包，请指定以下信息：

```xml
<?xml version="1.0"?>
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>en_gb</package>
    <sort_order>100</sort_order>
    <use vendor="oxford-university" package="en_us"/>
</language>
```

其中：

- `code` — 语言包区域设置（必需）
- `vendor` — 模块的供应商名称（必需）
- `package` — 语言包名称（必需）
- `sort_order` — 当存在多个可用于商店的语言包时，上传包的优先级
- `use` — 要继承字典的父语言包区域设置

如有必要，您可以指定多个父包。 父资源包是按第一个列出的、首次使用的基础应用的。

#### 语言继承示例

假定语言包从另外两个包继承，并且这些包也具有父包和“祖父”包。

如果语言包从两个包继承，则其 `language.xml` 可能如下所示：

```xml
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>language_pack</package>
    <sort_order>100</sort_order>
    <use vendor="parent-package-one" package="language_package_one"/>
    <use vendor= "parent-package-two" package="language_package_two"/>
</language>
```

在上例中：

- `language_package_one` 继承 `en_au_package` 和 `en_au_package` 继承 `en_ie_package`
- `language_package_two` 继承 `en_ca_package` 和 `en_ca_package` 继承 `en_us_package`

如果商务应用程序在 `en_GB` 包中，它会按照以下顺序查看其他包：

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

指定语言包之间的所有继承可能会导致创建循环继承链。 使用 [Magento\Test\Integrity\App\Language\CircularDependencyTest] 测试以定位和固定这些链。

### 为语言配置多个包

为帮助您提高存储的灵活性，您可以在存储中为同一语言上载多个语言包。 因此，您可以对商店的不同部分使用不同的自定义包，因为系统会从所有可用于某种语言的包中编译一个包。

要为现有语言启用附加包，请为新包命名任何名称（现有语言代码名称除外）（以避免混淆）。 在语言包的 `language.xml` 元信息文件，在下一节中讨论。

## 使用翻译命令的示例

以下各节提供了使用本主题中讨论的命令创建翻译字典和翻译包的端到端示例：

### 示例：为模块或主题创建翻译字典

要将德文翻译添加到要分发给其他商家的模块或主题，请执行以下操作：

1. 从模块中收集短语：

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >CSV文件名必须 _完全匹配_ 区域设置，包括字符的大小写。

1. 使用 [这些准则](#translation-guidelines).
1. 如有必要，请复制 `xx_YY.csv` to `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` 或模块的主题目录（取决于翻译词典是用于模块还是主题）。

### 示例：创建语言包

与上面的示例类似，生成CSV文件，但不指定模块或主题目录，而是指定整个Commerce应用程序根目录。 生成的CSV包含命令可以在代码中找到的任何短语。

1. 从模块中收集短语：

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >CSV文件名必须 _完全匹配_ 区域设置，包括字符的大小写。

1. 使用 [这些准则](#translation-guidelines).
1. 创建语言包。

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. 为语言包创建目录。

   例如，`/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. 在该目录中，添加以下所有内容：

   - 许可证（如果需要）
   - `composer.json` （示例如下）
   - `registration.php` （示例如下）
   - `language.xml` （示例如下）

   **示例`composer.json`**:

   ```json
   {
       "name": "examplecorp/language-xx_yy",
       "description": "Sample language",
       "version": "100.0.2",
       "license": [
           "OSL-3.0",
           "AFL-3.0"
       ],
       "require": {
           "magento/framework": "100.0.*"
       },
       "type": "magento2-language",
       "autoload": {
           "files": [
               "registration.php"
           ]
       }
   }
   ```

   **示例`registration.php`**:

   ```php
   <?php
   /**
    * Copyright &copy; Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **示例`language.xml`**:

   ```xml
   <?xml version="1.0"?>
   /**
   * Copyright &copy; Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
   */
   
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[翻译概述]: https://developer.adobe.com/commerce/frontend-core/guide/translations/
[翻译词典]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries
[配置翻译]: https://docs.magento.com/user-guide/stores/store-language-add.html?Highlight=translation
[了解有关语言包的更多信息]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[寄存器]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[&#39;de_de&#39;]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[&#39;composer.json&#39;]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[&#39;registration.php&#39;]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
