---
title: system.xml引用
description: 了解系统XML文件如何管理商务应用程序配置。
badge: label="Contributed by David Lambauer" type="Informative" url="https://github.com/DavidLambauer" tooltip="David Lambauer"
source-git-commit: d7f32690b25c61fa31a99e6d02f9f1025de2bb99
workflow-type: tm+mt
source-wordcount: '2685'
ht-degree: 0%

---


# system.xml引用

的 `system.xml` 文件，用于管理商务系统配置。 使用此主题作为 `system.xml` 文件。 的 `system.xml` 文件位于 `etc/adminhtml/system.xml` 在给定的Commerce 2扩展中。

以下代码片段显示了文件的裸机骨架：

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
>如果希望在IDE中执行即时*XSD验证，则可以运行 `bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>`.

## 制表符//节/组//字段

在 `system.xml` 文件中，可以定义四种不同类型的图元，它们彼此相关。 以下部分介绍选项卡、部分、组和字段之间的关系。 以下屏幕截图在管理员后端显示Commerce 2系统配置。
红色的正方形标记在 `system.xml` 文件：

![屏幕截图显示了“管理员”中配置的部分。](../../assets/configuration/magento2-system-configuration.png)

在语义上，使用制表符拆分不同的配置区域。 每个选项卡可以包含一个或多个部分，也可以作为子菜单引用这些部分。 部分包含一个或多个组。
每个组都列出一个或多个字段。 您还可以使用群组为以下字段添加常规说明。 如前所述，每个组可以有一个或多个字段。 字段是系统配置上下文中的最小实体。

## 选项卡

A `<tab>` — 标记对系统配置中现有或新选项卡的引用。

### 选项卡属性引用

A `<tab>`-Tag可以具有以下属性：

| 属性 | 描述 | 类型 | 必需 |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | 定义引用节的标识符。 | `typeId` | 必需 |
| `translate` | 定义应可翻译的字段。 提供 `label` 使标签可翻译。 | `string` | 可选 |
| `type` | 定义渲染的HTML元素的输入类型 — 默认为 `text`. | `string` | 可选 |
| `sortOrder` | 定义部分的排序顺序。 高数字会将部分推送到页面底部；低数将部分推至顶部。 | `float` | 可选 |
| `class` | 将定义的CSS类添加到已呈现的选项卡HTML元素。 | `string` | 可选 |

### 制表符节点引用

A `<tab>` — 标记可以具有以下子项：

| 节点 | 描述 | 类型 |
|---------|------------------------------------------------------|----------|
| `label` | 定义在前端显示的标签。 | `string` |

### 示例：创建选项卡

以下代码片段演示了如何使用示例数据创建新选项卡。

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

以上代码片段会创建一个包含标识符的新选项卡 `A_UNIQUE_ID`. 作为 `translate`-attribute已定义并引用标签、 `label` — 节点可转换。 在渲染过程中，CSS类 `a-custom-css-class-to-style-this-tab` 将应用于为此选项卡创建的HTML元素。
的 `sortOrder`-attribute，其值为 `10` 定义选项卡在呈现时在所有选项卡列表中的位置。

## 部分

A `<section>` — 标记对系统配置中现有部分或新部分的引用。

### 节属性引用

A `<section>`-Tag可以具有以下属性：

| 属性 | 描述 | 类型 | 必需 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | 定义引用节的标识符。 | `typeId` | 必需 |
| `translate` | 定义应可翻译的字段。 提供 `label` 使标签可翻译。 | `string` | 可选 |
| `type` | 定义呈现的HTML元素的输入类型。 默认为 `text`. | `string` | 可选 |
| `sortOrder` | 定义部分的排序顺序。 高数字会将部分推送到页面底部；低数字会将部分推至顶部。 | `float` | 可选 |
| `showInDefault` | 定义部分是否显示在默认配置范围中。 指定 `1` 显示部分和 `0` 来隐藏部分。 | `int` | 可选 |
| `showInStore` | 定义是否在存储级别显示部分。 指定 `1` 显示部分和 `0` 来隐藏部分。 | `int` | 可选 |
| `showInWebsite` | 定义是否在网站级别显示该部分。 指定 `1` 显示部分和 `0` 来隐藏部分。 | `int` | 可选 |
| `canRestore` | 定义能否将部分还原为默认值。 | `int` | 可选 |
| `advanced` | 自100.0.2起已弃用。 | `bool` | 可选 |
| `extends` | 通过提供其他部分的标识符，此节点的内容将扩展您引用的部分。 | `string` | 可选 |

