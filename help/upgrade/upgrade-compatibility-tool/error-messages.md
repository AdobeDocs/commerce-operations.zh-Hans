---
title: '"[!DNL Upgrade Compatibility Tool] 错误消息”'
description: 了解有关使用 [!DNL Upgrade Compatibility Tool] 在您的Adobe Commerce项目上。
source-git-commit: 97295df89fda393c8cf8675f8f4be92ac6f38a6a
workflow-type: tm+mt
source-wordcount: '3638'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] 错误消息

此错误消息引用提供有关执行 [!DNL Upgrade Compatibility Tool].

错误消息按级别（严重问题、错误和警告）和类型（核心代码、自定义代码和GraphQL架构）进行分类。 每种类型都包含以下信息：

- **错误代码**:Adobe Commerce为错误消息分配了标识符。
- **错误描述**:概述错误原因的描述。
- **错误建议的操作**:如果适用，将为故障诊断和解决错误提供指导。

## 关键问题

### 核心代码

当某些核心文件缺失或与原始文件不匹配时，会报告这些错误。

|错误代码 |错误描述 |建议的操作 | | - | - | - | | 2001 |未找到核心文件 |运行 `composer install` 命令。 | | 2002 |已修改核心文件 |运行 `composer install` 命令。 | | 2003 |未安装编辑器依赖项 |缺少编辑器依赖关系可能会导致问题。 通过运行恢复依赖项 `composer require package_name`. | | 2005 |未找到核心文件夹 |运行 `composer install` 命令。 |

{style=&quot;table-layout:auto&quot;}

### 自定义代码

当自定义代码引用目标Adobe Commerce版本中不存在的实体时，会引发严重错误。 当关键编码标准被破坏时，也会报告这些错误。

|错误代码 |错误描述 |建议的操作 | | - | - | - | | 1110 |实例化不存在的Adobe Commerce类/接口 |更新代码以使用标记为 `@api`. 实例化不存在的Adobe Commerce类/接口。 | | 1111 |从不存在的Adobe Commerce类扩展 |代码库中不再存在扩展类。 不建议使用继承来扩展Adobe Commerce功能。 更新代码以使用标记为 `@api`. | | 1112 |导入不存在的Adobe Commerce类 |更新代码以使用标记为 `@api`. | | 1113 |加载不存在的Adobe Commerce类 |更新代码以使用标记为 `@api`. | | 1114 |使用不存在的Adobe Commerce类 |更新代码以使用标记为 `@api`. | | 1214 |使用不存在的Adobe Commerce常量 |请考虑在自定义代码中引入和使用所需值的专用常量。 | | 1215 |覆盖不存在的Adobe Commerce常量 |请考虑在自定义代码中引入和使用所需值的专用常量。 | | 1216 |分配不存在的Adobe Commerce常量 |请考虑在自定义代码中引入和使用所需值的专用常量。 | | 1312 |导入的Adobe Commerce界面不存在 |考虑删除继承或将其替换为自定义范围中引入的界面。 | | 1314 |使用的Adobe Commerce界面不存在 |考虑删除继承或将其替换为自定义范围中引入的界面。 | | 1317 |继承的不存在Adobe Commerce界面 |考虑删除继承或将其替换为自定义范围中引入的界面。 | | 1318 |实施的Adobe Commerce界面不存在 |考虑删除继承或将其替换为自定义范围中引入的界面。 | | 1410 |调用不存在的Adobe Commerce方法 |更新代码以使用标记为 `@api`. | | 1514 |使用不存在的Adobe Commerce属性 |更新代码以使用标记为 `@api`. | | 1515 |覆盖不存在的Adobe Commerce属性 |更新代码以使用标记为 `@api`. | | 1516 |分配不存在的Adobe Commerce属性 |更新代码以使用标记为 `@api`. 如果资产访问级别只能在单个类中使用，则将其更新为private。 | | 5002 |开始的PHP标记必须是文件中的第一个内容 |确保PHP开始标记之前文件中没有内容。 | | 5003 |函数已弃用 |使用错误消息中建议的替换项。 如果消息不建议替换，则需要进行仔细审查才能选择替代功能或实施。 | | 5005 | PHP语法错误 |必须更新代码以符合PHP语法标准。 | | 5072 |可能的Magento2设计违规。 检测到典型的Magento1.x结构 |将构建更新为Magento2标准。 | | 5076 |无法在命名空间中使用，因为自PHP 7起已保留命名空间 |将命名空间中的保留字替换为非保留关键字。 | | 5077 |不能用作类名称，因为自PHP 7起保留该类名称 |将保留的类名称替换为非保留的名称。 |

