---
source-git-commit: bfad68a46b9b1a79a702f04efd39129decda1a1c
workflow-type: tm+mt
source-wordcount: '4413'
ht-degree: 0%

---
# Adobe Commerce修复了问题(v2.4.9-alpha2)

## 修复了v2.4.9-alpha2中的问题

我们已在Adobe Commerce 2.4.9-alpha2核心代码中修复了118个问题。 此版本中包含的已修复问题的子集如下所述。

### API

#### 在applySpecialPrice上验证的“至今特殊价格”有误

对于特殊价格和产品特殊价格，系统正常运转。产品特殊价格将在管理员设定的日期或第三方系统通过REST API设定的日期到期

_AC-13130 - [GitHub问题](https://github.com/magento/magento2/issues/39169) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39690)_

#### 格式错误的请求正文或参数导致“内部服务器错误”

_AC-746 - [GitHub问题](https://github.com/magento/magento2/issues/32784) - [GitHub代码贡献](https://github.com/magento/magento2/commit/f1adb44e)_

#### 订单“base_row_total”和“row_total”在REST API响应中显示单个项目价格

现在，订购详细信息的REST API响应包含“base_row_total”和“row_total”属性的正确值，以防订购了多个相同的项目

_ACP2E-3874 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4ca73607)_

### API、顺序

#### [CLOUD]订单000075568的行总计出现订单信息问题

修复了以下问题：当项目完全折扣时，订单API响应中的row_total_incl_tax值返回为近零残值，而不是0.00。

_ACP2E-3950 - [GitHub代码贡献](https://github.com/magento/magento2/commit/462ede94)_

### 帐户

#### 在包含o和.swiss域的管理面板中更新客户电子邮件时出现问题

_AC-13409 - [GitHub问题](https://github.com/magento/magento2/issues/39394) - [GitHub代码贡献](https://github.com/magento/magento2/commit/d3ea191d)_

#### 新闻稿订阅启用的开关无法按网站/商店工作

当我们在全局级别上禁用了多个网站/商店评论时，系统可正确处理新闻稿订阅

_AC-14283 - [GitHub问题](https://github.com/magento/magento2/issues/39751) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39752)_

#### 弃用“已查看产品”客户区段条件

_AC-14542_

#### [问题]已移除电子邮件泄漏

现在，系统显示“Display an error message indicating the incorrect email if the information email was not required to confirm the account （如果不需要确认输入的电子邮件，则无论客户是否存在，系统都会显示错误消息，指示错误的电子邮件）”。

_AC-14561 - [GitHub问题](https://github.com/magento/magento2/issues/39574) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39570)_

### 管理员UI

#### 对于简单产品的相同配置，购物车页面和产品页面中的FPT值是不同的

_AC-13066 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8953613e)_

#### 禁用样本模块时，无法保存多选/选择属性选项

_AC-13071 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8953613e)_

#### 对于动态产品的相同配置，购物车页面和产品页面中的FPT值不同

_AC-13075 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8953613e)_

#### 管理中的静态网格上未应用悬停颜色

现在，悬停颜色可按预期应用于管理员静态网格的行。[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [GitHub问题](https://github.com/magento/magento2/issues/35358) - [GitHub代码贡献](https://github.com/magento/magento2/pull/35384)_

#### 受限管理员用户无法批量更新产品状态

自定义管理员可以批量更新产品状态，因为它是网站级别的资产。 只有在受限制管理员有权访问的网站上才会更新状态。

_ACP2E-3772_

#### [暂存2]存储卡片在管理面板上不可见

修复了在升级后，“存储卡”支付选项不再出现在后端订单下单表单中的问题。

_ACP2E-3830 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7accebfa)_

### B2B

#### 来宾签出时公司字段验证失败

_AC-14987 - [GitHub问题](https://github.com/magento/magento2/issues/40011) - [GitHub代码贡献](https://github.com/magento/magento2/commit/f1adb44e)_

### 捆绑

#### 跨主题从捆绑输出中排除Hugerte编辑器JS文件

_AC-15128 - [GitHub代码贡献](https://github.com/magento/magento2/commit/43648891) - [GitHub代码贡献](https://github.com/magento/magento2/commit/2bc584af)_

### 购物车和结帐

#### 缺少已分组的产品前端数量验证

尝试添加负数量和最大数量时，系统现在工作正常并显示验证错误

_AC-13524 - [GitHub问题](https://github.com/magento/magento2/issues/39479) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39480)_

#### 来宾前缀未保存到报价地址2.4.8

_AC-14705 - [GitHub问题](https://github.com/magento/magento2/issues/39915) - [GitHub代码贡献](https://github.com/magento/magento2/commit/f1adb44e)_

#### [问题]设置报价单项目的价格，而不是base_price

如果前端的一个网站中有多种货币，则系统将正确处理报价项目的价格设置为base_price，而不是价格

_AC-9985 - [GitHub问题](https://github.com/magento/magento2/issues/38094) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36878)_

#### 如果订单是在一个商店视图中创建的，则[云]最近订单未出现在其他商店视图中

解决了“我的帐户”页面未显示同一商店中其他商店视图的最近订单的问题。 已更新订单检索逻辑，以确保所有商店视图中的订单可见性一致，与“我的订单”页面的行为一致。

_ACP2E-3807 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a20a6ff2)_

#### 数量显示为  添加捆绑包产品时管理员客户购物车部分中的0  

现在，客户活动中的购物车部分可显示正确的数量。 以前，数量显示为0。

_ACP2E-3872 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL购物车和结账

#### 通过GraphQL下订单时将消息映射到错误代码时出错

GraphQL调用对不存在或不活动的购物车下订单时，现在会在所有商店视图中正确返回CART_NOT_ACTIVE或CART_NOT_FOUND错误代码，从而修复了已翻译错误消息以前导致未定义代码的问题。

_ACP2E-3942 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7accebfa)_

### 购物车和结账、GraphQL、库存/MSI

#### 即使可销售库存很高，CartItemInterface中的is_available属性也会返回false

当可销售库存较高时，is_available属性返回true。 以前，它始终返回false。

_ACP2E-3885 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3ad96f6a)_

### 目录

#### 目录URL资源(_getCategories)中的作用域错误

如果在类别URL资源的存储作用域中未定义任何值，此PR会将回退添加到默认作用域。

_AC-11011 - [GitHub问题](https://github.com/magento/magento2/issues/38393) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38394)_

#### [问题]检查OpenGraph是否可以显示价格

当我们使用隐藏价格的插件时，系统工作正常，并且此更改价格不会显示在OG标签中。

_AC-11635 - [GitHub问题](https://github.com/magento/magento2/issues/38512) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38510)_

#### [错误] REST API：更新特殊价格未为所有商店视图设置值

_AC-13671 - [GitHub问题](https://github.com/magento/magento2/issues/39521) - [GitHub代码贡献](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] PHP错误未通知

此PR可更改循环变量名称，以便在给定的产品上正确添加“_cache_instance_product_ids”数据，以用于后续调用。

_AC-14159 - [GitHub问题](https://github.com/magento/magento2/issues/39641) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39642)_

#### [Mainline] [CLOUD]映像大小调整占用的磁盘空间超过400GB

修复后，与 — skip_hidden_images标志一起使用的`catalog:images:resize`命令将不会为没有图像的网站生成图像缓存。

_ACP2E-3869 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9ad7d277)_

#### 提供的CountryID不存在 — 爱尔兰(IE)

修复后，爱尔兰邮政编码可用于搜索取车地点。

_ACP2E-3932 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4ca73607) - [GitHub代码贡献](https://github.com/magento/inventory/commit/d2f1d6c6)_

### 目录、性能

#### 管理员中的类别加载速度非常慢

类别加载性能有显着改进。 以前，加载导致超时问题的类别需要很长时间。

_ACP2E-3891 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4ca73607)_

### 目录，定价

#### 应用于子产品的目录价格规则折扣错误

修复了以下问题：当两个规则具有相同的优先级时，变体的目录价格规则将由父可配置产品覆盖。

_ACP2E-3693 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a20a6ff2)_

### 目录，搜索

#### RestApi请求“/rest/default/V1/categories？searchCriteria%5Bpage_size%5D=1”失败，并出现超时错误

_AC-13358 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7bdafaa2)_

### 内容

#### 升级到magento 2.4.7后，p2无法看到新上传的文件媒体集

_AC-13262 - [GitHub问题](https://github.com/magento/magento2/issues/39275)_

#### 从图库映像中完全删除将保留设置范围的角色/类型（基本/小型/缩略图），重新添加“旧”角色/类型后会显示

系统在存储范围中按预期工作，映像根据默认范围继承新添加映像的角色/类型

_AC-13556 - [GitHub问题](https://github.com/magento/magento2/issues/39481) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39680)_

#### [小错误]当字段值包含`listing component`时，无法点击管理面板`\`的筛选器

过滤页面标题中存在斜杠时(例如：Magento\Store)，系统工作正常

_AC-13661 - [GitHub问题](https://github.com/magento/magento2/issues/39513) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39535)_

#### 包含“0” ID的CMS页面不存在”日志泛滥

创建管理员用户后以及创建新页面system后，系统按预期工作。log没有任何错误消息

_AC-14254 - [GitHub问题](https://github.com/magento/magento2/issues/39743) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39746)_

#### 目录链接构件使用错误的URL

添加目录产品链接和目录类别链接后，系统现在可以正确处理构件，并且还能在html源中显示正确的url

_AC-14437 - [GitHub问题](https://github.com/magento/magento2/issues/39464) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39710)_

#### 如果用户没有小组件权限，则页面生成器的产品组件无法正常工作

在修复之前，当访问没有权限的小组件时，页面会引发一般错误并显示“正在加载”GIF。 现在，修复后，将显示一个模式窗口，显示“抱歉，您需要权限才能查看此内容。” 消息。

_ACP2E-3664 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### GraphQL中未应用页面生成器产品小组件排序

修复了GraphQL“路由”查询响应未在Page Builder产品内容类型中按正确排序顺序返回产品的问题。

_ACP2E-3898 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### 由于ICU库版本，非英语店面出现定价显示问题

修复后，产品价格可在希伯来语（以色列）区域设置中正确显示。

_ACP2E-3938 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7accebfa)_

#### 正在更新已清除设计配置的存储区代码

修复了由于配置缓存未正确刷新而更新商店视图代码清除设计配置设置的问题。

_ACP2E-3941 - [GitHub代码贡献](https://github.com/magento/magento2/commit/462ede94)_

### 框架

#### 使用自定义数据库触发器运行命令安装程序:upgrade时出错

_AC-11487 - [GitHub问题](https://github.com/magento/magento2/issues/38481)_

#### 无法使用扩展属性的多值表单元素扩展网站/组/商店实体表单

此PR允许多值表单元素将数据提交到网站/组/商店表单。

_AC-11657 - [GitHub问题](https://github.com/magento/magento2/issues/24070) - [GitHub代码贡献](https://github.com/magento/magento2/pull/24094)_

#### [问题]删除作用域解析程序用法

此PR会全局解析管理员URL设置，而不是解析当前存储

_AC-11736 - [GitHub问题](https://github.com/magento/magento2/issues/38566) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38554)_

#### 通过设置路线使用默认Nginx配置公开的Magento版本

系统现在正按预期运行，不会公开站点正在运行的确切Magento版本

_AC-13205 - [GitHub问题](https://github.com/magento/magento2/issues/39227) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39228)_

#### [问题]重构报价地址验证方法

此PR包含对doValidate方法的可读性改进。

_AC-13214 - [GitHub问题](https://github.com/magento/magento2/issues/38230) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38219)_

#### Magento选项 — 运行cli时从未使用过magento-init-params？

_AC-13231 - [GitHub问题](https://github.com/magento/magento2/issues/39248) - [GitHub代码贡献](https://github.com/magento/magento2/commit/132b9e68)_

#### getItemsByColumnValue类型声明错误

现在，系统在getItemsByColumnValue函数中将输入参数$value正确定义为基元类型，而不是数组，从而确保该函数返回预期的集合。 以前，如果使用具有单个值的数组作为输入参数，该函数将返回空值，并且IDE会将其标记为错误。

_AC-13240 - [GitHub问题](https://github.com/magento/magento2/issues/33070) - [GitHub代码贡献](https://github.com/magento/magento2/pull/33120)_

#### 在Magento 2.4.7多存储实施中，与FPC关联的缓存密钥

_AC-13719 - [GitHub问题](https://github.com/magento/magento2/issues/39456) - [GitHub代码贡献](https://github.com/magento/magento2/commit/ae6f305b)_

#### Magento Rest API公开PII

_AC-13904 - [GitHub问题](https://github.com/magento/magento2/issues/39336)_

#### 部分索引停止适用于有大量更新的客户

_AC-14424 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7bdafaa2)_

#### 在模块内部无需调查“使用严格”

_AC-14517 - [GitHub代码贡献](https://github.com/magento/magento2/commit/77c589a6)_

#### 下载配送标签后，发现发现部分配送数量与运费和包装费不符。

_AC-14560_

#### MView机制在触发器执行时静默忽略错误

_AC-14567 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ae6f305b)_

#### [问题]避免在加载布局XML合并期间出现大量不必要的异常

此PR引入了一个新函数（对于B/C兼容性，我们不覆盖受保护的_loadXmlString）以加载并且不会引发异常

_AC-14580 - [GitHub问题](https://github.com/magento/magento2/issues/39877) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37570)_

#### [问题]在模块保险库图形Ql中使用构造函数属性提升

此PR将使用VaultGraphQl模块中的属性升级替换构造函数属性

_AC-14616 - [GitHub问题](https://github.com/magento/magento2/issues/39900) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36996)_

#### [问题]已删除模块前端布局的代码冗余。

此PR会删除Magento_Msrp、Magento_LoginAsCustomerAssistance、Magento_Newsletter和Magento_Sitemap模块前端布局的主题布局的代码冗余。

_AC-14625 - [GitHub问题](https://github.com/magento/magento2/issues/30673) - [GitHub代码贡献](https://github.com/magento/magento2/pull/30644)_

#### [问题]删除与Microsoft IIS相关的代码

此PR会按照Magento系统要求文档来清理与Microsoft IIS相关的代码，该文档指出Microsoft Windows操作系统不受支持

_AC-14702 - [GitHub问题](https://github.com/magento/magento2/issues/39910) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39894)_

#### Magnifier.js语法错误

系统Magnifier功能应保持以前的工作方式，magnifierOptions不应在全局范围内可用

_AC-14722 - [GitHub问题](https://github.com/magento/magento2/issues/36200) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39321)_

#### `setup:db:status` CLI命令中的反向端口详细模式

_AC-14807 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7bdafaa2)_

#### 使用tls和2.4.8发送SMTP邮件

_AC-14883 - [GitHub问题](https://github.com/magento/magento2/issues/39947) - [GitHub代码贡献](https://github.com/magento/magento2/commit/3717e6cb) - [GitHub代码贡献](https://github.com/magento/magento2/commit/8b453942) - [GitHub代码贡献](https://github.com/magento/magento2/commit/d3ea191d)_

#### [问题]修复静态内容部署中的并发问题

此PR修复了以下错误：多个并发进程启动以处理相同的主题包，具体取决于主题与其父级的定义方式。

_AC-14944 - [GitHub问题](https://github.com/magento/magento2/issues/39990) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39954)_

#### [问题]删除PHP版本&lt; 8.1的旧版兼容性代码

此拉取请求将删除设计在PHP &lt;8.1上运行的代码。
此外，删除了对PHP_VERSION_ID联系人可用性的检查，因为它在所有PHP版本中都可用

_AC-14971 - [GitHub问题](https://github.com/magento/magento2/issues/39891) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39882)_

#### 登录时FPC不起作用

_AC-14999 - [GitHub问题](https://github.com/magento/magento2/issues/40007) - [GitHub代码贡献](https://github.com/magento/magento2/commit/)_

#### [问题]改进了处理SchemaBuilder的错误

此PR改进了数据库架构的错误消息处理。 它有助于我们识别问题，而无需进行大量调试。

_AC-15020 - [GitHub问题](https://github.com/magento/magento2/issues/39816) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39799)_

#### 由于修改CliStateTest，针对2.4.9-alpha2-develop的SYNC PR集成测试失败

_AC-15136 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2d0f8066)_

#### PHP8.1类型bugfix

现在，当严格处理模式不活动或产品信息可用时，关联的产品会初始化为空数组，而不是false。 此更改确保后续逻辑处理相关产品的行为一致，提高了产品准备过程中的稳定性和可预测性。

_AC-6017 - [GitHub问题](https://github.com/magento/magento2/issues/35808) - [GitHub代码贡献](https://github.com/magento/magento2/pull/35842)_

#### [问题]从框架（第3部分）中删除禁止的`@author`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，从而提高整体代码质量。 以前，某些模块中存在此标记违反了既定的编码标准。

_AC-8343 - [GitHub问题](https://github.com/magento/magento2/issues/37270) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37020)_

#### [问题]在模块发送好友图QL中使用构造函数属性提升

该系统现在利用“发送朋友”GraphQL模块中的构造函数属性提升，增强了代码的可读性，降低了复杂性。 以前，模块使用的属性占据大量行，从而使代码变得更加复杂且不易读取。

_AC-8346 - [GitHub问题](https://github.com/magento/magento2/issues/37235) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37197)_

#### [问题]从`@author`中删除禁止的`Magento_Downloadable`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，从而提高整体代码质量。 以前，某些模块中存在此标记违反了既定的编码标准。

_AC-8355 - [GitHub问题](https://github.com/magento/magento2/issues/37251) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37001)_

#### [问题]删除禁止的`@author`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，从而提高代码质量和一致性。 以前，某些模块中存在此标记违反了既定的编码标准。

_AC-8358 - [GitHub问题](https://github.com/magento/magento2/issues/37264) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37014)_

#### [问题]删除禁止的`@author`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，从而提高整体代码质量。 以前，某些模块中存在此标记违反了既定的编码标准。

_AC-8360 - [GitHub问题](https://github.com/magento/magento2/issues/37261) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37011)_

#### [问题]删除禁止的`@author`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，确保代码更干净和标准化。 以前，某些模块中存在此标记违反了既定的编码标准。

_AC-8361 - [GitHub问题](https://github.com/magento/magento2/issues/37260) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37010)_

#### [问题]删除禁止的`@author`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，从而提高整体代码质量。 以前，某些模块中存在此标记违反了既定的编码标准。

_AC-8363 - [GitHub问题](https://github.com/magento/magento2/issues/37258) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37008)_

#### [问题]删除禁止的`@author`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，从而提高整体代码质量。 以前，某些模块中存在此标记违反了既定的编码标准。

_AC-8375 - [GitHub问题](https://github.com/magento/magento2/issues/37257) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37007)_

#### [问题]删除禁止的`@author`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，从而提高整体代码质量。 以前，某些模块中存在此标记违反了既定的编码标准。

_AC-8376 - [GitHub问题](https://github.com/magento/magento2/issues/37256) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37006)_

#### [问题]删除禁止的`@author`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，从而提高整体代码质量。 以前，某些模块中存在此标记违反了既定的编码标准。

_AC-8400 - [GitHub问题](https://github.com/magento/magento2/issues/37254) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37004)_

#### [问题]删除禁止的`@author`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，从而提高整体代码质量。 以前，某些模块中存在此标记违反了既定的编码标准。

_AC-8401 - [GitHub问题](https://github.com/magento/magento2/issues/37255) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37005)_

#### [问题]改进了服务URL生成的可扩展性

该系统现在允许通过插件自定义服务URL生成功能，从而促进更易于维护的修改方法。 以前，此功能的自定义是通过首选项实现的，这可能没有那么高效或可维护。

_AC-8813 - [GitHub问题](https://github.com/magento/magento2/issues/37404) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37403)_

#### 由于添加了新验证，导致升级2.4.7-p5时出现问题

修复了SchemaBuilder类中，未定义的数组键“列”在架构创建或更新期间导致崩溃的问题。 处理不包含“column”键的表数据时，会发生这种情况。

_ACP2E-3871 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9ad7d277)_

#### PHP8.4弃用错误：升级到Adobe Commerce 2.4.8后出现E_USER_ERROR

面向客户的方案不受此修复的影响。

_ACP2E-3963 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7accebfa)_

### 框架，搜索

#### 单价类别上的Opensearch 2.19.1 illegal_argument_exception

对于包含所有具有相同价格的产品的类别，Opensearch不再引发illegal_argument_exception。 以前，它具有此异常：“[from]参数不能为负”。

_ACP2E-3896 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### 删除产品时customerOrders graphql返回错误

即使订单中的产品被删除，customerOrders graphql请求也不再引发错误。 以前，引发“内部服务器错误”错误。

_ACP2E-3936_

#### 在GraphQL请求中，未在一个网站内的商店视图之间共享愿望清单项目

在修复之前，按商店ID过滤愿望清单项目。 现在，修复之后，愿望清单项目会按网站进行过滤。

_ACP2E-3987 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2a252ae6)_

### GraphQL，产品

#### MediaGalleryInterface中的产品graphql缺少media_type

MediaGallery GraphQL请求现在包含用于产品图像类型的“类型”字段。 以前，媒体集GraphQL请求中不存在此“类型”字段。

_ACP2E-3880 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3ad96f6a)_

### 库存/MSI

#### 重定向到主页并结帐后，没有可用的存储

现在，如果客户导航到付款页面，然后返回到主页，最后返回到结账页面，则以前选择的商店将在“店内提货”配送中预先选择。 以前，在反复返回到结账页面后，将清除“店内挑选”中的选定商店。

_ACP2E-3793 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a20a6ff2) - [GitHub代码贡献](https://github.com/magento/inventory/commit/62c0d79b)_

### 订购

#### AbstractAddress setData(&#39;custom_attributes&#39;， AttributeValue[])中断customAttributes

_AC-10568 - [GitHub问题](https://github.com/magento/magento2/issues/31644)_

#### v2.4.7-p1 Magento重新排序–1订单号

系统按预期工作，从后端重新排序后，订单编号将唯一8位

_AC-12854 - [GitHub问题](https://github.com/magento/magento2/issues/39089) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39399)_

#### 使用Adobe信用卡支付方法结账时丢失产品自定义选项文件上传

_AC-14306 - [GitHub问题](https://github.com/magento/magento2/issues/39647)_

#### 订单状态在处理时卡住

在修复之前，在订购启用了“Ship together”（一起发货）选项的捆绑产品时，在开票和发货后，订单状态不会自动切换为“complete”（完成）。 现在，修复之后，在订单开票并发运后，订单状态会自动切换为“完成”。

_ACP2E-3947 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud]Magento OOTB代码 — 电子邮件模板设置问题

在修复之前，使用异步电子邮件发送时，装运电子邮件与商店订单不一致。 现在，修复之后，将交付正确的商店发货电子邮件订单。

_ACP2E-3998 - [GitHub代码贡献](https://github.com/magento/magento2/commit/462ede94)_

### 其他开发人员工具

#### [问题]受保护成员$_urlHelper的类型提示错误

系统现在使用正确的提示来修复错误的类型提示，该提示也用于构造函数

_AC-10716 - [GitHub问题](https://github.com/magento/magento2/issues/32503) - [GitHub代码贡献](https://github.com/magento/magento2/pull/32496)_

### 性能

#### [问题]更新Store.php

此PR通过跳过当前的存储解析来提高性能。

_AC-14791 - [GitHub问题](https://github.com/magento/magento2/issues/39949) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38717)_

### 定价

#### 对于未设置动态价格的捆绑产品项目，订单Rest API中的价格始终为0

_AC-11925 - [GitHub问题](https://github.com/magento/magento2/issues/38687) - [GitHub代码贡献](https://github.com/magento/magento2/commit/7da46f52)_

### 产品

#### 根据原始价格计算的层价格和目录价格规则的折扣百分比（不含选定选项）。

_AC-12004 - [GitHub问题](https://github.com/magento/magento2/issues/38750)_

#### Magento 2.4.7 minAllowed缺少产品订单数量

系统工作正常，页面源正确显示产品的最小数量

_AC-12909 - [GitHub问题](https://github.com/magento/magento2/issues/39142) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39480)_

#### 执行Magento Payflow Pro测试时出现异常Magento

_AC-13681_

#### 管理面板中产品页面上的可自定义选项网格问题

当我们使用类型下拉菜单创建可自定义的选项时，系统按预期工作

_AC-14003 - [GitHub问题](https://github.com/magento/magento2/issues/39640) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39694)_

#### 申请列表页打印选项不起作用

_AC-14711_

#### 其他客户比较列表中的所有项目在通过管理员登录后都分配给客户

以前，当管理员在后端使用“以客户身份登录”功能时，先前登录的客户比较列表中的产品被错误地分配给当前模拟的客户。  修复后，会为正确的登录客户正确加载比较列表。

_ACP2E-3818 - [GitHub代码贡献](https://github.com/magento/magento2/commit/462ede94)_

### SEO

#### 通过REST API更新产品url_key不会生成301 URL重写

当通过REST API更新产品的URL密钥时，如果将“如果URL密钥已更改，则为URL创建永久重定向”设置设置为“是”，则产品URL重写会创建一个从旧URL到新URL的重定向。

_ACP2E-3900 - [GitHub代码贡献](https://github.com/magento/magento2/commit/462ede94)_

### 销售

#### 在订单状态下拉菜单中选择值时订单状态消失

_AC-15010_

### 安全性

#### 捆绑/合并的JS不属于SRI哈希

在修复之前，生成的包或合并的文件未添加到SRI哈希列表。 现在，这些文件被适当地添加到SRI哈希中。

_ACP2E-3854 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4ca73607)_

### 配送

#### [QUANS] - Magento_Fedex核心模块是否在发送获取新令牌的请求之前检查有效的活动令牌？

Adobe Commerce将不再向FedEx API服务发出许多访问令牌请求。 以前，即使访问令牌仍然有效，Adobe Commerce也始终会向FedEx API发出新请求，这会导致速率限制问题。

_ACP2E-3930 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4ca73607)_

### 暂存和预览

#### 启用类别权限后，无法预览计划产品更新

在修复之前，要启用的将来产品不会以预览模式显示。 现在，即使当前状态为禁用，也会显示它。

_ACP2E-3786 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7accebfa)_

#### 预览期间范围显示不同的存储视图

在此修复之前，cms块和cms页面内容的暂存更新预览可能已在不同存储中打开，而不是在从内容暂存仪表板访问时在cms块或页面上分配的存储中打开。 修复后，如果cms块或页面在暂存更新中仅分配了特定存储，则将从内容暂存仪表板打开预览，并选中正确的存储。

_ACP2E-3815_

#### 缺少对目录价格规则折扣金额字段的验证

以前，使用当前验证规则无法正确验证暂存计划更新中的discount_amount字段。 但是，应用修复后，将相应地验证discount_amount字段。

_ACP2E-3867 - [GitHub代码贡献](https://github.com/magento/magento2/commit/462ede94)_

### 税金

#### 订单总计错误，此舍入不适用于价格计算。

现在，系统在计算price_after_discount、discount_amount和税额时可正确处理。
订单的实际总计

_AC-11389 - [GitHub问题](https://github.com/magento/magento2/issues/38455) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39687)_

### 测试框架

#### [问题]忽略lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en...

系统现在会忽略运行单元测试时生成的“env.php”文件，从而确保git状态在运行测试后保持干净。 以前，运行单元测试会生成一个新文件“env.php”，导致git状态显示发现的新文件并使其显得脏兮兮的。

_AC-13293 - [GitHub问题](https://github.com/magento/magento2/issues/39304) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37631)_

#### [问题]修复侦听器的集成测试问题

系统现在可以在集成测试中正确识别并处理\Magento\TestFramework\App\Config\Interceptor ，从而确保测试可以访问必需的数据，即使存在类上的插件也是如此。 以前，系统无法考虑\Magento\TestFramework\App\Config成为\Magento\TestFramework\App\Config\Interceptor的可能性，导致在尝试访问$data属性时出错。

_AC-13305 - [GitHub问题](https://github.com/magento/magento2/issues/39324) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37187)_

#### [问题] MFTF：将电子邮件提交到已启用验证码的朋友表单

在启用CAPTCHA的情况下，测试案例将解决“Email to Friend”表单的功能，确保表单提交过程在验证码值不正确和正确的情况下正常工作。

_AC-13492 - [GitHub问题](https://github.com/magento/magento2/issues/39462) - [GitHub代码贡献](https://github.com/magento/magento2/pull/32830)_

#### 由于phpunit v10，[TestFramework]的TestCase：：getTestResultObject用法无效

_AC-13502 - [GitHub问题](https://github.com/magento/magento2/issues/39463)_

#### AC 2.4.7-p3中特定于环境的单元测试失败

此问题修复了未在所有版本和环境上重现的单元测试故障。 以前，修复某些单元测试失败，原因是库版本不同或缺少在更高版本中添加的功能。

_ACP2E-3712 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9ad7d277)_

### 工具/ DataMigrationTool

#### 无差异时出现[ATLH]致命错误

没有可显示的差异时，致命错误不再显示

_ACP2E-3901_

### UI框架

#### WYSIWYG在动态行中为空

_AC-12336 - [GitHub问题](https://github.com/magento/magento2/issues/38893) - [GitHub代码贡献](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [问题]修复MIME类型拼写错误

系统可正确处理并修复gif图像的mime类型和打字错误

_AC-8001 - [GitHub问题](https://github.com/magento/magento2/issues/36899) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36669)_

#### [问题]避免直接访问审阅列表Ajax

系统可正确处理并避免直接访问审阅列表Ajax

_AC-9381 - [GitHub问题](https://github.com/magento/magento2/issues/37920) - [GitHub代码贡献](https://github.com/magento/magento2/pull/33876)_

### 升级 — 升级兼容性工具

#### 已弃用的功能：创建动态属性Magento\Framework\Acl：：$_roleRegistry

_AC-12343 - [GitHub问题](https://github.com/magento/magento2/issues/37469)_