### 节点引用

A `<section>`-Tag可以具有以下子项：

| 节点 | 描述 | 类型 |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | 定义在前端显示的标签。 | `string` |
| `class` | 将定义的CSS类添加到呈现的节HTML元素。 | `string` |
| `tab` | 引用关联的选项卡。 应为选项卡的ID。 | `typeTabId` |
| `header_css` | 在编写本文时，未使用或评估。 | `string` |
| `resource` | 引用ACL资源以提供此部分的权限设置。 | `typeAclResourceId` |
| `group` | 定义一个或多个子组。 | `typeGroup` |
| `frontend_model` | 指定一个不同的前端模型来更改渲染并修改输出。 | `typeModel` |
| `include` | 用于包含其他 `system_include.xsd` 兼容文件。 通常用于构造大型 `system.xml` 文件。 | `includeType` |

### 示例：创建一个部分并将其分配给选项卡

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

上述部分定义了ID `A_UNIQUE_SECTION_ID`，在默认配置视图和存储上下文中可见。 的 `label` — 节点可转换。 部分与具有ID的选项卡关联 `A_UNIQUE_ID`. 只有具有ACL中所定义权限的用户才能访问该部分 `VENDOR_MODULE::path_to_the_acl_resource`.

## 群组

的 `<group>` — 标记用于将字段分组在一起。

### 组属性引用

A `<group>`-Tag可以具有以下属性：

| 属性 | 描述 | 类型 | 必需 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | 定义引用组时使用的标识符。 | `typeId` | 必需 |
| `translate` | 定义应可翻译的字段。 提供 `label` 使标签可翻译。 多个字段应以空格分隔。 | `string` | 可选 |
| `type` | 定义呈现的HTML元素的输入类型。 默认为 `text`. | `string` | 可选 |
| `sortOrder` | 定义部分的排序顺序。 高数字会将部分推送到页面底部；低数字会将部分推至顶部。 | `float` | 可选 |
| `showInDefault` | 定义组是否显示在默认配置范围中。 指定 `1` 显示组和 `0` 来隐藏群组。 | `int` | 可选 |
| `showInStore` | 定义是否在存储级别显示组。 指定 `1` 显示组和 `0` 来隐藏群组。 | `int` | 可选 |
| `showInWebsite` | 定义群组是否在网站级别显示。 指定 `1` 显示组和 `0` 来隐藏群组。 | `int` | 可选 |
| `canRestore` | 定义是否可将组还原为默认组。 | `int` | 可选 |
| `advanced` | 自100.0.2起已弃用。 | `bool` | 可选 |
| `extends` | 通过提供其他组的标识符，此节点的内容将扩展您引用的部分。 | `string` | 可选 |

### 组节点引用

A `<group>`-Tag可以具有以下子项：

| 节点 | 描述 | 类型 |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | 定义在前端显示的标签。 | `string` |
| `fieldset_css` | 向组字段集添加一个或多个CSS类。 | `string` |
| `frontend_model` | 指定一个不同的前端模型来更改渲染并修改输出。 | `typeModel` |
| `clone_model` | 指定克隆字段的给定模型。 | `typeModel` |
| `clone_fields` | 启用或禁用字段的克隆。 | `int` |
| `help_url` | 不可扩展。 请参阅下文。 | `typeUrl` |
| `more_url` | 不可扩展。 请参阅下文。 | `typeUrl` |
| `demo_link` | 不可扩展。 请参阅下文。 | `typeUrl` |
| `comment` | 在群组标签下添加评论。 使用 `<![CDATA[//]]>` HTML。 | `string` |
| `hide_in_single_store_mode` | 群组是否应在单存储模式下可见。 `1` 藏起群体； `0` 显示群组。 | `int` |
| `field` | 定义此组下应可用的一个或多个字段。 | `field` |
| `group` | 定义一个或多个子组。 | `unbounded` |
| `depends` | 可用于声明对其他字段的依赖关系。 仅当给定字段的值为 `1`. 此节点需要 `section/group/field`-string。 | `depends` |
| `attribute` | 前端模型可以使用自定义属性。 通常用于使给定前端模型更具动态性。 | `attribute` |
| `include` | 用于包含其他 `system_include.xsd` 兼容文件。 通常用于构造大型 `system.xml` 文件。 | `includeType` |