{style=&quot;table-layout:auto&quot;}

### GraphQL模式

GraphQL如果目标版本中不存在架构项，则会引发架构关键问题。

|错误代码 |错误描述 |建议的操作 | | - | - | - | | 3101 |类型已删除 |列出引用此字段的所有查询。 检查自定义实施是否使用这些查询。 更新客户端代码以处理更改的查询接口。 | | 3102 |从并集中删除的类型 |如果在GraphQL请求构建或响应处理实施中使用并集类型，则可能需要更新该类型。 | | 3103 |已删除字段 |检查自定义代码库中是否引用了该字段。 调整实施以正确处理新字段类型。 | | 3105 |已删除实施的接口 |检查自定义中是否使用了实施已删除界面的类型。 如果实施依赖于删除的接口，则可能需要更新该实施。 | | 3106 |从枚举中删除的值 |如果在GraphQL请求构建或响应处理实施中使用已删除的枚举值，则可能需要更新该值。 | | 3107 |已删除参数 |检查自定义代码库中是否使用了字段。 删除此字段的参数。 | | 3109 |指令已删除 |检查自定义代码库中是否使用了指令。 调整实施以删除对指令的引用。 | | 3110 |删除了指令参数 |检查自定义代码库中是否使用了指令。 删除指令参数。 | | 3111 |指令可重复删除 |检查自定义代码库中是否使用了指令。 调整实施以处理界面更改。 | | 3112 |指令位置已删除 |检查自定义代码库中是否使用了指令。 调整实施以处理界面更改。 | | 3201 |类型更改类型 |列出引用此字段的所有查询。 检查自定义实施是否使用这些查询。 更新客户端代码以处理更改的查询接口。 | | 3203 |字段更改类型 |检查自定义代码库中是否引用了该字段。 调整实施以正确处理新字段类型。 | | 3207 |参数更改类型 |检查自定义代码库中是否使用了字段。 更新此字段的参数类型。 | | 3303 |添加了必填输入字段 |如果自定义使用包含此字段的查询，则应将字段添加到请求中。 | | 3307 |已添加必需参数 |检查自定义代码库中是否使用了字段。 使用字段时应指定新的必需参数。 | | 3310 |添加了必需的指令参数 |检查自定义代码库中是否使用了指令。 添加指令参数。 |

{style=&quot;table-layout:auto&quot;}

## 错误

### 自定义代码

当自定义代码使用未被视为/标记为的Adobe Commerce入口点时，会引发自定义代码错误 `@api`. 这种入口点的保留行为是无法保证的。 自定义应依赖 `@api` 入口点。 应在升级后测试基于非API Adobe Commerce代码的功能。 当主要编码标准被破坏时，也会报告这些错误。

