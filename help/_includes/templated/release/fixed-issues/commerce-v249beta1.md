---
source-git-commit: 34e2262ad8b4fa1a2e7ade8d3b16258f9873822d
workflow-type: tm+mt
source-wordcount: '26949'
ht-degree: 0%

---
# Adobe Commerce修复了问题(v2.4.9-beta1)

## 修复了v2.4.9-beta1中的问题

我们已在Adobe Commerce 2.4.9-beta1核心代码中修复了560个问题。 此版本中包含的已修复问题的子集如下所述。

### API

#### 在applySpecialPrice上验证的“至今特殊价格”有误

对于特殊价格和产品特殊价格，系统正常运转。产品特殊价格将在管理员设定的日期或第三方系统通过REST API设定的日期到期

_AC-13130 - [GitHub问题](https://github.com/magento/magento2/issues/39169) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39690)_

#### 通过WebAPI悖论[WebAPI]客户电子邮件确认

修复了由于确认前需要令牌的授权悖论，客户无法通过WebAPI激活其帐户的问题。 该更新允许未确认的客户通过API成功激活其帐户，从而确保一致的功能确认流程。

_AC-13281 - [GitHub问题](https://github.com/magento/magento2/issues/39255) - [GitHub代码贡献](https://github.com/magento/magento2/commit/c95ed7d7)_

#### 通过仅包含付款信息的REST API创建订单时，管理控制面板中出现“缺少帐单地址”错误

修复了在没有账单地址的情况下通过API创建订单，从而导致管理员仪表板崩溃的问题。
现在，没有账单地址的订单将受到限制并且不再创建。

_AC-14049 - [GitHub问题](https://github.com/magento/magento2/issues/39651) - [GitHub代码贡献](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Rest API中的产品添加到购物车问题

修复了未分配到特定网站的产品仍可能被添加到购物车并购买的问题。
现在，显示一条错误消息：“您尝试添加的产品不可用。”

_AC-15054 - [GitHub问题](https://github.com/magento/magento2/issues/40029) - [GitHub代码贡献](https://github.com/magento/magento2/commit/f5cc09fc)_

#### 更新商店标签时，属性选项标签被覆盖

修复了通过REST API更新多选产品属性会覆盖所有store_labels，从而删除现有特定于存储的标签的问题。
现在，在更新默认商店视图标签时，Magento会将提供的标签与现有标签合并，而不是完全覆盖它们。
这可确保在更新后，其他商店视图的存储区特定标签保持不变。

_AC-15208 - [GitHub问题](https://github.com/magento/magento2/issues/40093) - [GitHub代码贡献](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [问题]已阐明属性选项已存在响应

现在，系统用更清晰、文法正确的版本替换了令人尴尬的短语“如果已存在则获取新文件名”：“如果已存在则获取新文件名。” 这提高了可读性和用户理解度。
属性选项响应也相同。

_AC-15473 - [GitHub问题](https://github.com/magento/magento2/issues/39943) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39941)_

#### /V1/products/special-price API端点中的内部服务器错误

修复了对/V1/products/special-price和相关定价API的格式错误的请求由于TypeError为null而返回500内部服务器错误的问题。
现在，API可正确验证输入并为无效负载返回400错误，从而提高错误处理和API可靠性。

_AC-6419 - [GitHub问题](https://github.com/magento/magento2/issues/35934) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a7ef6300)_

#### `/V1/order/&lbrace;orderId&rbrace;/ship` API终结点中的内部服务器错误

系统现在修复了`/V1/order/{orderId}/ship` API端点中的内部服务器错误，并返回400错误，因为请求格式不正确。

_AC-6420 - [GitHub问题](https://github.com/magento/magento2/issues/35931) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38282)_

#### /V1/creditmemo API终结点中的内部服务器错误

修复了对/V1/creditmemo API的格式错误的请求返回500内部服务器错误的问题。
现在，API正确验证请求并为无效负载返回400错误，从而提高错误处理和稳定性。

_AC-6422 - [GitHub问题](https://github.com/magento/magento2/issues/35924) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a7ef6300)_

#### 创建新属性时，Rest API和Magento后端对attribute_code使用不同的验证方法

修复了Magento管理员在attribute_code中允许使用大写字母，但REST API在创建产品属性期间拒绝使用的大写字母的不一致问题。
现在，管理员和REST API都遵循相同的验证方式，从而能够成功创建包含大写字母的属性。

_AC-6660 - [GitHub问题](https://github.com/magento/magento2/issues/33138) - [GitHub代码贡献](https://github.com/magento/magento2/commit/8670a2b4)_

#### 通过REST API在属性创建和更新之间执行不同的验证

修复了在通过REST API创建属性期间验证不一致导致分配的backend_type不正确的问题。
现在，系统在有效时设置正确的后端类型，为无效值引发异常，或者如果未提供，则适当回退，从而确保一致的属性行为。

_AC-6885 - [GitHub问题](https://github.com/magento/magento2/issues/36327) - [GitHub代码贡献](https://github.com/magento/magento2/commit/64823f95)_

#### 格式错误的请求正文或参数导致“内部服务器错误”

格式错误的请求正文或参数现在会返回清晰的“400 Bad Request”响应。
以前，将格式错误的请求正文或参数发送到各种REST API端点（如/V1/carts/search、/V1/orders、/V1/products等），会导致一般的“内部服务器错误”(500)，从而难以诊断输入问题。
现在，Adobe Commerce返回“400个错误请求”响应，在请求无效时提供更明确的反馈。

_AC-746 - [GitHub问题](https://github.com/magento/magento2/issues/32784) - [GitHub代码贡献](https://github.com/magento/magento2/commit/f1adb44e)_

#### `/orders`（或`/orders/:id`）终结点缺少“state”和“status”字段

修复了数据库值为null时，`/orders`和`/orders/{id}` API响应省略了状态和状态字段的问题。
现在，响应中会始终返回这两个字段，从而确保与API文档合规性并提高数据可靠性。

_AC-9244 - [GitHub问题](https://github.com/magento/magento2/issues/37807) - [GitHub代码贡献](https://github.com/magento/magento2/commit/01cee3c3)_

#### 对于async.magento.configurableproduct.api.optionrepositoryinterface.save.post，异步批量操作保持打开状态

如果请求正文不是Array，则批量API端点现在将引发错误，因此需要批量项目键是从0开始的连续数字。 以前，由于批量请求中提交的任意项目键，无法更新批量项目状态。

_ACP2E-3544 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9608ca21)_

#### is_subscribed值上的[CLOUD] API REST错误未考虑使用searchCriteria的当前存储中

API REST客户查询使用searchCriteria从正确的存储中提取正确的“is_subscribed”值
以前，API REST客户查询在提取is_subscribed”值时不考虑存储。

_ACP2E-3621 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9608ca21)_

#### async.operations.all可以为1个SKU创建多个条目

现在，保存和更新相同产品的并发请求会被序列化，以防止可能导致数据不一致或产品重复的竞争情况

_ACP2E-3744 - [GitHub代码贡献](https://github.com/magento/magento2/commit/520f9e30)_

#### 订单“base_row_total”和“row_total”在REST API响应中显示单个项目价格

现在，订购详细信息的REST API响应包含“base_row_total”和“row_total”属性的正确值，以防订购了多个相同的项目

_ACP2E-3874 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4ca73607)_

#### REST API端点export-stock-salable-qty返回不正确的项目total_count

修复了库存导出库存可销售数量API中total_count错误地限制为页面大小的分页问题。 以前，如果将/rest/all/V1/inventory/export-stock-salable-qty/website/base端点与分页参数（如page_size=5）一起使用，则响应中的total_count字段将返回5，而不是符合搜索条件的实际产品总数。 进行此修复后，total_count字段现在可正确反映可用的产品总数，而不考虑page_size参数，从而确保在所有Magento REST API端点之间具有一致的分页行为。

_ACP2E-4086 - [GitHub代码贡献](https://github.com/magento/inventory/commit/5632fb5e)_

#### 购物车项目REST API中的自定义选项ID存在验证问题。

REST API V1/guest-carts/&lt;cartId>/items/和V1/carts/mine/items/现在验证“product_options.extension_attributes.custom_options”。*.option_id”，以确保它为购物车项目SKU引用了有效的option_id。 以前，在数据库中处理和保存此参数时不会进行验证。

_ACP2E-4138 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 从购物车获取产品并更改商店标题语言时不会更改

GraphQL customerCart查询现在会根据商店标题值返回产品属性值。 以前，在通过GraphQL从购物车中检索产品时更改商店标题语言不会反映更新的语言，从而导致本地化不一致。

_ACP2E-4227 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6e134409)_

#### 礼品卡产品的REST API /media端点失败 — 返回“无法保存产品”

在修复之前，允许您创建不包括全球范围内的金额的礼品卡产品。 通过此修复，添加了一个检查全局范围中金额的验证。

_ACP2E-4395_

### API、购物车和结账

#### 对于配送信息，服务器端验证使用REST API不起作用

修复了REST API中的问题：运送地址信息验证不符合管理员后端中定义的属性配置。 现在，验证正确遵循配置的设置。

_ACP2E-4156 - [GitHub代码贡献](https://github.com/magento/magento2/commit/45cbf9b6)_

### API，目录

#### 删除默认网站/商店折扣价格API端点

以前，删除默认基本网站并将辅助网站用作默认网站会导致在尝试更新辅助网站的层价时出错。 但是，在应用此修复后，即使删除或停用基础网站，也可以成功更新层价格。

_ACP2E-4334 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0a3b7032)_

### API、框架

#### 应用程序服务器上的RedisRequestLogger\RedisClient（速率限制器）异常

修复后，如果安装了PHP redis扩展，则可以将速率限制功能与GraphQL应用程序服务器一起使用。

_ACP2E-4237 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e885088b)_

### API，导入/导出

#### 异步发票退款API创建离线退款而不是在线退款

修复了异步退款操作，其中无法正确处理带`is_online`参数的退款请求。

_ACP2E-4394 - [GitHub代码贡献](https://github.com/magento/magento2/commit/61c96348)_

### API、顺序

#### [CLOUD]订单000075568的行总计出现订单信息问题

修复了以下问题：当项目完全折扣时，订单API响应中的row_total_incl_tax值返回为近零残值，而不是0.00。

_ACP2E-3950 - [GitHub代码贡献](https://github.com/magento/magento2/commit/462ede94)_

### 帐户

#### [问题]修复目录小组件模板选项中的拼写错误

系统现在修复了目录构件模板选项中的拼写错误。

_AC-11576 - [GitHub问题](https://github.com/magento/magento2/issues/38185) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38178)_

#### [问题]删除了后端网格上不必要的间距

现在，当存在选定项时，系统会删除后端网格中不必要的间距

_AC-11579 - [GitHub问题](https://github.com/magento/magento2/issues/38502) - [GitHub代码贡献](https://github.com/magento/magento2/pull/32622)_

#### 使用多字节字符时，保存的客户组代码与输入不匹配

修复了使用多字节字符的客户组代码被截断并且与输入的值不匹配的问题。 此更新可确保正确保存完整的输入，从而能够准确创建具有多字节名称的客户组。

_AC-13335 - [GitHub问题](https://github.com/magento/magento2/issues/39342) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a06a4a57)_

#### 在包含o和.swiss域的管理面板中更新客户电子邮件时出现问题

管理员面板现在接受包含特殊字符和.swiss域的客户电子邮件。
以前，将客户电子邮件更新到max@mostermann.swiss等地址失败，并出现有关无效主机名和TLD的错误。
AC-13409

_AC-13409 - [GitHub问题](https://github.com/magento/magento2/issues/39394) - [GitHub代码贡献](https://github.com/magento/magento2/commit/d3ea191d)_

#### 新闻稿订阅启用的开关无法按网站/商店工作

当我们在全局级别上禁用了多个网站/商店评论时，系统可正确处理新闻稿订阅

_AC-14283 - [GitHub问题](https://github.com/magento/magento2/issues/39751) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39752)_

#### 弃用“已查看产品”客户区段条件

“已查看产品”客户区段条件现已弃用。
以前，使用此条件可能会由于MySQL查询繁重而导致站点中断。 条件现在标记为已弃用且不受支持。

_AC-14542_

#### [问题]已移除电子邮件泄漏

现在，系统显示“Display an error message indicating the incorrect email if the information email was not required to confirm the account （如果不需要确认输入的电子邮件，则无论客户是否存在，系统都会显示错误消息，指示错误的电子邮件）”。

_AC-14561 - [GitHub问题](https://github.com/magento/magento2/issues/39574) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39570)_

#### 无法通过`updateProductsInWishlist` GraphQL突变清除愿望清单项备注

修复了希望列表注释未通过GraphQL突变进行更新的问题。
现在，注释会正确更新，并反映在API响应和店面中。

_AC-14682 - [GitHub问题](https://github.com/magento/magento2/issues/39911) - [GitHub代码贡献](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 在重新登录之前，在移动设备上删除的产品仍会显示在Web的小型比较部分中

现在，系统删除产品后，产品会立即从移动和Web上的所有比较视图中消失，包括迷你比较部分。

_AC-14703 - [GitHub问题](https://github.com/magento/magento2/issues/39905) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40023)_

#### 当设置为“否”时，忽略显示前缀/后缀设置

修复了即使在配置中禁用客户名称前缀/后缀后，订单中仍继续显示客户名称前缀的问题。
现在，根据配置设置，从订单详细信息中去除前缀/后缀值。

_AC-15074 - [GitHub问题](https://github.com/magento/magento2/issues/40036) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Storefront客户帐户注册：电子邮件地址格式已转换为不同的域格式

此错误解决了域中具有特殊字符（例如òbe.com）的客户电子邮件自动转换为旁路代码格式(tec55241@xn--adbe-mqa.com)的问题。
在Magento 2.4.9-alpha3中，此修复程序可确保此类电子邮件ID保持不变并有效，从而防止出现投放错误。

_AC-15177 - [GitHub代码贡献](https://github.com/magento/magento2/commit/68a45d0a)_

#### 注册表单上缺少验证消息(mage-error)

修复了客户帐户创建页面上的必填字段在留空时未显示验证消息的问题。
现在，对于所有空或不正确的字段，会显示相应的错误消息。

_AC-15185 - [GitHub问题](https://github.com/magento/magento2/issues/40076) - [GitHub代码贡献](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 订单取消模式标题缺少翻译

系统现在修复了店面订单取消模式中缺少的翻译。 当客户单击“我的帐户”>“我的订单”页上的“取消”按钮时，系统将显示一个要求说明取消原因的模态。 但是，模态标题以前是硬编码的，无法翻译。 此更改可确保模态标题使用正确的翻译方法。

_AC-15260 - [GitHub问题](https://github.com/magento/magento2/issues/40098) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40100)_

#### 登录magento 2.4.8后出现的问题 — p1

修复了Magento 2.4.8-p1上登录后主页仍显示“Create an Account”（创建帐户）链接的问题。
现在，与其他页面一样，该链接在登录后正确隐藏。

_AC-15292 - [GitHub问题](https://github.com/magento/magento2/issues/40120)_

#### 删除客户之前的[问题]设置isSecureArea

系统现在工作正常，此PR将isSecureArea设置为删除流程，客户可以再次成功注册。

_AC-15723 - [GitHub问题](https://github.com/magento/magento2/issues/40211) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38462)_

#### 创建客户帐户期间出现当前区域错误，禁止执行[云]删除操作

修复程序保存地址无效的客户后，会返回一条描述无效原因的消息，而不是相关的“当前区域禁止执行删除操作”。

_ACP2E-3791 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6ea61121)_

#### 禁用“eav”缓存时，[B2B]已登录客户的Webapi请求进入无限循环

修复后，在某些REST请求期间，禁用eav缓存不会导致无限循环。

_ACP2E-4191 - [GitHub代码贡献](https://github.com/magento/magento2/commit/45cbf9b6)_

#### 加载某些区域设置时出错

修复了在使用阿拉伯区域设置且“出生日期”属性设置为显示在店面时创建客户帐户失败的问题。 现在可以在此配置中成功创建帐户。

_ACP2E-4311 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2687b487)_

#### 错误更新帐户信息时的日期无效

客户现在可以在使用阿拉伯区域设置时成功更新其帐户。 以前，尝试保存帐户信息时，由于日期无效错误，出生日期失败。

_ACP2E-4344 - [GitHub代码贡献](https://github.com/magento/magento2/commit/31258bf6)_

#### 发送邀请功能期间出现警告消息

修复了在“发送邀请”页面上添加电子邮件字段时，如果“允许客户向邀请电子邮件添加自定义消息”设置被禁用，则不会显示警告消息“允许的最大X个电子邮件地址”的问题。
以前，警告仅在启用自定义消息时出现，这会造成用户体验不一致。 现在，无论自定义消息配置设置如何，都会始终显示最大电子邮件限制警告。

_ACP2E-4374_

### 帐户，管理员UI

#### [Cloud]没有cartId的此类实体

解决了在同一会话中使用具有两个公司管理员帐户的作为客户登录时导致“没有具有cartId的此类实体”错误的问题。

_ACP2E-4137 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e885088b)_

#### 客户创建表单错误消息未翻译

修复了客户验证错误消息未正确翻译且未在不同界面间设置格式的问题。 验证错误现在会在应用程序的所有区域（storefront、adminhtml、rest api和graphql）中显示正确翻译的消息。

_ACP2E-4354 - [GitHub代码贡献](https://github.com/magento/magento2/commit/31258bf6)_

### 管理员UI

#### 按名称排序时，类别产品网格>状态和可见性列为空

修复了按产品名称排序时，“类别产品”网格中的“状态”和“可见性”列显示为空的问题。
现在，网格在排序后可正确显示所有列数据，从而确保在管理面板中提供了准确的产品信息。

_AC-10659 - [GitHub问题](https://github.com/magento/magento2/issues/38233) - [GitHub代码贡献](https://github.com/magento/magento2/commit/3cf1a106)_

#### 电子邮件模板存储区切换器

修复了由于已弃用jQuery代码，在单击时新闻稿电子邮件模板预览中的商店切换器未打开的问题。 更新加载事件可恢复正常运行，从而允许用户按预期访问存储切换器。

_AC-12334 - [GitHub问题](https://github.com/magento/magento2/issues/38892) - [GitHub代码贡献](https://github.com/magento/magento2/commit/8670a2b4)_

#### 对于简单产品的相同配置，购物车页面和产品页面中的FPT值是不同的

现在，简单产品的购物车页面和产品页面中的FPT值是一致的。
以前，即使应用了相同的配置，购物车和产品页面之间的固定产品税(FPT)值在小数位上可能有所不同。
AC-13066

_AC-13066 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8953613e)_

#### 禁用样本模块时，无法保存多选/选择属性选项

现在，在禁用样本模块时，可以保存多选/选择属性选项。
以前，在创建新的多选/选择属性选项时，禁用“样本”模块会导致异常。
AC-13071

_AC-13071 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8953613e)_

#### 对于动态产品的相同配置，购物车页面和产品页面中的FPT值不同

现在，动态产品的购物车页面和产品页面中的FPT值是一致的。
以前，对于同一配置，FPT（固定产品税）值在购物车和产品页面之间的小数位可能有所不同。
AC-13075

_AC-13075 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8953613e)_

#### 日期ui组件中未采用日期格式

解决了日期UI组件忽略配置的格式并显示错误值的问题。 此修复程序确保日期字段现在遵循指定的格式（例如Y-m-d）以便显示和输入。

_AC-13174 - [GitHub问题](https://github.com/magento/magento2/issues/39218) - [GitHub代码贡献](https://github.com/magento/magento2/commit/913bf1a6)_

#### 没有可用于删除源的选项

在管理UI中为清单源添加了删除选项，允许管理员删除额外的源，而不是仅启用或禁用它们。 此增强通过更好地控制未使用的来源来改进库存管理。

_AC-13354 - [GitHub问题](https://github.com/magento/magento2/issues/32362) - [GitHub代码贡献](https://github.com/magento/inventory/commit/1b6c8a3e)_

#### 管理员中的类别树未展开以显示级别3中所有选定的嵌套类别

修复了管理员类别树未展开以显示超过级别3的选定嵌套类别的问题。 修复后，所有选定类别都会自动展开，从而提高与类别相关的条件的可见性和可用性。

_AC-13363 - [GitHub代码贡献](https://github.com/magento/magento2/commit/913bf1a6)_

#### [问题]使用角色树改善用户体验

此拉取请求会添加按钮，以折叠所有项、展开所有项以及展开包含选定项的分支。 此功能类似于类别树（目录 — >库存 — >类别）中提供的功能

_AC-14020 - [GitHub问题](https://github.com/magento/magento2/issues/39654) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36511)_

#### 导入/导出操作日志不会在“系统”>“操作日志”>“报表网格”中创建

为导入/导出管理操作实施了日志记录，以便这些操作现在显示在系统>操作日志>报表中。 这通过记录以前缺失的导入活动，可确保更好地跟踪审核。

_AC-14266 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b5e99d20)_

#### Symfony\Component\Mime\Exception\LogicException： “Sender”标头必须为“Symfony\Component\Mime\Header\MailboxHeader”的实例（得到“Symfony\Component\Mime\Header\MailboxListHeader”）

现在，为SMTP配置自定义返回路径地址时，Adobe Commerce会成功发送注册电子邮件。 以前，在system/smtp/set_return_path设置为2且system/smtp/return_path_email设置为自定义地址的vanilla Adobe Commerce 2.4.8上，客户注册已完成，但未发送注册电子邮件，并且Adobe Commerce记录了以下错误：Symfony\Component\Mime\Exception\LogicException：“Sender”标头必须为“Symfony\Component\Mime\Header\MailboxHeader”的实例（得到“Symfony\Component\Mime\Header\MailboxListHeader”）。

_AC-14520 - [GitHub问题](https://github.com/magento/magento2/issues/39823) - [GitHub代码贡献](https://github.com/magento/magento2/commit/1e14bd72)_

#### 刷新顺序未获取最新的自定义属性数据

修复了刷新订单页面未显示最新客户自定义属性数据的问题；修复后，现在无需取消并重新创建订单即可反映更新的属性值。

_AC-14690 - [GitHub问题](https://github.com/magento/magento2/issues/30301)_

#### [问题]替换已弃用的转义符

删除了已弃用的getEscaper()，并通过构造函数注入添加了它。

_AC-15132 - [GitHub问题](https://github.com/magento/magento2/issues/40062) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38135)_

#### 在移动视图中欢迎消息重叠产品类别

修复了欢迎名称与移动设备视图中的产品类别重叠、阻止点击的UI问题。
现在，类别完全可见且可点击，没有重叠问题。

_AC-15166 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Ui表单重置按钮无法按预期工作

单击重置按钮时系统现在工作正常，没有重新加载整个页面，表单数据将被重置。

_AC-15204 - [GitHub问题](https://github.com/magento/magento2/issues/40092) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40094)_

#### [问题] PageCache/AccessList：添加CIDR支持

现在，系统接受网络中的清除请求，因此可以更轻松地只提供CIDR范围。

_AC-15804 - [GitHub问题](https://github.com/magento/magento2/issues/39953) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37809)_

#### [问题]将说明性标题添加到缓存管理按钮

现在，当您移动光标时，系统会向缓存管理按钮添加说明性标题

_AC-16212 - [GitHub问题](https://github.com/magento/magento2/issues/38607) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38598)_

#### 提供使用网格批量删除税率的功能

管理员用户现在可以同时从“管理员税率”网格中删除多个税率。  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [GitHub问题](https://github.com/magento/magento2/issues/33399) - [GitHub代码贡献](https://github.com/magento/magento2/pull/33484) - [GitHub代码贡献](https://github.com/magento/magento2/commit/5cd64dd0)_

#### 管理中的静态网格上未应用悬停颜色

现在，悬停颜色可按预期应用于管理员静态网格的行。[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [GitHub问题](https://github.com/magento/magento2/issues/35358) - [GitHub代码贡献](https://github.com/magento/magento2/pull/35384)_

#### Google reCAPTCHA管理面板的exception.log中的“无法解析reCAPTCHA参数”条目

已解决Google V3 reCAPTCHA管理员登录的`var/log/exception.log`文件中的reCaptcha错误，并且未记录任何错误消息。 以前，当管理员用户配置其&#x200B;**配置** > **安全性** > **Google reCAPTCHA管理员面板**&#x200B;设置时，每隔几秒会引发一次以下错误： `main.ERROR: Can not resolve reCAPTCHA parameter. {"exception":"[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)"} []`。  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [GitHub问题](https://github.com/magento/magento2/issues/34975) - [GitHub代码贡献](https://github.com/magento/magento2/commit/4f7e5983) - [GitHub代码贡献](https://github.com/magento/security-package/commit/804dbc2a)_

#### 条件SKU的购物车价格规则不考虑SKU中的“前导零”（sku：01234与1234相同）

系统现在可以正确处理购物车价格规则，其中条件SKU会考虑SKU中的“前导零”

_AC-9428 - [GitHub问题](https://github.com/magento/magento2/issues/37919) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39525)_

#### 多选的默认属性选项值行为问题

在修复多个选项属性的默认值之前，未正确保存。 现在，修复之后，值将正确地存储在数据库中。

_ACP2E-3523 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9608ca21)_

#### 后端管理菜单字幕未显示

现在将正确显示主菜单组的所有标题。 以前，如果主菜单的第二列或第三列只包含一组链接，则不会显示该组的标题。

_ACP2E-3540_

#### 从管理员将产品数量移回购物车时出现问题

从管理员创建订单时，侧边栏上的客户购物车中的产品在添加到订单时不会消失。

_ACP2E-3563 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### 受限管理员用户无法批量更新产品状态

自定义管理员可以批量更新产品状态，因为它是网站级别的资产。 只有在受限制管理员有权访问的网站上才会更新状态。

_ACP2E-3772_

#### [暂存2]存储卡片在管理面板上不可见

修复了在升级后，“存储卡”支付选项不再出现在后端订单下单表单中的问题。

_ACP2E-3830 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7accebfa)_

#### 受限管理员用户可以保存/更新默认配置，尽管具有特定于存储区的权限

修复了受限管理员用户能够查看和尝试更新“默认配置”范围（尽管仅分配给特定网站范围）的问题，这可能会导致混淆。

_ACP2E-4011 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 针对任何商店视图范围，将可配置产品价格保存在DB下，这会导致“类别中的产品”排序功能出现问题，即保存的价格与前端无关

当按网站配置了价格并在管理员UI可配置产品编辑页面上选择了商店视图时，删除了可配置产品的“使用默认值”复选框。

_ACP2E-4036 - [GitHub代码贡献](https://github.com/magento/magento2/commit/fab20b00)_

#### [QUANS]管理员密码策略不符合PCI DSS 4.0规范（至少12个字符）

管理员现在可以通过存储>配置>高级>管理员>安全来配置管理员用户的最低密码长度要求。 此增强功能提供了更大的安全灵活性，同时还能维护现有的密码策略。 验证在管理员用户创建/修改和配置保存期间强制执行，并实时前端验证以改善用户体验。

_ACP2E-4044 - [GitHub代码贡献](https://github.com/magento/magento2/commit/47721be6)_

#### 当管理员界面语言为日语时，出现日期过滤器问题

生日过滤器和列将使用统一格式M/d/y，与“客户开始时间”过滤器/列相同

_ACP2E-4052 - [GitHub代码贡献](https://github.com/magento/magento2/commit/52f46328)_

#### Admin Grid标题两侧出现白色块

修复了管理网格中的视觉对齐问题。 以前，在管理面板中的产品网格中水平滚动时，网格标题的左右两侧会显示未对齐的白色块。 现在，网格标题元素在滚动时可保持正确的垂直对齐方式，从而为管理大型产品目录的管理员提供更加简洁的视觉体验。

_ACP2E-4104_

#### Ui组件文件2.4.8-p1/ 2.4-develop上的Uploader无法正常工作

改进了自定义ui组件的文件上传功能，通过选择此选项，可在上传区域点击时上传。

_ACP2E-4162 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ee918f0d)_

#### [在本地]新创建的订单/公司/客户在选择流程期间自动包含在“全选”范围中

修复了在执行成批操作时，在过时的管理网格页面上手动选择所有记录会无意中删除所有记录的问题。 以前，当选定项目数量与总计数匹配时，网格会在内部自动切换到“全选”模式，从而导致批量操作影响所有记录，而不仅仅是明确选定的记录。

_ACP2E-4202 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6e134409)_

#### ACP2E-3362中的解决方案在MariaDB 10.6上运行缓慢

在出现大量历史搜索请求时，提高了前端搜索页面的性能。

_ACP2E-4225 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ab891304)_

#### 日期筛选器无法根据贷项通知单网格上的存储时区工作

在按日期属性修复过滤列表之前，由于选定日期与存储日期之间的时区差异，导致缺少项目现在，在正确应用修复日期过滤器之后。

_ACP2E-4239 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### 安装pagebuilder后，文件上传程序对话框打开两次

在修复自定义组件上传按钮触发两次之前。 修复后，上传按钮可按预期工作。

_ACP2E-4241 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/5c4ae802)_

#### 更改客户数据时已删除的客户属性发生验证错误。

在修复之前，如果客户和客户地址包含多个已删除的属性选项，则保存它们会失败。 修复后，即使仍然存在多个属性选项，也可以成功保存这两个字段。

_ACP2E-4281 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### 产品映像更改未记录到操作日志中

修复了管理操作日志中未跟踪产品图像上传和删除的问题。 以前，当管理员将新图像添加到产品或从产品的媒体库中删除现有图像时，这些更改不会记录在记录系统中。 仅记录对图像角色的更改（例如，将图像指定为主产品图像、缩略图或小图像）。 现在，所有媒体集更改（包括图像添加和删除）都正确地记录在“管理操作日志”中，从而为产品图像管理活动提供完整的审核跟踪可见性。

_ACP2E-4302_

#### 管理员仪表板中的JS警告：“应启动加载程序，但在dom中未找到加载程序”

修复了为管理员仪表板启用图表时浏览器控制台中显示的JavaScript警告。 以前，在启用图表的情况下访问管理员仪表板时，过时的调试检查会错误地警告“应该启动加载器，但在dom中找不到加载器”，即使功能运行正常。

_ACP2E-4336 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2687b487)_

#### 使用默认签入存储配置时，具有依赖项配置的[云]配置可编辑

修复了尽管选中了“使用默认值/网站”，系统配置字段在页面加载后仍可以呈现为启用的问题。

_ACP2E-4337 - [GitHub代码贡献](https://github.com/magento/magento2/commit/31258bf6)_

#### 管理员功能板订单图表按照最终大小显示动画

现在，管理员仪表板顺序图将立即显示，而无需重新调整动画大小。

_ACP2E-4398 - [GitHub问题](https://github.com/magento/magento2/issues/38860) - [GitHub代码贡献](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### 由于JS错误，页面生成器无法在移动设备视图中保存内容（类型错误：无法读取未定义的属性）

修复了在移动视图中添加横幅时阻止在页面生成器中保存页面的问题。

_ACP2E-4399 - [GitHub问题](https://github.com/magento/magento2/issues/38565) - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/bdac5bca)_

### 管理员UI，B2B

#### 作为客户标题的B2B登录仍具有Magento品牌

早些时候，店面标题显示“您现在作为&lt;store name>上的&lt;customer name>连接”与Magento品牌化。 现已修复，并且标题会显示为ADOBE品牌。

_AC-14361 - [GitHub代码贡献](https://github.com/magento/magento2/commit/fadcfa8b)_

### 管理员UI，目录

#### 当目录规则处于活动状态并启用实时模式时，产品保存失败

修复了在产品保存操作期间，通过分离目录规则索引与产品事务而导致的目录规则索引可能失败并出现DDL事务错误的问题。

_ACP2E-4378 - [GitHub代码贡献](https://github.com/magento/magento2/commit/f7bbcb4e)_

### 管理员UI，内容

#### 插入图像期间出现异常“无法为媒体资源路径创建演绎版”

删除媒体库图像优化配置的“最大宽度”和“最大高度”的值后，在图像优化过程中不再发生错误。

_ACP2E-3781 - [GitHub代码贡献](https://github.com/magento/magento2/commit/520f9e30)_

### 管理员UI，订单

#### 管理员订单创建：添加20多种产品时会话大小溢出（会话大小超过256KB限制）

通过阻止将大量HTML响应存储在JSON请求的会话中，解决了管理订单创建期间的会话大小溢出问题，从而确保批量产品添加工作顺利进行，而无需注销管理员。

_AC-15893_

### 管理员UI、安全性

#### 弱密码管理

使用相同密码时无法保存管理员用户。 以前，在没有进行正确验证的情况下成功保存了它。

_ACP2E-3657 - [GitHub代码贡献](https://github.com/magento/magento2/commit/df92debe)_

### 管理UI、安全性、暂存和预览

#### 内容暂存的操作日志

现在，操作日志将显示暂存更新活动。 以前，暂存更新日志不会记录在管理员操作日志中。

_ACP2E-3679_

### 管理员UI、税务

#### 税率管理员UI错误

该票证修复了以下税率管理员UI问题：切换国家/地区（例如，从美国→英国）仍显示之前选择的美国州，从而误导用户。
在2.4.9-alpha3中，如果所选国家没有国家，则状态字段现在重置为*。

_AC-8440 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a3b1abc2)_

### Analytics/报表

#### [问题]已添加Analytics的scp（如果您只使用Google Analytics）

此PR会将CSP白名单添加到Google Analytics模块，以便该模块可以独立运行，而无需Google Adwords依赖项。 现在，即使Google Adwords模块被禁用，Google Analytics也可以正常工作。

_AC-16311 - [GitHub问题](https://github.com/magento/magento2/issues/40051) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40032)_

#### 管理操作日志用户报告未显示应用过滤器时使用的过滤器的详细信息

在修复之前，管理活动报表中不会记录筛选参数。 现在，修复后，将记录所有请求数据。

_ACP2E-4099_

#### 高级报表CSV文件中重复的文件标头导致报表为空

修复之后，当行数超过批次大小时，为高级报告功能生成的报告不再包含重复的标题行。

_ACP2E-4187 - [GitHub代码贡献](https://github.com/magento/magento2/commit/45cbf9b6)_

#### 放弃的购物车报表包含无效字符

现在，作为CSV文件导出的放弃购物车报告包含在MS Excel中打开时正确呈现的货币符号（例如印度卢比）字符。

_ACP2E-4288 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### 更新了MDVA-19640，以兼容2.4.8

此修复将Analytics cron作业任务从默认组移至Analytics组

_ACP2E-4309 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c135fc3a)_

#### 收入未显示在Admin for Canada网站/货币中的订单/发票报表中

某些与订单相关的报表未应用商店货币汇率。 修复后，报表将正确应用配置的存储速率。

_ACP2E-4361 - [GitHub代码贡献](https://github.com/magento/magento2/commit/31258bf6)_

### B2B

#### 下单不起作用通过PayFlow Pro Credit Card付款方式的Transactional Quote进行结账

现在，在使用Payflow Pro信用卡付款方式从可转让报价结账时，Adobe Commerce可成功下单。 以前，当启用B2B功能并且买方从可转让报价中结账时，选择Payflow Pro并单击“下单”会导致页面无限期地加载且不会出现任何错误消息，并且永远不会创建订单。 AC-11973

_AC-11973_

#### 引用重命名后的成功消息间歇性消失

在店面重命名可转让报价或报价模板后，Adobe Commerce现在会始终显示成功消息。 以前，当购买者重命名可转让报价时，成功消息会间歇性地不出现（通常几乎立即清除），这还会导致等待此消息的自动测试失败，即使重命名操作本身成功也是如此。 AC-13447

_AC-13447_

#### 来宾签出时公司字段验证失败

来宾签出现在可以正确验证公司字段。
以前，当需要company属性时，来宾签出会失败，并出现以下错误：“Company是必需值”，即使填写字段也是如此。
AC-14987

_AC-14987 - [GitHub问题](https://github.com/magento/magento2/issues/40011) - [GitHub代码贡献](https://github.com/magento/magento2/commit/f1adb44e)_

#### 受限管理员无法将公司分配给共享目录

修复了受限管理员用户在将公司分配给共享目录时遇到异常的问题；更新可确保分配正确工作且无错误。

_AC-15662_

#### 启用类别权限时，将分组产品添加到申请列表时出现异常

修复了在将分组产品添加到具有类别权限的申请列表时发生的TypeError，该类别权限可通过确保产品选项作为阵列安全地处理，从而允许无例外添加所有产品类型。

_AC-15862_

#### Rest API products-render-info返回错误的已登录客户的最终价格

该票证已修复Rest API产品 — render-info会返回错误的已登录客户的最终价格

_AC-5979 - [GitHub问题](https://github.com/magento/magento2/issues/35757)_

#### 当我们尝试从目录页添加申请列表时，“添加到申请列表”按钮将消失

当我们尝试从类别页（现已修复）添加之前的“添加到申请列表”按钮时，该按钮将消失，我们可以在“类别”页上看到申请按钮

_AC-8575_

#### 总计计算不包括税额

在启用了跨境贸易的情况下，订单包含来自现有采购订单的订单的正确总计。

_ACP2E-3727_

#### 通过REST API取消分配B2B共享目录中的类别的操作缓慢

现在，在B2B中取消分配类别时，性能显着提高。 以前，取消分配B2B共享目录中的类别需要很长时间。

_ACP2E-3796_

### B2B、购物车和结账

#### 通过管理员功能“以客户身份登录”登录B2B公司用户时，Storefront上不会显示此类具有cartId = X错误的实体

现在，使用“以客户身份登录”功能从管理员后端成功登录后，不再显示“具有cartId = X的此类实体”错误。

_ACP2E-3994 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 缺少帐单地址导致无法使用“店内交货”配送方式下订单

解决了在选择“店内取货”作为交货方式时，结账期间未自动填写帐单地址的问题。 如果没有帐单地址，则无法完成签出。

_ACP2E-4030 - [GitHub代码贡献](https://github.com/magento/inventory/commit/42d23211)_

### 购物车和结帐

#### Magento 2.4.7更新（迷你）购物车不允许小数数量

现在，当我们从小型购物车更新具有小数的数量时(区域设置为NL（荷兰语）)，Magento可正确处理

_AC-13238 - [GitHub问题](https://github.com/magento/magento2/issues/39236) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39669)_

#### [问题]将EventPrefix和EventObject添加到签出协议模型

系统现在包含签出协议模型的EventPrefix和EventObject，允许使用事件前缀触发事件。 此增强功能为开发人员处理签出协议事件提供了更大的灵活性。 以前，签出协议模型不支持EventPrefix和EventObject，从而限制了自定义事件处理的能力。

_AC-13252 - [GitHub问题](https://github.com/magento/magento2/issues/32510) - [GitHub代码贡献](https://github.com/magento/magento2/pull/32451)_

#### [问题]开发人员体验：引用AbstractItem代码样式（SwiftOtter的SOP-348）

此拉取请求修复了Abstract Item方法的误导性方法声明。

_AC-13334 - [GitHub问题](https://github.com/magento/magento2/issues/39340)_

#### 缺少已分组的产品前端数量验证

尝试添加负数量和最大数量时，系统现在工作正常并显示验证错误

_AC-13524 - [GitHub问题](https://github.com/magento/magento2/issues/39479) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39480)_

#### [问题]更新subtotal.phtml

系统以正确的间距更新subtotal.phtml

_AC-13907 - [GitHub问题](https://github.com/magento/magento2/issues/39619) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39612)_

#### 无法向客人下订单

现在，当在管理员中根据需要配置了中间名字段时，Adobe Commerce允许访客购物者成功下订单。 以前，在Adobe Commerce 2.4.8-beta1 (PHP 8.3/8.4)中，根据需要配置中间名并作为访客签出，这会阻止下单，即使提供了中间名也会阻止签出的完成。 AC-14241

_AC-14241 - [GitHub代码贡献](https://github.com/magento/magento2/commit/27217d0e)_

#### [Graphql]无法为不可为空的字段“SelectedCustomizableOption.label”返回null

现在，当所选的选项不再存在时，系统不会引发包含消息的内部服务器错误

_AC-14256 - [GitHub问题](https://github.com/magento/magento2/issues/39729) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39888)_

#### 当一个愿望清单项目无效时，GraphQL addWishlistItemsToCart无法更新现有购物车项目的数量(Magento 2.4.7-p3)

修复了在遇到无效的可配置产品时GraphQL addWishlistItemsToCart突变停止处理的问题。 修复后，有效的愿望清单项目将添加到购物车并更新数量，而无效项目将被跳过，并返回适当的错误。

_AC-14464 - [GitHub问题](https://github.com/magento/magento2/issues/39820) - [GitHub代码贡献](https://github.com/magento/magento2/commit/3cf1a106)_

#### [2.4.8]无法在城市名称中包含数字0-9、与号、句号或圆括号的城市下订单

修复了包含特殊字符（如。 、 &amp;或圆括号）的城市名称签出失败的问题。
现在，成功下达了具有此类城市名称的订单，且没有出现验证错误。

_AC-14495 - [GitHub问题](https://github.com/magento/magento2/issues/39854) - [GitHub代码贡献](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### 来宾前缀未保存到报价地址2.4.8

访客客户前缀（先生/女士）现在会在结账期间保存。
以前，来宾客户选择的称呼在到达最终订单之前丢失，而所有其他地址字段均正确传输。
AC-14705

_AC-14705 - [GitHub问题](https://github.com/magento/magento2/issues/39915) - [GitHub代码贡献](https://github.com/magento/magento2/commit/f1adb44e)_

#### Salesrule Subselect with Quantity条件无法应用

修复了包含产品子选择条件的购物车价格规则在结账时未应用的问题。
现在，根据配置的规则成功应用折扣。

_AC-14884 - [GitHub问题](https://github.com/magento/magento2/issues/39965) - [GitHub代码贡献](https://github.com/magento/magento2/commit/fe72c407)_

#### [问题]删除类属性中的空间

现在，系统会删除class属性中的额外空间

_AC-14939 - [GitHub问题](https://github.com/magento/magento2/issues/39977) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39970)_

#### Graphql — 启用延交时，合并购物车无法正常工作

修复了在通过GraphQL合并购物车时访客购物车项目未与客户购物车合并的问题。
现在，客户购物车可正确反映访客和客户购物车的合并数量。

_AC-15148 - [GitHub问题](https://github.com/magento/magento2/issues/40064) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [集成] [签出] Depend指令已在失败的付款电子邮件模板中更新

更新了失败的付款电子邮件模板以正确处理depend指令。
修复程序可确保在适用的情况下正确显示送货地址和送货方式。
以前，失败的付款电子邮件中缺少这些字段。

_AC-15363 - [GitHub代码贡献](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 登录后，继续到“签出重定向我的帐户”页面

修复了在会话过期后，用户被重定向到“我的帐户”登录页面而不是签出登录页面的问题，确保用户正确带入并使用登录表单签出。

_AC-15962_

#### 启用固定产品税时，[购物车]购物车页面未加载

修复了在启用固定产品税(FPT)时购物车页面输入无限加载的问题。 问题是由小计计算错误导致的，因为税务与项目价格包含在相同的HTML元素中，从而导致中心小计和汇总小计不匹配。 修复后，购物车可正确加载并显示准确的总数。

_AC-16096 - [GitHub代码贡献](https://github.com/magento/magento2/commit/01cee3c3)_

#### 购物车价格规则操作“购物车中的价格”条件，在不应应用时应用

修复了将“购物车价格小于”条件的购物车价格规则错误地应用于不合格产品的问题。
现在，当购物车项目价格不符合配置的规则条件时，可以正确验证并拒绝优惠券。

_AC-6997 - [GitHub问题](https://github.com/magento/magento2/issues/36433) - [GitHub代码贡献](https://github.com/magento/magento2/commit/01cee3c3)_

#### [问题]设置报价单项目的价格，而不是base_price

如果前端的一个网站中有多种货币，则系统将正确处理报价项目的价格设置为base_price，而不是价格

_AC-9985 - [GitHub问题](https://github.com/magento/magento2/issues/38094) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36878)_

#### cron作业sales_clean_quotes不会清理过期的持久性报价

现在，当“persistent_clear_expired”cron作业运行时，将清除过期的持久引号。 以前，过期的持久引号不会被任何其他cron作业清除。

_ACP2E-3493 - [GitHub代码贡献](https://github.com/magento/magento2/commit/11be3dff)_

#### 签出非活动公司时出现“出现错误”错误

在修复之前，如果登录的用户公司不再启用，则无法在购物车页面上正确完成注销操作。 现在，如果公司不再可用，则正确执行注销。

_ACP2E-3541 - [GitHub代码贡献](https://github.com/magento/magento2/commit/df92debe)_

#### “使用多个地址签出”时未保存地址选择

在取消多送选项时进行修复之前，在恢复为多送时不会预先选择地址。 现在，默认地址将替换为多送货屏幕中所做的选择之一。

_ACP2E-3646 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6ea61121)_

#### 如果订单是在一个商店视图中创建的，则[云]最近订单未出现在其他商店视图中

解决了“我的帐户”页面未显示同一商店中其他商店视图的最近订单的问题。 已更新订单检索逻辑，以确保所有商店视图中的订单可见性一致，与“我的订单”页面的行为一致。

_ACP2E-3807 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a20a6ff2)_

#### 数量显示为  添加捆绑包产品时管理员客户购物车部分中的0  

现在，客户活动中的购物车部分可显示正确的数量。 以前，数量显示为0。

_ACP2E-3872 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3ad96f6a)_

#### 当购物车不再符合要求时，[云]免运费折扣未正确移除

小计(不包括 Tax)将合并以前规则中的折扣。

_ACP2E-3973 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 在多次配送中发现同一客户的重复订单

使用多个发运地址下达订单的并发请求不会再导致同一客户的订单重复

_ACP2E-4117 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 当达到缺货阈值时，[云]库存限制超出通知消息显示两次

修复了购物车更新可能显示重复错误横幅的问题。 以前，在AJAX验证错误后，后端在表单提交期间再次添加相同的消息，因此购物者会看到两个相同的警报。 现在，我们跳过添加额外的后端消息，将购物车页面保留在单个清除错误横幅中。

_ACP2E-4192 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e885088b)_

#### 帐单信息服务器端验证无法使用装运信息REST API工作

客户地址数据验证已得到改进，以便在REST和GraphQl之间更加一致地执行结账。

_ACP2E-4223 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### 购物车页面上的[Cloud]捆绑包产品价格问题

修复了多货币商店的购物车页面上的捆绑产品价格问题

_ACP2E-4245 - [GitHub代码贡献](https://github.com/magento/magento2/commit/cbca0396)_

#### 管理购物车存储范围问题

现在，在管理分配给非默认网站的客户的购物车时，将向管理员用户显示购物车错误。 以前，不会显示错误。

_ACP2E-4348 - [GitHub代码贡献](https://github.com/magento/magento2/commit/31258bf6)_

#### 取消部分发票后重置优惠券times_used

现在，当订单部分取消时，可正确更新优惠券times_used计数。

_ACP2E-4365 - [GitHub代码贡献](https://github.com/magento/magento2/commit/61c96348)_

### GraphQL购物车和结账

#### 通过GraphQL下订单时将消息映射到错误代码时出错

GraphQL调用对不存在或不活动的购物车下订单时，现在会在所有商店视图中正确返回CART_NOT_ACTIVE或CART_NOT_FOUND错误代码，从而修复了已翻译错误消息以前导致未定义代码的问题。

_ACP2E-3942 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7accebfa)_

#### [GraphQl]购物车查询购物车商品折扣问题在虚拟报价上

解决了GraphQL购物车查询为虚拟报价返回错误折扣金额的问题。 以前，折扣错误地应用于某些不符合条件的虚拟产品。

_ACP2E-4248 - [GitHub代码贡献](https://github.com/magento/magento2/commit/cbca0396)_

#### [Cloud] ACSD-68499_2.4.8-p2创建另一个问题

当对数量不足的项目发出graphQL请求时，返回了包含错误代码的正确错误消息，如果请求的数量可用，则购物车更新成功。

_ACP2E-4404 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1c547060)_

### 购物车和结账、GraphQL、库存/MSI

#### 即使可销售库存很高，CartItemInterface中的is_available属性也会返回false

当可销售库存较高时，is_available属性返回true。 以前，它始终返回false。

_ACP2E-3885 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3ad96f6a)_

### 购物车和结账、库存/MSI

#### 414具有大购物车大小的“搜索取车位置”端点错误

当购物车中有许多产品时，由于存在较长URL，在结账期间使用“Pick in Store”选择商店不再失败。
以前，这触发了414错误，导致在商店选择期间生成的URL过长，阻止客户完成结账。

_ACP2E-4266 - [GitHub代码贡献](https://github.com/magento/inventory/commit/ae1f272f)_

### 购物车和结帐、订购、产品

#### 即使订单发票失败，也会发送礼品卡电子邮件

在实施此修复之前，在创建发票后会发送礼品卡电子邮件。 但是，应用此修复后，现在会在成功保存和提交发票后发送礼品卡电子邮件。

_ACP2E-3905_

### 购物车和结账、促销活动

#### 礼品卡显示余额不受网站范围限制

已根据分配的网站范围限制礼品卡余额检查。

_ACP2E-4379_

### 购物车和结帐、SEO

#### 从辅助网站购买时，电子邮件中的礼品卡代码URL不正确

以前，非默认商店的多商店设置和礼品卡始终将礼品卡报销申请重定向到默认网站。 应用此修复后，电子邮件会将礼品卡报销申请链接重定向到正确的范围或网站。

_ACP2E-3699_

### 购物车和结帐、安全性

#### 实施sri修补程序后首次尝试时，在签出页面上获取[CLOUD]的JS文件404

在启用了精简和捆绑时，修复mixin之前的版本将不会加载到购物车和结账中。 修复后，所有mixin都应按预期加载。

_ACP2E-4128 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e457c5e2)_

### 购物车和结帐、送货

#### [Mainline]购物车价格规则未遵守多送货规则

在实施此更正之前，当应用子选择条件并启用免费配送时，多配送产品的购物车价格规则无法正确应用。 但是，由于应用了校正，因此多件运输购物车的购物车价格规则现在按预期运行。

_ACP2E-3666 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b12ffe36)_

### 目录

#### 具有相同查询的同一页面出现重复的缓存fpc

现在，系统可正确识别并使用相同的全页缓存(FPC)来查找查询参数相同的页面，而不管其顺序或尾随字符如何。 这可以防止页面缓存文件夹大小不必要的增加。 以前，如果查询参数的顺序不同或存在尾随字符，系统会为同一页面创建不同的FPC标识符，从而导致页面缓存文件夹大小增加。

_AC-10722 - [GitHub问题](https://github.com/magento/magento2/issues/38269) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38270)_

#### catalog_product_entity_int表中缺少所需列的索引

在catalog_product_entity_int表中添加了缺少的所需列的索引

_AC-10844 - [GitHub问题](https://github.com/magento/magento2/issues/38315) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38316)_

#### 目录URL资源(_getCategories)中的作用域错误

如果在类别URL资源的存储作用域中未定义任何值，此PR会将回退添加到默认作用域。

_AC-11011 - [GitHub问题](https://github.com/magento/magento2/issues/38393) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38394)_

#### [问题]检查OpenGraph是否可以显示价格

当我们使用隐藏价格的插件时，系统工作正常，并且此更改价格不会显示在OG标签中。

_AC-11635 - [GitHub问题](https://github.com/magento/magento2/issues/38512) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38510)_

#### 将税添加到显示价格时价格的舍入问题

目前，系统在向显示价格添加税时，修复了价格的舍入问题

_AC-11725 - [GitHub问题](https://github.com/magento/magento2/issues/18025) - [GitHub代码贡献](https://github.com/magento/magento2/pull/35730)_

#### [问题]允许自定义目录规则条件

解决了由于严格的类型检查而阻止使用自定义目录规则条件的问题。 此修复将类等式检查替换为实例，使自定义条件类能够正常工作，并启用成功的规则验证和索引。

_AC-13338 - [GitHub问题](https://github.com/magento/magento2/issues/39339) - [GitHub代码贡献](https://github.com/magento/magento2/commit/913bf1a6)_

#### 可配置产品在添加到愿望清单时丢失选项

修复了将产品添加到愿望清单后可配置产品选项丢失的问题。 现在，所选的选项会被保留，从而允许产品顺利地添加到购物车中，而不会提示用户重新选择选项。

_AC-13373 - [GitHub问题](https://github.com/magento/magento2/issues/39363) - [GitHub代码贡献](https://github.com/magento/magento2/commit/cc0ec250)_

#### 可配置产品的子产品（简单产品）的特殊价格显示不正确

修复了当“用于产品列表”设置为“否”时，可配置产品的子（简单）产品的特殊价格在产品列表页面上无法正确显示的问题。 现在，特殊价格与常规价格一起正确显示，从而确保跨产品类型显示一致的定价。

_AC-13594 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3cf1a106)_

#### [错误] REST API：更新特殊价格未为所有商店视图设置值

REST API现在可更新网站中所有商店视图的特殊价格。
以前，通过REST API更新特殊价格只会影响指定的商店视图，而不会影响网站中的所有商店视图。
AC-13671

_AC-13671 - [GitHub问题](https://github.com/magento/magento2/issues/39521) - [GitHub代码贡献](https://github.com/magento/magento2/commit/7bdafaa2)_

#### 价格范围和config.php的问题

在Magento 2.4.2中，通过config.php更改价格范围时，无法正确更新catalog_eav_attribute中price属性的is_global值。
因此，产品价格仍是全球性的，无法按网站进行保存，即使将价格范围设置为网站也是如此。
要解决此问题，需要手动更新数据库中的is_global列，这对于生产环境并不理想。
此行为与Magento的默认设计一致，即价格范围为全局或网站，但不是按商店视图定价。

_AC-13857 - [GitHub问题](https://github.com/magento/magento2/issues/33559)_

#### 未注意到[\Magento\ConfigurableProduct\Model\Product\Type\Configurable] PHP错误

更改了循环变量名称，以便正确添加要用于后续调用的给定产品上的“_cache_instance_product_ids”数据。

_AC-14159 - [GitHub问题](https://github.com/magento/magento2/issues/39641) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39642)_

#### 弹性搜索会干扰产品的默认排序顺序（将最新先更改为最旧先更改）

系统现在对数据库中的最新产品进行排序（entity_id最高的产品）最先显示

_AC-14411 - [GitHub问题](https://github.com/magento/magento2/issues/31043) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36900)_

#### After store切换页面来自2.4.8中的缓存(Store switcher not working)

修复了在手动清除缓存之前，从店面标题切换商店视图无法正常工作的问题。
现在，存储视图切换可以正常工作，而无需缓存清理。

_AC-14426 - [GitHub问题](https://github.com/magento/magento2/issues/39806)_

#### 已忽略最小宽度的.less样式： (@screen__l)

修复了在类别页面上每行仅显示三个产品的问题。
现在，每行按预期显示四个产品。

_AC-14463 - [GitHub问题](https://github.com/magento/magento2/issues/39817) - [GitHub代码贡献](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### 除客户菜单中的愿望清单页面外，愿望清单计数不显示在主页/其他页面上

修复了愿望清单计数在非愿望清单页面上显示为空括号的问题。
现在，所有页面的“我的愿望清单”旁边都会显示正确的愿望清单项目计数。

_AC-14607 - [GitHub问题](https://github.com/magento/magento2/issues/39892) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a3b1abc2) - [GitHub代码贡献](https://github.com/magento/magento2/commit/b3774fbe)_

#### 在没有存储级别值(getFinalPrice()问题)的情况下使用REST API时，catalog_product_save_before observer会引发与日期相关的错误

当日期作为DateTimeInterface实例提供时，此PR会调整SpecialFromDate的处理，以确保格式正确。 这样可以防止在某些情况下执行getFinalPrice()时出现错误。

_AC-14847 - [GitHub问题](https://github.com/magento/magento2/issues/39959) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40003)_

#### 紧急 — 当要添加的产品具有可自定义选项时，无法将产品添加到捆绑包

修复了具有可自定义选项的产品无法添加到捆绑产品的问题。
以前，在创建捆绑包时，此类产品会从“将产品添加到选项”列表中排除。
现在，带有可自定义选项的产品可以添加到捆绑包中，而无需包含其自定义选项，从而允许进行正确的库存管理。
这可以在不复制产品或影响库存水平的情况下创建捆绑包。

_AC-14958 - [GitHub问题](https://github.com/magento/magento2/issues/39993)_

#### 负`?p=`查询字符串导致Elasticsearch异常

现在，系统可处理类别分页中的负？p=值，该值当前会导致异常并被视为有效请求

_AC-15191 - [GitHub问题](https://github.com/magento/magento2/issues/40079) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40080)_

#### 对于具有单个选项的可配置产品，将显示“最低”价格标签

修复了可配置产品在PDP/PLP上显示具有不正确“As low as”标签的价格的问题。
现在，该产品显示了正确的价格（500美元），并且没有任何误导性标签。

_AC-15237 - [GitHub问题](https://github.com/magento/magento2/issues/40104) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 为“添加到比较”按钮调用了错误的方法

更正了\Magento\Catalog\Ui\DataProvider\Product\Listing\Collector\Url：：collect()中使用的方法。
以前，错误地调用getAddToCartButton()而不是getAddToCompareButton()。
此更改确保了在产品列表中显示“添加到比较”按钮的正确行为。
未引入任何功能行为更改；更新改进了开发人员体验和代码正确性。

_AC-15323 - [GitHub问题](https://github.com/magento/magento2/issues/39754) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 在不同的商店查看中，使用不同的货币在购物车上显示错误的产品价格

修复了在商店视图中使用不同货币时，购物车中显示错误的产品定价的问题。 修复后，购物车现在会根据配置的货币显示正确的折换价格，从而确保产品页面与购物车之间的一致性。

_AC-15385 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a8cf637b)_

#### 启用FPT时可配置产品的“最低”价格显示错误

已确认启用FPT时可配置产品的“最低”价格不正确是由两次计税引起的；此修复程序可确保最终价格计算尊重税务配置并且现在显示正确的价格。

_AC-15718 - [GitHub问题](https://github.com/magento/magento2/issues/40171) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a06a4a57)_

#### Eav\Model\Entity\Collection\AbstractCollection中_loadAttributes的时间复杂度会随着购物车和属性中的产品数量而增加

此PR通过用数组并集(+)替换嵌套循环并减少_setItemAttributeValue的调用，优化了Eav\Model\Entity\Collection\AbstractCollection中的_loadAttributes，从而提高了大型产品购物车的性能。

_AC-15833 - [GitHub问题](https://github.com/magento/magento2/issues/40216) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40217)_

#### 收藏集缓存与可配置产品库之间的交互存在错误

通过添加防御性类型检查来确保media_gallery_images始终被视为集合，从而解决了可配置产品库的缓存问题，并防止了由损坏的缓存数据导致的严重错误。

_AC-16066 - [GitHub问题](https://github.com/magento/magento2/issues/33965) - [GitHub代码贡献](https://github.com/magento/magento2/commit/3b5ac075)_

#### 在产品页面上创建属性时，删除下拉列表选项不起作用

无可用描述。

_AC-16437_

#### 产品页面因URL重写产生错误

现在，当我们重写URL时，产品页面加载成功

_AC-2950 - [GitHub问题](https://github.com/magento/magento2/issues/35371) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39670)_

#### 将产品添加到类别时出现[云]错误

现在，通过弹出网格将产品添加到类别时，分页和记录计数标签可正常工作。 以前，如果仅加载一个页面的项目等于页面大小，则会导致项目选择下拉列表出现问题。

_ACP2E-3526_

#### indexer_update_all_views cron错误(MAGE_INDEXER_THREADS_COUNT)

修复了MAGE_INDEXER_THREADS_COUNT > 2和客户区段索引器的问题

_ACP2E-3538 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9608ca21)_

#### 在页面生成器产品小组件条件中添加“条件组合”时出现异常

通过添加检查以跳过缺失或不完整的条件，此问题已得到修复。 以前，由于处理系统中不完整的条件，这会导致生成错误日志。

_ACP2E-3545 - [GitHub代码贡献](https://github.com/magento/magento2/commit/11be3dff)_

#### 加载属性集时浏览器崩溃

如果产品属性超过4千个，则浏览器不会再在属性集编辑页面上崩溃

_ACP2E-3633 - [GitHub问题](https://github.com/magento/magento2/issues/38810) - [GitHub代码贡献](https://github.com/magento/magento2/commit/b12ffe36)_

#### 未为新存储创建[CLOUD]产品URL重写：上线阻止程序

已成功创建新商店的产品URL重写。
之前操作因内存泄漏或超时而结束。

_ACP2E-3669 - [GitHub代码贡献](https://github.com/magento/magento2/commit/df92debe)_

#### 选项无效的属性默认值

以前，当我们更改product select属性的默认值时，它会显示为具有先前值的数组元素。 应用此修复后，当我们更新产品属性值时，它将在eav_attribute表中保存为单个元素。

_ACP2E-3688 - [GitHub代码贡献](https://github.com/magento/magento2/commit/520f9e30)_

#### 编辑时礼品卡验证因千位分隔符而失败

修复了在礼品卡金额为1000及更高时礼品卡产品类型保存的问题。

_ACP2E-3704_

#### [Mainline] [CLOUD]映像大小调整占用的磁盘空间超过400GB

修复后，与`catalog:images:resize`标志一起使用的`--skip_hidden_images`命令将不会为没有图像的网站生成图像缓存。

_ACP2E-3869 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9ad7d277)_

#### 动态图像生成生成大量图像

修复后，将仅为分配了产品的网站生成图像。

_ACP2E-3927 - [GitHub代码贡献](https://github.com/magento/magento2/commit/fab20b00)_

#### 提供的CountryID不存在 — 爱尔兰(IE)

修复后，爱尔兰邮政编码可用于搜索取车地点。

_ACP2E-3932 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4ca73607) - [GitHub代码贡献](https://github.com/magento/inventory/commit/d2f1d6c6)_

#### 由于布局中缓存的布局结构不正确，前端出现500错误

修复了由于布局中缓存的布局结构不正确而导致页面返回500错误代码的问题

_ACP2E-4040 - [GitHub代码贡献](https://github.com/magento/magento2/commit/47721be6)_

#### 产品查看报告不正确 — 计数比正式发布时低

修复了report_viewed_product_index表未显示正确产品页面查看次数的错误。

_ACP2E-4045 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6e134409)_

#### 计划更新中的目录价格规则折扣金额字段的验证错误

以前，在解决此问题之前，对于目录价格规则的计划更新，如果折扣金额为by_fixed ，则由于validation-number-range规则的原因，无法正确验证该金额。 应用此修复后，验证可对固定价格目录价格规则正常工作。

_ACP2E-4054 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 增值税验证因VAT API费率限制器而失败 — 触发误报客户组更改

优化了对Europa Vat验证工具的请求，这将减少“比率限制器”错误

_ACP2E-4072 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ee918f0d)_

#### 核心索引器中的批量删除触发生产上的最大写集大小错误

通过实施两种基于数据量的删除策略，优化目录规则产品索引清理。

_ACP2E-4085 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0a3b7032)_

#### 禁用后，产品显示为缺货

修复后，产品小部件中不存在禁用的产品。

_ACP2E-4136 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [云]重复条目错误(temp_category_descendants_%)

修复了在为具有高嵌套类别数的环境创建计划更新期间重复条目的问题

_ACP2E-4159 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD]比较不同商店的产品计数不匹配问题

现在，在切换到其他商店后，比较产品列表可正常工作

_ACP2E-4249 - [GitHub代码贡献](https://github.com/magento/magento2/commit/98f028ab)_

#### 在可配置产品创建期间，对受限管理员用户可见的“添加新属性”按钮

“添加新属性”按钮现在仅在创建可配置产品的过程中对常规管理员用户可见。
之前显示的“添加新属性”按钮适用于受限制的管理员用户

_ACP2E-4279_

#### 在“图像和视频”中没有用于“使用默认值”进行图像角色分配的选项

“使用默认值”选项已添加到产品图像和视频部分，允许从默认范围继承设置。

_ACP2E-4280 - [GitHub代码贡献](https://github.com/magento/magento2/commit/61c96348)_

#### 客户组更新后，受限制类别产品仍会计入愿望清单

在修复之前，类别权限未正确应用于客户愿望清单项目。 现在，修复之后，在Web和GraphQL中均可正确显示愿望清单项目并进行分页。

_ACP2E-4294 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c135fc3a)_

#### PDP和PLP上的[云]捆绑产品价格问题

对于非默认货币，使用固定价格的捆绑产品价格可在PDP/PLP上正确显示

_ACP2E-4298 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0a3b7032)_

#### 客户组更改后，客户可以订购无法访问的产品

以前，当从管理员更改客户组时，前端目录和购物车不反映目录权限中的更改。 但是，在应用此修复后，当客户组从管理员更改为其他成员时，前端报价现在会根据更新的目录权限进行更改。

_ACP2E-4300 - [GitHub代码贡献](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### 由于内存使用率较高，重新索引卡住

修复了目录规则索引器占用过多内存且无法完成，从而导致不稳定和内存不足错误的问题。

_ACP2E-4303 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c135fc3a)_

#### [CMS]计划更新预览链接重定向到维护页面

带有可配置产品的主页链接的计划更新预览可正确显示产品列表。 以前，它将用户重定向到维护页面

_ACP2E-4401 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1c547060)_

#### 相关产品将被自动删除

现在，在整个重新索引过程中，目标规则匹配的相关产品均可正确关联

_ACP2E-4430_

### 目录，GraphQL

#### GraphQl折扣计算无效

现在，当目录价格配置为包含税时，GraphQL可正确显示折扣百分比和基本价格。 以前，出现舍入错误，例如显示19.99%而不是20%。

_ACP2E-3993 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e457c5e2)_

#### GetCart GraphQL Media Gallery字段在缓存刷新后返回空数据

修复后，产品的media_gallery在购物车请求的GraphQL响应中按预期返回。

_ACP2E-4185 - [GitHub代码贡献](https://github.com/magento/magento2/commit/45cbf9b6)_

### 目录、GraphQL、搜索

#### 产品graphql在类别聚合中返回了禁用的类别

修复后，不会为产品GraphQl请求返回禁用的类别。

_ACP2E-2885 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b12ffe36)_

### 目录、性能

#### 管理员中的类别加载速度非常慢

类别加载性能有显着改进。 以前，加载导致超时问题的类别需要很长时间。

_ACP2E-3891 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4ca73607)_

### 目录，定价

#### 应用于子产品的目录价格规则折扣错误

修复了以下问题：当两个规则具有相同的优先级时，变体的目录价格规则将由父可配置产品覆盖。

_ACP2E-3693 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a20a6ff2)_

#### [Cloud]捆绑包产品价格问题

非默认货币的PDP/PLP上正确显示了具有特殊价格的捆绑产品的价格

_ACP2E-4110 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6e134409)_

### 目录、产品

#### 未加载[随机错误]Fotorama库

现在，系统可确保Fotorama库已正确加载，从而允许所有附加的图像按预期显示在图像库中。 以前，由于Fotorama库未正确加载的问题，因此仅显示第一个图像。

_AC-12124 - [GitHub代码贡献](https://github.com/magento/magento2/commit/45b51c9c) - [GitHub代码贡献](https://github.com/magento/magento2/commit/27217d0e)_

#### “手动添加产品”链接应始终可见

修复了在创建没有现有配置的可配置产品时，“手动添加产品”链接不可见的问题。 该链接现在始终显示，允许管理员轻松关联简单产品而不创建虚拟配置。

_AC-13866 - [GitHub问题](https://github.com/magento/magento2/issues/39595) - [GitHub代码贡献](https://github.com/magento/magento2/commit/ef666cd9)_

#### 在后端编辑产品从产品选项定价中删除额外的小数位

修复了管理员在编辑产品时，将产品选项定价截断为两位小数的问题。 系统现在以更高的小数精度保留定价，确保保存后保留精确值。

_AC-14050 - [GitHub问题](https://github.com/magento/magento2/issues/39655) - [GitHub代码贡献](https://github.com/magento/magento2/commit/3b5ac075)_

#### 通过GraphQL在PDP中未显示通过相关产品规则关联的产品

以前，在应用此修复之前，相对产品规则为与规则匹配的产品返回空/空。 应用此修复后，将针对匹配的产品成功返回产品的相对规则。

_ACP2E-3949_

### 目录，返回

#### 已自动取消选择捆绑产品行的[云]订单退货页面

以前，对于管理面板网格视图中的捆绑产品Ship Together Return，我们有一个选项“选择项目”，该选项会导致捆绑产品Ship Together选项混乱。 应用此修复后，对于捆绑产品发运，不再有“选择项目”选项。

_ACP2E-4180_

### 目录，搜索

#### RestApi请求“/rest/default/V1/categories？searchCriteria%5Bpage_size%5D=1”失败，并出现超时错误

类别REST API请求不再因超时错误而失败。
以前，对/rest/default/V1/categories？searchCriteria[page_size]=1的请求会在某些代码更改后因超时而失败。
AC-13358

_AC-13358 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7bdafaa2)_

### 内容

#### graphql (magento 2.4.6-p4 ) — 尝试获取非活动状态cms页面时出错

修复了针对已禁用的CMS页面的GraphQL查询返回内部服务器错误的问题。
现在，查询会获取正确的响应，并且不会出现错误。

_AC-12302 - [GitHub问题](https://github.com/magento/magento2/issues/38877) - [GitHub代码贡献](https://github.com/magento/magento2/commit/1b1baf1d)_

#### 希望列表共享表单允许名称字段中存在随机代码

修复了愿望清单共享表单中的关键服务器端模板注入(SSTI)漏洞，该漏洞可在消息字段中输入恶意代码并通过电子邮件发送。 更新将输入验证添加到块模板指令和不安全模式，现在在检测到无效内容时显示错误消息。

_AC-12730 - [GitHub问题](https://github.com/magento/magento2/issues/39024) - [GitHub代码贡献](https://github.com/magento/magento2/commit/01cee3c3)_

#### 将csp_whitelist.xml置于主题中不起作用，并会产生间歇性问题

按网站区域实施了CSP白名单缓存。

_AC-13069 - [GitHub问题](https://github.com/magento/magento2/issues/38933) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39672)_

#### 升级到magento 2.4.7后，p2无法看到新上传的文件媒体集

升级后，新上传的文件现在会显示在介质集中。
以前，升级到Magento 2.4.7 p2后，新上传的图像在执行手动同步之前不会显示在媒体集中。
AC-13262

_AC-13262 - [GitHub问题](https://github.com/magento/magento2/issues/39275)_

#### 媒体集从名称相同但大小写不同的目录中显示不正确的图像

现在，系统解决了上载到媒体集中特定目录的文件在名称相似但大小写不同的目录中也可见的问题。

_AC-13489 - [GitHub问题](https://github.com/magento/magento2/issues/39382) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39502)_

#### 从图库映像中完全删除将保留设置范围的角色/类型（基本/小型/缩略图），重新添加“旧”角色/类型后会显示

系统在存储范围中按预期工作，映像根据默认范围继承新添加映像的角色/类型

_AC-13556 - [GitHub问题](https://github.com/magento/magento2/issues/39481) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39680)_

#### [小错误]当字段值包含`listing component`时，无法点击管理面板`\`的筛选器

过滤页面标题中存在斜杠时（例如：Magento\Store），系统工作正常

_AC-13661 - [GitHub问题](https://github.com/magento/magento2/issues/39513) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39535)_

#### 错误：加载产品后管理内容pagebuilder的“Magento_Catalog/js/validate-product”出现脚本错误

此PR修复了使用products条件编辑pagebuilder时catalogAddToCart出现脚本错误

_AC-13891 - [GitHub问题](https://github.com/magento/magento2/issues/39604) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39677)_

#### 配置产品小组件时出现catalogAddToCart脚本错误。

修复了在页面生成器中使用“条件组合”配置产品小部件时发生的脚本错误。 该问题是由缺少前端JS文件导致的，从而导致控制台错误。 修复后，构件会正确加载，且不会出现控制台错误。

_AC-13892 - [GitHub代码贡献](https://github.com/magento/magento2/commit/528af81a)_

#### 阻止具有相同标识符的构件中的选择

现在，当我们具有相同的标识符块时，系统可以在创建构件时正确处理选择块

_AC-14132 - [GitHub问题](https://github.com/magento/magento2/issues/39692) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39722)_

#### 包含“0” ID的CMS页面不存在”日志泛滥

创建管理员用户后以及创建新页面system后，系统按预期工作。log没有任何错误消息

_AC-14254 - [GitHub问题](https://github.com/magento/magento2/issues/39743) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39746)_

#### [GraphQl]路由查询无限循环

此工单修复了请求路径和目标路径相同的GraphQL路由查询导致无限循环并最终超时的问题。
在2.4.9-alpha3中，查询现在返回正确的错误响应，而不是循环。

_AC-14269 - [GitHub问题](https://github.com/magento/magento2/issues/39707) - [GitHub代码贡献](https://github.com/magento/magento2/commit/68a45d0a)_

#### 不存在的Sitemap使用产品图像做出响应

系统现在可以修复我们访问具有产品图像的Unexisting Sitemap响应时的问题，响应为： 404 NOT FOUND

_AC-14295 - [GitHub问题](https://github.com/magento/magento2/issues/39756) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40135)_

#### 目录链接构件使用错误的URL

添加目录产品链接和目录类别链接后，系统现在可以正确处理构件，并且还能在html源中显示正确的url

_AC-14437 - [GitHub问题](https://github.com/magento/magento2/issues/39464) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39710)_

#### 未考虑表前缀

现在，在Admin中加载“设计”>“配置”主题网格时，Adobe Commerce会正确遵循数据库表前缀。 以前，在app/etc/env.php中配置了表前缀的Adobe Commerce 2.4.8上，导航到“内容”>“设计”>“配置”会导致错误，因为未考虑表前缀，并且未呈现主题的网格。

_AC-14556 - [GitHub问题](https://github.com/magento/magento2/issues/39847) - [GitHub代码贡献](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### 将常量IMAGE_FILE_NAME_PATTERN更改为公共可见，以获得更大的灵活性

GenerateRenditions.php中的常量IMAGE_FILE_NAME_PATTERN已公开，以便开发人员在处理图像呈现时具有更大的灵活性。 此修补程序包含在Magento 2.4.9-alpha3中，具有完整的单元测试和集成测试范围。

_AC-15338 - [GitHub问题](https://github.com/magento/magento2/issues/39733) - [GitHub代码贡献](https://github.com/magento/magento2/commit/68a45d0a)_

#### 多批发运的审核订单页中显示的发运方法不正确

修复了多配送结账中的问题：审查订单页面显示的配送成本不正确（5 INR而不是10 INR）；更新可确保为每个地址显示正确的配送金额。

_AC-15664 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3cf1a106)_

#### bin/magento配置:show（或set） design/theme/theme_id失败

修复了design/theme/theme_id路径的CLI命令bin/magento config:show和config:set在配置存在的情况下失败的问题。
现在，这些命令已成功执行，允许查看和设置主题ID，并且没有错误。

_AC-5915 - [GitHub问题](https://github.com/magento/magento2/issues/35751) - [GitHub代码贡献](https://github.com/magento/magento2/commit/64823f95)_

#### 无法上传宽度相对较小的图像

系统不再无法以相对于其高度的相对较小的宽度来调整图像大小。

_ACP2E-3558 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9608ca21)_

#### 如果用户没有小组件权限，则页面生成器的产品组件无法正常工作

在修复之前，当访问没有权限的小组件时，页面会引发一般错误并显示“正在加载”GIF。 现在，修复后，将显示一个模式窗口，显示“抱歉，您需要权限才能查看此内容。” 消息。

_ACP2E-3664 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### 远程存储路径样式配置的配置路径不正确

修复后，设置远程存储路径样式配置将影响实际的AWS S3路径样式配置。

_ACP2E-3734 - [GitHub代码贡献](https://github.com/magento/magento2/commit/df92debe)_

#### GraphQL中未应用页面生成器产品小组件排序

修复了GraphQL“路由”查询响应未在Page Builder产品内容类型中按正确排序顺序返回产品的问题。

_ACP2E-3898 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### 由于ICU库版本，非英语店面出现定价显示问题

修复后，产品价格可在希伯来语（以色列）区域设置中正确显示。

_ACP2E-3938 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7accebfa)_

#### 正在更新已清除设计配置的存储区代码

修复了由于配置缓存未正确刷新而更新商店视图代码清除设计配置设置的问题。

_ACP2E-3941 - [GitHub代码贡献](https://github.com/magento/magento2/commit/462ede94)_

#### 内容暂存预览不适用于搜索结果

在暂存预览中搜索现在会根据选定的范围返回产品。 以前，搜索会在默认范围中返回结果，而不考虑所选存储。

_ACP2E-4095_

#### 页面生成器 — 产品条件逻辑问题（OR逻辑行为不正确显示较少产品）

现在，在“匹配任意”条件中使用具有全局范围的属性时，页面生成器产品小组件会返回正确结果

_ACP2E-4096 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e457c5e2)_

#### 产品轮播会将不正确的产品添加到页面生成器

在修复之前，如果某个可配置产品的任何子项已经满足筛选条件，则该产品会自动包含在PageBuilder产品轮播列表中。 现在，修复后，仅当子产品本身不可见时，才会包含父产品。

_ACP2E-4341 - [GitHub代码贡献](https://github.com/magento/magento2/commit/61c96348)_

#### 如果在类别条件中列出了多个类别，则产品列表构件会返回不正确的结果

现在，当在“类别是其中之一”条件中列出了多个类别时，“目录产品列表”构件会显示准确的结果。 以前，仅处理列表中的第一个类别。

_ACP2E-4353 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0a3b7032) - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/1c1b3419)_

#### [云]媒体集文件夹创建需要新媒体集中的delete_folder权限 — 仅具有create_folder的角色无法创建文件夹

以前，在实施此修复之前，仅具有内容创建文件夹权限的管理员用户无法在CMS媒体集中创建文件夹。 但是，修复后，媒体集中的内容创建者现在可以创建仅具有创建文件夹权限的文件夹。

_ACP2E-4376 - [GitHub代码贡献](https://github.com/magento/magento2/commit/61c96348)_

#### [QUANS]复制CMS页面

在此修复之前，复制具有自定义布局更新的cms页面会失败。 现在，可以复制包含自定义布局更新的CMS页面而不会出现错误。

_ACP2E-4449 - [GitHub代码贡献](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### 具有网站级别权限的管理员无法编辑动态块

现在，具有网站范围权限的管理员用户可以在可访问的存储视图中编辑横幅的内容。

_ACP2E-4468_

### 客户/客户

#### 当管理员通过CMS页面内容添加CustomerCustomAttribute块时，Storefront出现异常

修复了通过CMS页面内容添加CustomerCustomAttribute块时导致店面异常并阻止页面加载的问题。
现在，Storefront可正常显示，并在无法呈现内容时显示一条有意义的消息，从而避免出现严重错误。

_AC-11004_

#### 客户现在在线管理网格会在每次用户登录、注销、然后登录时显示重复行

修复了客户现在在线管理网格在注销并重新登录时显示重复行的问题。
该网格现在使用最新活动更新现有记录，而不是创建重复条目，从而确保准确的客户会话跟踪。

_AC-11511 - [GitHub代码贡献](https://github.com/magento/magento2/commit/528af81a)_

#### 最小值和最大值验证不适用于店面上的DOB属性

此错误修复了出生日期(DOB)属性的最小和最大日期验证在店面中不起作用的问题（尽管在管理员中起作用）。
在2.4.9-alpha3中，验证现在会正确阻止使用DOB超出允许范围的客户进行保存，并显示错误消息。

_AC-13535 - [GitHub代码贡献](https://github.com/magento/magento2/commit/68a45d0a)_

#### 以客户身份登录权限被撤销时，在管理员面板的警告屏幕上加载Ajax 401错误

此错误修复了以客户权限撤销的登录导致警告弹出窗口中显示原始HTML的Ajax 401错误的问题。
修复后，系统现在可正确显示普通警告消息，而不是原始HTML。
解决方案是在Magento 2.4.9-alpha3中提供的

_AC-15336 - [GitHub代码贡献](https://github.com/magento/magento2/commit/68a45d0a)_

### 框架

#### 编译已禁用模块的代码

此拉取请求转义在代码编译之前禁用了模块。

_AC-10933 - [GitHub问题](https://github.com/magento/magento2/issues/38241) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39723)_

#### 使用自定义数据库触发器运行命令安装程序:upgrade时出错

自定义数据库触发器在安装过程中不再导致错误:upgrade。
以前，使用自定义数据库触发器运行bin/magento设置:upgrade（例如，在存储表上执行AFTER INSERT）可能会导致以下错误：
“警告：正在尝试访问vendor/magento/framework/Mview/View/Subscription.php第357行中类型为null的值上的数组偏移”
AC-11487

_AC-11487 - [GitHub问题](https://github.com/magento/magento2/issues/38481)_

#### [问题]使方法签名与接口一致

getAttributes的方法签名现在与其接口一致，从而防止在覆盖方法时发生任何错误。 以前，在尝试覆盖getAttributes方法时，方法签名不一致会导致错误。

_AC-11578 - [GitHub问题](https://github.com/magento/magento2/issues/38501) - [GitHub代码贡献](https://github.com/magento/magento2/pull/31955)_

#### 无法使用扩展属性的多值表单元素扩展网站/组/商店实体表单

此PR允许多值表单元素将数据提交到网站/组/商店表单。

_AC-11657 - [GitHub问题](https://github.com/magento/magento2/issues/24070) - [GitHub代码贡献](https://github.com/magento/magento2/pull/24094)_

#### [问题]修复用户界面组件的验证电子邮件规则

系统现在可以正确验证在UI组件中输入的多个电子邮件地址，确保正确裁剪和验证每个电子邮件。 以前，系统使用不正确的方法修剪电子邮件地址，这可能导致验证错误。

_AC-11719 - [GitHub问题](https://github.com/magento/magento2/issues/38528) - [GitHub代码贡献](https://github.com/magento/magento2/pull/33470)_

#### [问题]删除作用域解析程序用法

此PR会全局解析管理员URL设置，而不是解析当前存储

_AC-11736 - [GitHub问题](https://github.com/magento/magento2/issues/38566) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38554)_

#### [问题]删除冗余方法

代码质量：删除了AsynchronousOperations和Sales组件中仅调用父方法而没有添加功能的冗余方法，从而提高了代码可维护性。

_AC-11915 - [GitHub问题](https://github.com/magento/magento2/issues/29748) - [GitHub代码贡献](https://github.com/magento/magento2/pull/29147)_

#### Magento_Theme title.phtml模板对于PHP 8.2无效

此拉取请求修复了使用null标题创建的CMS页的问题，如Php 8.x中的，将null传递给trim()会引发异常：已弃用的功能： trim()：将null传递给string类型的参数#1($string)

_AC-12856 - [GitHub问题](https://github.com/magento/magento2/issues/39092) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39398)_

#### 对于在字段项下包含注释的etc/adminhtml/system.xml文件，xsd验证失败。

此PR修复了phpstorm中注释节点的XML架构定义

_AC-12945 - [GitHub问题](https://github.com/magento/magento2/issues/39148) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39867)_

#### 通过设置路线使用默认Nginx配置公开的Magento版本

系统现在正按预期运行，不会公开站点正在运行的确切Magento版本

_AC-13205 - [GitHub问题](https://github.com/magento/magento2/issues/39227) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39228)_

#### [问题]将对象参数解包为命名参数

系统现在利用PHP 8.1的功能来解压缩具有命名参数的数组，从而消除对array_values调用的需要，并潜在地提高整体性能。 以前，系统需要array_values调用来解压缩对象参数。

_AC-13210 - [GitHub问题](https://github.com/magento/magento2/issues/39233) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37411)_

#### [问题]重构报价地址验证方法

此PR包含对doValidate方法的可读性改进。

_AC-13214 - [GitHub问题](https://github.com/magento/magento2/issues/38230) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38219)_

#### Magento选项 — 运行cli时从未使用过magento-init-params？

现在，运行CLI命令时使用 — magento-init-params选项。
以前，将 — magento-init-params传递给CLI命令对MAGE_MODE等参数没有影响。
AC-13231

_AC-13231 - [GitHub问题](https://github.com/magento/magento2/issues/39248) - [GitHub代码贡献](https://github.com/magento/magento2/commit/132b9e68)_

#### getItemsByColumnValue类型声明错误

现在，系统在getItemsByColumnValue函数中将输入参数$value正确定义为基元类型，而不是数组，从而确保该函数返回预期的集合。 以前，如果使用具有单个值的数组作为输入参数，该函数将返回空值，并且IDE会将其标记为错误。

_AC-13240 - [GitHub问题](https://github.com/magento/magento2/issues/33070) - [GitHub代码贡献](https://github.com/magento/magento2/pull/33120)_

#### 当使用文件存储作为锁定提供程序时，我们会获得不断增加的文件目录，而不会进行任何清理

此拉取请求引入了一个新的cronjob，每天运行一次，并搜索过去24小时内未修改并因此可安全移除的锁定文件。 这将使锁定文件目录的内容处于控制之下。
只有当锁提供程序配置为使用文件时，此cronjob才会执行某些操作，而不是当使用其他文件之一时（数据库 — 默认、zookeeper或缓存）

_AC-13367 - [GitHub问题](https://github.com/magento/magento2/issues/39369) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39372)_

#### [问题]清理：不使用方法调用中的void返回值。

此PR会进行细微的清理。 有时我们调用不会返回任何内容(void)的方法，然后使用该结果值。 其实并不需要。

_AC-13664 - [GitHub问题](https://github.com/magento/magento2/issues/39524) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39516)_

#### 在Magento 2.4.7多存储实施中，与FPC关联的缓存密钥

修复了多存储设置中的全页缓存(FPC)缓存键不包含MAGE_RUN_CODE和MAGE_RUN_TYPE的问题，该问题会导致与早期版本相比的缓存键行为不一致。 现在，缓存键正确地包括存储上下文，从而确保跨存储区进行正确的缓存隔离。

_AC-13719 - [GitHub问题](https://github.com/magento/magento2/issues/39456) - [GitHub代码贡献](https://github.com/magento/magento2/commit/ae6f305b)_

#### [问题] [PHPDOC]修复Magento\Framework\Message\ManagerInterface的错误phpdoc

此PR修复了\Magento\Framework\Message\ManagerInterface的错误phpdoc并删除了\Magento\Framework\Message\Manager中的所有重复phpdoc（使用inheritdoc语法）。

_AC-14312 - [GitHub问题](https://github.com/magento/magento2/issues/39593) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39153)_

#### 部分索引停止适用于有大量更新的客户

部分索引现在适用于有大量更新的客户。
以前，如果达到changelog表中version_id列的最大值，则会导致索引更新停止。
AC-14424

_AC-14424 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Magento 2.4.8使用不遵循语义版本控制的开发包

Magento 2.4.8需要开发版本的pdeat/pdepend和phpmd/phpmd (3.x-dev)才能兼容PHP 8.4。
这些开发版本与第三方工具冲突，这些工具需要符合SemVer的包，从而阻止某些升级。
临时解决方法是为composer.json中的开发版本别名（例如，“3.x-dev as 3.99.0”），以便在满足语义版本控制的同时允许兼容性。
这可确保PHP 8.4的支持并避免冲突，直到稳定发行版可用。

_AC-14519 - [GitHub问题](https://github.com/magento/magento2/issues/39796)_

#### 下载配送标签后，发现发现部分配送数量与运费和包装费不符。

运费标签数量现在与运费和包装费一致。
以前，下载送货标签后，显示的数量与送货和包装价格不匹配。
AC-14560

_AC-14560_

#### MView机制在触发器执行时静默忽略错误

MView机制现在可以正确报告触发器执行错误。
以前，在触发器执行期间出现的错误会被静默忽略，这可能会导致缺少索引更新而不发送任何通知。
AC-14567

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

#### [问题]包含构造函数以使其成为`CommandListInterface` API的一部分，扩展内联文档

此PR更新将Magento\Framework\Console\CommandList标记为API，并将构造函数引入到CommandListInterface中以实现更好的可扩展性。 它还改进了内联文档，以增强扩展控制台命令的开发人员的清晰度和可维护性。

_AC-14680 - [GitHub问题](https://github.com/magento/magento2/issues/31102) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37901)_

#### [问题]删除与Microsoft IIS相关的代码

此PR会按照Magento系统要求文档来清理与Microsoft IIS相关的代码，该文档指出Microsoft Windows操作系统不受支持

_AC-14702 - [GitHub问题](https://github.com/magento/magento2/issues/39910) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39894)_

#### Magnifier.js语法错误

系统Magnifier功能应保持以前的工作方式，magnifierOptions不应在全局范围内可用

_AC-14722 - [GitHub问题](https://github.com/magento/magento2/issues/36200) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39321)_

#### `setup:db:status` CLI命令中的反向端口详细模式

`setup:db:status` CLI命令现在支持详细模式。
以前，很难了解升级所需的数据库更改。 现在，运行`bin/magento setup:db:status -v`提供了有关架构和数据差异的详细信息。
AC-14807

_AC-14807 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7bdafaa2)_

#### 使用tls和2.4.8发送SMTP邮件

使用TLS发送SMTP电子邮件现在可按预期运行。
以前，通过带有TLS的SMTP发送电子邮件会导致错误： error:1408F10B:SSL例程:ssl3_get_record:版本号错误。
AC-14883

_AC-14883 - [GitHub问题](https://github.com/magento/magento2/issues/39947) - [GitHub代码贡献](https://github.com/magento/magento2/commit/3717e6cb) - [GitHub代码贡献](https://github.com/magento/magento2/commit/d3ea191d)_

#### [问题]修复静态内容部署中的并发问题

此PR修复了以下错误：多个并发进程启动以处理相同的主题包，具体取决于主题与其父级的定义方式。

_AC-14944 - [GitHub问题](https://github.com/magento/magento2/issues/39990) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39954)_

#### [问题]删除PHP版本&lt; 8.1的旧版兼容性代码

此拉取请求将删除设计在PHP &lt;8.1上运行的代码。
此外，删除了对PHP_VERSION_ID联系人可用性的检查，因为它在所有PHP版本中都可用

_AC-14971 - [GitHub问题](https://github.com/magento/magento2/issues/39891) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39882)_

#### 登录时FPC不起作用

全页缓存(FPC)现在可适用于已登录的客户。
以前，在登录后，主页不会从缓存加载，并且x-magento-cache-debug标头显示MISS而不是HIT。
AC-14999

_AC-14999 - [GitHub问题](https://github.com/magento/magento2/issues/40007)_

#### 在某些php类中添加泛型类型，以改善静态分析支持

现在，系统使用泛型类型定义来显着改进此功能，方法是将其解释为方法调用返回的确切类

_AC-15013 - [GitHub问题](https://github.com/magento/magento2/issues/40017) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40119)_

#### [问题]改进了处理SchemaBuilder的错误

此PR改进了数据库架构的错误消息处理。 它有助于我们识别问题，而无需进行大量调试。

_AC-15020 - [GitHub问题](https://github.com/magento/magento2/issues/39816) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39799)_

#### Rest API：在null时调用成员函数getVideoProvider()

修复了在子产品只有YouTube视频而没有其他图像的情况下，调用可配置产品子级API返回500内部服务器错误的问题。
该错误是由ExternalVideoEntryConverter中的空引用导致的。
现在，API可正确返回包含媒体集条目的子产品，包括外部视频数据，而不会引发错误。
这可确保通过REST API正确检索子产品的所有媒体类型。

_AC-15046 - [GitHub问题](https://github.com/magento/magento2/issues/40021)_

#### [W3C]从Cookie脚本标记声明中删除text/javascript

此PR从Cookie脚本标记中删除了不必要的type=&quot;text/javascript&quot;属性，以符合HTML5的要求。

_AC-15061 - [GitHub问题](https://github.com/magento/magento2/issues/39982) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39983)_

#### [问题]修复PHPDoc注释中的几个拼写错误

此PR修复了phpdoc中的几个拼写错误

_AC-15075 - [GitHub问题](https://github.com/magento/magento2/issues/40042) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38809)_

#### [问题]删除短语调用中的sprintf用法

此PR会删除Magento核心中短语函数调用中的sprintf用法。

_AC-15183 - [GitHub问题](https://github.com/magento/magento2/issues/40050) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40033)_

#### 无法重新索引具有活动应用程序锁的多线程索引器上的所有无效

此问题修复了在启用use_application_lock时多线程索引器失败的问题。
以前，在并行处理期间数据库锁定丢失，导致索引器保持工作状态并引发SQL错误（未找到表）。
在Magento 2.4.9-alpha3中，此修复程序确保在启用应用程序锁的情况下正确重新索引索引器。

_AC-15270 - [GitHub问题](https://github.com/magento/magento2/issues/40102) - [GitHub代码贡献](https://github.com/magento/magento2/commit/68a45d0a)_

#### Magento\Framework\Escaper中的返回类型不明确/无效

使用5级phpstan执行静态分析时，系统将接受转义器方法的类型

_AC-15272 - [GitHub问题](https://github.com/magento/magento2/issues/40012) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40114)_

#### [问题]允许特定于队列的配置超出默认最大消息数量值

系统现在允许队列特定的配置超过默认的最大消息数

_AC-15284 - [GitHub问题](https://github.com/magento/magento2/issues/40121) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40110)_

#### [问题]使用清漆时相同查询的相同页面出现重复的缓存fpc

此PR通过标准化查询参数顺序来修复使用Varnish时重复的全页缓存条目，从而确保相同请求的缓存键一致。
对于不同序列中具有相同参数的URL，提高缓存命中率和性能。

_AC-15325 - [GitHub问题](https://github.com/magento/magento2/issues/39706) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39704)_

#### 社区主题包含Commerce版本模块的资源

通过将其重新定位到各自的模块目录，从社区主题中移除了仅限Commerce的样式资源。 这样可防止未使用的CSS在Community Edition中捆绑在一起，从而减少不必要的负载并消除无效的样式规则，同时确保在启用Commerce模块时设置正确的样式。

_AC-15347 - [GitHub问题](https://github.com/magento/magento2/issues/21446) - [GitHub代码贡献](https://github.com/magento/magento2/commit/9bcd880a)_

#### [问题]将存储代码添加到Url应为全局的

此PR通过确保使用核心代码中的全局范围检索“将存储代码添加到Url”设置来解决问题

_AC-15365 - [GitHub问题](https://github.com/magento/magento2/issues/40069) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40065)_

#### [问题]仅当插件未禁用时记录未声明的插件

此PR可修复并记录实际未声明且未使用的插件（已启用且缺少实例）。

_AC-15386 - [GitHub问题](https://github.com/magento/magento2/issues/40086) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40081)_

#### [问题]小规模清理，已从数组中移除重复的键

系统现在进行了小规模清理，发现与阵列相关的“未发现错误”具有2个值为“粗细（及以上）”的重复键

_AC-15414 - [GitHub问题](https://github.com/magento/magento2/issues/39851) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39844)_

#### Magento 2.4.8-p2，magento/framework版本103.0.8-p2：EmailMessage类调用不存在的方法

EmailMessage类现在可以正确处理电子邮件正文检索。
以前，在带有magento/framework版本103.0.8-p2的Magento 2.4.8-p2中，Magento\Framework\Mail\EmailMessage类尝试在Symfony邮件消息对象上调用不存在的方法(getTextBody)。 当第三方模块或自定义项依赖此方法处理电子邮件时，这会导致错误。
现在，EmailMessage类不再调用未定义的方法，从而防止了这些错误。 AC-15446

_AC-15446 - [GitHub问题](https://github.com/magento/magento2/issues/40170) - [GitHub代码贡献](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x]数据/架构修补程序getAliases()在`setup:upgrade`期间导致错误

getAliases()在安装:upgrade期间导致错误，此PR修复了相同的

_AC-15559 - [GitHub问题](https://github.com/magento/magento2/issues/31396) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38239)_

#### 非法混合操作的归类

无可用描述。

_AC-15614 - [GitHub问题](https://github.com/magento/magento2/issues/40138) - [GitHub代码贡献](https://github.com/magento/magento2/commit/44329e9d)_

#### [问题] [PHPDOC]修复错误的phpdoc Magento\Framework\DB\Adapter\AdapterInterface：：quoteColumnAs()

此PR将更新\Magento\Framework\DB\Adapter\AdapterInterface：：quoteColumnAs()的PHPDoc，以正确反映$alias参数除了字符串外也可以为空。 这解决了级别为5及更高的PHPStan问题，并改进了代码质量工具兼容性。

_AC-15626 - [GitHub问题](https://github.com/magento/magento2/issues/39598) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39581)_

#### 在urlrewrite模块中非法混合归类

无可用描述。

_AC-15647 - [GitHub问题](https://github.com/magento/magento2/issues/40189) - [GitHub代码贡献](https://github.com/magento/magento2/commit/44329e9d)_

#### `\Magento\Framework\Escaper::escapeScriptIdentifiers`中从未满足条件

更正了\Magento\Framework\Escaper：：escapeScriptIdentifiers中无法访问的情况，方法是将false检查替换为null，将其与preg_replace返回值对齐，从而提高代码准确性而不影响功能。

_AC-15667 - [GitHub问题](https://github.com/magento/magento2/issues/40195) - [GitHub代码贡献](https://github.com/magento/magento2/commit/cc0ec250)_

#### 清漆7.3（最新版本） — 默认类别的子类别链接/选项未显示在店面主页上

已确认使用Varnish 7.3时店面主页上缺少子类别链接是由于ESI请求处理和服务器配置所致，而非Magento代码缺陷；该问题可通过建议的Varnish配置调整来解决，而无需更改核心代码。

_AC-15674 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3cf1a106) - [GitHub代码贡献](https://github.com/magento/magento2/commit/9a62604c)_

#### [问题]将额外的调试数据添加到`cache_invalidate`日志

此PR增强了cache_invalidate日志，以包含用于完全缓存清除的请求上下文和栈栈跟踪，从而改进了调试和可见性。
这有助于在不更改现有功能的情况下识别意外完全缓存失效的来源。

_AC-15719 - [GitHub问题](https://github.com/magento/magento2/issues/40204) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40196)_

#### [问题]稍微改进了编辑器的自动加载器排除列表。

此PR可优化Composer自动加载器排除以跳过测试类，从而减少不必要的类映射条目并防止PSR-4警告。

_AC-15743 - [GitHub问题](https://github.com/magento/magento2/issues/40109) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40107)_

#### [问题]阻止包含`db_schema.xml`的`comment=""`声明破坏零停机部署

现在，系统可防止带有comment=&quot;&quot;的db_schema.xml声明破坏零停机时间部署

_AC-15980 - [GitHub问题](https://github.com/magento/magento2/issues/40254) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40242)_

#### 无法清除`\Magento\Framework\Filesystem\Glob::glob(...)`缓存

此PR更新引入了一种清除\Magento\Framework\Filesystem\Glob使用的内部静态缓存的方法，以确保在文件结构更改时产生新鲜而准确的结果。 它提高了可靠性和开发人员体验，尤其是在测试场景和长时间运行的流程中，其中glob结果必须保持最新。

_AC-15989 - [GitHub问题](https://github.com/magento/magento2/issues/35741) - [GitHub代码贡献](https://github.com/magento/magento2/pull/35742)_

#### ReadME领导者链接URL具有永久重定向

更新了README领导者链接，将永久重定向和过期的URL替换为正确的工作链接，确保参与者和维护者页面正确打开。

_AC-16046 - [GitHub问题](https://github.com/magento/magento2/issues/40292) - [GitHub代码贡献](https://github.com/magento/magento2/commit/913bf1a6)_

#### [问题] [PHPDOC]修复错误的phpdoc Magento\Eav\Model\ResourceModel\Entity\Attribute\Collection

更正了Attribute Collection中joinLeft()的PHPDoc注释，以允许正确的数组定义，增强代码正确性和与PHPStan等工具的兼容性。

_AC-16187 - [GitHub问题](https://github.com/magento/magento2/issues/40354) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39155)_

#### 确保单个命令失败记录错误（文件或stderr）而不停止后续CLI命令的执行。

系统现在确保单个命令失败记录错误（file或stderr）而不停止后续CLI命令的执行

_AC-16244 - [GitHub问题](https://github.com/magento/magento2/issues/40006) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40063)_

#### [问题]将int类型添加到PageCache内核中的$maxAge

此PR可确保PageCache内核中的$maxAge参数被严格键入为整数，以提高类型安全性并防止在缓存处理中出现PHPStan/静态分析错误。

_AC-16313 - [GitHub问题](https://github.com/magento/magento2/issues/40438) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36600)_

#### 伪模块需要扩展存储库中的dev/目录

无可用描述。

_AC-16487_

#### 添加到购物车事件：空价格

修复了在添加到购物车流程期间，在checkout_cart_product_add_after事件观察器中将产品价格返回为null的问题。
现在，可以正确检索基本价格和相关价格值，确保为观察者和自定义实施提供准确的数据。

_AC-5966 - [GitHub问题](https://github.com/magento/magento2/issues/35638) - [GitHub代码贡献](https://github.com/magento/magento2/commit/3b5ac075)_

#### PHP8.1类型bugfix

现在，当严格处理模式不活动或产品信息可用时，关联的产品会初始化为空数组，而不是false。 此更改确保后续逻辑处理相关产品的行为一致，提高了产品准备过程中的稳定性和可预测性。

_AC-6017 - [GitHub问题](https://github.com/magento/magento2/issues/35808) - [GitHub代码贡献](https://github.com/magento/magento2/pull/35842)_

#### 应为类型“Magento\Customer\Api\Data\GroupInterface”。 找到&#39;Magento\Customer\Model\Group&#39;。

修复了使用GroupFactory通过GroupRepositoryInterface保存客户组时导致类型错误的问题。
以前，存储库需要GroupInterface，但传递了组模型实例，从而导致致命错误。
现在，通过确保正确的界面实施，可以通过存储库成功保存客户组。
这解决了以编程方式创建或更新客户组时IDE警告和运行时错误。

_AC-6909 - [GitHub问题](https://github.com/magento/magento2/issues/36269)_

#### 贷项通知的字段验证

修复了在填写必填自定义字段后，贷项通知单页面上的字段验证仍阻止提交的问题。
现在，验证工作正常，并且在填写完所有必填字段后启用了提交按钮。

_AC-8308 - [GitHub问题](https://github.com/magento/magento2/issues/37182) - [GitHub代码贡献](https://github.com/magento/magento2/commit/64823f95)_

#### [问题]从框架（第3部分）中删除禁止的`@author`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，从而提高整体代码质量。 以前，某些模块中存在此标记违反了既定的编码标准。

_AC-8343 - [GitHub问题](https://github.com/magento/magento2/issues/37270) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37020)_

#### [问题]在模块发送好友图QL中使用构造函数属性提升

该系统现在利用“发送朋友”GraphQL模块中的构造函数属性提升，增强了代码的可读性，降低了复杂性。 以前，模块使用的属性占据大量行，从而使代码变得更加复杂且不易读取。

_AC-8346 - [GitHub问题](https://github.com/magento/magento2/issues/37235) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37197)_

#### [问题]删除禁止的`@author`标记

此PR从代码库中移除`@author`标记

_AC-8349 - [GitHub问题](https://github.com/magento/magento2/issues/37266) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37016)_

#### [问题]删除禁止的`@author`标记

此PR从代码库中移除`@author`标记

_AC-8350 - [GitHub问题](https://github.com/magento/magento2/issues/37265) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37015)_

#### [问题]从`@author`中删除禁止的`Magento_Downloadable`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，从而提高整体代码质量。 以前，某些模块中存在此标记违反了既定的编码标准。

_AC-8355 - [GitHub问题](https://github.com/magento/magento2/issues/37251) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37001)_

#### [问题]删除禁止的`@author`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，从而提高代码质量和一致性。 以前，某些模块中存在此标记违反了既定的编码标准。

_AC-8358 - [GitHub问题](https://github.com/magento/magento2/issues/37264) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37014)_

#### [问题]删除禁止的`@author`标记

此PR从代码库中移除`@author`标记

_AC-8359 - [GitHub问题](https://github.com/magento/magento2/issues/37262) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37012)_

#### [问题]删除禁止的`@author`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，从而提高整体代码质量。 以前，某些模块中存在此标记违反了既定的编码标准。

_AC-8360 - [GitHub问题](https://github.com/magento/magento2/issues/37261) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37011)_

#### [问题]删除禁止的`@author`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，确保代码更干净和标准化。 以前，某些模块中存在此标记违反了既定的编码标准。

_AC-8361 - [GitHub问题](https://github.com/magento/magento2/issues/37260) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37010)_

#### [问题]删除禁止的`@author`标记

此PR从代码库中移除`@author`标记

_AC-8362 - [GitHub问题](https://github.com/magento/magento2/issues/37259) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37009)_

#### [问题]删除禁止的`@author`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，从而提高整体代码质量。 以前，某些模块中存在此标记违反了既定的编码标准。

_AC-8363 - [GitHub问题](https://github.com/magento/magento2/issues/37258) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37008)_

#### [问题]从`@author`和`Magento_Backup`中删除禁止的`Magento_Bundle`标记

此PR从代码库中移除`@author`标记

_AC-8367 - [GitHub问题](https://github.com/magento/magento2/issues/37244) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36979)_

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

#### [问题]修复catalogsearch中的变量名称

系统现在可以在搜索引擎模块中正确命名变量，从而提高代码清晰度和可维护性。 以前，在搜索引擎模块中使用不相关的变量名称$defaultCountry，从而导致混淆。

_AC-9215 - [GitHub问题](https://github.com/magento/magento2/issues/37810) - [GitHub代码贡献](https://github.com/magento/magento2/pull/33533)_

#### allow_parallel_generation应通过环境变量设置

修复后，“MAGENTO_DC_CACHE_ALLOW__PARALLEL_GENERATION”环境变量可用于设置“allow_parallel_generation”配置。

_ACP2E-3673 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b12ffe36)_

#### [Cloud]在Magento 2中使用db_schema.xml文件将表列类型从Int更改为Decimal会导致错误

无法正确更改列数据类型。 以前，它会引发错误：不允许使用属性“identity”。

_ACP2E-3709 - [GitHub代码贡献](https://github.com/magento/magento2/commit/df92debe)_

#### Adobe支持的新货币(XCG)

加勒比盾(XCG)被添加到货币列表。

_ACP2E-3790 - [GitHub代码贡献](https://github.com/magento/magento2/commit/520f9e30)_

#### 由于添加了新验证，导致升级2.4.7-p5时出现问题

修复了SchemaBuilder类中，未定义的数组键“列”在架构创建或更新期间导致崩溃的问题。 处理不包含“column”键的表数据时，会发生这种情况。

_ACP2E-3871 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9ad7d277)_

#### [QUANS]服务器问题可能是由无效的S3访问密钥导致的

错误的AWS S3凭据不再导致页面无限期地加载到店面。

_ACP2E-3890 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [Cloud] Minify js不起作用

启用JS缩小功能后，以下JS文件现在可以完全且正确地缩小： mage/backend/tabs.min.j、jquery/jquery.validate.min.js和Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js。 因此，页面生成器CSS类字段验证可按预期工作。

_ACP2E-3925 - [GitHub代码贡献](https://github.com/magento/magento2/commit/47721be6)_

#### PHP8.4弃用错误：升级到Adobe Commerce 2.4.8后出现E_USER_ERROR

*不需要发行说明*
面向客户的方案不受此修复的影响。

_ACP2E-3963 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7accebfa)_

#### Cron作业未清除数据库表 — 导致因Galera崩溃而发生中断

Changelog表清理现在批量运行，以避免大量删除操作。

_ACP2E-3995 - [GitHub代码贡献](https://github.com/magento/magento2/commit/52f46328)_

#### 未缩小的JS有时会加载，忽略“启用js缩小”

在修复之前，即使启用了缩小，也会请求一些JS文件，但其中不包含导致404状态代码的“min”前缀。 修复后，在启用缩小功能时，不会请求非缩小的JS资源。

_ACP2E-4058 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 自定义属性组中的日期属性无法在管理员中显示日期选取器

修复了将日期属性的日历弹出窗口分配给自定义属性组时显示在屏幕外的问题。

_ACP2E-4060 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 生产ACL权限检查导致性能下降 — populateAcl方法是瓶颈

优化了ACL规则处理

_ACP2E-4114 - [GitHub代码贡献](https://github.com/magento/magento2/commit/98f028ab)_

#### 使用AC-15867 + ACP2E-4296和SCD压缩实现最新版本的签出时不加载

在修复之前，通过头部分加载自定义javascript可能会导致问题。 引入新设置后，可以自动延迟此类脚本，以确保与Magento 2框架更好地兼容。

_ACP2E-4319 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1c547060)_

#### 弃用警告：使用moment.updateLocale(localeName， config)更改现有区域设置。 moment.defineLocale(localeName， config)

在修复之前，浏览器控制台中会引发一个已弃用的警告。 现在，修复后，不再显示此类警告。

_ACP2E-4338 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2687b487)_

#### 通过REST API保存产品更改时出现[CLOUD] DateTimeZone错误

在修复之前，如果不存在代码为“default”的存储，则产品更新REST API请求将生成错误。 现在，修复之后，产品更新请求可以正常运行，无论是否存在“默认”存储。

_ACP2E-4339_

#### 与MariaDB 10.11不兼容

以前，使用MariaDB 10.11安装最新Magento 2版本时失败，导致安装过程无法完成。 通过更新数据库兼容性处理以解决此问题，以便在安装期间支持MariaDB 10.11.x。

_ACP2E-4367 - [GitHub代码贡献](https://github.com/magento/magento2/commit/31258bf6)_

### 框架，搜索

#### 单价类别上的Opensearch 2.19.1 illegal_argument_exception

对于包含所有具有相同价格的产品的类别，Opensearch不再引发illegal_argument_exception。 以前，它具有此异常：“[from]参数不能为负”。

_ACP2E-3896 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### 在GraphQL中成功下订单的配送方法无效

修复了可能会使用禁用或无效的配送方式通过GraphQL下达订单的问题。
现在，系统会验证选定的配送方式，如果无法提供，则会返回错误，从而阻止创建订单。

_AC-10472 - [GitHub代码贡献](https://github.com/magento/magento2/pull/38268) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a8cf637b)_

#### 运行GraphQl查询时引发异常

修复了GraphQL查询因排序参数无效而引发异常的问题；修复后，查询成功执行而不会生成错误或异常日志。

_AC-14835 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a8cf637b)_

#### 通过AddProductsToCart突变（包括custom_attributesV2）将礼品卡产品添加到购物车时出现内部服务器错误

解决了通过GraphQL使用custom_attributesV2将礼品卡（和类似的自定义选项）产品添加到购物车时触发的内部服务器错误；该修复程序正确处理复杂的属性值，从而允许添加产品而不会出现错误。

_AC-15856 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7fa400a7)_

#### `Country`查询中有Null字段

修复了包含虚拟、已退款和已发运项目的订单仍在处理中的问题，方法是确保虚拟项目包含在已发运数量计算中，从而允许订单状态正确转换以完成。

_AC-7731 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ef666cd9)_

#### GraphQL查询具有“number”属性的“customerOrders”导致内部服务器错误

修复了在请求数字字段时GraphQL customerOrders查询返回内部服务器错误的问题。
现在，解析程序正确返回了订单增量ID，从而允许查询成功执行并检索订单号。

_AC-8949 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3b5ac075)_

#### GraphQL对订单安排的响应不包括异常消息

还原以前以不同格式返回错误的更改。 现在，以一致的方式返回了潜在错误，而不会破坏GraphQL架构。 应作为已知BIC添加，PM可在此处批准： https://jira.corp.adobe.com/browse/ACP2E-3399?focusedId=45248897&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-45248897

_ACP2E-3399 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9608ca21)_

#### 订单投放的GraphQL响应已部分本地化

placeOrder GraphQl突变返回的错误未完全本地化。 现在，在多语言上下文中，错误会被正确翻译。

_ACP2E-3506 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9608ca21)_

#### 对重新排序GraphQL API的并发调用 — 将相同的产品添加到不同的行

修复了以下问题：同时调用重新排序GraphQL API会导致相同的产品被添加为不同的行，进而导致数据不一致。

_ACP2E-3774 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### updateCustomerEmail GraphQL突变（更改电子邮件地址）不会触发电子邮件通知

以前，成功更新客户帐户中的电子邮件地址后不会向客户发送电子邮件。 应用此修复后，客户现在会在成功更新其电子邮件地址后收到电子邮件通知。

_ACP2E-3785 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### 动态属性未通过updateGiftRegistry变异在礼品注册表中更新

以前，在通过updateGiftRegistry突变进行此修复之前，不会通过GraphQL突变来修改或更新礼品注册表的自定义属性。 应用此修复后，可通过updateGiftRegistry变异成功更新礼品注册表的动态属性。

_ACP2E-3805_

#### 删除产品时customerOrders graphql返回错误

即使订单中的产品被删除，customerOrders graphql请求也不再引发错误。 以前，引发“内部服务器错误”错误。

_ACP2E-3936_

#### 客户订单GraphQL ：检索关联产品的产品类别“不可单独显示”

在修复之前，如果订单包含隐藏的产品，则其类别将在客户订单GraphQl响应中显示空数组。
现在，修复之后，即使产品已隐藏，产品类别也会包含在客户订单GraphQl请求的响应中。

_ACP2E-3945 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 在GraphQL请求中，未在一个网站内的商店视图之间共享愿望清单项目

在修复之前，按商店ID过滤愿望清单项目。 现在，修复之后，愿望清单项目会按网站进行过滤。

_ACP2E-3987 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2a252ae6)_

#### [云] getRemoteAddress在生产环境中返回127.0.0.1

在此修复之前，在使用应用程序服务器时，无法正确确定远程地址。 修复后，将正确确定远程地址，并结合nginx中的正确标头设置和标头配置。

_ACP2E-3991 - [GitHub代码贡献](https://github.com/magento/magento2/commit/47721be6)_

#### [QUANS]确认GQL订单放置异常处理行为反转

解决了对placeOrder突变的向后不兼容更改。

_ACP2E-4031 - [GitHub代码贡献](https://github.com/magento/magento2/commit/52f46328)_

#### 通过GraphQL下订单时将翻译后的消息映射为错误代码的问题

修复了已翻译异常消息用于映射GraphQL请求的错误代码时导致已知错误的未知错误代码的问题。

_ACP2E-4033 - [GitHub代码贡献](https://github.com/magento/magento2/commit/fab20b00)_

#### [CLOUD]客户订单筛选器不适用于日期

修复后，使用日期范围过滤器通过GraphQL检索订单会返回正确结果。

_ACP2E-4090 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 解决ACP2E-4031中提出的问题

在修复之前，错误节点位置不提供与2.4.7和2.4.9版本的无缝兼容性。 现在，修复后，错误节点已正确放置以适应这两个版本。

_ACP2E-4115 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e457c5e2)_

#### 即使子级在Graphql调用中已安装，捆绑父级仍显示缺货

修复后，使用GraphQL请求产品列表会返回捆绑产品的正确库存状态。

_ACP2E-4168 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a1c57b2e) - [GitHub代码贡献](https://github.com/magento/inventory/commit/5632fb5e)_

#### SWAT中的GraphQL异常

修复后，GraphQL请求的响应将通过HTTP规范与GraphQL保持一致。 当无法解析请求、请求未获授权或请求存在其他一般问题时，将返回4XX响应代码。 如果请求经过解析并且可以处理，则将返回200响应代码。

_ACP2E-4194 - [GitHub代码贡献](https://github.com/magento/magento2/commit/45cbf9b6)_

#### 将列表分配给客户后，不会从比较列表中删除产品

将访客用户的比较列表分配给客户帐户后，客户现在可以删除作为访客添加的产品。
以前，移除操作失败，因为来宾添加的项目在分配后未正确链接到客户的帐户。

_ACP2E-4244 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c135fc3a)_

#### updateCartItems GraphQL错误响应不正确

以前，当对数量不足的物料发出graphQL请求时，即使该物料不可用，也会返回带有错误代码的正确错误消息，以及请求的数量和价格计算。 应用此修复后，现在会返回一个带有错误代码的正确错误消息，如果响应中无法使用项目的数量，则会将项目数量设置为旧值。

_ACP2E-4283 - [GitHub代码贡献](https://github.com/magento/magento2/commit/cbca0396)_

#### MergeGuestOrder插件中的跨网站访客订单分配错误

在修复之前，来宾订单客户分配不考虑帐户共享选项。 现在，修复之后，如果客户和订单商店匹配（假定客户帐户共享选项设置为“每个网站”），则会向客户分配订单。

_ACP2E-4312 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c135fc3a)_

### GraphQL、库存/MSI

#### Magento 2 GraphQL中的only_x_left_in_stock问题 — 使用阈值时计算不正确

修复了only_x_left_in_stock GraphQL字段由于不正确的双倍扣除MinQty而返回null的问题；该计算已更正，现在可根据阈值返回准确的库存值。

_AC-15832 - [GitHub代码贡献](https://github.com/magento/inventory/commit/35458c7f)_

#### GraphQL mergeCart突变差异

修复后，合并购物车GraphQL请求会根据库存配置正确检查产品数量。

_ACP2E-4184 - [GitHub代码贡献](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL，产品

#### MediaGalleryInterface中的产品graphql缺少media_type

MediaGallery GraphQL请求现在包含用于产品图像类型的“类型”字段。 以前，媒体集GraphQL请求中不存在此“类型”字段。

_ACP2E-3880 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL，安全性

#### 通过GraphQL重置客户密码不符合限制

解决了通过GraphQL突变发出的客户密码重置请求不符合在商店>配置>客户>客户配置>密码选项下配置的密码重置限制的问题。 这些设置现已正确实施。

_ACP2E-3992 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6dd3fa99)_

### 导入/导出

#### [问题]修复参数类型

修复了导入/导出模块中参数类型不匹配的问题，该问题导致之前定义为字符串的值现在正确设置为数组。 这符合导出控制器的预期输入，并防止出现静态分析警告。

_AC-11665 - [GitHub问题](https://github.com/magento/magento2/issues/38529) - [GitHub代码贡献](https://github.com/magento/magento2/commit/64823f95)_

#### [问题] Copyedit：将“coping”更改为“coping”

PR修复了次要复制以更正“copying”的拼写

_AC-13300 - [GitHub问题](https://github.com/magento/magento2/issues/39311) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39307)_

#### REST端点产品导入Json不验证必填字段

现在，通过导入流程（管理员或API）创建新产品时，需要填写名称字段。 在修复之前，您可能创建了无名称的新产品，这会破坏管理员界面并创建无效产品。

_ACP2E-3660 - [GitHub代码贡献](https://github.com/magento/magento2/commit/df92debe)_

#### 导出过程中缺少网站筛选器选项

现在，在创建产品导出时可以按网站过滤产品。

_ACP2E-3720 - [GitHub代码贡献](https://github.com/magento/magento2/commit/520f9e30)_

#### AC-13913重复 — 静态属性异步清理。

修复后，在创建\Magento\CatalogImportExport\Model\Import\Product\Type\AbstractType的众多实例时，不会出现“未定义数组键“apply_to”错误。

_ACP2E-3752 - [GitHub代码贡献](https://github.com/magento/magento2/commit/520f9e30)_

#### Csv产品导入：无法取消设置样本图像

在修复之前，您无法通过产品导入更新产品的样本图像。 现在，修复之后，如果您使用配置的空标记来标记产品样本图像列，则图像将设置为“隐藏”。

_ACP2E-3972 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 产品导入为商店范围生成空URL

如果url_key在导入数据源中具有空值，则存储视图中的产品URL密钥现在将继承默认范围中设置的值。 以前，如果将存储视图记录的导入数据源中的url_key设置为空值，则会导致该范围中的url_key被空值覆盖。

_ACP2E-4038 - [GitHub代码贡献](https://github.com/magento/magento2/commit/52f46328)_

#### 如果根据需要配置了多选属性，则产品导入流程会遇到错误

解决了当包含多选类型的必需属性时，产品导入失败的问题。 数据验证现在可正确通过，从而成功完成产品导入过程。

_ACP2E-4057 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD]在管理库存上未选择延交订单的产品在导入时仍允许客户订购超出我们库存水平的产品

修复后，无法再为产品的“allow_backorders”属性导入不可接受的值。

_ACP2E-4116 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 产品导入失败，因为描述长度超过65,536个字符验证

修复后，可能会导入文字值超过65,536个字符的产品属性。

_ACP2E-4119 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a1c57b2e)_

#### 导出产品筛选器是 — 否属性未按预期发挥作用

修复后，按“是/否”属性过滤的导出产品将包含与所应用过滤器相符的预期产品。

_ACP2E-4160 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ee918f0d)_

#### 通过“导入”更新每个网站的捆绑包选项价格时出现问题

现在可以导出和导入每个网站的捆绑包选项选择价格

_ACP2E-4243 - [GitHub代码贡献](https://github.com/magento/magento2/commit/98f028ab)_

#### 无法导入具有大写电子邮件地址的客户

修复了当“帐户共享”设置为“全局”时，导入具有大写电子邮件的客户时出现的未定义数组键错误。 现在，电子邮件标准化在整个导入过程中是一致的，从而确保客户无论使用何种电子邮件均可导入。 网站级别的帐户共享行为保持不变。

_ACP2E-4373 - [GitHub代码贡献](https://github.com/magento/magento2/commit/31258bf6)_

### 导入/导出，客户/客户

#### 管理员可以导入出生日期晚于当前日期的客户

修复了管理员可以导入出生日期设置在未来客户的问题。 现在，系统会在导入期间验证DOB，为无效记录显示错误，并阻止导入未来出生日期客户，从而确保客户数据的准确性。

_AC-13641 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8670a2b4)_

### 库存/MSI

#### 结帐时地址更改时商店代答未考虑最大搜索半径

现在，如果配送地址发生更改，“店内提货”中预先选定的商店将会更新。 以前，预先选择商店后，即使新送货地址不在所选商店的半径内，商店也不会更改

_ACP2E-3728 - [GitHub代码贡献](https://github.com/magento/inventory/commit/07620383)_

#### 重定向到主页并结帐后，没有可用的存储

现在，如果客户导航到付款页面，然后返回到主页，最后返回到结账页面，则以前选择的商店将在“店内提货”配送中预先选择。 以前，在反复返回到结账页面后，将清除“店内挑选”中的选定商店。

_ACP2E-3793 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a20a6ff2) - [GitHub代码贡献](https://github.com/magento/inventory/commit/62c0d79b)_

#### 库存删除操作未完成

修复后，删除源项目不会导致完全重新索引，而只更新受影响的产品以提高性能。

_ACP2E-3917 - [GitHub代码贡献](https://github.com/magento/inventory/commit/ee0bf4ad)_

#### [MSI]管理员中没有指示是否已异步通知客户订单已准备好提货

已添加到有关客户的订单历史记录通知中，该通知是有关订单已准备好取货的异步通知

_ACP2E-3968 - [GitHub代码贡献](https://github.com/magento/inventory/commit/29653b1d)_

#### 报价加载时重复的库存状态查询

修复了在店面加载报价时重复执行cataloginventory_stock_status查询的问题，该问题会导致多余的数据库调用。

_ACP2E-4102 - [GitHub代码贡献](https://github.com/magento/inventory/commit/fc15a9ae)_

#### 补丁后ACP2E-4118：管理员中的库存阈值更改导致可销售数量减少和库存状态不匹配

现在，在通过导入更新全局库存配置数量、延交订单和缺货阈值时，库存库存库存状态会自动调整。

_ACP2E-4142 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a1c57b2e) - [GitHub代码贡献](https://github.com/magento/inventory/commit/5632fb5e)_

#### 更新库存时，[云]管理报告不显示详细信息

产品库存源更改现在由日志记录模块记录。 在修复之前，在保存产品和执行库存相关更改时，不会记录详细信息。

_ACP2E-4167 - [GitHub代码贡献](https://github.com/magento/magento2/commit/cbca0396) - [GitHub代码贡献](https://github.com/magento/inventory/commit/76b88f7c)_

#### 将产品标记为有存货时无法添加到购物车的捆绑产品

捆绑产品库存状态现在可正确反映子产品预留和缺货阈值。
以前，即使一个或多个子产品缺少足够的可销售数量，捆绑产品也会标记为“有货”。 在将捆绑包添加到购物车时，这导致“没有足够的商品可供销售”错误。

_ACP2E-4220 - [GitHub代码贡献](https://github.com/magento/magento2/commit/cbca0396) - [GitHub代码贡献](https://github.com/magento/inventory/commit/76b88f7c)_

#### 将子项分配给自定义源/库存时，如果分组产品在从CSV导入后在PDP上错误地显示为缺货（在手动重新索引后修复）

修复后，使用import创建复合产品会自动执行库存重新索引，从而使产品无需手动重新索引即可使用。

_ACP2E-4233 - [GitHub代码贡献](https://github.com/magento/magento2/commit/98f028ab) - [GitHub代码贡献](https://github.com/magento/inventory/commit/5704166a)_

#### [MSI]与最新主线更改相关的MFTF测试失败。

在固定访客选择不提供送货地址的“店内提货”之前，他们的帐单地址自动填写了商店地址，该地址无法更改，从而导致发票详细信息不正确。 在修复帐单地址之后，现在可在此方案中编辑，允许来宾输入自己的详细信息。 注册用户将看到其保存的账单地址，而不是商店的账单地址。

_ACP2E-4260 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ab891304) - [GitHub代码贡献](https://github.com/magento/inventory/commit/13e432a6)_

#### 为虚拟礼品卡创建的库存预留不正确

在实施此修复之前，包含多个物品的虚拟礼品卡的数量未准确反映在库存预订中。 但是，在应用修复之后，库存预留量和库存量变得同步。

_ACP2E-4267 - [GitHub代码贡献](https://github.com/magento/inventory/commit/5704166a)_

#### 库存预留补偿命令因产品引用为Null和不存在而失败

修复了当处理的组合缺少订单ID时，库存预留补偿CLI会引发异常的问题

_ACP2E-4301 - [GitHub代码贡献](https://github.com/magento/inventory/commit/76b88f7c)_

#### 更改SKU外壳后产品缺货

修改SKU事例后，店面中的产品不再缺货。

_ACP2E-4375 - [GitHub代码贡献](https://github.com/magento/inventory/commit/0836c2ed)_

#### 具有无效数据的按价格/价格彩块化排序

在修复之前，当子产品在自定义来源下有库存时，捆绑价格未正确索引。 现在，修复后，无论子产品库存分配如何，捆绑价格都会正确索引。

_ACP2E-4380 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1c547060) - [GitHub代码贡献](https://github.com/magento/inventory/commit/1f83ed24)_

#### 在暂存更新期间SKU更改后，库存状态与数量一起错误地重置为库存

现在禁止对计划更新处于活动状态的产品进行SKU更改；保存将失败，并出现明确的错误，而且管理员SKU字段在活动更新期间被禁用。 这样可以防止在暂存回滚期间由SKU更改导致的MSI库存不一致。

_ACP2E-4389_

### 订购

#### AbstractAddress setData(&#39;custom_attributes&#39;， AttributeValue[])中断customAttributes

现在，在签出和API操作期间，可以正确处理地址上的自定义属性。
以前，使用$address->setCustomAttributes(&#39;custom_attributes&#39;， $attributes)可能会中断自定义属性处理，导致属性值结构不正确。
AC-10568

_AC-10568 - [GitHub问题](https://github.com/magento/magento2/issues/31644)_

#### 当客户设置为报价单时，仍为来宾订单

无可用描述。

_AC-11689 - [GitHub问题](https://github.com/magento/magento2/issues/38540)_

#### 将虚拟、已退款和已发运的项目混合在一起时，订单未完成

修复了包含虚拟、已退款和已发运项目的订单仍在处理中的问题，方法是确保虚拟项目包含在已发运数量计算中，从而允许订单状态正确转换以完成。

_AC-11691 - [GitHub问题](https://github.com/magento/magento2/issues/38547)_

#### v2.4.7-p1 Magento重新排序–1订单号

系统按预期工作，从后端重新排序后，订单编号将唯一8位

_AC-12854 - [GitHub问题](https://github.com/magento/magento2/issues/39089) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39399)_

#### 使用Adobe信用卡支付方法结账时丢失产品自定义选项文件上传

使用Adobe信用卡支付方式结账时，现在会保留产品自定义选项文件上传。
以前，使用此付款方法时文件上传会丢失，但可以与其他付款方法配合使用。
AC-14306

_AC-14306 - [GitHub问题](https://github.com/magento/magento2/issues/39647)_

#### 管理员订单 — 无法搜索Will

修复了在管理订单网格中按客户名称（例如“Will”）搜索订单时未返回任何结果的问题。 修复后，在按客户名称过滤时可正确显示相关订单。

_AC-14360 - [GitHub问题](https://github.com/magento/magento2/issues/36596) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a8cf637b)_

#### Magento 2.4.8 GraphQL — 订单项目order_date格式错误

修复了GraphQL响应中的order_date字段以yyyy-mm-dd格式返回的问题。
现在，order_date以dd-mm-yyyy格式正确显示。

_AC-14431 - [GitHub问题](https://github.com/magento/magento2/issues/39805) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 对于不可为空的字段\“AppliedCoupon.code\”意外问题，无法返回null

Adobe Commerce现在可在查询客户订单时通过GraphQL正确返回应用的优惠券代码。 以前，在Adobe Commerce 2.4.8中，使用applied_coupons.code字段（例如通过customer.orders查询）获取订单可能会失败，并出现内部服务器错误，并且消息“无法为不可为空的字段“AppliedCoupon.code”返回null，而applied_coupons返回为[null]，而不是包含优惠券代码的列表。 AC-14484

_AC-14484 - [GitHub问题](https://github.com/magento/magento2/issues/39841) - [GitHub代码贡献](https://github.com/magento/magento2/commit/97b2ea42)_

#### 从管理员订单视图提交时未发送装运电子邮件，尽管在商店配置中启用了此功能

系统现在会发送装运确认电子邮件，因为它在下达订单的商店配置中启用。

_AC-14563 - [GitHub问题](https://github.com/magento/magento2/issues/39861) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39897)_

#### 由于字段名称不明确，无法按日期过滤

在Magento 2.4.7-p6中，按日期过滤订单网格已报告由于与Braintree模块的连接而引发错误。
该问题涉及在应用日期过滤器时联接braintree_transaction_details和sales_order表的查询。
Adobe Commerce Engineering已审查此案例，但无法在环境中重现错误。
预期行为是，按日期过滤应返回与过滤器匹配的订单并且没有错误。

_AC-15037 - [GitHub问题](https://github.com/magento/magento2/issues/40024)_

#### 在后台创建多个产品（其中至少有一个包含自定义选项）的订单，会导致将不需要的额外产品添加到订单中

修复了在Backoffice中使用多个产品（包括一个具有自定义选项的产品）创建订单、无意中添加额外产品并引发错误的问题。 现在，系统仅添加选定的产品，以便创建订单时不会出现任何意外项目。

_AC-15286 - [GitHub问题](https://github.com/magento/magento2/issues/40122) - [GitHub代码贡献](https://github.com/magento/magento2/commit/b5e99d20)_

#### Magento2：无法创建促销活动规则

此PR修复，我们
\Magento\Catalog\Model\ResourceModel\Eav\Attribute模型，而不是\Magento\SalesRule\Model\Rule\Condition\Product：：loadAttributeOptions方法中的\Magento\Catalog\Model\ResourceModel\Eav\Attribute

_AC-15358 - [GitHub问题](https://github.com/magento/magento2/issues/12176) - [GitHub代码贡献](https://github.com/magento/magento2/pull/30479)_

#### Magento在调用$invoice = $this->_invoiceService->prepareInvoice($order)之后更改了$order的实体类型；

修复了在编辑子类别的现有计划更新时，会错误地增加数据库中父类别的children_count的问题。 在保存更新后，该问题导致类别层次结构数据不准确。 修复后，子项计数保持正确且不再意外增加。

_AC-15401 - [GitHub问题](https://github.com/magento/magento2/issues/40154)_

#### 如果物料获得部分退款，则在发运后，订单仍处于“正在处理”状态

修复了在部分退款项目并发运其余项目后，订单仍处于“正在处理”状态的问题。 现在，一旦发运数量和退款数量合计与开票数量匹配，订单状态将正确更新为“完成”，从而确保订单生命周期管理准确无误。

_AC-15419 - [GitHub代码贡献](https://github.com/magento/magento2/commit/cc0ec250)_

#### 从后端发送销售电子邮件始终会取得成功 — 在禁用此功能时也是如此

修复了后端销售电子邮件通知，通过验证电子邮件服务结果来显示准确的消息，确保在禁用订单或发票电子邮件且未发送时通知用户。

_AC-16059 - [GitHub问题](https://github.com/magento/magento2/issues/40309) - [GitHub代码贡献](https://github.com/magento/magento2/commit/c95ed7d7)_

#### 无法为分配给新网站和来源的产品创建申请列表

修复了在启用“将商店代码添加到URL”后，无法为分配给新网站和源的产品创建申请列表的问题。 发生该问题的原因是从API请求中剥离了存储代码，导致出现未经授权的错误。 修复后，将保留正确的商店上下文，并成功创建申请列表。

_AC-16226_

#### 重新订购时，自定义价格0会重置为原始价格。

修复了自定义价格为0的产品在重新订购期间恢复到其原始价格的问题。
现在，自定义价格会正确保留，从而确保在重新订购项目时能够准确定价。

_AC-8147 - [GitHub问题](https://github.com/magento/magento2/issues/36970) - [GitHub代码贡献](https://github.com/magento/magento2/commit/01cee3c3)_

#### 禁用付款方法正常工作的下单

修复了可以通过GraphQL使用禁用的付款方式下达订单的问题。
现在，当尝试设置或使用不可用的付款方法时，返回一个错误，导致无法创建订单。

_AC-9605 - [GitHub问题](https://github.com/magento/magento2/issues/37983) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a8cf637b)_

#### [云]升级到magento 2.4.6-p7后，某些内联Javascript不起作用

单击admin中“Add to Order by SKU”（按SKU添加至订单）中的“delete”（删除）按钮现在会删除SKU。 以前，单击“按SKU添加到订单”中的“删除”按钮不会删除SKU。

_ACP2E-3515_

#### sales_order表中的gift_cards序列化数据不一致

sales_order表中的gift_cards数据现在已正确序列化。 以前，每次更新订单时都会序列化。

_ACP2E-3662_

#### 订单状态在处理时卡住

在修复之前，在订购启用了“一起发货”选项的捆绑产品时，在开具发票和发运后，订单状态不会自动切换为“完成”。 现在，修复之后，在订单开票并发运后，订单状态会自动切换为“完成”。

_ACP2E-3947 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud]Magento OOTB代码 — 电子邮件模板设置问题

在修复之前，使用异步电子邮件发送时，装运电子邮件与商店订单不一致。 现在，修复之后，将交付正确的商店发货电子邮件订单。

_ACP2E-3998 - [GitHub代码贡献](https://github.com/magento/magento2/commit/462ede94)_

#### 取消发票重定向至404

取消使用“非捕获”类型开具的发票不会导致第404页。

_ACP2E-4001 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 销售存档Cron作业导致数据库锁定问题

在修复之前，按存档cron顺序找到的未绑定DELETE查询导致Galera出现问题。 现在，更新后，删除查询的执行受到限制。

_ACP2E-4010_

#### 使用REST API的配置选项导致更新订单出现问题

通过rest api端点更新订单时，保留销售订单物料上的现有产品选项。

_ACP2E-4061 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 商店特定发件人未用于礼品卡电子邮件

以前，在从其他商店创建发票后发送礼品卡的电子邮件模板时，当客户收到电子邮件时，管理员配置设置中的所有者名称不会反映在电子邮件标头中。 应用此修复后，电子邮件标头现在包含相应商店所有者的电子邮件信息。

_ACP2E-4310_

#### 按ID异步插入的销售在每个cron运行时限制为100个条目

改进了销售网格异步插入的处理。 一个cron run现在以批量方式插入所有待处理行，而不是严格为每个运行100行。

_ACP2E-4360 - [GitHub代码贡献](https://github.com/magento/magento2/commit/31258bf6)_

#### 错误消息“ID为“1”的产品不存在。” 重复记录到exception.log中

在修复之前，如果在“上次订购的项目”部分中遇到已删除的产品，则会记录严重错误。 修复后，商家可以通过di.xml中的`skipDeletedProductLogging`参数配置是记录还是跳过已删除的产品。 默认情况下，为了向后兼容，行为保持不变，但商家可以将参数设置为`true`，以静默跳过已删除的产品并防止日志噪音。

_ACP2E-4366 - [GitHub代码贡献](https://github.com/magento/magento2/commit/61c96348)_

#### 对第二个贷项通知单退税的双重税

修复了在从订单视图页创建上一贷项通知单后从发票创建部分退税时贷项通知单中计税不正确的问题。

_ACP2E-4384 - [GitHub代码贡献](https://github.com/magento/magento2/commit/61c96348)_

### 订单，定价

#### 管理员在创建退货时显示的货币符号不正确

在使用不同货币（欧元/美元/英镑）的多网站设置中，管理员的退货产品选择页面现在显示正确的货币符号。 以前，它显示默认货币符号。

_ACP2E-3658 - [GitHub代码贡献](https://github.com/magento/magento2/commit/df92debe)_

### 订单，退货

#### 创建离线退款的贷项通知单时出错

修复了使用设置动态价格=否为捆绑产品创建贷项通知单失败的问题。 现在可以成功创建贷项通知单，而不会出现错误。

_ACP2E-4157 - [GitHub代码贡献](https://github.com/magento/magento2/commit/45cbf9b6)_

### 其他

#### 无法将“将奖励积分余额限制在”的值留空 — 已保存

Adobe Commerce现在允许商家将“上限奖励积分余额”字段留空，同时仍设置奖励积分余额兑换阈值。 以前，当在商店>配置>客户>奖励点数下配置奖励点数时，为奖励点数余额赎回阈值输入正数并将上限奖励点数余额留空会触发验证错误：“上限奖励点数余额”无效。 余额必须为正数或留空。 验证并重试。”，阻止商家保存无上限的配置。 ACP2E-3977

_ACP2E-3977_

### 其他开发人员工具

#### [问题]受保护成员$_urlHelper的类型提示错误

系统现在使用正确的提示来修复错误的类型提示，该提示也用于构造函数

_AC-10716 - [GitHub问题](https://github.com/magento/magento2/issues/32503) - [GitHub代码贡献](https://github.com/magento/magento2/pull/32496)_

#### [问题]正在清除未使用的代码。

系统现在删除有关未使用导入的未使用代码。

_AC-10980 - [GitHub问题](https://github.com/magento/magento2/issues/38424) - [GitHub代码贡献](https://github.com/magento/magento2/pull/33499)_

#### Lighthouse辅助功能失败

系统现在通过，辅助功能得分为100

_AC-12783 - [GitHub问题](https://github.com/magento/magento2/issues/39054) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39164)_

#### 禁用captcha storefront配置仍加载captcha js文件

在禁用验证码时，系统现在不加载验证码js文件
店面

_AC-14267 - [GitHub问题](https://github.com/magento/magento2/issues/32987) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39154)_

#### [问题]辅助功能：菜单中的WAI-ARIA角色嵌套错误

系统现在可以生成Lighthouse辅助功能，并且菜单错误中的WAI-ARIA角色嵌套没有错误，报告应为绿色

_AC-15082 - [GitHub问题](https://github.com/magento/magento2/issues/40045) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38617)_

#### 在Magento管理员中预览电子邮件时出现控制台错误

在预览电子邮件模板时，系统不会引发任何控制台错误

_AC-9245 - [GitHub问题](https://github.com/magento/magento2/issues/37820) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37933)_

### 支付/支付方式

#### 在后端成功配置时，店面中不显示Paylater消息

修复了在后端配置后， PayPal Pay Later消息仍无法在“主页”和“购物车”页面上显示的问题。 对于没有默认地址的来宾或客户，当买方国家/地区为null时，无法呈现横幅。 修复后，店面可正确显示“Pay Later（稍后付款）”信息。

_AC-12335 - [GitHub代码贡献](https://github.com/magento/magento2/commit/528af81a)_

### 支付

#### [问题]修复脱机发票捕获(404)

它修复了从Magento管理员处捕获离线支付方法的发票时出现404页面错误的问题

_AC-13336 - [GitHub问题](https://github.com/magento/magento2/issues/39298) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39297)_

#### 来自PayPal的未知IPN滥用应用程序IPN处理器

IPN处理程序现在会忽略不支持的或未知的IPN类型。 它不会返回500错误，而是会记录问题并继续处理，不会出现中断。

_ACP2E-4049 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6dd3fa99)_

#### PayflowPro保存的卡令牌付款时失败

PayPal PayFlow Pro交易ID (PNREF)现在可在12个月的固定期限内的参考交易中使用。 过期后，保存的卡将不再显示，必须再次添加。 以前，有效性由原始交易中使用的支付卡的到期日确定。

_ACP2E-4064 - [GitHub代码贡献](https://github.com/magento/magento2/commit/52f46328)_

#### 对管理员下订单时出现保险存储卡问题

将带有存储信用卡的订单放在具有不同支付操作配置的网站下不再会导致错误或错误的交易类型

_ACP2E-4270 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [Cloud] PayflowPro保存的卡（保险库）最后4位未按顺序显示

现在，将已保存的卡与Sales付款活动一起使用时，可以正确保留并显示卡信息，这与PayflowPro使用Authorization付款活动时的行为相匹配。

_ACP2E-4346 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0a3b7032)_

### 性能

#### [问题]更新Store.php

此PR通过跳过当前的存储解析来提高性能。

_AC-14791 - [GitHub问题](https://github.com/magento/magento2/issues/39949) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38717)_

#### [问题]更新使用静态站点不可变的缓存控制

此PR通过以下方式提高了性能：在&amp;发生更改之前，不验证每个页面加载上的静态内容。

_AC-15171 - [GitHub问题](https://github.com/magento/magento2/issues/39486) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39484)_

#### [问题]缓存isCacheable调用的结果以提高性能

此PR为isCacheable()方法添加了缓存，从而导致布局渲染过程减少冗余检查，并提高整体页面渲染性能。

_AC-16054 - [GitHub问题](https://github.com/magento/magento2/issues/40156) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40112)_

#### [问题]异步订单网格处理的性能稍有改进

此PR通过将该基于临时缓存的last_updated_at查找替换为存储在标志表中的持久数据库支持标志，为Magento的异步订单网格处理引入了性能优化。 这可确保即使在缓存刷新或部署后，系统始终保留上次处理的时间戳，从而防止对大型sales_order数据集进行不必要的全表扫描。 因此，异步网格更新变得更加高效和可预测，尤其是在订单活动频繁的高容量存储上。

_AC-16109 - [GitHub问题](https://github.com/magento/magento2/issues/40282) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40271)_

#### 类别权限模块可能会阻止缓存

第三方控制器现在通过客户区段正确缓存

_ACP2E-3721_

#### [云]无法将产品添加到类别

改进了通过Visual Merchandiser将产品添加到类别时的性能。

_ACP2E-3946 - [GitHub代码贡献](https://github.com/magento/inventory/commit/29653b1d)_

#### [云] cache_invalidate超过10K日志

以前，在每次访问PLP或购物车时都会清除缓存，从而造成不必要的性能开销。 Target规则缓存不再在这些页面上失效，从而提高了浏览效率。

_ACP2E-4059_

#### [Cloud] php-fpm未遵守max_execution_time

现在，部署配置会在单个请求中加载一次。

_ACP2E-4201_

#### ACP2E-3995之后的Changelog清理性能问题

修复后， indexer_clean_all_changelogs cron作业将完全清除更改日志，并保持批处理不变。

_ACP2E-4211 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ee918f0d)_

#### [CLOUD]升级到2.4.8后，Fastly缓存不起作用

解决了可缓存页面未正确存储或未从Fastly缓存提供服务，从而导致缓存行为不一致和性能下降的问题。

_ACP2E-4324 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2687b487)_

#### 调查redis密钥和缓存密钥创建增加的原因

在修复之前，用于远程存储元数据的缓存键不会过期。 现在，修复之后，您可以通过依赖关系注入为此类缓存键设置TTL。

_ACP2E-4345 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0a3b7032)_

### 定价

#### 对于未设置动态价格的捆绑产品项目，订单Rest API中的价格始终为0

现在，Order REST API会返回捆绑产品项目的正确价格而不使用动态价格。
以前，通过REST API导出订单时，未动态定价的捆绑产品项目的价格始终返回为0，而不是捆绑页面上显示的实际价格。
AC-11925

_AC-11925 - [GitHub问题](https://github.com/magento/magento2/issues/38687) - [GitHub代码贡献](https://github.com/magento/magento2/commit/7da46f52)_

#### 创建时分配给价格属性的范围不正确

修复了以下问题：新创建的价格属性未正确分配商店视图范围（不考虑配置）；修复之后，属性范围现在默认与目录价格范围设置（全局或网站）保持一致。

_AC-14945 - [GitHub问题](https://github.com/magento/magento2/issues/39986) - [GitHub代码贡献](https://github.com/magento/magento2/commit/8670a2b4)_

#### 即使使用成批活动的特殊价格起始日期迟于终止日期也会保存产品

修复了在保存产品时可能使用无效的特殊价格日期范围而不进行验证的问题。
现在，显示一条错误消息：“确保结束日期晚于或等于开始日期。”

_AC-15252 - [GitHub问题](https://github.com/magento/magento2/issues/40113) - [GitHub代码贡献](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 完成可转让报价的Paypal Express结帐后，装运详细信息不匹配。

此问题修复了在为已批准的可转让报价完成PayPal Express签出时运费不匹配的问题。
在修正价格之前，运费错误地翻了一番（显示为10美元，而不是5美元），导致运费总额被夸大。
Magento 2.4.9-alpha3中的修复可确保应用正确的运输成本

_AC-15280_

#### 对于在不同时区创建的网站，特价未生效

在修复之前，会在当前商店时间戳的范围中创建特殊价格日期有效期。 现在，完成修复后，会考虑默认存储时区。

_ACP2E-4002_

#### 即使应用了特殊价格，常规价格也不可见。

解决了在应用特殊价格时未显示常规价格的问题。 现在，常规价格与特殊价格一起按预期正确显示。

_ACP2E-4100 - [GitHub代码贡献](https://github.com/magento/magento2/commit/47721be6)_

### 产品

#### 前端行为不佳的可配置产品

修复了在包含颜色样本属性时，可配置产品显示错误前端行为，从而导致定价、下拉布局和必填字段指示器显示不正确的问题。
现在，可配置产品可以通过正确的定价、对齐的下拉菜单和预期的UI行为来正确呈现。

_AC-1014 - [GitHub问题](https://github.com/magento/magento2/issues/14296) - [GitHub代码贡献](https://github.com/magento/magento2/commit/ef666cd9)_

#### 当可配置产品被分配给测试库存和测试网站，并且启用了显示缺货产品的选项时，价格断言字符串不匹配

更新了失败的测试，以便在所有子产品具有相同的价格时符合可配置产品的实际定价行为。
该断言现在可以正确验证所显示的价格，从而在不影响功能的情况下防止错误测试失败。

_AC-10843 - [GitHub代码贡献](https://github.com/magento/inventory/commit/1ccc786b)_

#### 对于测试用例AC-6158的可配置产品，仍会显示“低至”标签

具有相应的变体和类别分配的实现和验证的可配置产品(P1-P7)。 已确保C类产品正确显示店面价格和“最低”标签行为。

_AC-10847 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 根据原始价格计算的层价格和目录价格规则的折扣百分比（不含选定选项）。

层价格和目录价格规则的百分比折扣现在包括所选的自定义选项。
以前，在计算原始产品价格时不会考虑选定的自定义选项，从而导致最终价格不正确。
AC-12004

_AC-12004 - [GitHub问题](https://github.com/magento/magento2/issues/38750)_

#### [问题]验证评级不起作用，审阅评级的选择器已更改

修复了由于选择器更改而未触发审阅评级验证的问题。 以前，无需选择评级即可保存审核。 修复后，验证可正确运行，除非选择了评级，否则无法保存审阅。

_AC-12686 - [GitHub问题](https://github.com/magento/magento2/issues/33424) - [GitHub代码贡献](https://github.com/magento/magento2/commit/528af81a)_

#### Magento 2.4.7 minAllowed缺少产品订单数量

系统工作正常，页面源正确显示产品的最小数量

_AC-12909 - [GitHub问题](https://github.com/magento/magento2/issues/39142) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39480)_

#### 产品收藏集 — 在可能加载或将加载收藏集时，addMediaGalleryData调用getSize（可以使用count避免额外的DB查询）

如果在调用Product Graphql时已经加载了产品收藏集，并且其中包含media_gallery字段，则此PR会减少使用count()进行的额外查询调用。

_AC-13055 - [GitHub问题](https://github.com/magento/magento2/issues/39111) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39681)_

#### Magento中链接产品的SKU处理无效

修复了由于SKU验证无效，无法将SKU为“0”的产品关联为相关、追加销售或交叉销售项目的问题。 此更新可确保成功链接此类产品，从而保存产品时不会出错。

_AC-13311 - [GitHub问题](https://github.com/magento/magento2/issues/39329) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a8cf637b)_

#### 管理面板中产品页面上的可自定义选项网格问题

当我们使用类型下拉菜单创建可自定义的选项时，系统按预期工作

_AC-14003 - [GitHub问题](https://github.com/magento/magento2/issues/39640) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39694)_

#### 将所有产品属性都设置为全局范围时，出现“管理产品页面”错误

修复了将所有产品属性设置为全局范围时，管理员产品编辑页面显示错误的问题。 该错误是由空数据库查询导致的，导致页面不可用。 修复后，产品页面会正确呈现，并且可以毫无问题地创建产品。

_AC-14011 - [GitHub问题](https://github.com/magento/magento2/issues/39646)_

#### [2.4.8]未找到cron作业catalog_product_alert的回调

现在，当产品警报cron作业重命名为product_alert后，Adobe Commerce可正确阻止计划错误的catalog_product_alert cron作业。 以前，在Adobe Commerce 2.4.8中，配置存储>配置>目录>目录>产品警报运行设置会导致在core_config_data中创建catalog_product_alert cron条目，并且cron运行时，会记录错误Magento_Cron.CRITICAL：异常：找不到对cron作业catalog_product_alert的回调，即使有效的product_alert作业已正确运行。

_AC-14494 - [GitHub问题](https://github.com/magento/magento2/issues/39800) - [GitHub代码贡献](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### 申请列表页打印选项不起作用

现在，“申请列表”页面上的“打印”选项可正常工作。
以前，单击“打印”会导致错误：“应用程序运行期间出现错误。 有关详细信息，请参阅异常日志。”
AC-14711

_AC-14711_

#### [产品比较]比较列表将不可用

修复了在从不同的商店视图添加相同产品时，比较列表变得不可用的问题；修复后，比较列表会正确加载并显示基于特定商店的项目。

_AC-14885 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8670a2b4)_

#### 通过存储库请求产品时额外的日志记录失败

改进了未找到SKU或ID时ProductRepository：：get和getById的错误消息。
以前，异常不提供有关哪个SKU或ID导致错误的上下文。
现在，异常消息包括缺少的SKU或ID，有助于调试和改进开发人员体验。
此更改不会影响API的任何功能行为。

_AC-15199 - [GitHub问题](https://github.com/magento/magento2/issues/40090) - [GitHub代码贡献](https://github.com/magento/magento2/commit/1b1baf1d)_

#### 属性集不存在错误中断了此页

修复了在URL中输入无效的属性集ID导致严重错误的问题；系统现在显示正确的错误消息，指出属性集不存在，而不是中断页面。

_AC-15753 - [GitHub问题](https://github.com/magento/magento2/issues/40213) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a06a4a57)_

#### 负数量退款始终退款折扣

修复了创建具有负数量的贷项通知单时错误地退款折扣金额的问题。
现在，负数量不退款折扣，并且退款数量正确设置为零。

_AC-9424 - [GitHub问题](https://github.com/magento/magento2/issues/37917) - [GitHub代码贡献](https://github.com/magento/magento2/commit/ef666cd9)_

#### 当通过pagebuilder包含产品小部件时，执行缓慢查询

优化了用于创建产品小部件（包括产品SKU）的查询。

_ACP2E-3449 - [GitHub代码贡献](https://github.com/magento/magento2/commit/df92debe)_

#### 产品图像在添加为可配置产品时未调整大小

以前，通过管理面板中的配置添加的映像不符合最大上传大小限制，这可能导致不一致和管理挑战。 现在，已实施了一项修复，以确保在上传期间自动调整图像大小以符合最大大小限制，从而简化流程和维护系统标准。

_ACP2E-3504 - [GitHub代码贡献](https://github.com/magento/magento2/commit/df92debe)_

#### 其他客户比较列表中的所有项目在通过管理员登录后都分配给客户

以前，当管理员在后端使用“以客户身份登录”功能时，先前登录的客户比较列表中的产品被错误地分配给当前模拟的客户。  修复后，会为正确的登录客户正确加载比较列表。

_ACP2E-3818 - [GitHub代码贡献](https://github.com/magento/magento2/commit/462ede94)_

#### 按受限角色编辑可配置产品时未分配简单产品

在此修复之前，如果受限管理员用户保存的可配置产品包含管理员用户无权访问的简单产品，则会在保存时从可配置产品中删除。 修复后，可配置产品将按从完全权限管理员保存的形式保留。

_ACP2E-4081_

#### [B2B]共享目录保存返回已弃用的功能错误

管理员可以成功地从共享目录取消分配产品。
以前，从共享目录取消分配具有大量长产品SKU的产品会导致错误

_ACP2E-4097 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ab891304)_

#### [云] Sitemap生成性能显着降低

针对带图像的产品生成Sitemap的过程不再出现指数级放缓。 以前，为启用了图像包含的存储生成站点地图会导致处理时间较长。

_ACP2E-4153 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e457c5e2)_

#### 客户区段排序顺序不一致导致X-Magento-Vary Cookie在某些页面上不断重新生成

现在，X-Magento-Vary Cookie在产品页面上设置一次，而在以前，对于某些客户区段的配置，Cookie会在PDP加载期间设置多次

_ACP2E-4261_

### 产品、税

#### 固定产品税(FPT)无法与可配置产品分开显示

修复了在选择选项后，无法单独显示可配置产品的固定产品税(FPT)的问题。 现在，FPT划分正确显示在产品列表和详细信息页面上，与简单产品的显示格式匹配。

_AC-13171 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b5e99d20)_

### 促销活动

#### 购买X获取Y购物车价格规则在应用其他规则时添加了错误的折扣

修复了购买X获取Y购物车价格规则使用原始产品价格计算折扣的问题，即使是在其他规则已减少该价格之后。 此更新可确保第二个规则现在将折扣应用于调整后的价格，从而在多个促销活动处于活动状态时获得准确的总折扣。

_AC-12325 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8670a2b4)_

#### 通过GraphQl客户请求获取客户订单的订单物料折扣appliced_to时出错

之前，当通过GraphQl客户请求获取客户订单的appliced_to折扣时出现内部服务器错误，该错误现已修复，并且会获取包含应用折扣的正确客户订单数据

_AC-14888 - [GitHub问题](https://github.com/magento/magento2/issues/39963) - [GitHub代码贡献](https://github.com/magento/magento2/commit/fe72c407)_

#### 通过GraphQl客户请求获取客户订单的订单项目优惠券代码时出错

修复了通过GraphQL获取包含优惠券详细信息的订单时返回内部服务器错误的问题。
现在，查询执行成功，并在响应中返回正确的优惠券信息。

_AC-14889 - [GitHub问题](https://github.com/magento/magento2/issues/39962) - [GitHub代码贡献](https://github.com/magento/magento2/commit/fe72c407)_

#### 在修复ACP2E-2926后，每个结账请求都将匹配客户区段，从而导致不必要的处理

客户区段功能现在包括缓存机制以提高性能。

_ACP2E-4299_

#### 未应用`[Cloud][experienceleague]`目录价格规则

在固定目录价格规则应用之前，当`special_price`仅在网站级别（而不是在“所有商店视图”）设置时。 现在，当在网站级别设置`special_price`时，通过先检查网站的默认商店，在固定目录价格规则之后正确应用。

_ACP2E-4372 - [GitHub代码贡献](https://github.com/magento/magento2/commit/61c96348)_

### SEO

#### DynamicStorage.findProductRewriteByRequestPath()缺少entity_type筛选，导致CMS页面被视为类别URL中的产品

修复了DynamicStorage未按entity_type进行筛选的问题，该问题会导致CMS页面被错误地视为类别URL中的产品；现在，格式错误的URL会正确返回404而不是提供CMS内容。

_AC-14991 - [GitHub问题](https://github.com/magento/magento2/issues/39996) - [GitHub代码贡献](https://github.com/magento/magento2/commit/64823f95)_

#### 在产品URL中启用类别路径会以多种方式中断存储切换器

修复了在产品URL中启用类别路径导致存储切换器失败的问题；存储切换现在可以跨存储视图正确解析产品URL，而不会重定向到主页或返回错误。

_AC-15110 - [GitHub问题](https://github.com/magento/magento2/issues/40037) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a7ef6300)_

#### ProductRepository getById中未定义数组键

在调用具有无效ID（如123abc）的ProductRepository：：getById()时出现了此问题，导致出现“未定义数组键值”错误。
在Magento 2.4.9-alpha3中进行修复后，此类请求现在可正确返回404页面，而不是引发异常。
QA使用有效且格式错误的ID进行了确认，没有发现其他问题。

_AC-15345 - [GitHub问题](https://github.com/magento/magento2/issues/40146) - [GitHub代码贡献](https://github.com/magento/magento2/commit/68a45d0a)_

#### Storefront比较产品创建Google SEO错误 — 链接不可搜索

解决了SEO问题，该问题导致搜索引擎无法搜索店面“比较产品”链接，因为href属性缺失或绑定不正确。 此更新可确保链接现在包含有效的可爬网URL，从而提高网站可发现性并帮助通过Google SEO审核。

_AC-15547 - [GitHub问题](https://github.com/magento/magento2/issues/40185) - [GitHub代码贡献](https://github.com/magento/magento2/commit/c95ed7d7)_

#### 通过REST API更新产品url_key不会生成301 URL重写

当通过REST API更新产品的URL密钥时，如果将“如果URL密钥已更改，则为URL创建永久重定向”设置设置为“是”，则产品URL重写会创建一个从旧URL到新URL的重定向。

_ACP2E-3900 - [GitHub代码贡献](https://github.com/magento/magento2/commit/462ede94)_

#### [云]站点地图生成从不会结束

在此修复之前，如果目录包含超过100万个产品，则无法成功完成Sitemap生成。 修复后，Sitemap的生成将以较低的内存分配完成，每个商店有多达100万个产品。

_ACP2E-3902 - [GitHub代码贡献](https://github.com/magento/magento2/commit/52f46328)_

#### [Cloud]存储切换器无法从EN工作到FR以查找常见问题页

修复了在商店视图之间切换时，将用户重定向到主页而不是对应的已翻译CMS页面的问题。 现在，商店切换器会检查目标商店中的URL重写，以确保正确重定向（例如，英语的常见问题页面→法语的常见问题页面）。

_ACP2E-4112_

#### [云]取消激活旧站点地图生成

新的配置选项现在可用于在标准Sitemap生成过程和新实施的批处理模式之间进行切换。 此增强功能允许在Sitemap创建工作流中提供更大的灵活性和可扩展性。

_ACP2E-4132 - [GitHub代码贡献](https://github.com/magento/magento2/commit/45cbf9b6)_

#### 可疑请求会在exception.log中引发异常

修复了恶意或格式错误的URL请求导致数据库排序错误并填充异常日志的问题。
以前，如果收到包含无效字符编码或不支持字符的可疑请求，系统会尝试对其进行解码和处理，从而导致MySQL归类冲突。

_ACP2E-4328 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2687b487)_

### 销售

#### 在订单状态下拉菜单中选择值时订单状态消失

订单状态分配现在按预期运行。
以前，在分配自定义订单状态时，“正在处理”状态会在取消分配状态后从下拉列表中消失，从而无法重新分配。
AC-15010

_AC-15010_

#### 如果在订单层启用了礼品消息，但用户未输入任何数据和订单，则仍在“管理员”中输入“发件人姓名”和“发件人姓名”，显示客户的名字和姓氏。

修复了即使未输入礼品消息，礼品消息发件人和收件人字段也会自动填充客户名称的问题；这些字段现在保持空白，除非用户提供详细信息。

_AC-15140 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a8cf637b)_

### Search

#### 使用“记住类别分页”对目录搜索进行“确认表单重新提交”

在修改工具栏设置后，从产品页面导航回目录搜索结果页面时，在启用“记住类别分页”后，将不再触发“确认表单重新提交”对话框。
以前，用户在更改工具栏参数（如排序顺序）后返回到搜索结果页面时，遇到浏览器错误或有关表单重新提交的警告。

_ACP2E-4208 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e885088b)_

#### 搜索查询中不再使用聚合搜索字段“_search”

现在，如果所有可搜索字段中的最小匹配条件共同满足，则全文搜索将返回匹配产品，而不是要求条件由单个字段满足。

_ACP2E-4285 - [GitHub代码贡献](https://github.com/magento/magento2/commit/cbca0396)_

### 安全性

#### 内部服务器错误

现在，当使用异步REST端点POST /rest/default/async/V1/carts/mine/items时，Magento可成功将产品添加到客户的购物车。 以前，此异步“添加到购物车”请求导致内部服务器错误，Magento记录以下错误：错误：在app/code/Magento/Quote/Model/Quote/Item/AbstractItem.php:162中的null上调用成员函数setFinalPrice()。

_AC-16344 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8670a2b4)_

#### 捆绑/合并的JS不属于SRI哈希

在修复之前，生成的包或合并的文件未添加到SRI哈希列表。 现在，正在将文件正确添加到SRI哈希中。

_ACP2E-3854 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4ca73607)_

#### [CLOUD]在Newrelic中遇到可写权限问题

在修复之前，日志中杂乱无章，但有一些例外。 应用此修复后，日志现在干净且没有异常。

_ACP2E-4296 - [GitHub代码贡献](https://github.com/magento/magento2/commit/61c96348)_

### 配送

#### 在少数贷项后要发运的数量不正确

修复了在多个贷项通知单后错误地计算了“数量对发货”值，从而允许发运已退款物料的问题。
现在，系统会根据已发运和已退款的物料准确地更新剩余可发运数量，从而防止无效的发运。

_AC-1479 - [GitHub问题](https://github.com/magento/magento2/issues/34289) - [GitHub代码贡献](https://github.com/magento/magento2/commit/913bf1a6)_

#### 装载装运方法上的潜在性能问题

通过确保在请求时仅加载有效承运人，优化了配送方法加载流程。 以前，初始化所有配送方法的工厂，导致不必要的性能开销。 该修复程序通过有条件地仅加载活跃的航运承运人来提高效率，从而减少加载时间和资源使用。

_AC-15415 - [GitHub问题](https://github.com/magento/magento2/issues/40153) - [GitHub代码贡献](https://github.com/magento/magento2/commit/cc0ec250)_

#### [问题]商业目标不应被视为住宅目标

修复了UPS REST航运集成中的一个问题，该问题导致商业目标被错误地视为住宅目标。 现在，ResidentialAddressIndicator仅包含在针对住宅地址的UPS费率请求中，以防止意外的住宅附加费，并确保准确的商业运费。

_AC-16285 - [GitHub问题](https://github.com/magento/magento2/issues/40314) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40307)_

#### 创建UPS装运标签时出现异常

修复了警告：在UPS配送标签创建期间数组到字符串的转换

_ACP2E-3676 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b12ffe36)_

#### [QUANS] - Magento_Fedex核心模块是否在发送获取新令牌的请求之前检查有效的活动令牌？

Adobe Commerce将不再向FedEx API服务发出许多访问令牌请求。 以前，即使访问令牌仍然有效，Adobe Commerce也始终会向FedEx API发出新请求，这会导致速率限制问题。

_ACP2E-3930 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4ca73607)_

### 暂存和预览

#### 暂存更新调整规则时，受目录价格规则影响的购物车中产品的价格不会更改

修复了在通过暂存更新修改目录价格规则后购物车中的产品价格未完全更新的问题。 以前，更新的价格仅显示在摘要部分中，而中央购物车块显示旧值。 现在，修订后的规则正确更新了整个购物车中的产品价格。

_AC-15304 - [GitHub代码贡献](https://github.com/magento/magento2/commit/913bf1a6)_

#### 删除类别的计划更新时，父类别的子项数量不会减少

修复了删除类别的计划更新未减少父类别的子类别计数的问题，确保在删除计划更新或子类别时计数会正确更新。

_AC-15670 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ef666cd9)_

#### 编辑类别的计划更新时，会将子金额添加到父类别

修复了在编辑子类别的现有计划更新时，会错误地增加数据库中父类别的children_count的问题。 在保存更新后，该问题导致类别层次结构数据不准确。 修复后，子项计数保持正确且不再意外增加。

_AC-16239 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8670a2b4)_

#### 预览计划更新将按字母顺序打开第一个商店视图，而不是感兴趣的商店视图

在修复之前，计划更新的预览在第一个商店视图中按字母顺序打开，而不是在分配的商店视图中打开。
修复后，预览现在会在分配给CMS块暂存更新的存储视图中正确打开。

_ACP2E-3671 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b12ffe36)_

#### Staging_apply_version Cron行为问题 — 已忽略special_price

完成此修复后，通过计划的产品更新更改特殊价格后，将重新计算报价总额。

_ACP2E-3674_

#### 启用类别权限后，无法预览计划产品更新

在修复之前，要启用的将来产品不会以预览模式显示。 现在，即使当前状态为禁用，也会显示它。

_ACP2E-3786 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7accebfa)_

#### 预览期间范围显示不同的存储视图

在此修复之前，cms块和cms页面内容的暂存更新预览可能已在不同存储中打开，而不是在从内容暂存仪表板访问时在cms块或页面上分配的存储中打开。 修复后，如果cms块或页面在暂存更新中仅分配了特定存储，则将从内容暂存仪表板打开预览，并选中正确的存储。

_ACP2E-3815_

#### 缺少对目录价格规则折扣金额字段的验证

以前，使用当前验证规则无法正确验证暂存计划更新中的discount_amount字段。 但是，应用修复后，将相应地验证discount_amount字段。

_ACP2E-3867 - [GitHub代码贡献](https://github.com/magento/magento2/commit/462ede94)_

#### 使用其他管理域时，签出时暂存更新预览中断

当商店基本URL与管理员URL不同时，客户可以登录并在商店预览模式下查看其购物车。

_ACP2E-3906_

#### 内容暂存功能板显示的时间不正确

现在，“内容暂存仪表板”中的“开始时间”和“结束时间”日期过滤器显示正确的日期和时间。 以前，在日期选取器中选择日期和时间后，显示不正确的日期和时间

_ACP2E-3969_

#### 在预览计划更新产品和类别时，范围显示不同的“商店视图”

在此修复以前的版本中，类别和产品的预览链接未针对正确的存储生成。 进行此修复后，预览链接将自动选择创建预览的存储区。

_ACP2E-4053_

#### 具有计划更新的捆绑产品将删除产品保存操作中的捆绑项目选项

在计划更新中删除捆绑产品选项或关联产品不再影响原始捆绑产品选项和相关产品，反之亦然。 此外，在计划更新后删除原始产品中的捆绑生产选项并使用其他选项替换不再导致删除新添加的选项

_ACP2E-4212 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ab891304)_

#### 促销活动预览模式中应用的优惠券在应用后不久即消失的问题。

在修复之前，无法在暂存预览模式下正确使用优惠券代码。 现在，修复后，优惠券代码正确应用于结账页面。

_ACP2E-4226_

#### 无法在计划更新预览中的网站之间导航

在此修复之前，当尝试预览具有自定义域的商店的内容时，计划的更新预览将中断。 进行此修复后，可以按原样预览自定义存储域，并在预览iframe中导航。 该修复涵盖了产品、类别、CMS页面和CMS块，并支持使用`{{store url}}`Adobe Commerce变量和标记标记[中记录的](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/variables/markup-tags)标记标记的导航链接。

_ACP2E-4308 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0a3b7032)_

### 税金

#### 订单总计错误，此舍入不适用于价格计算。

现在，系统在计算price_after_discount、discount_amount和税额时可正确处理。
订单的实际总计

_AC-11389 - [GitHub问题](https://github.com/magento/magento2/issues/38455) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39687)_

#### [问题]修复：贷项通知单项目的base_weee_tax_applied_row_amnt值不正确

通过使用base_weee_tax_applied_row_ament的适当设置程序更正贷项通知单计算，确保税额仅反映退款数量。 以前，行金额错误地使用了完整的订单值，而不是部分贷项通知单金额。

_AC-12049 - [GitHub问题](https://github.com/magento/magento2/issues/38765) - [GitHub代码贡献](https://github.com/magento/magento2/commit/3b5ac075)_

#### 从购物车中移除礼品包装时未更新税额

当通过setGiftOptionsOnCart GraphQL突变删除礼品包装时，Magento现在可以正确更新购物车税总计。 以前，当选择了礼品包装选项并且传递“giftWrappingId”来取消设置时：在突变输入中为null，则不更新报价中的税额，并且Magento继续在购物车总计中包含礼品包装税，即使未应用礼品包装。

_AC-14637_

#### 迷你购物车中的商品显示外币价格而不进行换算

微型购物车现在可以正确兑换货币，并根据配置的兑换率显示准确的金额。

_ACP2E-4364 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1c547060)_

### 测试框架

#### [问题]从MFTF测试AdminSetUpWatermarkForSwatchImageTest中删除重复的&lt;severity>标记

现在，系统在AdminSetUpWatermarkForSwatchImageTest中仅包含一个严重性标记，从而提高代码清晰度和一致性。 以前，此测试包含两个相同的严重程度标记，这没有必要，并且可能会导致混淆。

_AC-11873 - [GitHub问题](https://github.com/magento/magento2/issues/38504) - [GitHub代码贡献](https://github.com/magento/magento2/pull/31862)_

#### [问题]忽略lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en...

系统现在会忽略运行单元测试时生成的“env.php”文件，从而确保git状态在运行测试后保持干净。 以前，运行单元测试会生成一个新文件“env.php”，导致git状态显示发现的新文件并使其显得脏兮兮的。

_AC-13293 - [GitHub问题](https://github.com/magento/magento2/issues/39304) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37631)_

#### [问题]修复侦听器的集成测试问题

系统现在可以在集成测试中正确识别并处理\Magento\TestFramework\App\Config\Interceptor ，从而确保测试可以访问必需的数据，即使存在类上的插件也是如此。 以前，系统无法考虑\Magento\TestFramework\App\Config成为\Magento\TestFramework\App\Config\Interceptor的可能性，导致在尝试访问$data属性时出错。

_AC-13305 - [GitHub问题](https://github.com/magento/magento2/issues/39324) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37187)_

#### [问题] MFTF：将电子邮件提交到已启用验证码的朋友表单

在启用CAPTCHA的情况下，测试案例将解决“Email to Friend”表单的功能，确保表单提交过程在验证码值不正确和正确的情况下正常工作。

_AC-13492 - [GitHub问题](https://github.com/magento/magento2/issues/39462) - [GitHub代码贡献](https://github.com/magento/magento2/pull/32830)_

#### [Cloud Native Service] CNS生成失败 — 2.4.9-beta1 — 集成

无可用描述。

_AC-16427_

#### 硬编码夹具路径在Composer构建中失败

无可用描述。

_AC-16488_

#### PR和编辑器内部版本之间的PHPUnit配置文件不匹配

无可用描述。

_AC-16501_

#### [问题] magento/magento2#： GraphQl突变。 客户storeConfig设置的附加测试范围。

系统现在为下一个客户storeConfig选项添加了额外的测试范围：
required_character_classes_number
minimum_password_length

_AC-9370 - [GitHub问题](https://github.com/magento/magento2/issues/37915) - [GitHub代码贡献](https://github.com/magento/magento2/pull/28761)_

#### AC 2.4.7-p3中特定于环境的单元测试失败

此问题修复了未在所有版本和环境上重现的单元测试故障。 以前，修复某些单元测试失败，原因是库版本不同或缺少在更高版本中添加的功能。

_ACP2E-3712 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9ad7d277)_

#### [单元测试] Magento\GiftCardImportExport\Test\Unit\Model\Import\Product\Type\GiftCardTest：：testIsRowValid

修复了随机失败单元测试

_ACP2E-4263_

### UI框架

#### [问题]从较少的文件中删除重复的变量

系统现在可以从较少的文件中删除重复的变量，确保代码更干净且更有效。 以前，这些重复的变量存在于较少的文件中，从而导致代码中出现不必要的冗余。

_AC-11743 - [GitHub问题](https://github.com/magento/magento2/issues/31154) - [GitHub代码贡献](https://github.com/magento/magento2/pull/31150)_

#### WYSIWYG在动态行中为空

动态行中的WYSIWYG字段现在已正确初始化和填充。
以前，动态行中的WYSIWYG字段（例如设计配置表单中的）可能会显示为空或在执行某些操作后丢失其内容，需要手动干预以恢复数据。
AC-12336

_AC-12336 - [GitHub问题](https://github.com/magento/magento2/issues/38893) - [GitHub代码贡献](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [问题]修复MIME类型拼写错误

系统可正确处理并修复gif图像的mime类型和打字错误

_AC-8001 - [GitHub问题](https://github.com/magento/magento2/issues/36899) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36669)_

#### [问题]从`@author`中删除禁止的`Magento_Backend`标记

此PR从代码库中移除`@author`标记

_AC-8814 - [GitHub问题](https://github.com/magento/magento2/issues/37522) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36976)_

#### [问题]避免直接访问审阅列表Ajax

系统可正确处理并避免直接访问审阅列表Ajax

_AC-9381 - [GitHub问题](https://github.com/magento/magento2/issues/37920) - [GitHub代码贡献](https://github.com/magento/magento2/pull/33876)_

#### 标头登录/注销在使用共享Cookie的多存储设置中未更新

注销时，登录标头会根据配置设置正确更新。 如果在全球共享客户帐户，customer-data.js将使用Cookie存储“mage-customer-login”值。 否则，将使用本地存储。

_ACP2E-4149 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e885088b)_

#### [Mobile] Fotorama可以在图像查看器关闭操作时打开迷你购物车

修复了Fotorama的问题。 以前，迷你购物车会在图像查看器的关闭操作中打开

_ACP2E-4231 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e885088b)_

#### 在包含许多存储的项目中，无法正确生成合并的js文件。

现在，当配置了多个存储区时，合并JavaScript文件可正常工作。
以前，文件在多存储设置中有时无法正确合并，导致结果不完整或不一致。

_ACP2E-4246 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ab891304)_

### 升级 — 升级兼容性工具

#### 已弃用的功能：创建动态属性Magento\Framework\Acl：：$_roleRegistry

已弃用的功能错误在升级后不再阻止访问管理员面板。
以前，升级到Magento 2.4.6后，尝试访问管理面板可能会导致以下错误：
“已弃用的功能：在vendor/magento/framework/Session/SessionManager.php第186行上已弃用创建动态属性Magento\Framework\Acl：：$_roleRegistry”
这会阻止管理员登录。
AC-12343

_AC-12343 - [GitHub问题](https://github.com/magento/magento2/issues/37469)_

#### GUID未保存为安全格式

无可用描述。

_AC-15809_

#### 升级兼容性工具，但存在错误的关键问题

不适用

_ACP2E-3856_