>[!WARNING]
>
>节点 `more_url`, `demo_url` 和 `help_url` 由仅使用一次的PayPal前端模型定义。 这些节点不可重复使用。

### 示例：为给定部分创建组

以下代码片段演示了创建新组的基本用法。

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

上述组定义了ID `A_UNIQUE_GROUP_ID`，在默认配置视图和存储上下文中可见。 两者， `label` 和 `comment` 标记为可翻译。

## 字段

的 `<field>` — 标记在 `<group>` — 用于定义特定配置值的标记。

### 字段属性引用

A `<field>`-Tag可以具有以下属性：

| 属性 | 描述 | 类型 | 必需 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | 定义引用字段的标识符。 | `typeId` | 必需 |
| `translate` | 定义应可翻译的字段。 提供 `label` 使标签可翻译。 多个字段应以空格分隔。 | `string` | 可选 |
| `type` | 定义呈现的HTML元素的输入类型。 默认为 `text`. | `string` | 可选 |
| `sortOrder` | 定义部分的排序顺序。 高数字会将部分推送到页面底部；低数将部分推至顶部。 | `float` | 可选 |
| `showInDefault` | 定义字段是否显示在默认配置范围中。 指定 `1` 显示字段和 `0` 来隐藏字段。 | `int` | 可选 |
| `showInStore` | 定义字段是否在存储级别显示。 指定 `1` 显示字段和 `0` 来隐藏字段。 | `int` | 可选 |
| `showInWebsite` | 定义字段是否显示在网站级别。 指定 `1` 显示字段和 `0` 来隐藏字段。 | `int` | 可选 |
| `canRestore` | 定义字段是否可恢复为默认值。 | `int` | 可选 |
| `advanced` | 自100.0.2起已弃用。 | `bool` | 可选 |
| `extends` | 通过提供其他字段的标识符，此节点的内容将扩展您引用的部分。 | `string` | 可选 |

### 字段类型引用

A `<field>` — 标记可以具有 `type=""` 属性：

| 类型 | 描述 |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | 标准，单行文本字段 |
| `textarea` | 文本块 |
| `select` | 普通下拉菜单，可能需要自定义 `source_model`. 也用于 `Yes/No` 选项。 请参阅 `Magento\Search\Model\Adminhtml\System\Config\Source\Engine` 例如。 |
| `multiselect` | 赞 `select` 但多个选项有效。 |
| `button` | 触发即时事件的按钮。 需要自定义前端模型来定义按钮文本和操作。 请参阅 `Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean` 例如。 |
| `obscure` | 值加密并显示为 `****`. 在浏览器中使用“Inspect元素”更改类型时，不会显示该值。 |
| `password` | 赞 `obscure` 但是，隐藏值未加密，并且在浏览器中使用“Inspect元素”强制更改类型确实会显示该值。 |
| `file` | 允许上传文件以进行处理。 |
| `label` | 显示标签，而不是可编辑的字段。 当字段仅在特定范围（例如“仅存储视图”级别）上可编辑时，可使用此类型。 |
| `time` | 使用“小时”、“分钟”和“秒”三个下拉菜单来设置时间的控制。 |
| `allowspecific` | 特定国家/地区的多选列表。 需要 `source_model` 例如 `Magento\Shipping\Model\Config\Source\Allspecificcountries` |
| `image` | 允许上传图像。 |
| `note` | 用于向页面添加信息性注释。 此类型需要 `frontend_model` 来渲染注释。 |

也可以创建自定义字段类型。 通常，当需要使用带有操作的特殊按钮时，才会执行此操作。 要执行此操作，需要两个主要元素：

- 在中创建块 `adminhtml` 面积
- 设置 `type=""` 到此块的路径

块本身至少需要 `__construct` 方法和 `getElementHtml()` 方法。 的 [Magento_OfflineShipping](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping) 是自定义类型的一个简单示例。

例如，在OfflineShipping模块中，导出按钮在 `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export` 字段定义如下所示：

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### 字段节点引用

A `<field>`-Tag可以具有以下子项：

