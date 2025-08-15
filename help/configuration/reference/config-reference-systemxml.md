---
title: system.xml引用
description: 了解系统XML文件如何管理Commerce应用程序配置。
feature: Configuration, System
badge: label="作者：David Lambauer" type="Informative" url="https://github.com/DavidLambauer" tooltip="大卫·兰鲍尔"
exl-id: a6c5de6c-e8da-4eca-bbfb-592904b2c53f
source-git-commit: e231a27d70e29b01c872b0655168e31f590d4876
workflow-type: tm+mt
source-wordcount: '2709'
ht-degree: 0%

---

# system.xml引用

`system.xml`文件允许您管理Commerce系统配置。 使用此主题作为`system.xml`文件的常规引用。 `system.xml`文件位于给定Commerce 2扩展名中的`etc/adminhtml/system.xml`下。

以下代码片段显示了文件的裸骨架：

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <!-- PLACE YOUR MODULE SPECIFIC CONFIGURATION HERE -->
    </system>
</config>
```

>[!TIP]
>
>如果希望在IDE中进行即时*XSD验证，则可以运行`bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>`。

## 选项卡//区域//组//字段

在`system.xml`文件中，可以定义四个相互关联的不同类型的实体。 以下部分介绍选项卡、部分、组和字段之间的关系。 以下屏幕截图显示了管理员后端中的Commerce 2系统配置。
红色方块标记在`system.xml`文件中定义的不同类型：

![在管理员中显示已配置分区的屏幕截图。](../../assets/configuration/magento2-system-configuration.png)

选项卡用于在语义上分割不同的配置区域。 每个选项卡可以包含一个或多个部分，这些部分也可以作为子菜单引用。 分区包含一个或多个组。
每个组列出一个或多个字段。 您还可以使用组为以下字段添加一般说明。 如前所述，每个组可以有一个或多个字段。 字段是最小的实体
在系统配置上下文中。

## 选项卡

`<tab>` — 标记引用了系统配置中的现有选项卡或新选项卡。

### 选项卡属性引用

`<tab>` — 标记可以具有以下属性：

| 属性 | 描述 | 类型 | 必填 |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | 定义用于引用部分的标识符。 | `typeId` | 必填 |
| `translate` | 定义应可翻译的字段。 提供`label`以使标签可翻译。 | `string` | 可选 |
| `sortOrder` | 定义部分的排序顺序。 高数字会将部分推到页面底部；低数字会将部分推到页面顶部。 | `float` | 可选 |
| `class` | 将定义的CSS类添加到渲染的选项卡HTML元素。 | `string` | 可选 |

### 选项卡节点引用

`<tab>` — 标记可以具有以下子项：

| 节点 | 描述 | 类型 |
|---------|------------------------------------------------------|----------|
| `label` | 定义在前端中显示的标签。 | `string` |

### 示例：创建选项卡

以下代码段演示了使用示例数据创建新选项卡的过程。

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>
    </system>
</config>
```

上面的代码片段将创建一个标识符为`A_UNIQUE_ID`的新选项卡。 由于`translate`属性已定义并引用了标签，因此`label`节点是可翻译的。 在渲染过程中，CSS类`a-custom-css-class-to-style-this-tab`将应用于为此选项卡创建的HTML元素。
值为`sortOrder`的`10`属性定义呈现时选项卡在所有选项卡列表中的位置。

## 区域

`<section>` — 标记引用了系统配置中的现有节或新节。

### 章节属性参考

`<section>` — 标记可以具有以下属性：