|错误代码 |错误描述 |建议的操作 | | - | - | - | | 1104 |使用继承API接口的非API类 |未标记为 `@api` 的值。 请考虑更新代码以依赖标记为 `@api` 中。 否则，应在升级后测试依赖此实施的功能。 | | 1121 |从非Adobe Commerce API类扩展 |代码库中不再存在扩展类。 不建议使用继承来扩展Adobe Commerce功能。 更新代码以使用标记为 `@api`. | | 1122 |导入非Adobe Commerce API类 |代码库中不再存在扩展类。 更新代码以使用标记为 `@api`. 否则，应在升级后测试依赖此实施的功能。 | | 1123 |加载非Adobe Commerce API类 |代码库中不再存在扩展类。 更新代码以使用标记为 `@api`. 否则，应在升级后测试依赖此实施的功能。 | | 1124 |使用非Adobe Commerce API类 |代码库中不再存在扩展类。 更新代码以使用标记为 `@api`. 否则，应在升级后测试依赖此实施的功能。 | | 1224 |使用非Adobe Commerce API常量 |未标记为的常量 `@api` 的值。 请考虑在自定义代码中引入和使用所需值的专用常量。 | | 1225 |覆盖非Adobe Commerce API常量 |未标记为的常量 `@api` 的值。 请考虑在自定义代码中引入和使用所需值的专用常量。 | | 1226 |分配非Adobe Commerce API常量 |未标记为的常量 `@api` 的值。 请考虑在自定义代码中引入和使用所需值的专用常量。 | | 1322 |导入的非Adobe Commerce API接口 |界面未标记为 `@api` 的值。 考虑删除此继承，或将其替换为Adobe Commerce界面中标记为 `@api` 或在自定义代码范围中引入的界面。 | | 1324 |使用的非Adobe Commerce API接口 |界面未标记为 `@api` 的值。 考虑删除此继承，或将其替换为Adobe Commerce界面中标记为 `@api` 或在自定义代码范围中引入的界面。 | | 1327 |继承的非Adobe Commerce API接口 |未标记为的常量 `@api` 的值。 请考虑在自定义代码中引入和使用所需值的专用常量。 | | 1328 |已实施非Adobe Commerce API接口 |界面未标记为 `@api` 的值。 考虑删除此继承，或将其替换为Adobe Commerce界面中标记为 `@api` 或在自定义代码范围中引入的界面。 | | 1420 |实例化非Adobe Commerce API类/接口 |未标记为 `@api` 的值。 请考虑更新代码以依赖标记为 `@api` 中。 否则，应在升级后测试依赖此实施的功能。 此外，检索类实例的推荐方法是使用ID。 如果需要类的新实例，请考虑使用工厂。 | | 1428 |可能依赖于实施详细信息。 |未标记为 `@api` 的值。 请考虑更新代码以依赖标记为 `@api` 中。 否则，应在升级后测试依赖此实施的功能。 | | 1429 |调用非Adobe Commerce API方法 |未标记为的方法 `@api` 或未在API类/接口中声明，可能会发生更改。 即使方法的界面在新版本中未更新，其行为或输出也可能有所不同。 请考虑依赖接口方法。 否则，应在升级后测试依赖此实施的功能。 | | 1449 |调用非接口方法（在实施中存在） |未在界面中声明的方法可能会发生更改。 请考虑依赖接口方法。 否则，应在升级后测试依赖此实施的功能。 | | 1524 |使用非Adobe Commerce API属性 |未标记为 `@api` 的值。 请考虑改用API接口方法。 | | 1525 |覆盖非Adobe Commerce API属性 |未标记为 `@api` 的值。 请考虑改用API接口方法。 | | 1526 |分配非Adobe Commerce API属性 |未标记为 `@api` 的值。 请考虑改用API接口方法。 | | 5004 |已弃用不带参数的函数 |传递要验证的输入作为函数的第一个参数。 | | 5007 |不鼓励使用某些功能 |避免使用这些函数。 | | 5009 |模板指令不能调用方法。 只允许标量数组访问 |从模板中删除方法调用。 | | 5010 |模板 `@vars` 注释块包含无效的JSON |修复无效的JSON。 | | 5011 |模板 `@vars` 注释块包含无效标签 |修复无效标签。 | | 5012 |模板 `@vars` 注释块缺少模板中使用的变量 |将缺少的变量添加@vars注释块。 | | 5013 |避免将自闭标记与非void html元素结合使用 |请改用关闭标记。 | | 5014 | `"active"` 属性过时 |在部署配置中定义活动模块的列表。 | | 5015 | `<param>` 节点已过时 |使用 `<argument name="..." xsi:type="...">` 中。 | | 5016 | `<instance>` 节点已过时 |使用 `<argument name="..." xsi:type="object">` 中。 | | 5017 | `<array>` 节点已过时 |使用 `<argument name="..." xsi:type="array">` 中。 | | 5018 | `<item key="...">` 节点已过时 |使用 `<item name="..." xsi:type="...">` 中。 | | 5019 | `<value>` 节点已过时 |相反，请提供实际值作为文本文字。 | | 5020 |过时的节点： `<supported_blocks>` |替换为 `<supported_containers>`. | | 5021 |过时的节点： `<block_name>` |替换为 `<container_name>`. | | 5022 |检测到工厂名称 |小组件类型不应以/开头。 | | 5023 |在行中检测到过时的ACL结构 |查看lib/internal/Magento/Framework/Acl/etc/acl.xsd。 | | 5024 |在行中检测到过时的菜单结构 |查看app/code/Magento/Backend/etc/menu.xsd。 | | 5025 |在文件中检测到过时的系统配置结构 |查看app/code/Magento/Config/etc/system_file.xsd。 | | 5026 |请勿使用 `"text/javascript"` 类型属性 |仅使用公共成员。 | | 5028 |访问 `Block` phtml模板中的类过时 |仅使用公共成员。 | | 5031 |包含过时的方法 |使用 `getConnection()` 方法。 | | 5032 | `loadLayout` 方法已弃用 |使用 `\Magento\Framework\View\Layout\Builder::build` 中。 | | 5033 | `renderLayout` 方法已弃用 |使用 `\Magento\Framework\Controller\ResultInterface::renderResult` 中。 | | 5034 | `_redirect` 方法已弃用 |使用 `\Magento\Backend\Model\View\Result\Redirect::render` 中。 | | 5035 | `_forward` 方法已弃用 |使用 `\Magento\Backend\Model\View\Result\Forward::forward` 中。 | | 5036 | `_setActiveMenu` 方法已弃用 |使用 `\Magento\Backend\Model\View\Result\Page::setActiveMenu` 中。 | | 5037 | `_addBreadcrumb` 方法已弃用 |使用 `\Magento\Backend\Model\View\Result\Page::addBreadcrumb` 中。 | | 5038 | `_addContent` 方法已弃用 |使用 `\Magento\Backend\Model\View\Result\Page::addContent` 中。 | | 5039 | `_addLeft` 方法已弃用 |使用 `\Magento\Backend\Model\View\Result\Page::addLeft` 中。 | | 5040 | `_addJs` 方法已弃用 |使用 `\Magento\Backend\Model\View\Result\Page::addJs` 中。 | | 5041 | `_moveBlockToContainer` 方法已弃用 |使用 `\Magento\Backend\Model\View\Result\Page::moveBlockToContainer` 中。 | | 5042 | PHP类引用的格式不正确 |检查是否仅使用驼峰字母、数字和无前导斜杠引用类。 | | 5043 |模块引用的格式不正确 |检查是否仅使用字母、数字、下划线和无前导斜杠引用模块。 | | 5044 |类 `Zend_Db_Select` 受限 |建议的替换： `\Magento\Framework\DB\Select`. | | 5045 |类 `Zend_Db_Adapter_Pdo_Mysql` 受限 |建议的替换： `\Magento\Framework\DB\Adapter\Pdo\Mysql`. | | 5046 |类 `Magento\Framework\Serialize\Serializer\Serialize` 受限 |建议的替换： `Magento\Framework\Serialize\SerializerInterface`. | | 5047 |类 `ArrayObject` 受限 |建议的替换：自定义类，从扩展 `ArrayObject` 的问题。 | | 5048 |类 `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` 受限 |建议的替换：创建自定义类的工厂，从 `ArrayObject` 的问题。 | | 5050 |正在引用的块已删除 |删除对块的引用。 | | 5051 | `output="toHtml"` 已过时 |使用 `output="1"`. | | 5052 |类 `\Magento\Framework\View\Element\Text\ListText` 不应再在布局中使用 |删除类 `\Magento\Framework\View\Element\Text\ListText` 的上界。 | | 5053 |通过布局指令调用方法 `<action>` 不允许 |避免在 `<action>`. | | 5054 | `helper` 属性包含 `/` |删除 `/` 从帮助程序属性。 | | 5055 | `helper` 属性不包含 `::` |添加 `::` 到帮助程序属性。 | | 5056 |安装脚本已过时 |在模块的etc/db_schema.xml文件中使用声明性架构方法。 | | 5057 | InstallSchema脚本已过时 |在模块的etc/db_schema.xml文件中使用声明性架构方法。 | | 5058 | InstallData脚本已过时 |在模块的“设置”/“修补”/“数据”目录中使用数据修补程序方法。 | | 5059 |安装脚本已过时 |在模块的Setup文件夹中创建一个类InstallData。 | | 5060 |升级脚本已过时 |在模块的etc/db_schema.xml文件中使用声明性架构方法。 | | 5061 |升级架构脚本已过时 |在模块的etc/db_schema.xml文件中使用声明性架构方法。 | | 5062 |升级数据脚本已过时 |在模块的“设置”/“修补”/“数据”目录中使用数据修补程序方法。 | | 5063 |升级脚本已过时 |在模块的“设置”/“修补”/“数据”目录中使用数据修补程序方法。 | | 5064 |循环脚本已过时 |在模块的Setup文件夹中创建重复的类。 | | 5065 |“data”位于无效目录中 |在模块的Setup/Patch/Data文件夹中创建数据修补程序，以便进行数据升级，或在模块的etc/db_schema.xml文件中使用声明式架构方法进行架构更改。 | | 5066 |“sql”位于无效目录中 |在模块的Setup/Patch/Data文件夹中创建数据修补程序，以便进行数据升级，或在模块的etc/db_schema.xml文件中使用声明式架构方法进行架构更改。 | | 5067 |由XPath标识的节点已过时 |错误中指出的过时XML应更新。 请遵循错误消息中的建议。 | | 5068 |指令 `{{htmlescape}}` 已过时 |使用 `{{var}}` 中。 | | 5069 |指令 `{{escapehtml}}` 已过时 |使用 `{{var}}` 中。 | | 5070 |不再需要第3个参数 `getChildHtml()` |从调用中删除第3个参数 `getChildHtml()`. | | 5071 |不再需要第4个参数 `getChildHtml()` |从调用中删除第4个参数 `getChildHtml()`. | | 5073 |带斜杠的旧表名必须修复为直接表名 |请改用直接表名。 | | 5075 |应用程序模块不应使用测试模块中的类 |从测试模块中删除类的使用情况。 | | 5078 |类必须在构造函数中请求，否则编译器将无法找到并生成这些类 |将类添加到构造函数。 | | 5079 |不鼓励使用var类变量 |避免使用“var”声明类变量。 | | 5080 |检测到可能的原始SQL语句 |请改用存储库或数据修补程序。 | | 5081 |不鼓励在模板中使用帮助程序 |请改用ViewModel。 | | 5082 |弃用了$this在模板中的用法 |请改用$block。 | | 5083 |不允许将常量作为转换函数的第一个参数 |请改用字符串文字。 | | 5085 |不鼓励使用某些功能 |请改用消息中建议的替代函数。 | | 5087 | PHP跨版本兼容性问题 |按照消息中的建议进行操作，并查看 [迁移指南](https://www.php.net/manual/en/migration81.php). | | 5088 |在必需参数之后找到的可选参数 |将所需参数移动到可选参数之后。 | | 5089 |方法可见性 `final private` 已找到 |将方法可见性从 `final private` 仅 `private`. | | 5090 |魔术方法 `__set_state` 未定义为 `static` |魔术方法 `__set_state` 必须定义为 `static`. | | 5091 |类，具有 `__toString()` 不继承的方法 `Stringable` 界面 |添加 `Stringable` 接口与 `__toString()` 方法。 | | 5092 | `is_resource()` 用于现在返回对象的函数的方法 |更改 `is_resource()` to `instanceof` 对象。 | | 6001 | `jQuery.andSelf()` 已删除 |使用 `jQuery.addBack()`. | | 6002 | jQuery `$.bind` 和 `$.unbind` 已弃用 |使用 `$.on` 和 `$.off` 中。 | | 6003 | jQuery方法已弃用，不应使用 |使用 `.on("event name", fn)` 方法来订阅该事件。 | | 6003 | jQuery方法已弃用，不应使用 |使用 `.trigger("event name")` 方法来触发该事件。 | | 6004 | jQuery `$.delegate` 和 `$.undelegate` 已弃用 |使用 `$.on` 和 `$.off` 中。 | | 6005 |(`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`)已删除 |使用(`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`)。 | | 6006 | `jQuery.size()` 已删除 |使用 `jQuery.length`. | | 6007 | `jQuery.trim` 已弃用 |使用 `String.prototype.trim`. | | 6008 |(`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`，“inlite”主题、“mobile”主题、“modern”主题) |更新代码以与Tinymce5兼容。 | | 6009 | `jQuery.isFunction()` 已弃用 |在大多数情况下，可将其替换为 [x === &quot;function&quot;类型]. | | 6009 | `jQuery.type()` 已弃用 |替换为相应的类型检查，如 [x === &quot;function&quot;类型]. | | 6009 | `jQuery.isArray()` 已弃用 |请改用本机Array.isArray方法。 | | 6009 | `jQuery.parseJSON()` 已弃用 |要解析JSON字符串，请改用本机JSON.parse方法。 | | 6010 |(`jQuery.expr[":"]`, `jQuery.expr.filters`)已弃用 |请改用jQuery.expr.pseudos。 |

{style=&quot;table-layout:auto&quot;}

## 警告

### 核心代码

当核心代码库中存在细微不一致时，会报告这些警告。

|错误代码 |错误描述 |建议的操作 | | - | - | - | | 2004 |编辑器依赖项版本不匹配 |问题表示标准和实际项目中的编辑器依赖关系版本不同。 通过运行更新依赖项 `composer update <package_name>`. |

{style=&quot;table-layout:auto&quot;}

### 自定义代码

在检测到对已弃用代码的引用时，会引发自定义代码警告。 此类引用应替换为支持的扩展点。 注意 `@see` 推荐的已弃用项的注释。 当次要编码标准被破坏时，也会报告这些错误。

|错误代码 |错误描述 |建议的操作 | | - | - | - | | 1131 |从Adobe Commerce扩展 ``@deprecated`` 类 |扩展类将在即将发布的版本中删除。 不建议使用继承来扩展Adobe Commerce功能。 更新代码以使用标记为 `@api`. | | 1132 |导入Adobe Commerce `@deprecated` 类 |扩展类将在即将发布的版本中删除。 考虑使用标记为 `@api` 中。 | | 1133 |加载Adobe Commerce `@deprecated` 类 |扩展类将在即将发布的版本中删除。 考虑使用标记为 `@api` 中。 | | 1134 |使用Adobe Commerce `@deprecated` 类 |扩展类将在即将发布的版本中删除。 考虑使用标记为 `@api` 中。 | | 1234 |使用Adobe Commerce `@deprecated` 常量 |已弃用的常量将在即将发布的版本中删除。 考虑使用标记为 `@api` 或实施中的专用常量。 | | 1235 |覆盖Adobe Commerce `@deprecated` 常量 |已弃用的常量将在即将发布的版本中删除。 考虑使用标记为 `@api` 或实施中的专用常量。 | | 1236 |分配Adobe Commerce `@deprecated` 常量 |已弃用的常量将在即将发布的版本中删除。 考虑使用标记为 `@api` 或实施中的专用常量。 | | 1332 |导入的Adobe Commerce `@deprecated` 界面 |已弃用的界面将在即将发布的版本中删除。 考虑使用标记为 `@api` 中。 | | 1334 |已使用的Adobe Commerce `@deprecated` 界面 |已弃用的界面将在即将发布的版本中删除。 考虑使用标记为 `@api` 中。 | | 1337 |从Adobe Commerce继承 `@deprecated` 界面 |已弃用的界面将在即将发布的版本中删除。 考虑使用标记为 `@api` 或在实施中引入的界面。 | | 1338 |已实施Adobe Commerce `@deprecated` 界面 |已弃用的界面将在即将发布的版本中删除。 考虑使用标记为 `@api` 或在实施中引入的界面。 | | 1430 |调用未声明的dataobject方法 |未声明的幻方法可能会发生更改。 请考虑改用接口方法。 | | 1439 |调用Adobe Commerce `@deprecated` 方法 |已弃用的方法将在即将发布的版本中删除。 请考虑改用API接口中声明的方法。 | | 1534 |使用Adobe Commerce `@deprecated` 属性 |已弃用的方法将在即将发布的版本中删除。 请考虑改用API接口中声明的方法。 | | 1535 |覆盖Adobe Commerce `@deprecated` 属性 |已弃用的属性将在即将发布的版本中删除。 请考虑依赖在API接口中声明的方法，或改为使用实施中的私有属性。 | | 1536 |分配Adobe Commerce `@deprecated` 属性 |已弃用的方法将在即将发布的版本中删除。 请考虑改用API接口中声明的方法。 | | 5006 |构造函数中不得显式请求代理和截取器 |应将原始类声明为构造函数参数的类型。 侦听器/代理类将通过框架依赖项注入实现进行传递。 | | 5074 |使用已弃用的方法 `getResource()` （保存/加载/删除）数据。 |请改用存储库。 | | 5086 |不在常量上声明可见性 |声明所有常量的可见性。 |

{style=&quot;table-layout:auto&quot;}

### GraphQL模式

在新版本的架构中将其他项目添加到架构时，会引发GraphQL架构警告。 建议查看实施，以确定是否应将实施用于请求。

|错误代码 |错误描述 |建议的操作 | | - | - | - | | 3206 |参数默认值已更改 |如果在自定义中使用查询，则可能必须显式指定参数值。 | | 3302 |添加到并集的类型 |类型已添加到并集。 检查处理查询返回此并集类型的结果的实现，并确保它能够处理添加的类型。 | | 3304 |添加了可选输入字段 |添加了可选输入字段。 检查实施以确保。 | | 3305 |已添加实施的界面 |字段可以接受/提供可在实施中考虑的更多信息。 | | 3306 |添加到枚举的值 |值已添加到枚举。 如果客户端在枚举值中包含switch语句而不包含默认大小写，则此更改可能会导致意外行为。 | | 3308 |已添加可选参数 |如果查询在自定义中使用新参数，则可能需要将其添加到请求中。 |

{style=&quot;table-layout:auto&quot;}