| 节点 | 描述 | 类型 |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | 定义在前端显示的标签。 | `string` |
| `comment` | 在字段标签下添加注释。 使用 `<![CDATA[//]]>` HTML。 | `string` |
| `tooltip` | 可用于描述此字段含义的另一个可能的前端元素。 显示为字段旁的小图标。 | `string` |
| `hint` | 显示其他信息。 仅适用于特定 `frontend_model`. | `string` |
| `frontend_class` | 将定义的CSS类添加到呈现的节HTML元素。 | `string` |
| `frontend_model` | 指定一个不同的前端模型来更改渲染并修改输出。 | `typeModel` |
| `backend_model` | 指定其他后端模型以修改配置的值。 | `typeModel` |
| `source_model` | 指定提供一组特定值的不同源模型。 | `typeModel` |
| `config_path` | 可用于覆盖字段的常规配置路径。 | `typeConfigPath` |
| `validate` | 定义不同的验证规则（空格分隔）。 可用验证规则的完整参考列表如下所示。 | `string` |
| `can_be_empty` | 在 `type` is `multiselect` ，以指定字段可为空。 | `int` |
| `if_module_enabled` | 仅在启用给定模块时才用于显示字段。 | `typeModule` |
| `base_url` | 与 `upload_dir` 文件上传。 | `typeUrl` |
| `upload_dir` | 指定上传的目标目录。 此节点具有其他属性和节点。 在使用之前先查找它们。 | `typeUploadDir` |
| `button_url` | 在 `button_url` 和 `button_label` 指定。 通常与自定义前端模型结合使用。 | `typeUrl` |
| `button_label` | 在 `button_label` 和 `button_url` 指定。 通常与自定义前端模型结合使用。 | `string` |
| `more_url` | 不可扩展。 请参阅下文。 | `typeUrl` |
| `demo_url` | 不可扩展。 请参阅下文。 | `typeUrl` |
| `hide_in_single_store_mode` | 群组是否应在单存储模式下可见。 `1` 藏起群体； `0` 显示群组。 | `int` |
| `source_service` | 用于填充选定选项的服务。 | `complexType` |
| `options` | 未使用。 可能已弃用。 | `complexType` |
| `depends` | 可用于声明对其他字段的依赖关系。 当给定字段的值为 `1`. 此节点需要 `section/group/field`-string。 | `complexType` |
| `attribute` | 前端模型可以使用自定义属性。 通常用于使给定前端模型更具动态性。 | `complexType` |
| `requires` | 不可扩展。 请参阅下文。 | `complexType` |

>[!WARNING]
>
>节点 `more_url`, `demo_url`, `requires` 和 `options` 由不同的核心支付模式定义，且仅使用一次。 这些节点不可重复使用。

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

以上示例创建了两个字段，它们在默认和存储视图中均可见/配置。 这两个字段都带有注释和工具提示，用于描述它们对用户的用途。 的 `label` — 节点可转换。
具有标识符的字段 `ANOTHER_UNIQUE_FIELD_ID` 在 `if_module_enabled` 全局启用。 该字段还会根据规则验证其值 `required-entry` 和 `no-whitespace`.
具有标识符的字段 `A_UNIQUE_FIELD_ID` 定义提供这些值的不同源模型 `Yes` 和 `No`.

### 常见源模型

商务2核心提供了以下源模型。 一般来说，源模型还有很多；下表介绍了最常见的列表。 请注意，这些源模型需要字段属性 `type` 设置为 `select` 才能正常工作。

| 源模型 | 描述 |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | 提供值 `Yes`, `No` 和 `Specified`. |
| `Magento\Config\Model\Config\Source\Enabledisable` | 提供值 `Enable`, `Disable`. 将值另存为 `0` 和 `1` 在数据库中。 |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | 提供值 `1 Hour`,`2 Hours`,`6 Hours`,`12 Hours` 和 `24 Hours`. 值将另存为整数。 |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | 提供时间格式(12 h/24 h)的值。 |
| `Magento\Cron\Model\Config\Source\Frequency` | 提供值 `Daily`, `Weekly` 和 `Monthly`. 值在数据库中保存为 `D`, `W` 和 `M`. |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | 提供ISO 639-1格式（例如en）中给定语言的双字母代码的值。 |
| `Magento\Config\Model\Config\Source\Locale` | 提供与上述值类似的值，但属于区域设置代码（例如en_US）。 |

### 字段验证

可以为字段分配一个或多个验证器类，以确保用户的输入满足扩展的要求。 验证规则可与 `<validate>` — 标记。
以下示例将验证一个字段并添加多个不同的验证规则。

