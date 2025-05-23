---
title: 翻译词典和语言包
description: 了解如何生成翻译词典和构建语言包。
exl-id: dd27ccdd-158d-40a6-a2e2-563857820ae9
source-git-commit: 4116d0983edc797ce42d24e711fb5ecdbf8fdec9
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 0%

---

# 本地化

{{file-system-owner}}

通过Commerce翻译，您可以通过生成以下内容为多个地区和市场自定义商店并使其本地化：

- **翻译词典**，这是自定义或翻译&#x200B;_某些_&#x200B;单词和短语（如自定义模块或主题的词典）的简便方法。
- 允许您在Commerce应用程序中翻译&#x200B;_任何或所有_&#x200B;单词和短语的&#x200B;**语言包**。

请参阅[翻译概述]。

## 生成翻译词典

您可以生成[翻译字典]以自定义现有字符串、在自定义模块中翻译单词和短语、本地化主题或创建语言包。

要开始翻译，请使用命令生成一个词典CSV文件，其中包含所有现有短语和单词的收集列表。

要生成词典并开始翻译，请执行以下操作：

1. 使用翻译收集命令从启用的组件中提取可翻译的单词和短语。 内容提取到CSV文件中。
1. 翻译现有单词和短语。 您可以根据需要添加其他自定义术语。

   您可以选择使用翻译的词典：

1. 您可以将翻译字典打包到一个语言包中，并将该包提供给Commerce商店管理员。

1. 在管理员中，商店管理员[配置翻译]。

命令选项：

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

下表说明了参数和值：

| 参数 | 值 | 必需？ |
|--- |--- |--- |
| `<path to directory to translate>` | 具有可翻译代码的目录的路径；换句话说，是指具有要翻译的短语的PHP、PHTML或XML文件。<br><br>工具开始搜索您输入的路径，并搜索它包含的所有文件和子目录。<br><br>如果您使用`-m --magento`，则不要使用此参数。 | 是（词典），否（包）。 |
| `-m --magento` | 需要从此翻译词典创建语言包。 如果使用，则搜索包含bin/magento的目录。 此选项将主题或模块添加到词典中的每一行。<br><br>以下示例：<br><br>“未找到项目”、“未找到项目”、module、Magento_Wishlist | 否 |
| `-o --output="<path>"` | 指定要创建的翻译字典CSV文件的绝对文件系统路径和文件名。 您输入的值区分大小写。 CSV文件的名称必须与区域设置名称（包括字符的大小写）完全匹配。<br><br>如果忽略此参数，输出将定向到stdout。 | 否 |

>[!INFO]
>
>若要从翻译词典创建语言包，您&#x200B;_必须_&#x200B;使用`-m|--magento`选项。

### 翻译准则

翻译单词和短语时，请遵循以下准则：

- 仅更改第二列的内容。 将短语从英语(`US`)翻译成所需的语言。
- 为区域设置创建字典时，使用默认的Commerce字符串。
- 翻译时，请注意占位符： `%1`，`%2`

Commerce使用占位符插入上下文值；它们&#x200B;_不_&#x200B;用于翻译。 例如：

```text
Product '%1' has been added to shopping cart.
```

使用一个值填充：

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

生成的短语必须至少包含每个占位符中的一个。 例如，假设原始短语中存在从`%1`到`%3`的占位符。 翻译可以按任意顺序包含这些占位符，但必须至少有一个匹配项`%1`、`%2`和`%3`。 转换不能包含原始值中不存在的占位符值（例如，`%4`、`%5`等）。

翻译短语的示例：

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## 创建语言包

与翻译词典不同，您可以在Commerce应用程序中使用语言包翻译任何或所有单词和短语。 您可以使用翻译词典翻译特定组件（如模块或主题）。 [了解有关语言包的更多信息]。

此部分讨论如何创建将CSV文件写入模块和主题的语言包。 要创建语言包，您必须执行以下部分中讨论的任务：