| 属性 | 描述 | 类型 | 必填 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | 定义用于引用部分的标识符。 | `typeId` | 必填 |
| `translate` | 定义应可翻译的字段。 提供`label`以使标签可翻译。 | `string` | 可选 |
| `type` | 定义渲染的HTML元素的输入类型。 默认为`text`。 | `string` | 可选 |
| `sortOrder` | 定义部分的排序顺序。 高数字会将部分推到页面底部；低数字会将部分推到页面顶部。 | `float` | 可选 |
| `showInDefault` | 定义节是否显示在默认配置范围内。 指定`1`显示节，指定`0`隐藏节。 | `int` | 可选 |
| `showInStore` | 定义节是否显示在存储级别。 指定`1`显示节，指定`0`隐藏节。 | `int` | 可选 |
| `showInWebsite` | 定义是否在网站级别显示部分。 指定`1`显示节，指定`0`隐藏节。 | `int` | 可选 |
| `canRestore` | 定义能否将部分还原为默认值。 | `int` | 可选 |
| `advanced` | 自100.0.2起已弃用。 | `bool` | 可选 |
| `extends` | 通过提供另一部分的标识符，此节点的内容将扩展您引用的部分。 | `string` | 可选 |

### 节节点引用

`<section>` — 标记可以具有以下子项：

| 节点 | 描述 | 类型 |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | 定义在前端中显示的标签。 | `string` |
| `class` | 将定义的CSS类添加到渲染的部分HTML元素。 | `string` |
| `tab` | 引用关联的选项卡。 需要选项卡的ID。 | `typeTabId` |
| `header_css` | 在编写本报告时既未使用也未评估。 | `string` |
| `resource` | 引用ACL资源以提供此部分的权限设置。 | `typeAclResourceId` |
| `group` | 定义一个或多个子组。 | `typeGroup` |
| `frontend_model` | 指定其他前端模型以更改渲染并修改输出。 | `typeModel` |
| `include` | 用于包含其他`system_include.xsd`个兼容文件。 通常用于构造大型`system.xml`文件。 | `includeType` |

### 示例：创建部分并将其分配给选项卡

以下代码片段演示了创建新部分的基本用法。

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>
        </section>
    </system>