```xml
<field id="A_CUSTOM_IDENTIFIER" showInDefault="1" showInWebsite="0" showInStore="1">
    <validate>required-entry validate-clean-url no-whitespace</validate>
</field>
```

可以使用以下验证规则：

| 规则 | 描述 |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `alphanumeric` | 仅允许字母、数字、空格或下划线。 |
| `integer` | 允许非小数为正数或负数。 |
| `ipv4` | 允许有效的IP v4地址。 |
| `ipv6` | 允许有效的IP v6地址。 |
| `letters-only` | 仅允许字母。 例如， `abcABC`. |
| `letters-with-basic-punc` | 仅允许字母或标点符号。<br>必须传递以下表达式： `/^[a-z\-.,()\u0027\u0022\s]+$/i`. |
| `mobileUK` | 允许（英国）手机号码。 |
| `no-marginal-whitespace` | 不允许在值的开始或结束处出现空格。 |
| `no-whitespace` | 不允许有空格。 |
| `phoneUK` | 允许（英国）电话号码。 |
| `phoneUS` | 允许（美国）电话号码。 |
| `required-entry` | 不允许空值(等同于 `validate-no-empty`)。<br>验证失败消息：“这是必填字段。” |
| `time` | 允许以24小时格式在00:00到23:59之间有效。 例如 `15`, `15:05` 或 `15:05:48`. |
| `time12h` | 允许以12小时格式在午夜12:00到11之间生效:59:下午59点。 例如 `3 am`, `11:30 pm`, `02:15:00 pm`. |
| `validate-admin-password` | 允许使用数字和字母的7个或更多字符。 |
| `validate-alphanum-with-spaces` | 仅允许使用字母（a-z或A-Z）、数字(0-9)或空格。 |
| `validate-clean-url` | 允许有效的URL。 例如， `https://www.example.com` 或 `www.example.com`. |
| `validate-currency-dollar` | 允许有效（美元）金额。 例如，100.00美元。 |
| `validate-data` | 仅允许使用字母（a-z或A-Z）、数字(0-9)或下划线(\_)。<br>第一个字符必须是字母。<br>(必须匹配表达式： `/^[A-Za-z]+[A-Za-z0-9_]+$/`)<br>验证失败消息：&quot;请在此字段中仅使用字母（a-z或A-Z）、数字(0-9)或下划线(\_)，第一个字符应为字母。&quot; |
| `validate-date-au` | 强制使用以下日期格式：dd/mm/yyyy。 例如，2006年3月17日的17/03/2006。 |
| `validate-email` | 允许有效的电子邮件地址。 例如， johndoe@domain.com。 |
| `validate-emailSender` | 允许有效的电子邮件地址。 例如， johndoe@domain.com。 |
| `validate-fax` | 允许有效的传真号码。 例如，123-456-7890。 |
| `validate-no-empty` | 不允许空值(等同于 `requried-entry`)。<br>验证失败消息：&quot;空值。&quot; |
| `validate-no-html-tags` | 不允许使用HTML标记。 |
| `validate-password` | 允许6个或更多字符。 将忽略前导和尾随空格。 |
| `validate-phoneLax` | 允许有效的电话号码。 例如，(123)456-7890或123-456-7890。 |
| `validate-phoneStrict` | 允许有效的电话号码。 例如，(123)456-7890或123-456-7890。 |
| `validate-select` | 强制选择的选项不具有 `null` 值，字符串值 `none` 或字符串长度为0。 |
| `validate-ssn` | 允许使用有效的（美国）社会保险号。 例如，123-45-6789。 |
| `validate-street` | 仅允许使用字母（a-z或A-Z）、数字(0-9)、空格和“#”。 |
| `validate-url` | 允许有效的URL。 协议是必需的(http://、https://或ftp://)。 |
| `validate-xml-identifier` | 允许有效的XML标识符。 例如，something_1、block5、id-4。 |
| `validate-zip-us` | 允许有效的（美国）邮政编码。 例如，90602或90602-1234。 |
| `vinUS` | 允许（美国）车辆识别号(VIN)值。 |

### 默认值

字段的默认值可以在模块的 `etc/config.xml` 文件，方法是指定 `section/group/field_ID` 节点。

#### 示例：设置的默认值 `ANOTHER_UNIQUE_FIELD_ID` （默认范围）

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

#### 示例：设置的默认值 `ANOTHER_UNIQUE_FIELD_ID` （网站范围）

使用 `websites` 标记时，请指定特定网站的默认值。

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