1. [收集并翻译单词和短语](#generate-a-translation-dictionary)。 （需要`--magento`参数。）
1. [运行语言包命令](#run-the-language-package-command)。
1. [创建目录和文件](#create-directories-and-files)。
1. （可选。） [为一种语言配置多个包](#configure-multiple-packages-for-a-language)。

### 运行语言包命令

命令用法：

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

下表说明了language package命令的参数和值：

| 参数 | 值 | 必需？ |
|--- |--- |--- |
| `<source>` | CSV文件的绝对文件系统路径和文件名，该文件包含组合翻译词典和分解为语言包所需的元信息。<br><br>使用[`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict)创建CSV文件，然后创建语言包，如[创建目录和文件](#m2devgde-xlate-files)中所述。 | 是 |
| `<locale>` | [ISO 639-1]（语言）和[ISO 3166]（国家/地区）用作所有生成的CSV文件文件文件名的语言标识符。 示例： `de_DE`、`pt_PT`、`pt_BR`。 | 是 |
| `-m --mode` | 如果目标文件存在，则指定是替换现有语言包还是与新语言包合并。 合并将覆盖任何现有的短语并添加新短语。<br><br>值：合并或替换（默认）。 | 否 |
| `-d --allow-duplicates` | 包括此选项以允许语言包中存在重复项。 否则，如果命令在多个包含不同翻译的条目中遇到相同的短语，则会失败并出现错误。 | 否 |

### 创建目录和文件

语言包位于Commerce文件系统中`app/i18n/<VendorName>`下的目录，其中包含以下内容：

- 所需的许可证文件
- `composer.json`
- [注册]语言包的`registration.php`
- [`language.xml`](#language-package-languagexml)元信息文件

>[!INFO]
>
>必须将整个路径变为小写。 例如，请参阅[`de_de`]。

要创建这些文件，请执行以下操作：

1. 在`app/i18n`下创建目录。

   例如，Commerce语言包位于`app/i18n/magento`中

1. 添加所需的许可证文件。
1. 添加指定语言包依赖项的[`composer.json`]。
1. 向[`registration.php`]注册语言包
1. 按照下一节中所述添加`language.xml`元信息文件。

#### 语言包语言.xml

在`language.xml`配置文件中声明语言包时，必须指定此包的语言继承顺序。

语言继承允许您基于名为&#x200B;_父项_&#x200B;的现有翻译创建名为&#x200B;_子项_&#x200B;的翻译。 子翻译将覆盖父翻译。 但是，如果子翻译无法上传或显示或者缺少短语或单词，Commerce将使用父区域设置。 [语言包继承示例](#example-of-language-inheritance)。

要声明包，请指定以下信息：

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
- `sort_order` — 当有多个语言包可用于存储区时，上载包的优先级
- `use` — 要从中继承词典的父语言包区域设置

如有必要，您可以指定多个父包。 父包以首先列出的第一个使用为基础应用。

#### 语言继承示例

假设语言包继承自其他两个包，并且这些包还具有父包和“祖父”包。

如果语言包从两个包继承，则其`language.xml`可能如下所示：

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

- `language_package_one`继承自`en_au_package`，`en_au_package`继承自`en_ie_package`
- `language_package_two`继承自`en_ca_package`，`en_ca_package`继承自`en_us_package`

如果Commerce应用程序在`en_GB`包中找不到单词或短语，则会按以下顺序查看其他包：

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

指定语言包之间的所有继承可能会导致创建循环继承链。 使用[Magento\Test\Integrity\App\Language\CircularDependencyTest]测试来查找和修复此类链。

### 为一种语言配置多个包

为了帮助您使商店更灵活，您可以在商店中上传多个相同语言的语言包。 因此，您可以对商店的不同部分使用不同的自定义包，因为系统从可用于某种语言的所有包中编译单个包。

要为现有语言启用其他包，请为新包命名除现有语言代码名称之外的任何名称（以避免混淆）。 在语言包的`language.xml`元信息文件中指定包的配置，如下一节所述。

## 使用翻译命令的示例

以下部分提供了使用本主题中讨论的命令创建翻译词典和翻译包的端到端示例：

### 示例：为模块或主题创建翻译字典

要将德语翻译添加到要分发给其他商家的模块或主题，请执行以下操作：

1. 从模块中收集短语：

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >CSV文件名必须&#x200B;_与_&#x200B;区域设置完全匹配，包括字符的大小写。

1. 使用[这些指南](#translation-guidelines)翻译单词和短语。
1. 如有必要，请将`xx_YY.csv`复制到`/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n`或模块的主题目录（具体取决于翻译词典是用于模块还是主题）。

### 示例：创建语言包

与上述示例类似，生成CSV文件，但不要指定模块或主题目录，而是指定整个Commerce应用程序根目录。 生成的CSV包含命令可在代码中找到的所有短语。

1. 从模块中收集短语：

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >CSV文件名必须&#x200B;_与_&#x200B;区域设置完全匹配，包括字符的大小写。

1. 使用[这些指南](#translation-guidelines)翻译单词和短语。
1. 创建语言包。

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. 为语言包创建目录。

   例如，`/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. 在该目录中，添加以下所有内容：

   - 许可（如果需要）
   - `composer.json` （示例关注）
   - `registration.php` （示例关注）
   - `language.xml` （示例关注）

   **示例`composer.json`**：

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

   **示例`registration.php`**：

   ```php
   <?php
   /**
    * Copyright [first year code created] Adobe
    * All Rights Reserved.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **示例`language.xml`**：

   ```xml
   <?xml version="1.0"?>
   <!--
   Copyright [first year code created] Adobe
   All Rights Reserved.
   -->
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[翻译概述]: https://developer.adobe.com/commerce/frontend-core/guide/translations/
[翻译词典]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries
[配置翻译]: https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/stores-sales/site-store/store-localize
[了解有关语言包的更多信息]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[寄存器]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[&#39;de_de&#39;]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[&#39;composer.json&#39;]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[&#39;registration.php&#39;]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