</config>
```

上述部分定义了ID `A_UNIQUE_SECTION_ID`，在默认配置视图和存储上下文中可见。 `label`节点是可翻译的。 分区与ID为`A_UNIQUE_ID`的选项卡相关联。 只有在ACL `VENDOR_MODULE::path_to_the_acl_resource`中定义权限的用户才能访问该部分。

## 组

`<group>` — 标记用于将字段组合在一起。

### 组属性引用

`<group>` — 标记可以具有以下属性：

| 属性 | 描述 | 类型 | 必填 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | 定义用于引用组的标识符。 | `typeId` | 必填 |
| `translate` | 定义应可翻译的字段。 提供`label`以使标签可翻译。 多个字段应使用空格分隔。 | `string` | 可选 |
| `type` | 定义渲染的HTML元素的输入类型。 默认为`text`。 | `string` | 可选 |
| `sortOrder` | 定义部分的排序顺序。 高数字会将部分推到页面底部；低数字会将部分推到页面顶部。 | `float` | 可选 |
| `showInDefault` | 定义组是否显示在默认配置范围内。 指定`1`显示组，指定`0`隐藏组。 | `int` | 可选 |
| `showInStore` | 定义组是否显示在存储级别。 指定`1`显示组，指定`0`隐藏组。 | `int` | 可选 |
| `showInWebsite` | 定义是否在网站级别显示组。 指定`1`显示组，指定`0`隐藏组。 | `int` | 可选 |
| `canRestore` | 定义是否可以将该组还原为默认值。 | `int` | 可选 |
| `advanced` | 自100.0.2起已弃用。 | `bool` | 可选 |
| `extends` | 通过提供另一个组的标识符，此节点的内容将扩展您引用的部分。 | `string` | 可选 |

### 组节点引用

`<group>` — 标记可以具有以下子项：

| 节点 | 描述 | 类型 |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | 定义在前端中显示的标签。 | `string` |
| `fieldset_css` | 向组字段集添加一个或多个CSS类。 | `string` |
| `frontend_model` | 指定其他前端模型以更改渲染并修改输出。 | `typeModel` |
| `clone_model` | 指定给定模型以克隆字段。 | `typeModel` |
| `clone_fields` | 启用或禁用了字段的克隆。 | `int` |
| `help_url` | 不可扩展。 请参阅下文。 | `typeUrl` |
| `more_url` | 不可扩展。 请参阅下文。 | `typeUrl` |
| `demo_link` | 不可扩展。 请参阅下文。 | `typeUrl` |
| `comment` | 在组标签下添加注释。 通过使用`<![CDATA[//]]>`，可以应用HTML。 | `string` |
| `hide_in_single_store_mode` | 该组是否应该在单存储模式下可见。 `1`隐藏组；`0`显示该组。 | `int` |
| `field` | 定义此组下应可用的一个或多个字段。 | `field` |
| `group` | 定义一个或多个子组。 | `unbounded` |
| `depends` | 可用于声明对其他字段的依赖关系。 仅当给定字段的值为`1`时才用于显示特定字段/组。 此节点需要`section/group/field`字符串。 | `depends` |
| `attribute` | 前端模型可以使用自定义属性。 通常用于使给定的前端模型更动态。 | `attribute` |
| `include` | 用于包含其他`system_include.xsd`个兼容文件。 通常用于构造大型`system.xml`文件。 | `includeType` |

>[!WARNING]
>
>节点`more_url`、`demo_url`和`help_url`由只使用一次的PayPal前端模型定义。 这些节点不可重用。

### 示例：为给定节创建组

以下代码段演示了创建新组的基本用法。

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label comment" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>
                <!-- Add your fields here. -->
            </group>
        </section>
    </system>
</config>
```

上述组定义ID `A_UNIQUE_GROUP_ID`，在默认配置视图和存储上下文中可见。 `label`和`comment`都标记为可翻译。

## 字段

`<field>` — 标记用在`<group>` — 标记内部以定义特定的配置值。

### 字段属性引用

`<field>` — 标记可以具有以下属性：

| 属性 | 描述 | 类型 | 必填 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | 定义用于引用字段的标识符。 | `typeId` | 必填 |
| `translate` | 定义应可翻译的字段。 提供`label`以使标签可翻译。 多个字段应使用空格分隔。 | `string` | 可选 |
| `type` | 定义渲染的HTML元素的输入类型。 默认为`text`。 | `string` | 可选 |
| `sortOrder` | 定义部分的排序顺序。 高数字会将部分推到页面底部；低数字会将部分推到页面顶部。 | `float` | 可选 |
| `showInDefault` | 定义字段是否显示在默认配置范围中。 指定`1`显示字段，指定`0`隐藏字段。 | `int` | 可选 |
| `showInStore` | 定义字段是否显示在存储级别。 指定`1`显示字段，指定`0`隐藏字段。 | `int` | 可选 |
| `showInWebsite` | 定义字段是否显示在网站级别。 指定`1`显示字段，指定`0`隐藏字段。 | `int` | 可选 |
| `canRestore` | 定义字段是否可以还原为默认值。 | `int` | 可选 |
| `advanced` | 自100.0.2起已弃用。 | `bool` | 可选 |
| `extends` | 通过提供另一个字段的标识符，此节点的内容将扩展您引用的部分。 | `string` | 可选 |

### 字段类型引用

`<field>` — 标记的`type=""`属性可以具有以下值：

| 类型 | 描述 |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | 标准、单行文本字段 |
| `textarea` | 文本块 |
| `select` | 普通下拉列表，可能需要自定义`source_model`。 也用于`Yes/No`选择。 有关示例，请参阅`Magento\Search\Model\Adminhtml\System\Config\Source\Engine`。 |
| `multiselect` | 类似`select`，但多个选项有效。 |
| `button` | 触发即时事件的按钮。 需要自定义前端模型来定义按钮文本和操作。 有关示例，请参阅`Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean`。 |
| `obscure` | 一个文本字段，其值已加密并显示为`****`。 在浏览器中使用“检查元素”更改类型不会显示值。 |
| `password` | 与`obscure`类似，只是隐藏值未加密，在浏览器中使用“Inspect Element”强制更改类型确实会显示该值。 |
| `file` | 允许上传文件以供处理。 |
| `label` | 显示标签而不是可编辑字段。 当字段仅在特定范围上可编辑时（例如，仅存储视图级别），使用此类型。 |
| `time` | 使用三个下拉菜单（小时、分钟和秒）进行控制以设置时间。 |
| `allowspecific` | 特定国家/地区的多选列表。 需要`source_model`，例如`Magento\Shipping\Model\Config\Source\Allspecificcountries` |
| `image` | 允许上传图像。 |
| `note` | 允许向页面添加信息性注释。 此类型需要`frontend_model`才能渲染注释。 |

也可以创建自定义字段类型。 这通常在需要带有操作的特殊按钮时完成。 要实现此目的，需要两个主要元素：

- 在`adminhtml`区域中创建块
- 正在将`type=""`设置为此块的路径

块本身至少需要`__construct`方法和`getElementHtml()`方法。 [Magento_OfflineShipping](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping)是自定义类型的简单示例。

例如，在OfflineShipping模块中， Export按钮在`Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export`中定义，字段定义如下所示：

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### 字段节点引用

`<field>` — 标记可以具有以下子项：

| 节点 | 描述 | 类型 |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | 定义在前端中显示的标签。 | `string` |
| `comment` | 在字段标签下添加评论。 通过使用`<![CDATA[//]]>`，可以应用HTML。 | `string` |
| `tooltip` | 另一个可用于描述此字段含义的前端元素。 在字段旁边显示为小图标。 | `string` |
| `hint` | 显示附加信息。 仅对特定`frontend_model`可用。 | `string` |
| `frontend_class` | 将定义的CSS类添加到渲染的部分HTML元素。 | `string` |
| `frontend_model` | 指定其他前端模型以更改渲染并修改输出。 | `typeModel` |
| `backend_model` | 指定其他后端模型以修改配置的值。 | `typeModel` |
| `source_model` | 指定提供一组特定值的不同源模型。 | `typeModel` |
| `config_path` | 可用于覆盖字段的常规配置路径。 | `typeConfigPath` |
| `validate` | 定义不同的验证规则（用空格分隔）。 下面列出了可用验证规则的完整参考列表。 | `string` |
| `can_be_empty` | 在`type`为`multiselect`时使用，以指定字段可以为空。 | `int` |
| `if_module_enabled` | 仅在启用给定模块时用于显示字段。 | `typeModule` |
| `base_url` | 与`upload_dir`结合使用进行文件上载。 | `typeUrl` |
| `upload_dir` | 指定上载的目标目录。 此节点具有其他属性和节点。 使用此项之前先查找它们。 | `typeUploadDir` |
| `button_url` | 如果指定了`button_url`和`button_label`，则显示按钮。 通常与自定义前端模型结合使用。 | `typeUrl` |
| `button_label` | 如果指定了`button_label`和`button_url`，则显示按钮。 通常与自定义前端模型结合使用。 | `string` |
| `more_url` | 不可扩展。 请参阅下文。 | `typeUrl` |
| `demo_url` | 不可扩展。 请参阅下文。 | `typeUrl` |
| `hide_in_single_store_mode` | 该组是否应该在单存储模式下可见。 `1`隐藏组；`0`显示该组。 | `int` |
| `options` | 未使用。 可能已被弃用。 | `complexType` |
| `depends` | 可用于声明对其他字段的依赖关系。 用于当给定字段的值为`1`时仅显示特定字段/组。 此节点需要`section/group/field`字符串。 | `complexType` |
| `attribute` | 前端模型可以使用自定义属性。 通常用于使给定的前端模型更动态。 | `complexType` |
| `requires` | 不可扩展。 请参阅下文。 | `complexType` |

>[!WARNING]
>
>节点`more_url`、`demo_url`、`requires`和`options`由不同的核心付款模型定义，并且只使用一次。 这些节点不可重用。

### 示例：在给定组中创建两个字段

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>

                <field id="A_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="select">
                    <label>Feature Flag Example</label>
                    <comment>This field is an example for a basic yes or no select.</comment>
                    <tooltip>Usually these kinds of fields are used to enable or disable a given feature. Other fields might be dependent to this and will only appear if this field is set to yes.</tooltip>
                    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
                </field>

                <field id="ANOTHER_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="text">
                    <label>A meaningful field label</label>
                    <comment>A descriptive text explaining this configuration field.</comment>
                    <tooltip>Another possible frontend element that also can be used to describe the meaning of this field. Will be displayed as a small icon beside the field.</tooltip>
                    <validate>required-entry no-whitespace</validate> <!-- Field is required and must not contain any whitespace. -->
                    <if_module_enabled>VENDOR_MODULE</if_module_enabled>
                    <depends> <!-- This field will only be visible if the field with the id A_UNIQUE_FIELD_ID is set to value 1 -->
                        <field id="A_UNIQUE_FIELD_ID">1</field>
                    </depends>
                </field>
            </group>
        </section>
    </system>
</config>
```

上面的示例创建了两个字段，它们在默认视图和存储视图中均可见/可配置。 这两个字段均具有注释和工具提示以向用户描述其用途。 `label`节点是可翻译的。
全局启用`ANOTHER_UNIQUE_FIELD_ID`中的给定模块时，标识符为`if_module_enabled`的字段可见。 该字段还根据规则`required-entry`和`no-whitespace`验证其值。
标识符为`A_UNIQUE_FIELD_ID`的字段定义了一个不同的源模型，它提供该值`Yes`和`No`。

### 通用源模型

Commerce 2 Core提供了以下源模型。 一般来说，源模型要多得多；以下列表描述了最常见的模型。 请注意，这些源模型需要将字段属性`type`设置为`select`才能正常工作。

| Source模型 | 描述 |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | 提供值`Yes`、`No`和`Specified`。 |
| `Magento\Config\Model\Config\Source\Enabledisable` | 提供值`Enable`、`Disable`。 在数据库中将值保存为`0`和`1`。 |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | 提供值`1 Hour`、`2 Hours`、`6 Hours`、`12 Hours`和`24 Hours`。 值将另存为整数。 |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | 提供时间格式（12小时/24小时）的值。 |
| `Magento\Cron\Model\Config\Source\Frequency` | 提供值`Daily`、`Weekly`和`Monthly`。 值在数据库中保存为`D`、`W`和`M`。 |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | 以ISO 639-1格式提供给定语言的双字母代码值（例如en）。 |
| `Magento\Config\Model\Config\Source\Locale` | 提供与上述值类似的值，但属于区域设置代码（例如en_US）。 |

### 字段验证

字段可以分配一个或多个验证器类，以确保用户的输入符合扩展的要求。 可以使用`<validate>`标记应用验证规则。
以下示例验证一个字段并添加多个不同的验证规则。

```xml
<field id="A_CUSTOM_IDENTIFIER" showInDefault="1" showInWebsite="0" showInStore="1">
    <validate>required-entry validate-clean-url no-whitespace</validate>
</field>
```

可以使用以下验证规则：

| 规则 | 描述 |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `alphanumeric` | 仅允许使用字母、数字、空格或下划线。 |
| `integer` | 允许正数或负数非小数。 |
| `ipv4` | 允许使用有效的IP v4地址。 |
| `ipv6` | 允许使用有效的IP v6地址。 |
| `letters-only` | 仅允许使用字母。 例如，`abcABC`。 |
| `letters-with-basic-punc` | 仅允许使用字母或标点。<br>必须传递以下表达式：`/^[a-z\-.,()\u0027\u0022\s]+$/i`。 |
| `mobileUK` | 允许（英国）手机号码。 |
| `no-marginal-whitespace` | 不允许在值的开头或结尾使用空格。 |
| `no-whitespace` | 不允许使用空格。 |
| `phoneUK` | 允许（英国）电话号码。 |
| `phoneUS` | 允许（美国）电话号码。 |
| `required-entry` | 不允许空值（等效验证为`validate-no-empty`）。<br>验证失败消息：“这是必填字段。” |
| `time` | 允许以24小时格式显示有效时间，介于00:00和23:59之间。 例如`15`、`15:05`或`15:05:48`。 |
| `time12h` | 允许以12小时格式显示有效时间，介于上午12:00到晚上11:59:59之间。 例如`3 am`、`11:30 pm`、`02:15:00 pm`。 |
| `validate-admin-password` | 允许7个或更多字符，同时使用数字和字母。 |
| `validate-alphanum-with-spaces` | 仅允许使用字母（a-z或A-Z）、数字(0-9)或空格。 |
| `validate-clean-url` | 允许有效的URL。 例如，`https://www.example.com`或`www.example.com`。 |
| `validate-currency-dollar` | 允许有效的（美元）金额。 例如，$100.00。 |
| `validate-data` | 仅允许使用字母（a-z或A-Z）、数字(0-9)或下划线(\_)。<br>第一个字符必须是字母。<br>（必须匹配表达式： `/^[A-Za-z]+[A-Za-z0-9_]+$/`）<br>验证失败消息：“请仅在此字段中使用字母（a-z或A-Z）、数字(0-9)或下划线(\_)，第一个字符应为字母。” |
| `validate-date-au` | 强制采用以下日期格式：dd/mm/yyyy。 例如，2006年3月17日的17/03/2006。 |
| `validate-email` | 允许有效的电子邮件地址。 例如，johndoe@domain.com。 |
| `validate-emailSender` | 允许有效的电子邮件地址。 例如，johndoe@domain.com。 |
| `validate-fax` | 允许使用有效的传真号码。 例如，123-456-7890。 |
| `validate-no-empty` | 不允许空值（等效验证为`requried-entry`）。<br>验证失败消息：“空值。” |
| `validate-no-html-tags` | 禁止使用HTML标记。 |
| `validate-password` | 允许6个或更多字符。 将忽略前导空格和尾随空格。 |
| `validate-phoneLax` | 允许使用有效的电话号码。 例如，(123) 456-7890或123-456-7890。 |
| `validate-phoneStrict` | 允许使用有效的电话号码。 例如，(123) 456-7890或123-456-7890。 |
| `validate-select` | 强制选择的选择选项不具有`null`值、字符串值`none`或字符串长度0。 |
| `validate-ssn` | 允许有效的（美国）社会保险号。 例如，123-45-6789。 |
| `validate-street` | 仅允许使用字母（a-z或A-Z）、数字(0-9)、空格和“#”。 |
| `validate-url` | 允许有效的URL。 协议是必需的(http://、https://或ftp://)。 |
| `validate-xml-identifier` | 允许使用有效的XML标识符。 例如，something_1、block5、id-4。 |
| `validate-zip-us` | 允许有效的（美国）邮政编码。 例如，90602或90602-1234。 |
| `vinUS` | 允许（美国）车辆识别号(VIN)值。 |

### 默认值

可以通过在`etc/config.xml`节点中指定默认值，在模块的`section/group/field_ID`文件中设置字段的默认值。

#### 示例：设置`ANOTHER_UNIQUE_FIELD_ID`的默认值（默认范围）

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <A_UNIQUE_SECTION_ID>
            <A_UNIQUE_GROUP_ID>
                <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
            </A_UNIQUE_GROUP_ID>
        </A_UNIQUE_SECTION_ID>
    </default>
</config>
```

#### 示例：设置`ANOTHER_UNIQUE_FIELD_ID`的默认值（网站范围）

使用`websites`标记指定特定网站的默认值。

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <websites>
        <WEBSITE_CODE>
            <A_UNIQUE_SECTION_ID>
                <A_UNIQUE_GROUP_ID>
                    <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
                </A_UNIQUE_GROUP_ID>
            </A_UNIQUE_SECTION_ID>
        </WEBSITE_CODE>
    </websites>
</config>
```
