---
source-git-commit: 1f377ab6e4dcdd2d350366f3889b8befd233474b
workflow-type: tm+mt
source-wordcount: '27924'
ht-degree: 0%

---
# Adobe Commerce修复了问题(v2.4.8)

## 修复了v2.4.8中的问题

我们已在Adobe Commerce 2.4.8核心代码中修复了581个问题。 此版本中包含的已修复问题的子集如下所述。

### API

#### /V1/事务REST API在parent_txn_id = txn_id时返回错误

现在，系统可正确处理父事务ID与事务ID相同的父概念事务和子概念事务，从而防止在查询/V1/事务REST API端点时发生无限循环。 以前，由于超出最大执行时间，此方案会导致致命错误。

_AC-10042 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1bafc571)_

#### 2.4.7中的[Graphql]类型问题

现在，系统在执行GraphQL查询时可正确处理GetCustomSelectedOptionAttributes函数中的整数值，从而防止出现任何与类型相关的错误。 以前，启动使用具有整数参数的GetCustomSelectedOptionAttributes的GraphQL查询会导致类型错误。

_AC-11878 - [GitHub问题](https://github.com/magento/magento2/issues/38662) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38663)_

#### 类别url_key中的特殊字符（通过REST API创建时）

以前的在category_url_key中，修复后特殊字符不在，它在category_url_key中显示特殊字符

_AC-3223 - [GitHub问题](https://github.com/magento/magento2/issues/35577) - [GitHub代码贡献](https://github.com/magento/magento2/commit/c699c206)_

#### 显示来自其他网站的订单的REST API。 

系统现在支持REST API管理员令牌和Magento_Sales端点的范围授权访问，确保REST API仅显示管理员有权访问的订单。 以前，REST API会显示所有网站的订单，而不管管理员用户分配的网站是什么。

_ACP2E-2703_

#### 启用2FA Duo后rest api出现问题

带双核安全性选项的2FA现在可为Rest API生成正确的签名

_ACP2E-2755 - [GitHub代码贡献](https://github.com/magento/security-package/commit/412fa642)_

#### [REST API]：为可配置产品添加配置后，在存储视图中使用默认值不会保持选中状态

通过确保非默认存储的可自定义选项的正确数据库条目，该问题已得到修复。 由于数据库条目不准确，因此以前在“管理员>目录>产品编辑>可自定义选项”部分中针对自定义商店的复选框处于未选中状态，即使自定义商店的选项标题与默认商店的标题保持相同也是如此。

_ACP2E-2927 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3056e9cb)_

#### 使用Oauth1时，REST API无法在SKU中使用斜杠(/)发出请求

在修复之前，您无法为SKU中具有“/”的产品成功进行API调用。 现在，即使其SKU中存在正斜杠，您仍可以成功发出API GET请求以获取产品详细信息。

_ACP2E-2969 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b21e5d91)_

#### 启用“validateDefaultAddress”后，通过REST API更新客户地址时失败

在解决API有效负载中缺少ID密钥的问题后，API端点现在可以按预期工作。

_ACP2E-3079 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9af794a4)_

#### [Cloud]在层价格Api中创建重复的网站组价格客户组。

现在，Tier Price Rest Api不允许创建重复的网站组价格客户组。
以前，可以在层价格Api中创建重复的网站组价格客户组，以免在产品保存期间通过管理员验证。

_ACP2E-3091 - [GitHub代码贡献](https://github.com/magento/magento2/commit/148c3ead)_

#### 无法通过REST API添加具有状态的订单评论

通过允许更改顺序状态（如果该状态仅来自当前状态），该问题已得到解决。 以前，它不会遵循订单状态并阻止任何订单状态中的更改，即使订单状态来自同一状态也是如此。

_ACP2E-3130 - [GitHub代码贡献](https://github.com/magento/magento2/commit/93d50f8d)_

#### 当有效负载中缺少SKU时，异步操作失败

以前，如果有效负载中缺少sku，则由于产品保存错误而导致异步和同步操作失败。 修复后，异步和同步产品保存rest api操作失败，并显示相关的异常消息。

_ACP2E-3236 - [GitHub代码贡献](https://github.com/magento/magento2/commit/66dea0de)_

#### [CLOUD]无法使用REST API更新基本价格（“catalog_product_entity_decimal”中“value_id”的值未正确递增。）

在此修复之前，调用rest api /rest/default/V1/products/base-prices时，增量id错误地增加，从而会在值之间留下间隙。 修复后，增量ID将按预期递增。 此外， value_id字段范围也增加了。

_ACP2E-3376 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d50f6b5d)_

#### 在API POST V1/order/:orderId/refute的贷项通知单电子邮件中看不到订单项目

以前，在本次修复之前，当客户通过通知send_email的API请求创建贷项通知单时，它不包含产品详细信息网格。 进行此修复后，客户发送了贷项通知单API请求，并将发现电子邮件中显示了产品项目详细信息。

_ACP2E-3460 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3f12d152)_

#### 产品RestAPI未设置日期和时间属性的默认值

现在，通过RestAPI为日期、日期和时间属性正确设置了默认值

_ACP2E-3486 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1984c61c)_

### API、购物车和结账

#### 严重500错误：Magento\Framework\Webapi\Exception与接受HTTP标头相关

修复后，指定“接受”标头没有任何问题。

_ACP2E-3343 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1366ae5e)_

### API， GraphQL

#### 没有可用于为客户订阅奖励点更新的graphQl

以前，无法通过GraphQL突变和Rest API调用更新客户属性reward_warning_notification。 现在可以像更新客户属性reward_update_notification一样进行更新。

_ACP2E-3348_

### API、GraphQL、税费

#### 仅提供邮政编码时，Luma (Rest API)和Graphql都不会计算税额。

现在，系统仅在提供邮政编码时正确计算税额，从而确保Luma (Rest API)和GraphQL的准确税务估计。 以前，只提供邮政编码时才会计算运费估计数，而不包括税款。

_AC-12060_

### 帐户

#### 客户地址表单允许名称字段中存在随机代码

现在，系统会验证客户地址表单中“名字”和“姓氏”字段的输入，防止使用随机代码。 以前，系统允许在这些字段中使用随机代码，而不会引发错误。

_AC-10782 - [GitHub问题](https://github.com/magento/magento2/issues/38331) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38345)_

#### 管理员密码更新。

_AC-10886 - [GitHub问题](https://github.com/magento/magento2/issues/38352) - [GitHub代码贡献](https://github.com/magento/magento2/commit/4bca5dfe)_

#### 保存时我的帐户添加地址崩溃

现在，即使未显示“区域”字段，系统也能正确保存客户地址，从而防止在保存过程中崩溃。 以前，尝试添加或编辑没有显示区域字段的地址会导致异常错误。

_AC-10990 - [GitHub问题](https://github.com/magento/magento2/issues/38406) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38407)_

#### URL大写时的重定向循环

现在，系统会自动将URL中的大写字符转换为小写，以防止在访问主页时出现重定向循环。 以前，如果安全基础URL中包含大写字符，则在尝试访问主页时会引发连续的重定向循环。

_AC-11718 - [GitHub问题](https://github.com/magento/magento2/issues/38538) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38539)_

#### 没有为来宾帐户保存middlename(&#39;s)

系统现在会在结账时正确保存访客帐户的中间名，使其可在电子邮件模板中访问。 以前，中间名未保存在报价表中，并且无法在来宾帐户的电子邮件模板中访问。

_AC-11755 - [GitHub问题](https://github.com/magento/magento2/issues/38593) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39067)_

#### 管理员：页面操作按钮向左浮动而不是向右浮动

现在，系统可正确地将页面操作按钮与管理面板中粘性标题的右侧对齐，从而增强专业外观。 以前，这些按钮错误地浮动到粘性标题的左侧。

_AC-11919 - [GitHub问题](https://github.com/magento/magento2/issues/38701) - [GitHub代码贡献](https://github.com/magento/magento2/commit/44cef3a9)_

#### magento 2.4.7中的`dev:di:info`错误

现在，系统在执行`dev:di:info`命令时可正确显示构造函数参数，从而防止出现任何错误。 以前，执行此命令会导致错误，因为参数中的类型不匹配。

_AC-11999 - [GitHub问题](https://github.com/magento/magento2/issues/38740) - [GitHub代码贡献](https://github.com/magento/magento2/commit/0c53bbf7)_

#### “以客户选择加入身份登录”复选框不可翻译

现在，系统允许在“商店视图”范围中设置“以客户身份登录选择加入复选框”和“以客户身份登录复选框工具提示”字段，从而为不同的商店视图启用翻译。 以前，这些字段仅在“网站”范围中设置，导致无法翻译各个商店视图。

_AC-13000 - [GitHub问题](https://github.com/magento/magento2/issues/32329) - [GitHub代码贡献](https://github.com/magento/magento2/pull/32359)_

#### 我的个人资料下拉列表中的前端UI主页按钮不存在。（间歇性）

_AC-14299_

#### 客户已登录，但在前端显示404错误。

现在，当客户登录时，店面客户仪表板页面会按预期加载。 以前，客户可以登录，但此页面显示404错误。 [GitHub-35838](https://github.com/magento/magento2/issues/35838)

_AC-6071 - [GitHub问题](https://github.com/magento/magento2/issues/35838) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36263)_

#### 无法在管理员编辑客户部分中保存客户属性信息；

现在，可以按照管理员客户编辑表单的网站范围，正确实施客户的商店ID。

_ACP2E-2791 - [GitHub代码贡献](https://github.com/magento/magento2/commit/488c1034)_

#### [Cloud]启用私有销售时，无法通过API创建客户

现在，在启用了网站限制的情况下，客户既可以通过经过身份验证的管理员用户创建，也可以通过REST API使用经过身份验证的集成令牌创建。

_ACP2E-3115_

#### 登录后，无法显示以访客用户身份添加到比较列表的产品。

现在，以客户身份登录之前添加到产品比较列表中的产品在登录之后将被保留。
以前，在登录后，以访客用户身份添加到比较列表的产品不可见。

_ACP2E-3329 - [GitHub代码贡献](https://github.com/magento/magento2/commit/078c387e)_

#### 允许国家/地区配置导致客户地址配置中出现问题

现在，选择“允许国家/地区”配置不会影响为给定范围之外显示的国家/地区。 以前，允许国家/地区配置会影响给定范围之外的客户地址属性

_ACP2E-3433 - [GitHub代码贡献](https://github.com/magento/magento2/commit/078c387e)_

#### 共享礼品注册表将事件日期显示为1天之前的日期

现在，店面上正确显示了礼品注册日期

_ACP2E-3445_

#### VAPT：业务逻辑错误 — 将来日期作为客户出生日期

客户的出生日期不能晚于今天

_ACP2E-3501 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d4de4726)_

### 帐户、API、GraphQL

#### 客户API — 成功登录后登录失败次数无法重置为0

现在，客户通过API端点成功登录后，客户实体表中的故障数量将重置为零。

_ACP2E-3246 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ec7e32a9)_

### 帐户、管理员UI、B2B

#### 受限管理员用户无法始终查看自定义共享目录

受限管理员用户现在可以始终查看和管理客户以及为其分配产品的所有共享目录，前提是他们有权访问特定商店。 以前，具有特定商店访问权限的受限管理员用户无法始终查看分配给产品的所有共享目录，或者无法查看客户，从而导致系统中出现不一致的情况。

_ACP2E-3038 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7377de59)_

### 帐户、购物车和结帐

#### 对于新客户地址，“select”自定义客户地址属性不会呈现

_AC-2341 - [GitHub问题](https://github.com/magento/magento2/issues/34950)_

### 管理员UI

#### [问题]针对“重新加载数据”数据按钮的添加权限检查

现在，系统包含对“重新加载数据”按钮的权限检查，以确保该数据仅向具有相应权限的用户显示和访问。 以前，“重新加载数据”按钮对所有用户可见和可点击，导致在没有必要权限的用户单击时出现“不允许”页面。

_AC-10705 - [GitHub问题](https://github.com/magento/magento2/issues/38283) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38279)_

#### [问题]营销规则中属性的标签不一致

系统现在可以正确填充购物车价格规则中类别和属性选项的标签

_AC-11427 - [GitHub问题](https://github.com/magento/magento2/issues/31232) - [GitHub代码贡献](https://github.com/magento/magento2/pull/31231)_

#### 在导入具有替换行为的产品期间，数据验证成功且存在导入按钮

现在，系统可正确验证数据，并在产品导入过程中使用“替换”行为隐藏“导入”按钮，从而防止任何意外的数据替换。 以前，系统会错误地验证数据并显示“导入”按钮，从而导致潜在的数据不一致。

_AC-11588 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0574ac23)_

#### [错误] Magento 2.4.7不允许使用大写字母文件扩展名的产品照片。

现在，系统接受使用大写字母文件扩展名的产品图像上传，以确保平稳的产品创建过程。 以前，使用大写字母文件扩展名的图像上传被拒绝，从而迫使用户将文件扩展名更改为小写。

_AC-12167 - [GitHub问题](https://github.com/magento/magento2/issues/38831) - [GitHub代码贡献](https://github.com/magento/magento2/commit/c8f87c25)_

#### 具有选择操作的网格中的隐藏下拉列表（例如“内容”>“元素”>“页面”）

现在，系统已修复所有网格的所有类似下拉菜单。

_AC-12319 - [GitHub问题](https://github.com/magento/magento2/issues/38891) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39371)_

#### [问题]修复警告：未定义数组键“筛选器”

系统现在可处理新用户尚未与书签进行交互的情况，从而防止记录未定义的数组键“过滤器”警告。 以前，当新用户未与书签交互时，将记录此警告。

_AC-13131 - [GitHub问题](https://github.com/magento/magento2/issues/39013) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38996)_

#### 由于Validate.php文件中的代码更改，产品导入带有特殊字符的csv文件失败

现在，系统可正确验证和导入包含特殊字符的产品CSV文件，从而允许成功传输数据。 以前，尝试导入包含特殊字符的产品CSV文件会导致错误，从而阻止导入过程。

_AC-13529 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### 当“密码重置请求的最大数量”设置大于0时，例如： 3 ，“超过限制错误消息，在达到限制之前发送，即从第二次开始

_AC-13767_

#### 虽然“密码重置请求的最大数量”设置为0（已禁用） ，但“从第2次发送超过限制的错误消息”

_AC-13768_

#### 必填电话号码字段没有红色星号

早期的红色星号未显示电话号码，但是  电话号码为必填项。 现在修复的红色星号可在电话号码上显示为必填字段。

_AC-13850 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c699c206)_

#### 在管理员中，当我们尝试重新排序时，提交订单按钮不可单击。 （间歇性）

_AC-14300_

#### [问题]将默认索引器模式设置为“计划”

默认情况下，所有新索引器都处于&#x200B;**[!UICONTROL Update by Schedule]**&#x200B;模式。  以前，默认模式为&#x200B;**[!UICONTROL Update on Save]**。 现有的索引器不受影响。 [GitHub-36419](https://github.com/magento/magento2/issues/36419)

_AC-6975 - [GitHub问题](https://github.com/magento/magento2/issues/36419) - [GitHub代码贡献](https://github.com/magento/magento2/commit/0b410856)_

#### [问题]在mview取消订阅时删除索引器更改日志表

现在，当索引从“按计划更新”切换到“保存时更新”时，系统自动删除未使用的更改日志表，将索引标记为无效，以确保没有丢失任何条目。 以前，将索引切换为“保存时更新”会在系统中保留未使用的changelog表，并将所有更改的索引标记为“有效”。

_AC-7700 - [GitHub问题](https://github.com/magento/magento2/issues/29789) - [GitHub代码贡献](https://github.com/magento/magento2/pull/25859)_

#### 在手机视图中签出付款时没有指向送货的链接

系统现在确保签出标题/链接“Shipping”和“Review &amp; Payments”在移动视图的页面顶部始终可见，从而使用户能够在各个步骤之间轻松导航并进行必要的更正。 以前，这些标题/链接在移动视图中隐藏，使用户难以了解其当前步骤或返回之前的步骤。

_AC-7962 - [GitHub问题](https://github.com/magento/magento2/issues/36856) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36982)_

#### 客户订单查询装运注释created_at在+0时区中返回，不在商店配置的时区中

使用客户订单查询时，系统现在可以正确显示客户配置时区中发运注释的“created_at”字段。 以前，“created_at”字段以+0时区显示，无论客户配置的时区如何。

_AC-8109 - [GitHub问题](https://github.com/magento/magento2/issues/36947) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37642)_

#### i18n:collect-phrases破坏了翻译完整性

`bin/magento i18n:collect-phrases -o`命令现在可以从JavaScript和.phtml文件中正确收集和添加新短语，确保翻译文件能够准确反映翻译。 以前，系统无法在翻译文件中包含来自JavaScript文件的多行翻译短语以及来自.phtml文件的短语，从而导致翻译不完整或不正确。

_AC-9843 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0c53bbf7)_

#### 访问动态块的权限问题

以前，对于受限管理员，添加新的动态块会引发错误。 实施此修复后，受限制的管理员可以成功添加动态块，并在没有任何错误的情况下编辑块

_ACP2E-2687_

#### 存储视图名称中的撇号将替换为&amp;#039；

网格的存储视图过滤器现在可正确显示撇号

_ACP2E-2787 - [GitHub问题](https://github.com/magento/magento2/issues/38395) - [GitHub代码贡献](https://github.com/magento/magento2/commit/39d54c2d)_

#### Favicon上传无法验证.ico文件

文件验证错误已更新为“文件验证失败。 请验证存储配置中的图像处理设置。” 以前，它只是“文件验证失败”。

_ACP2E-2847 - [GitHub代码贡献](https://github.com/magento/magento2/commit/39d54c2d)_

#### PageBuilder中的图库显示的是旧图像缩略图而不是新上传的图像

为通过页面生成器内容中的媒体集删除并重新上传的同名图像重新生成图像预览。

_ACP2E-2957 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/60140cd2) - [GitHub代码贡献](https://github.com/magento/magento2/commit/001e5188)_

#### 由具有不同角色范围的管理员用户保存产品将覆盖/删除产品中现有的相关产品信息

以前，在修复之前，如果辅助管理员用户单击保存按钮时相关产品未更改相关产品，则相关产品会重置并变空。 进行此修复后，辅助管理员用户单击“保存”按钮，产品未重置且保存成功。

_ACP2E-2978 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3056e9cb)_

#### 无法导出200个以上的订单

已忽略先前提交的选定ID的请求大小的服务器限制，方法是将GET中的HTTP请求更改为POST以修复此问题。 以前，由于GET请求大小的服务器限制，遇到问题。

_ACP2E-3033 - [GitHub代码贡献](https://github.com/magento/magento2/commit/93d50f8d)_

#### 签出页面验证消息不正确。

如果有任何必填字段留空（如“address”），则服务器端验证不会显示消息。 客户端验证将确保显示必填字段错误通知，说明“这是必填字段”。 以前，如果任何必填字段留空，除了客户端验证消息之外，还会显示“地址为必填项”消息。

_ACP2E-3037 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9af794a4)_

#### 管理员用户的密码重置模板问题

该问题已通过使用正确的密钥得到解决，密钥现在包括电子邮件模板中的管理员用户名，并正确填写了主题。 以前，问题源自正在使用的过时键。

_ACP2E-3125 - [GitHub代码贡献](https://github.com/magento/magento2/commit/93d50f8d)_

#### 客户区段URL中的双斜杠

在网格中单击“重置筛选器”时，URL中不会出现双斜杠。

_ACP2E-3149 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8459b17d)_

#### COD不适用于允许的特定国家/地区

现在，特定国家/地区在需要时可以使用“货到付款”，并且   AC-3216按预期工作。

_ACP2E-3171 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6f4805f8)_

#### 无法更新自定义创建的订单状态

“我们现在可以更新自定义创建的订单状态，而以前，仅当当前状态为”正在处理“或”欺诈“时，才能更改状态。”

_ACP2E-3178 - [GitHub问题](https://github.com/magento/magento2/issues/38659) - [GitHub代码贡献](https://github.com/magento/magento2/commit/8459b17d)_

#### 配送地址状态未自动更新

在修复之前，送货地址区域（或区域ID）与地址帐单信息不同步。 现在，当帐单地址信息更改时，送货地址区域和区域ID都会正确更新。

_ACP2E-3294 - [GitHub代码贡献](https://github.com/magento/magento2/commit/581b7ef1)_

#### 重置按钮对添加/编辑管理员用户不起作用

以前，重置按钮在添加/编辑管理员用户页面上不起作用。 现在，在“管理员”面板中“系统” — >“权限” — >“所有用户”下，“重置”按钮将在“添加/编辑管理员用户”页面上正常工作。

_ACP2E-3364 - [GitHub代码贡献](https://github.com/magento/magento2/commit/5184c067)_

#### Magento管理员URL路由错误检测和CORS错误

修复后，如果自定义管理域是主域的子域，则只能从配置的子域访问管理员。

_ACP2E-3373 - [GitHub问题](https://github.com/magento/magento2/issues/37663) - [GitHub代码贡献](https://github.com/magento/magento2/commit/3f12d152)_

#### “购物车中允许的最大数量”的验证已损坏

以前，当我们将`Maximum Qty Allowed in Shopping Cart`设置为空时，它不会引发任何异常，尽管此处不接受空值。 进行此修复后，输入空字符串将会引发异常，并且不允许保存产品。

_ACP2E-3392 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d50f6b5d)_

#### [Pagebuilder预览UI问题]“页面生成器”列中的按钮未正确对齐

页面生成器列中的按钮现在正确对齐。 以前，它们在页面生成器列中不会对齐。

_ACP2E-3408 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/1a52ef4c)_

#### 未导出订购的产品报表。 而是404错误。

产品订购报表导出为CSV和XML的流程现在按预期运行

_ACP2E-3431 - [GitHub代码贡献](https://github.com/magento/magento2/commit/88660e79)_

#### 在生产模式下启用Js缩小后，控制台中出现TinyMCE JS错误

以前，在“管理”面板的生产模式下启用JavaScript缩小功能会导致浏览器控制台中出现与TinyMCE 6相关的JavaScript错误，从而影响功能和用户体验。 现在，此问题已得到解决，从而确保TinyMCE 6平稳运行，不会生成任何错误，即使启用了JS缩小也是如此。

_ACP2E-3457 - [GitHub代码贡献](https://github.com/magento/magento2/commit/56463d5e)_

#### 请求其他更改以完全完成ACP2E-3375修复

&#39;-

_ACP2E-3459 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d50f6b5d)_

#### 自动启用新ACL权限

除非明确配置，否则添加到自定义模块的新权限将不再自动授予对所有现有用户角色的访问权限。

_ACP2E-3503 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3f12d152)_

#### 管理员操作日志用户报告没有显示管理员html_user_delete的详细信息

adminhtml_user_delete现在可正确记录重要详细信息。 以前，不会为用户删除生成日志。

_ACP2E-3509 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4de008a9)_

#### 从管理员下订单时，带有配送条件的购物车规则不适用

以前，如果购物车价格规则具有带有优惠券的配送方式折扣，则无法通过管理员UI应用该规则。 应用此修复后，将从Admin UI成功应用带有特定配送方式优惠券的购物车价格规则折扣。

_ACP2E-3536 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a52ff98f) - [GitHub代码贡献](https://github.com/magento/inventory/commit/11ce816b)_

#### [FRESH]十六进制代码未在样本中正确更新

用户在可视样本拾色器中手动输入的十六进制代码不再由系统更改。 以前，某些十六进制代码会因颜色模型之间的转换错误而稍有调整。

_ACP2E-3559 - [GitHub代码贡献](https://github.com/magento/magento2/commit/344fce23) - [GitHub代码贡献](https://github.com/magento/inventory/commit/1ef984c0)_

### 管理员UI，B2B

#### 作为客户标题的B2B登录仍具有Magento品牌

早些时候，店面标题显示“您现在作为&lt;store name>上的&lt;customer name>连接”与Magento品牌化。 现已修复，并且标题会显示为ADOBE品牌。

_AC-13628 - [GitHub代码贡献](https://github.com/magento/magento2/commit/96dec499)_

### 管理员UI，目录

#### 无法作为受限管理员用户更改允许网站中类别产品的位置

允许受限管理员用户在受限网站下分配的根类别所包含的类别下添加和排序产品。

_ACP2E-2708_

### 管理员UI、支付/支付方式、订单

#### 按PayPal智能按钮排序后，交易授权未显示在“交易”选项卡中

使用PayPal智能按钮下达订单后，系统现在会在“交易”选项卡中正确显示交易授权。 以前，单击“授权”按钮后，授权交易未显示在Transaction选项卡中，并且未创建“授权”类型的新交易。

_AC-13520 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6cfb9b6b)_

### 管理员UI，性能

#### 更新至2.4.5之后，从admin创建订单时出现500错误

以前，在启用HTML缩小功能时，无法下达管理员的订单。 现在，启用HTML缩小功能后，管理员的订单就可以成功下达。

_ACP2E-3169 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b21e5d91)_

### 管理员UI，配送

#### 优惠券代码计数不会在   如果订单是多次发运的，则“管理优惠券代码”选项卡中的“已用时间”列。

以前，在多次发运订单时，在“管理优惠券代码”选项卡的“使用时间”列中，优惠券代码计数不会更新。 现在，正确计数会同时显示在“使用时间”中，以反映多次配送的所需值。

_ACP2E-2519 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4745100c)_

### 管理UI、暂存和预览

#### [Cloud]删除缺少映像的模板会导致发布/媒体被删除

以前，在本修复中，如果pagebuilder模板缺少预览图像名称，则会删除pub/media文件夹。 修复后，将仅删除模板和预览图像（如果找到）。

_ACP2E-3424 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/0986853b)_

### Analytics/报表

#### Google Analytics CSP错误https://region1.analytics.google.com

启用Google Analytics后，系统现在可正确连接到“https://region1.analytics.google.com&#39;”，从而防止出现内容安全策略(CSP)错误。 以前，由于拒绝连接到“https://region1.analytics.google.com&#39;”，因此启用Google Analytics并从欧盟查看网站会导致CSP控制台错误。

_AC-9922 - [GitHub问题](https://github.com/magento/magento2/issues/37750) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38991)_

#### 提前报告不起作用

现在，系统支持通过以10,000个批次加载和编写报表，为超大型数据集生成高级报表数据文件。 以前，高级报告模块无法为超大型数据集生成数据文件，导致在执行analytics_collect_data cron作业期间出现“MySQL服务器已消失”错误。

_ACP2E-2570 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a12063bd)_

#### 管理员订购产品报表日期范围可见性问题。

用户将从订购的产品报表中选择任意日期。 以前，在刷新表后，选择“起始”日期将重置“截止”日期。

_ACP2E-3080 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6f4805f8)_

#### Curl标头不正确，导致`newrelic:create:deploy-marker`无法正常工作

系统现在可以正确设置curl标头的格式，从而允许`newrelic:create:deploy-marker`命令在New Relic中成功创建部署标记。 以前，错误的curl标头会阻止在New Relic中创建部署标记。

_ACP2E-3096 - [GitHub问题](https://github.com/magento/magento2/issues/37641) - [GitHub代码贡献](https://github.com/magento/magento2/commit/6a185204)_

#### 对于具有自定义选项的可配置产品，GTM在dataLayer中缺少addToCart事件

以前，不会为可配置产品触发addToCart事件。 现在，事件已正确添加到GTM dataLayer变量中。

_ACP2E-3146_

#### NewRelic浏览器监控内联JS脚本导致CSP错误

NewRelic浏览器监控脚本现在由应用程序而不是APM代理插入，以符合CSP（内容安全策略）。 以前，由APM代理插入的NewRelic浏览器监控脚本与CSP不兼容，并导致脚本无法执行。

_ACP2E-3183 - [GitHub代码贡献](https://github.com/magento/magento2/commit/66dea0de)_

#### 对销售订单量大的项目上的sales_bestsellers_aggregated_daily表的INSERT查询变慢

以前，对于大量下订单，汇总的畅销商品每日报表需要花费大量时间才能生成。 现在，报告已及时生成。

_ACP2E-3189 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7377de59)_

#### 订单报表显示错误的货币符号

订单报表中订单金额的货币符号错误地取自currency/options/base。 现已更正为使用“货币”/“选项”/“默认”报表，以便进行准确的报告。

_ACP2E-3276 - [GitHub代码贡献](https://github.com/magento/magento2/commit/fd5cf3af)_

#### 优惠券使用情况报告中的[云]计算不正确

现在，通过合并“折扣税收补偿金额”和“装运折扣税收补偿金额”，可以准确计算优惠券报表网格中的销售总计。 以前，计算中缺少这些金额，导致销售总额与销售订单数据之间存在差异。

_ACP2E-3302 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d75cff27)_

#### 共享“&lt;project_id>/var/tmp”时出现问题

Analytics DataExport临时文件将使用sys tmp目录，该目录更适合频繁访问和更改。 为了避免在同一服务器上运行多个实例时发生冲突，更新了tmp路径以使用实例的唯一id

_ACP2E-3339 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a4cf5e62)_

### Analytics/报表，B2B

#### B2B - Sitemap包括未分配给共享目录的产品/类别

将Sitemap生成的类别和产品限制为仅分配给公共共享目录和/或目录类别权限设置的类别和产品。

_ACP2E-2300 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ea79f7dd)_

### Analytics/报表、云

#### Magento舍弃了大部分New Relic cron交易#34108

AC正在向NewRelic正确报告cron作业相关事务。 以前，某些cron作业相关事务在NR中显示为“OtherTransaction/Action/unknown”

_ACP2E-3067 - [GitHub代码贡献](https://github.com/magento/magento2/commit/35b1b1da)_

#### NR中的量度可能对后台事务产生误导性 — ACP2E-3067的跟进

后台事务(cron)将使用配置设置中定义的New Relic应用程序名称

_ACP2E-3187 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ec7e32a9)_

### B2B

#### 2.4.8-beta102 package Enterprise edition失败，出现应用程序异常

_AC-13501_

#### 执行部分索引时，分配给共享目录的产品不会反映在前端

现在，在完成部分索引后，通过REST API分配到共享目录的产品会立即在店面中可见。 以前，产品仅在完全重新索引后可见。

_ACP2E-2139 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7377de59)_

#### 移动版和桌面版中的[云]价格显示方式与“我的报价”中的不同

当目录总价部分已用时，不需要的包括税行不再显示在可转让报价中。

_ACP2E-2873_

#### 我的订单部分中存在不必要的边框

以前，创建了一个附加容器（订单引用），该容器应用了附加的CSS类，这会导致“我的订单”部分中的订单编号下方出现不必要的边框行，而现在该订单编号不可见。

_ACP2E-3044 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9af794a4)_

#### sales_clean_quotes cron会从尚未批准的采购订单中删除报价

sales_clean_quotes cron作业不会删除采购订单中现在使用的报价

_ACP2E-3247 - [GitHub代码贡献](https://github.com/magento/magento2/commit/581b7ef1)_

#### 采购订单详细信息中的“下单”按钮消失

修复了在产品变体指定的卡中最小数量时为批准的采购订单隐藏“下单”按钮的问题

_ACP2E-3465_

#### [CLOUD]没有ID = 0且带有b2b模块的此类实体

启用共享目录功能后，登录用户能够将产品添加到购物车。
之前将产品添加到购物车会导致“无ID = 0的此类实体”错误

_ACP2E-3474_

#### 从申请列表批量添加时，库存产品的未显示错误消息

在修复之前，无论未能添加到购物车的产品数量如何，都会显示成功消息。 现在，将为成功添加到购物车的产品和失败的产品显示单独的消息。

_ACP2E-3562_

#### 在计划更新后进行SKU更新时出现问题，导致产品权限不正确（–2拒绝）

通过过去的计划更新修改产品的SKU不会再导致有权查看产品的共享目录客户无法访问产品。

_ACP2E-3628_

### B2B，目录

#### 使用NoDDL和类别权限时索引期间可见的产品/类别

在执行目录权限索引时，避免在店面中显示受限制的类别及其内容。

_ACP2E-2860_

### B2B，框架

#### 筛选公司网格，然后尝试导出网格CSV将失败，并引发异常

现在，即使应用了“未付余额”和“公司类型”等过滤器，系统仍允许成功以CSV格式导出管理面板中的公司网格数据。 以前，应用某些过滤器并尝试导出网格数据会导致失败并引发异常。

_AC-9607 - [GitHub代码贡献](https://github.com/magento/magento2/commit/44cef3a9)_

### B2B，GraphQL

#### [云]通过graphql调用创建公司时无法设置custom_attributes

修复后，可在使用graphql请求创建公司期间为公司管理员设置“custom_attributes”属性。

_ACP2E-3391_

### Braintree

#### Admin Express签出按钮已禁用。

_AC-14293_

#### 通过LPM付款

现在，即使登录客户的送货地址和账单地址不匹配，系统在首次加载时也可以正确呈现本地支付方法(LPM)，从而确保顺利的结账过程。 以前，客户的送货地址和账单地址不匹配会导致LPM无法呈现，进而在结账期间导致潜在中断。

_BUNDLE-3367_

#### 可使用Virtual as Child产品进行配置

该系统现在允许对具有虚拟子产品的可配置产品使用快捷的支付方法，确保顺利的结账过程。 以前，当将带有虚拟子产品的可配置产品添加到购物车时，快速付款方法不可用。

_BUNDLE-3368_

#### CVV验证失败错误

_BUNDLE-3369_

#### 通过帐户区域进行保险存储问题247

该系统现在允许客户跨多个网站保存新卡或PayPal帐户信息，而不会遇到授权错误。 以前，客户无法跨不同网站保存新的支付方式，并收到授权错误消息。

_BUNDLE-3370_

#### 从另一个国家/地区发送到地址

现在，该系统允许在将交易从其他国家发送到某个地址时无错误地进行处理，从而确保顺利的结账过程。 以前，尝试从其他国家/地区发送地址会导致控制台错误，尽管前端没有明显错误。

_BUNDLE-3371_

#### 信用卡 — Teardown功能

现在，当客户从付款页面导航回送货页面时，系统可正确处理Braintree PayPal组件的拆卸过程，从而防止任何错误并确保PayPal Express按钮正确呈现。 以前，在尝试拆卸Braintree PayPal组件时，从付款页面导航回送货页面有时会导致错误。

_BUNDLE-3372_

#### PayPal Express回拨运费

现在，系统可在PayPal Express模式中正确显示可用的配送方式，允许客户在继续查看页面或完成其交易之前选择其首选配送方式。 以前，在PayPal Express模式中无法选择配送方式，这要求客户在完成交易之前，在单独的审核页面上选择配送方式。

_BUNDLE-3373_

### 捆绑

#### 店面捆绑包复选框验证错误消息计数大于1

现在，单击“添加到购物车”按钮时，系统只显示一条验证错误消息，而未选择捆绑产品的任何复选框选项。 以前，系统会为每个未选复选框显示多个验证错误消息。

_AC-10826 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3ea26621)_

#### 在某些与顺序相关的测试用例中抛出Magento异常

现在，系统可以在各种测试用例中正确处理“sendGuestPaymentInformation”步骤，从而防止引发Magento异常。 以前，这些例外是由于空的支付方法而发生的，导致在几种测试情况下发生故障。

_AC-13321_

### 购物车和结帐

#### 在比较产品页面中将产品添加到购物车时未正确处理异常

现在，当从比较产品页面将产品添加到购物车时，系统可正确处理异常，并在控制器中显示消息管理器消息。 以前，异常会导致返回JSON编码页面，而不是正确捕获和处理该页面。

_AC-10660 - [GitHub问题](https://github.com/magento/magento2/issues/38200) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38257) - [GitHub代码贡献](https://github.com/magento/magento2/commit/0c53bbf7)_

#### GTag不发送交易价格和总计。

现在，在启用GTag的情况下，系统可正确地向Google Tag发送交易价格和总计，从而确保对电子商务数据的准确跟踪。 以前，该货币作为“所有”订单的一部分错误地发送，而不是与单个订单相关联。

_AC-10698 - [GitHub问题](https://github.com/magento/magento2/issues/37348) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37504) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37349)_

#### [问题] [签出] Depend指令已在失败的付款电子邮件模板中更新

系统现在可以从虚拟产品的失败付款电子邮件模板中正确忽略送货地址和送货方法，确保电子邮件中仅包含相关信息。 以前，虚拟产品付款失败的电子邮件错误地包含送货地址和送货方法。

_AC-11641 - [GitHub问题](https://github.com/magento/magento2/issues/32781) - [GitHub代码贡献](https://github.com/magento/magento2/pull/32511)_

#### Magento 2与现有客户一起在签出内登录时，在Firefox浏览器中引发控制台错误

现在，系统允许用户在结账过程中登录，而不会在Firefox浏览器中遇到任何控制台错误。 以前，在签出期间尝试以现有客户身份登录会导致Firefox中出现控制台错误。

_AC-11717 - [GitHub问题](https://github.com/magento/magento2/issues/38557) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39509)_

#### [问题] 2.4.7中的销售规则回归

系统现在可以正确验证销售规则，防止在产品条件与任何产品名称不匹配时将优惠券代码应用到购物车。 以前，即使产品条件与任何产品名称不匹配，也可以应用销售规则并根据运费金额提供折扣。

_AC-11876 - [GitHub问题](https://github.com/magento/magento2/issues/38671) - [GitHub代码贡献](https://github.com/magento/magento2/commit/0574ac23)_

#### [问题]销售规则CartFixed计算：折扣金额不正确

现在，系统可正确计算具有购物车固定金额的销售规则的折扣金额，从而确保无论购物车项目如何变化，均会应用准确的折扣。 以前，当购物车项目更改时，折扣金额可能会错误地变化，有时会导致折扣显着高于预期。

_AC-11914 - [GitHub问题](https://github.com/magento/magento2/issues/38694) - [GitHub代码贡献](https://github.com/magento/magento2/commit/581b7ef1)_

#### [问题]更改邮政编码后，加载程序将阻止装运方法，装运费率验证规则

系统现在可以正确处理自定义发运方法，而无需使用运费验证规则，从而确保在结帐期间更改发运地址中的邮编后，加载程序不会阻止发运方法。 以前，在结帐期间更改装运地址中的邮政编码会导致加载程序阻止装运方法，并且在使用没有装运费率验证规则的自定义装运方法时不会消失。

_AC-11993 - [GitHub问题](https://github.com/magento/magento2/issues/38742) - [GitHub代码贡献](https://github.com/magento/magento2/commit/1bafc571)_

#### 优惠券代码功能在Magento 2.4.7上的签出页面中无法正常工作

系统现在为虚拟和可下载产品在结账页面上启用折扣代码/优惠券输入字段，使用户能够按预期应用折扣代码。 以前，折扣代码/优惠券输入被禁用，并且按钮标题文本显示为“取消优惠券”，阻止用户应用折扣代码。

_AC-12170 - [GitHub问题](https://github.com/magento/magento2/issues/38826) - [GitHub代码贡献](https://github.com/magento/magento2/commit/1bafc571)_

#### 条款和条件复选框不允许店面上的HTML

现在，系统支持店面的“条款和条件”复选框文本中包含HTML格式，从而增强了自定义和可读性。 以前，复选框文本以纯文本格式显示，忽略使用的任何HTML标记。

_AC-12479 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### 为已登录用户创建的购物车价格规则错误地应用于未登录用户

现在，当登录用户由于Cookie过期而被自动注销时，系统可正确删除购物车价格规则，从而确保折扣不会应用到非登录用户。 以前，即使用户已注销，购物车价格规则仍会应用，从而导致将错误的折扣应用于非登录用户。

_AC-12541 - [GitHub问题](https://github.com/magento/magento2/issues/38944) - [GitHub代码贡献](https://github.com/magento/magento2/commit/7d5e3906)_

#### [问题] [功能]通过阻止……

该系统现在通过防止重复的getActions调用、提高购物车操作的速度和效率来优化大型购物车的性能。 以前，对于包含多个项目的购物车，会多次调用getActions函数，这会降低系统的性能。

_AC-13302 - [GitHub问题](https://github.com/magento/magento2/issues/39292) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39290)_

#### 礼品注册产品显示不正确

_AC-13797_

#### 礼品注册产品显示不正确

_AC-13841_

#### 地址渲染器中的翻译VAT

系统现在允许在地址呈现器中翻译文本“VAT”、“T”、“F”，从而使用户能够将这些术语翻译为商店的特定语言。 以前，这些术语无法翻译，因此用户必须采用解决方法。

_AC-8103 - [GitHub问题](https://github.com/magento/magento2/issues/36942) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36943)_

#### 具有相同报价ID的重复订单同时存在很少的时间差异

修复了Adobe Commerce客户在使用同一QuoteID下重复订单时的问题

_ACP2E-2055 - [GitHub代码贡献](https://github.com/magento/magento2/commit/f89a447e)_

#### 永久购物车在结账步骤中清除

修复后，在未登录时结账期间选择支付方式不会终止永久会话。

_ACP2E-2470 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a4fbf702)_

#### 重新排序将未分配的产品添加到购物车

以前，对于不同的商店，可以从其他商店对产品重新排序。 仅应用此修复后，在启用客户帐户共享时，可对同一范围产品重新排序

_ACP2E-2518 - [GitHub代码贡献](https://github.com/magento/magento2/commit/f89a447e)_

#### 在admin中，选择项目时左侧的“购物车”和右侧的“移至购物车”不会更新

选择项目时，左侧的“购物车”将会更新，并且管理员右侧的“移至购物车”也会更新。 以前，此功能不起作用，因为转换后的购物车项目不会从会话中清空。

_ACP2E-2620 - [GitHub代码贡献](https://github.com/magento/magento2/commit/39d54c2d)_

#### [Cloud]销售规则未应用于第一笔多送货订单

修复之后，将正确显示同一多发运报价的每张订单的折扣。

_ACP2E-2646 - [GitHub代码贡献](https://github.com/magento/magento2/commit/f89a447e)_

#### 将相同产品添加到购物车的[云]生产并行请求在购物车REST API中生成两个不同的项目

现在，系统可正确处理多个并行请求，以将同一产品添加到购物车中，并成为单个行项目，从而防止为同一SKU创建单独的行项目。 以前，并行请求通过REST API将同一产品添加到购物车会导致同一SKU出现多个行项目。

_ACP2E-2664 - [GitHub代码贡献](https://github.com/magento/magento2/commit/f89a447e)_

#### 从礼品注册表Magento 2.4.4 Enterprise/Commerce订购时出现问题

已解决无法从礼品登记处成功购买产品的问题，从而能够下订单并适当更新礼品登记处。 以前，尝试从礼品注册处下订单时出现错误，导致购买无法完成。

_ACP2E-2676 - [GitHub问题](https://github.com/magento/magento2/issues/35432)_

#### 获取无法发送Cookie。 尝试重新排序时“图像消息”的大小

重新排序过程现在不会生成自己的错误。 它将依赖购物车列表的内置项目检查。

_ACP2E-2704 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ba25af8a)_

#### 结账时未选择默认送货地址

在启用地址搜索的上下文中，默认送货地址现在为选定事件。

_ACP2E-2798 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7e0e5582)_

#### 带有自定义选项的[CLOUD] graphql addProductsToCart api问题

GraphQL使用不同的自定义选项将相同的产品正确地添加到购物车

_ACP2E-2897 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c971859e)_

#### 更改商店视图时，[云]相关产品规则不起作用

通过确认在购物车页面上已成功收到自定义属性值，该问题已得到修复。 以前，在店面购物车页面上的商店之间切换时，无法正确获取购物车。

_ACP2E-2917_

#### 在结账为新客户时，多个地址添加到帐户

现在，系统仅在创建订单失败时保存一次新的客户地址，从而防止在出现订单放置错误时创建多个相同的地址。 以前，每次尝试下订单时，无论是否成功创建了订单，系统都会保存一个新地址。

_ACP2E-2923 - [GitHub代码贡献](https://github.com/magento/magento2/commit/001e5188) - [GitHub代码贡献](https://github.com/magento/inventory/commit/2ebcef39)_

#### 通过访客订单表单重新订购客户订单导致出现空购物车

以前，在通过“订单和退货”页面进行重新订购时，客户会被重定向到登录页面。 应用此修复后，进行重新订购时，注册的客户会被正确重定向到“查看购物车”页面。 该流的工作方式与访客客户相同。

_ACP2E-3004 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6a185204)_

#### 角色资源有限的管理员用户无法查看购物车

以前，受限制的管理员无法从关联网站的管理员面板中看到放弃的购物车。 应用此修复后，受限管理员可以从管理员面板中看到放弃的购物车。

_ACP2E-3025 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d1f7dc95)_

#### [云]快速订购大量SKU性能

当购物车价格规则条件中使用的属性对于所有产品都不存在，并且启用了MAP（最低广告价格）功能时，结账性能已得到改进。

_ACP2E-3176 - [GitHub代码贡献](https://github.com/magento/magento2/commit/66dea0de)_

#### 购物车中重复的项目

现在，系统可正确处理多个并行请求，以将同一产品添加到购物车中，并成为单个行项目，从而防止为同一SKU创建单独的行项目。 以前，并行请求将同一产品添加到店面的购物车会导致同一SKU出现多个行项目。

_ACP2E-3211 - [GitHub代码贡献](https://github.com/magento/magento2/commit/66dea0de)_

#### 对以名字/姓氏输入的电子邮件发送结账订单电子邮件确认函

不再发送结账单电子邮件确认，该确认之前在名字和姓氏字段中输入类似电子邮件的模式时发送。

_ACP2E-3296 - [GitHub代码贡献](https://github.com/magento/magento2/commit/5184c067)_

#### 签出送货地址表单使用错误的地址进行更新

现在，每个网站的shippingAddressFromData已保存到本地存储中。 以前，如果在URL中使用商店代码，并且在同一访客会话期间从多个网站启动了结账，则来自错误网站的地址可能会在结账期间自动填充到送货地址表单中。

_ACP2E-3402 - [GitHub代码贡献](https://github.com/magento/magento2/commit/078c387e)_

#### 启用地址搜索时，[CLOUD]签出未保留所选的帐单地址

启用地址搜索后，结帐付款页面现在将保留所选的帐单地址。 以前，如果“客户地址数限制”配置为1，并且客户有多个地址，则在重新加载页面后，选定的账单地址将消失。

_ACP2E-3405_

#### 礼品卡产品 | 购物车合并正在合并礼品卡

Giftcard产品现已正确合并到购物车中

_ACP2E-3407 - [GitHub代码贡献](https://github.com/magento/magento2/commit/88660e79)_

#### 注销时未遵循购物车持久性

添加了从客户登录到身份验证弹出窗口和签出登录时记住我的功能。

_ACP2E-3415 - [GitHub代码贡献](https://github.com/magento/magento2/commit/344fce23)_

#### 现有报价数据未更新/不可见，而是在trigger_recollect = 1时创建新的报价记录

客户的购物车项目不会再因产品在添加到购物车后被删除而消失。

_ACP2E-3488 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1984c61c)_

#### 购买礼品注册项目时，客户会看到其注册表中没有的项目

礼品注册更新不再包含不属于礼品注册表的项目。

_ACP2E-3495_

#### [云]出现“全部删除”确认弹出窗口，无需确认即删除购物车项目的问题

现在，对于需要注意的产品，单击“全部删除”按钮会提示出现确认弹出窗口，以确保仅在确认后删除项目。 以前，会立即删除项目而不进行任何确认

_ACP2E-3510_

#### [CLOUD]重新排序按钮功能

从管理员区域重新订购的订单现在会将带库存的产品添加到报价中，即使原始订单中有一些产品不再有库存。 在修复之前，如果原始订单中没有库存的产品，则不会向新报价添加任何产品。

_ACP2E-3618 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a52ff98f)_

#### 搜索商店无法按邮政编码工作

无法按邮政编码正确搜索取车位置，因此无法进行荷兰本地化。 修复后，取车地点搜索将根据邮政编码提供结果。

_ACP2E-3622 - [GitHub代码贡献](https://github.com/magento/magento2/commit/344fce23)_

### 购物车和结帐、结帐/单页结帐

#### [随机错误]电子邮件字段未呈现，或者需要很长时间才能在结帐送货或付款页面中显示

Commerce现在按预期在结账送货和付款页面上渲染&#x200B;**[!UICONTROL Email]**&#x200B;字段。 以前，此字段不存在或呈现缓慢。

_AC-9386 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e1babcfd)_

### 购物车和结帐、订购

#### 从管理员下订单时，具有多个可自定义选项（日期字段不起作用）的产品的日期选取器

现在，在管理订单创建过程中为产品配置多个可自定义的日期选项时，系统可正确显示所有日期字段的日期选取器。 以前，仅为第一个日期字段显示日期选取器，而其余字段没有日期选取器。

_ACP2E-3097 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b21e5d91)_

### 购物车和结帐、送货

#### 可配置产品的即时购买“最便宜的运输”中断

即时购买功能错误地为可配置产品选择了更昂贵的店内交付选项，而不是最便宜的统一费率方法。 这一修复措施可确保根据实际价格选择正确的配送方式。”

_AC-12119 - [GitHub问题](https://github.com/magento/magento2/issues/38811) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38819) - [GitHub代码贡献](https://github.com/magento/magento2/commit/29fe9097)_

### 目录

#### 清除cron_schedule数据库表不会清除不存在的作业

系统现在会自动清理cron_schedule数据库表，删除系统中不再存在的作业的条目。 这通过保持表中的最小行数来确保最佳性能。 以前，不清理非活动模块或已移除模块中作业的条目，导致cron_schedule表中出现不必要的数据积累。

_AC-10910 - [GitHub问题](https://github.com/magento/magento2/issues/38217) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38693)_

#### 未从可配置产品中删除层价格

现在，当产品从简单产品转换为可配置产品时，系统可正确地删除产品的层级价格，从而确保在前端准确显示价格。 以前，当产品从简单产品转换为可配置产品时，不会删除可配置产品的层价格，从而导致显示的价格不匹配。

_AC-10953 - [GitHub问题](https://github.com/magento/magento2/issues/38390) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38427)_

#### 类别描述WYSIWYG在非默认存储上为空

现在，在商店视图级别编辑类别时，系统会在WYSIWYG编辑器中正确保存并显示类别说明。 以前，在商店视图级别保存类别描述后，WYSIWYG编辑器将显示为空。

_AC-11804 - [GitHub问题](https://github.com/magento/magento2/issues/38622) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38623)_

#### 无法通过选中自定义选项的一个复选框对可配置产品重新排序

系统现在使用单个选定的复选框自定义选项正确处理可配置产品的重新排序，从而成功创建购物篮。 以前，尝试重新排序此类产品会导致错误，并阻止将商品添加到购物车。

_AC-11970 - [GitHub问题](https://github.com/magento/magento2/issues/38736) - [GitHub代码贡献](https://github.com/magento/magento2/commit/1d144bce)_

#### [问题]修复分层导航上筛选器项的措辞

系统现在正确使用了分层导航过滤项中的“项”和“项”，提高了过滤器描述的清晰度和准确性。 以前，这些词语使用不正确，这可能导致导航过滤器选项的用户混淆。

_AC-12076 - [GitHub问题](https://github.com/magento/magento2/issues/38789) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37852)_

#### 自定义选项的日期和时间格式不起作用

系统现在可以将配置的日期格式正确应用于日期类型的产品自定义选项，确保日期格式能在前端正确显示。 以前，对日期格式配置的更改不会反映在日期类型的产品自定义选项的前端。

_AC-12164 - [GitHub问题](https://github.com/magento/magento2/issues/32990) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38925)_

#### 下拉列表选项缺失

现在，在创建具有超过20个值的新属性时，系统会在下拉列表中正确显示所有值。 以前，仅显示前20个值或其他选定的页面值，从而导致其余值缺失。

_AC-13068 - [GitHub代码贡献](https://github.com/magento/magento2/commit/47b448e2)_

#### [问题]将当前的存储ID用于类别运行时缓存

现在，系统正确地将当前存储ID用于类别运行时缓存，从而防止在使用模拟或自定义代码将类别保存到不同存储时覆盖数据。 以前，存储在运行时的对象可能来自错误的存储，从而导致数据覆盖。

_AC-13296 - [GitHub问题](https://github.com/magento/magento2/issues/39310) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36394)_

#### bin/magento sampledata:deploy —no-update引发异常

在sampledata:deploy命令中使用 — no-update选项时，系统现在可以正确接受布尔值，从而防止在示例数据部署期间出现任何错误。 以前，使用此命令时引发错误，因为系统错误地期望整数值。

_AC-13324 - [GitHub问题](https://github.com/magento/magento2/issues/39344) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39345)_

#### [问题]修复EAV缓存类型的用法

现在，系统在所有相关位置都正确使用了EAV缓存类型，从而确保一致而高效的数据缓存。 以前，EAV缓存类型使用不一致，这会导致数据缓存效率低下和不一致。

_AC-13355 - [GitHub问题](https://github.com/magento/magento2/issues/32322) - [GitHub代码贡献](https://github.com/magento/magento2/pull/31264)_

#### 包含空数据的目录高级搜索将转到搜索结果页面[2.4.dev分支]

现在，系统在高级搜索页面上正确地保留用户，并在用户尝试执行搜索时显示错误消息，而不输入任何数据。 以前，执行空搜索会将用户重定向到“目录高级搜索”页面，并显示一条消息，提示用户修改其搜索。

_AC-13596 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### [问题]产品布局基于attribute_set

该系统现在允许根据属性集调整产品布局，为管理前端商店中的产品展示提供了一种更实际和有效的方式。 以前，布局只能根据SKU或产品类型进行调整，这对于许多产品或特定文章并不总是可行的。

_AC-13622 - [GitHub问题](https://github.com/magento/magento2/issues/38790) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36244)_

#### eav_attribute_option_value表上缺少唯一键

现在，系统在“eav_attribute_option_value”表的“option_id”和“store_id”列中包含唯一键，从而防止了选项可能为同一商店视图具有多个值。 以前，错误代码可能会导致同一商店视图的选项具有多个值，从而导致在编辑产品或属性时出现问题。

_AC-6738 - [GitHub问题](https://github.com/magento/magento2/issues/24718) - [GitHub代码贡献](https://github.com/magento/magento2/pull/28796)_

#### [问题]使用类别产品索引器的可见性类，而不是硬编码值

系统现在使用类别产品索引器的可见性类，而不是硬编码值，增强了模块性。 以前，在类别产品索引器中使用硬编码值，限制了灵活性和适应性。

_AC-8297 - [GitHub问题](https://github.com/magento/magento2/issues/37200) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37199)_

#### 新产品小部件中的货币代码未更改

现在，当货币在前端发生更改时，系统可正确更新新产品小组件中的货币代码，从而确保网站中货币显示的一致性。 以前，更改前端中的货币不会影响新产品小部件中显示的货币代码。

_AC-9375 - [GitHub问题](https://github.com/magento/magento2/issues/37898) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37899)_

#### 可配置产品的PLP上不显示常规价格

对于具有具有特价子产品的可配置产品，产品列表页面上现在会显示常规价格。

_ACP2E-2224 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a4fbf702)_

#### 库存信息未直接显示在可视化促销网格上

库存现在会根据选定的商店显示。

_ACP2E-2478 - [GitHub代码贡献](https://github.com/magento/inventory/commit/bdbf97ea)_

#### cms页面上未更新构件内容

现在，当产品设置为新产品且已保存时，系统会更新CMS页面上的小组件内容，以确保该页面显示更新的产品集合。 以前，由于缓存中用于小部件的缓存标识不正确，页面未更新以显示新产品。

_ACP2E-2621 - [GitHub代码贡献](https://github.com/magento/magento2/commit/f89a447e)_

#### 保存捆绑产品高级定价时出现问题

捆绑产品保存性能改进。

_ACP2E-2630 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b2286ecf)_

#### 创建目录价格规则时，[内部部署]重新索引过程效率低下

现在，保存目录价格规则将不会使索引器失效，而是只为受影响的产品重新编制索引

_ACP2E-2652 - [GitHub代码贡献](https://github.com/magento/magento2/commit/f89a447e)_

#### 通过CSV导入更新日期和时间类型产品属性的时间

现在，日期时间属性将在导出的数据中具有时间部分。 也可以使用导入来更新此类属性的时间。 此外，如果启用了“Fields Enclosure”，则“additional_attributes”列中的属性值将用双引号括起来。

_ACP2E-2679 - [GitHub问题](https://github.com/magento/magento2/issues/38306) - [GitHub代码贡献](https://github.com/magento/magento2/commit/ea79f7dd)_

#### 请求中的网站ID错误时没有相应的错误消息

现在，当请求中的网站ID错误时，添加了相应的错误消息，以便显示。 以前，当请求中的网站ID错误时，不会进行验证。

_ACP2E-2689 - [GitHub代码贡献](https://github.com/magento/magento2/commit/39d54c2d)_

#### 删除不会影响映像的现有计划更新后，产品映像丢失

删除暂存更新时不会删除产品图像。

_ACP2E-2785 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c8931218)_

#### [云]与层价格一起使用时捆绑产品价格错误

以前，在计算四舍五入到2个小数点的某些百分比折扣时，将会为购物车和产品列表页面/产品详细信息页面生成不同的最终价格。 应用此修复后，捆绑包产品的最终价格与产品详细信息页面、产品列表页面和迷你购物车页面中的价格相同。

_ACP2E-2799 - [GitHub问题](https://github.com/magento/magento2/issues/38091) - [GitHub代码贡献](https://github.com/magento/magento2/commit/b2286ecf)_

#### 目录促销规则不适用于quantity_and_stock_status属性

现在，目录促销规则将考虑quantity_and_stock_status属性，之前在从管理员端生成新产品时未考虑该属性。

_ACP2E-2805 - [GitHub问题](https://github.com/magento/magento2/issues/35627) - [GitHub代码贡献](https://github.com/magento/inventory/commit/cf34971d)_

#### 通过REST API更新价格时，产品实体updated_at列值未更新

在通过REST API更新现有产品时，管理员中的产品“上次更新时间”列将更新正确的日期时间。 以前，列“上次更新时间”未正确更新。

_ACP2E-2837 - [GitHub代码贡献](https://github.com/magento/magento2/commit/39d54c2d)_

#### 可以通过产品导入设置非唯一值

现在，系统在产品导入期间可正确地强制实施唯一产品属性的唯一值约束，从而防止此类属性的值重复。 以前，对于通过产品导入配置为具有唯一值的产品属性，可以设置非唯一值。

_ACP2E-2840 - [GitHub问题](https://github.com/magento/magento2/issues/38445) - [GitHub代码贡献](https://github.com/magento/magento2/commit/7e0e5582)_

#### 启用单存储模式后，前端产品会使用存储特定数据

以前，当我们为默认商店视图启用单商店模式时，更改未迁移到网站级别的范围。 应用此修复后，当我们启用单商店模式时，默认商店视图特定的数据将与网站级别特定的数据同步，并将解决产品和类别可能存在的冲突。

_ACP2E-2843 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c8931218)_

#### 无法使用Rest API在类别中设置“默认排序依据”

通过REST/SOAP API请求正确更新类别上的default_sort_by

_ACP2E-2857 - [GitHub代码贡献](https://github.com/magento/magento2/commit/57a32313)_

#### [云]商家面临愿望清单计数问题

在一个商店中将产品添加到愿望清单不再增加在同一浏览器中打开的其他商店中的愿望清单计数。 以前，如果两个存储都加载到同一浏览器中，则另一个存储中的愿望清单计数也会增加。

_ACP2E-2871 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3a7c4d17)_

#### 使用捆绑产品时，前端的类别页面显示空插槽

在当前存储上下文中不可销售的捆绑产品不再编制索引。

_ACP2E-2874 - [GitHub代码贡献](https://github.com/magento/inventory/commit/bc37ec76)_

#### [说明]捆绑产品序列表问题

现在，删除捆绑产品或删除捆绑产品选项时，将会删除捆绑产品序列表(sequence_product_bundle_option、sequence_product_bundle_selection)中的记录。
以前，不会删除捆绑产品序列表中的记录。

_ACP2E-2888_

#### 多网站架构中的[云]报价问题

以前，使用不同货币和客户组的多网站架构无法正确为商店应用折扣。 实施此修复后，具有不同客户组价格折扣的多网站架构将成功应用于不同的商店。

_ACP2E-2905 - [GitHub问题](https://github.com/magento/magento2/issues/38506) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a4fbf702)_

#### dynamic-rows.js:658编辑捆绑产品时未捕获的TypeError： dataRecord.slice

从捆绑产品中删除选项时，浏览器控制台中没有javascript错误。

_ACP2E-2909 - [GitHub问题](https://github.com/magento/magento2/issues/38505) - [GitHub代码贡献](https://github.com/magento/magento2/commit/93d50f8d)_

#### 订单确认中的[云]捆绑产品定价错误

当使用基础货币以外的货币时，将按顺序在Storefront上显示捆绑选项的正确数量。

_ACP2E-2950 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a4fbf702)_

#### YouTube视频添加错误

产品图像和视频是在全局范围内配置的。 鉴于您无法在一个范围中拥有产品视频，而不能在另一个范围中拥有产品视频，因此Youtube API密钥设置已设置为全局范围。

_ACP2E-2956 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a4fbf702)_

#### 仅对store_id=0进行[云] URL更新

“URL路径”现在使用正确的存储ID进行存储。 以前，商店ID不正确，导致在移动类别时数据库中保留不正确的URL路径。

_ACP2E-2964 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9af794a4)_

#### async.operations.all已执行并创建错误。

REST API调用中的产品链接数据不正确不再导致严重错误。

_ACP2E-3009 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a4fbf702)_

#### [云]移动问题仅无法在PDP图像上捏合

现在，系统支持在Chrome上的移动设备视图中缩放产品详细信息页面图像的功能，从而增强移动设备用户体验。 以前，在Chrome上的移动视图中双击图像时，无法按预期放大图像。

_ACP2E-3029 - [GitHub代码贡献](https://github.com/magento/magento2/commit/148c3ead)_

#### 具有选项名称0的LayeredNavigation中缺少标签

通过跳过属性值0的空值检查器，该问题已得到解决。 以前，它被视为空并导致问题。

_ACP2E-3058 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3a7c4d17)_

#### 客户查看来自其他客户组的价格

修复了由于请求中的X-Magento-Vary的旧值而导致客户组相关信息保存在错误的区段中的问题

_ACP2E-3069 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d1f7dc95)_

#### 删除捆绑包选项时出错

系统现在可以正确删除包选项，而不会触发错误或导致页面无响应。 以前，尝试删除捆绑包选项会导致“页面无响应”错误并阻止保存产品。

_ACP2E-3076 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6a185204)_

#### 类别权限内存不足浏览器问题

类别权限UI经过重新设计，允许使用现成UI组件和分页呈现大量权限。 以前的类别权限会导致浏览器崩溃，同时为该类别分配大量权限。

_ACP2E-3094_

#### New Relic错误日志中不存在[Cloud]图像文件

现在，系统会将自定义占位符图像同步到本地存储，以确保在使用远程存储(如AWS S3)时正确呈现这些图像。 以前，自定义占位符图像在使用远程存储时无法渲染，从而导致图像显示中断和错误日志。

_ACP2E-3100 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d1f7dc95)_

#### 由于缓存，新产品RSS馈送未更新为新产品

现在，当产品设置为新并保存时，将更新“新产品”的Rss源

_ACP2E-3103 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d01ee51e)_

#### [Cloud]产品媒体集GQL响应未按图像位置排序

系统现在可以在GraphQL响应中按位置对媒体集中的项目进行正确排序，确保显示顺序准确无误。 以前，媒体集中的项目不按位置排序，从而导致显示顺序不正确。

_ACP2E-3126 - [GitHub问题](https://github.com/magento/magento2/issues/37671) - [GitHub代码贡献](https://github.com/magento/magento2/commit/b21e5d91)_

#### [云]子类别项未显示在管理员后端的构件编辑中

新构件页面上的类别树在加载5级以上的类别时不会再出现问题。 以前，在加载树以超过5级类别时缺少某些类别。

_ACP2E-3136 - [GitHub代码贡献](https://github.com/magento/magento2/commit/148c3ead)_

#### [云]实际移动设备上的双指缩放和移动问题

该系统现在确保移动设备上具有一致的图像缩放功能，从而提供流畅且可预测的用户体验。 以前，图像缩放功能不一致，并且在通过移动设备查看特定点后突然缩小。

_ACP2E-3198 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1366ae5e)_

#### 从共享目录取消分配产品时，不会清除愿望清单产品

现在，如果共享目录中没有产品，则愿望清单中不会显示任何项目。 以前，即使愿望清单中实际上没有项目，愿望清单页面也会错误地显示“1个项目”的计数。

_ACP2E-3282 - [GitHub代码贡献](https://github.com/magento/magento2/commit/5184c067)_

#### 相关产品全选/取消全选

以前，如果手动选择了产品，则相关产品的“全选”/“取消全选”按钮无法正常工作。 修复后，这些按钮现在可以正常工作（即使手动选择按钮也是如此），确保所有产品都已正确选择或取消选择。

_ACP2E-3286 - [GitHub代码贡献](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [云]库存警报电子邮件翻译为错误的语言

在使用不同语言发送具有多个商店视图的网站的库存/价格警报时，将在电子邮件上使用创建警报的商店视图所使用的语言。

_ACP2E-3336 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a4cf5e62) - [GitHub代码贡献](https://github.com/magento/inventory/commit/9f3e63d1)_

#### 禁用类别的名称在类别树中不再灰显

以前，禁用的类别在类别树中不会显示为灰色。 现在，它们以灰显效果显示。

_ACP2E-3350 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d75cff27)_

#### 可配置产品编辑表单加载导致超时和内存耗尽

在固定配置之前，基于所有可能的属性选项组合构建可配置产品变体。 如果属性具有许多选项，这将导致冗长且耗费资源的操作。 现在，可配置产品变体是基于现有的子产品属性构建的。 这大大减少了计算，从而改进了资源的使用。

_ACP2E-3410 - [GitHub代码贡献](https://github.com/magento/magento2/commit/078c387e)_

#### 使用样本时，Fotorama无法正确加载视频，且已通过URL预先选择选项

现在，如果URL包含所选选项，则产品视频将在可配置的产品详细信息页面上正确呈现。

_ACP2E-3454 - [GitHub代码贡献](https://github.com/magento/magento2/commit/078c387e)_

#### PageBuilder轮播构件显示不符合条件的产品

构件中使用的产品列表现在遵循类别条件

_ACP2E-3461 - [GitHub代码贡献](https://github.com/magento/magento2/commit/078c387e)_

#### 当组中的所有产品的数量无效时触发验证错误

现在，当一个产品的数量无效时（以前未发生这种情况），就会正确触发组中所有产品的验证错误。

_ACP2E-3469 - [GitHub代码贡献](https://github.com/magento/magento2/commit/56463d5e)_

#### 可配置产品中未显示[CLOUD]特殊价格

修复后，更改特殊价格属性的“在产品列表中使用”值将不会影响可配置产品的特殊价格的显示。

_ACP2E-3513 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d4de4726)_

#### 索引器如果进程终止，将不会清理临时表

如果索引器进程终止，现在将清除CatalogRule索引器临时表

_ACP2E-3516 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1984c61c)_

#### 2.4.7-p3中的[QUANS]核心单元测试失败

此测试不需要发行说明，因为它是单元测试改进。

_ACP2E-3520 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1984c61c)_

#### 多来源分组产品的库存量检索性能问题

现在，当分配的产品具有大量库存来源时，会优化分组产品和捆绑包产品编辑页面。

_ACP2E-3533 - [GitHub代码贡献](https://github.com/magento/inventory/commit/0208e433)_

#### 重新修复ACP2E-3389

在锚点类别数量较大时，提高了管理类别页面的性能

_ACP2E-3641 - [GitHub代码贡献](https://github.com/magento/magento2/commit/982b1c42)_

### 目录，内容

#### [云]缓存未失效。

以前，在保存具有更新设计布局的CMS页面时，该页面不会适当地反映在前端。 应用此修复后，当我们更改设计布局并保存CMS页面时，会在前端看到相应的设计布局。

_ACP2E-3063 - [GitHub代码贡献](https://github.com/magento/magento2/commit/66dea0de)_

#### 在内容小部件中反转了[云]锚点/非锚点类别

以前，当我们选择“显示在锚点类别上” -> “锚点类别”时，会显示所有未反映锚点与非锚点之间的父子关系的类别。 应用此修复后，“显示位置 — >锚点类别”仅显示锚点类别（可选），“显示位置 — >非锚点类别”则显示非锚点类别（可选）

_ACP2E-3131 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7377de59)_

#### 类别无法使用小组件

以前，如果我们为不同的锚点/非锚点类别保存CMS块，那么当该块显示在前端时，它不适用于子类别。 应用此修复后，块会显示在不同类别的前端。

_ACP2E-3152 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d01ee51e)_

### 目录、框架

#### Order get(Shipments|Creditmemos|Invoice)Collection — 不应加载集合

系统现在可以确保在从订单中检索时，不会预装发运和贷项通知单的收款，从而允许对这些收款应用附加的筛选条件或订单。 以前，会自动加载这些收藏集，从而防止进行任何进一步的修改。

_AC-9111 - [GitHub问题](https://github.com/magento/magento2/issues/37561) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37562)_

#### [云]跟进：检查数据是否更改时，数据比较不匹配

以前，每次在没有任何数据更改的情况下调用save对象（对于任何数值数据字段，如int/float/double）。 它会触发将_hasDataChanges标志设置为true并调用save函数。 它也不会检查由字符串封装的浮动数字。 进行此修复后，仅当数据发生更改时，才会调用save函数。 int/float/double-check的数据值，其值传递给函数并执行严格的类型匹配

_ACP2E-2949 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c8931218)_

### 目录，GraphQL

#### 在GraphQL中处理类别过滤器： includeDirectChildrenOnly和category_uid

按category_uid筛选时，仅获取直接子类别。

_ACP2E-3090 - [GitHub代码贡献](https://github.com/magento/magento2/commit/93d50f8d)_

#### [云] Graphql产品排序不起作用

在变量中传递字段时，GraphQl产品按多个字段排序现在可按预期工作。

_ACP2E-3166 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8459b17d)_

#### 层级价格在GraphQL产品中返回了错误的值（与Storefront相比）

修复后，为graphql请求返回的产品层价格具有每一项的价格。

_ACP2E-3312 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1366ae5e)_

#### [CLOUD] B2B：通过GraphQL的类别问题

修复后，即使根类别没有“允许”权限，类别graphql查询也会返回具有“允许”权限的类别。

_ACP2E-3385_

### 目录、定价、暂存和预览

#### 同时更新大量产品时，[Cloud]特殊价格API端点返回错误

现在，特价批量更新API将为每个日期范围创建一个营销活动，而不是为每个产品和日期范围创建多个计划更新。 此外，它支持并发API请求，以更快地处理大量SKU。

_ACP2E-2672 - [GitHub代码贡献](https://github.com/magento/magento2/commit/f89a447e)_

### 目录、产品

#### 编辑产品中的类别选择树的顺序与在目录 — >类别中设置的顺序不同

现在，系统会按照在目录 — >类别中设置的相同顺序，在产品编辑部分中正确显示类别选择树，从而简化大型目录中的产品管理。 以前，产品编辑部分中的类别树按类别创建顺序显示，而不管在目录 — >类别中设置的显示顺序如何。

_AC-7050 - [GitHub问题](https://github.com/magento/magento2/issues/36101) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36104)_

### 目录，SEO

#### 页面> 1时类别的规范URL不正确

以前，多页面内容的规范URL无法正常运行，始终显示基本URL。 但是，在实施此修复后，多页面内容的规范URL现在可以正确显示具有页面ID的URL。

_ACP2E-3653 - [GitHub代码贡献](https://github.com/magento/magento2/commit/982b1c42)_

### 目录，搜索

#### 产品未在类别和搜索中显示，但直接链接有效

以前，带price_* attribute_code的Yes/No自定义属性不适用于索引编制。 进行此修复后，“是/否”自定义属性会按预期工作。

_ACP2E-2757 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ba25af8a)_

#### 某些类别页面出现[云]弹性搜索错误

以前，通过提及配置工单，我们为多个产品定价0时，会在前端类别页面引发异常。 应用此修复后，当多个产品价格0并且我们在前端加载类别页面时，它不会引发任何异常，并且将成功加载类别页面。

_ACP2E-3053 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c8931218)_

#### 创建对象时出现类型错误： Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor异常

修复后，无需指定$data即可创建Magento\CatalogSearch\Model\Indexer\Fulltext类的实例。

_ACP2E-3345 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1366ae5e)_

#### 在Magento Admin中保存后，产品的[CLOUD]问题在前端不可见

在修复了具有长名称子产品的可配置产品之后，店面中将不会丢失这些产品。

_ACP2E-3521 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1984c61c)_

### 目录，运输

#### 为礼品注册项目下订单时送货地址为空

以前，对于访客用户礼品注册项目，当从电子邮件功能返回时，会生成一个空的空白地址，该地址不适合下订单。 应用此修复后，礼品注册表将检查已登录的用户/来宾用户和分配的地址（如果存在）。

_ACP2E-3195_

### 云

#### [云] PHPSESSID正在更改每个POST请求

如果启用了L2 Redis缓存并且客户从后端进行了更新，则PHPSESSID不再在已登录客户的前端区域上重新生成POST请求

_ACP2E-3010 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6a185204)_

#### Sitemap生成警告

修复后，将在系统tmp目录中生成Sitemap并复制到最终目标。

_ACP2E-3532 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d4de4726)_

### 内容

#### 在“最近查看的”小组件中显示价格时出现[问题]问题

现在，系统可在“最近查看的产品”构件中正确显示缺货的简单产品的价格，确保所有构件和产品列表页面的一致性。 以前，由于价格加载模板中的条件，缺货的简单产品的价格不会显示在“最近查看的产品”小部件中。

_AC-10539 - [GitHub问题](https://github.com/magento/magento2/issues/38167) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38159)_

#### [问题] acl.xsd文件中的拼写错误和语法正确

系统现在更正了acl.xsd文件中的拼写错误和语法错误，提高了文档的清晰度和准确性。 以前， acl.xsd文件包含拼写错误和语法错误，这可能会导致混淆。

_AC-10596 - [GitHub问题](https://github.com/magento/magento2/issues/38061) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38046)_

#### Pagebuilder横幅图像在图库中不可见

现在，系统可正确显示在Pagebuilder图库中新创建的文件夹中上传的横幅图像，从而消除之前的控制台错误。 在此修复之前，如果横幅图像上载到新文件夹中，则不会在图库中显示这些图像，从而导致控制台错误。

_AC-10845 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c8f87c25)_

#### 更新到2.4.5-p8后，出现“区码未设置”

现在，在启用Magento_CSP模块并将“dev/js/translate_strategy”设置为“embedded”时，系统可成功完成静态内容部署过程，而不会触发“未设置区码”错误。 以前，在这些情况下，静态内容部署过程会失败，并出现“未设置区码”错误。

_AC-12283 - [GitHub问题](https://github.com/magento/magento2/issues/38845) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38922)_

#### 构件类别树未正确呈现

_AC-12692 - [GitHub问题](https://github.com/magento/magento2/issues/39008) - [GitHub代码贡献](https://github.com/magento/magento2/commit/58e40ceb)_

#### 在设计配置页面中更改主题时，无法看到“使用默认值”消息

系统现在包含单独的列，以根据设计配置页面中选择的主题显示“使用默认值”消息。 这确保默认值状态清晰可见。 以前，不会显示“使用默认值”消息，这会导致对所选主题状态的混淆。

_AC-13054 - [GitHub代码贡献](https://github.com/magento/magento2/commit/47b448e2)_

#### [问题]再次恢复与TinyMCE插件的向后兼容性(之后……

系统现在恢复与TinyMCE插件的向后兼容性，从而允许从其他位置使用小组件时调用插件中定义的函数。 以前，由于TinyMCE版本中的更改，插件不会将构件作为对象返回，从而导致在尝试调用构件实例上的某些函数时出错。

_AC-13569 - [GitHub问题](https://github.com/magento/magento2/issues/39262) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39258)_

#### 产品页面上WYSIWYG编辑器中的[问题]文件上传问题

现在，系统可正确显示文件夹树，并允许在产品页面上的WYSIWYG编辑器中上传图像，即使先展开“图像和视频”选项卡后也是如此。 以前，先展开“图像和视频”选项卡，导致文件夹树无法显示，以及尝试在WYSIWYG编辑器中上传图像时出现错误消息。

_AC-9638 - [GitHub问题](https://github.com/magento/magento2/issues/38026) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38025)_

#### [内部部署]动态块问题

现在，在动态块中正确呈现了小工具。

_ACP2E-2392 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a12063bd)_

#### YouTube nocookie url在页面生成器中不起作用

现在，页面生成器允许在验证规则的表单元素设置中使用youtube无Cookie URL。 以前，youtube无cookie url在pagebuilder中不起作用。

_ACP2E-2606_

#### 由于新闻稿模板中出现问题，[云]前端未加载

通过CMS的“页面内容”部分添加块不会再导致异常

_ACP2E-2693 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ea79f7dd)_

#### ACP2E-2836： [Cloud]调查日志中发现的异常： InvalidArgumentException：类在vendor/magento/module-rule/Model/ConditionFactory.php中不存在

删除PageBuilder产品内容设置的条件不会再导致在日志文件中记录异常。 以前，删除PageBuilder产品内容设置上的条件会导致在日志中记录严重异常，即使不会导致前端出现任何问题。

_ACP2E-2836 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/36c0f5df)_

#### 切换到单存储模式 — 不再显示全局内容

现在，当启用单商店模式时，系统会将商店视图设计配置与网站设计配置同步，以确保内容更新在前端可见。 以前，切换到单商店模式会阻止内容更新反映在店面上。

_ACP2E-2842 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7e0e5582)_

#### 在尝试添加链接和其他可用性问题时，页面生成器会替换图像。

现在，单击某个图像，页面生成器文本元素中的wysiwyg编辑器中的链接将在图像链接配置对话框中加载正确的数据。 现在，在编辑器中添加指向图像的链接也可正常使用。 以前，图像会被替换为链接。

_ACP2E-2903 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### 将0字节的图像放入目录后，旧媒体集无法呈现图像

系统现在可以在不中断功能的情况下处理媒体集中的0字节图像，从而允许按预期显示和选择目录中的其他图像。 以前，如果媒体集中存在0字节图像，则会阻止显示或选择目录中的所有图像。

_ACP2E-2970 - [GitHub代码贡献](https://github.com/magento/magento2/commit/35b1b1da)_

#### 编辑CMS块时页面生成器出错

现在，系统使用页面生成器正确地保存了在管理区域中所做的更改，并且没有引发错误“页面生成器呈现了5秒钟，没有释放锁定”。 在浏览器控制台中。 以前，在尝试保存更改时会发生此错误，从而阻止内容成功更新。

_ACP2E-3064 - [GitHub代码贡献](https://github.com/magento/magento2/commit/35b1b1da) - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### [CLOUD]购物车分区中没有结帐或编辑购物车的按钮

现在，捆绑产品通过小组件添加到购物车中，且未出现错误。

_ACP2E-3092 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b21e5d91) - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/4ebe3f1d)_

#### 类别页面上的内容暂存预览不显示产品小部件

通过确保将链接到CMS块的其他类别的产品条目准确记录到数据库中，该问题已得到修复。 以前，在请求类别预览页面时返回空结果集。

_ACP2E-3113_

#### [云]上传图像按钮不起作用

在PageBuilder中的横幅和滑块的“上传图像”按钮无法按预期使用之前，现在按该按钮时，会打开本地文件管理器以选择要上传的图像。

_ACP2E-3122 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/476ef8ea)_

#### imagecreatetruecolor()：参数#2 ($height)必须大于0。 无法上传特定图像

解决了通过媒体库上传高度为0的图像时导致管理员出错的问题，并使用sync命令成功实现了资产同步。 以前无法通过媒体集上传图像，并且当特定图像位于媒体集内时，同步命令也会失败。

_ACP2E-3127 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6f4805f8)_

#### Prototype.js Array.from与Google映射API冲突

Google映射现在在PageBuilder编辑器中正确呈现。 以前，Javascript错误会导致Google映射无法正确呈现。

_ACP2E-3154 - [GitHub代码贡献](https://github.com/magento/magento2/commit/148c3ead)_

#### [Cloud] - CMS滑块未反映最新更改

通过确保在编辑幻灯片屏幕上触发保存事件时刷新滑块列表，已修复此问题。 以前，它会触发并导致问题。

_ACP2E-3275 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_

#### 使用页面生成器按特定顺序插入CMS块时，CSM页面中出错

以前，在PHP和操作系统(Linux)的某些版本上，通过PageBuilder引用其他cms块的块的块呈现会失败，并出现“发生未知错误。 请重试。” 现在，cms块的内容在PageBuilder控制的内容中正确呈现。

_ACP2E-3326 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_

#### [云]动态块将无法正常工作

现在，注销后会清除已登录的客户区段，以防止来宾会话继承先前登录的区段

_ACP2E-3388_

#### 大型内容的Pagebuilder模板预览失败

大型内容导致画布元素溢出浏览器的限制，并返回不正确的值，这会破坏后端代码（无法正确解码图像）。 修复了将画布大小限制为通用浏览器限制的问题。

_ACP2E-3428 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/adfb1747)_

#### TinyMCE 7缺少字体大小的最新安全更新

字体大小和字体系列选择器现在在WYSIWYG编辑器中可用。 在此修复之前，使用TinyMCE 7时，这些在编辑器界面中不可用。

_ACP2E-3430 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d50f6b5d) - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/2c2f7a0e)_

#### 请澄清TinyMCE 7编辑器在管理员中的字体大小（PT而非PX）

在修复之前，无法在WYSIWYG区域中以px为单位指定字体大小。 现在，您可以用px而不是pt来设置字体大小。

_ACP2E-3483 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3f12d152) - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_

#### 页面生成器中的产品内容类型将折叠，并且消息不正确

在修复之前，当构件中没有产品时，无法正确生成预览html。 现在，可以正确生成空响应，并在预览中正确显示产品小部件。

_ACP2E-3490 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3f12d152) - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_

#### [页面生成器]添加产品列表以阻止导致错误

现在，通过页面生成器添加要阻止的捆绑包产品列表不会导致错误

_ACP2E-3534 - [GitHub代码贡献](https://github.com/magento/magento2/commit/344fce23)_

### 内容，SEO

#### CMS页面层次结构可能导致URL重写问题

以前，对于非网站根页面的自定义永久URL重写，会无限期重定向，并且永远不会加载页面。 应用此修复后，非网站根页面的自定义URL重写可按预期运行，并且不会发生重定向循环。

_ACP2E-2870_

### 内容、暂存和预览

#### 当目录价格规则设置为使用动态块进行计划时，该规则不显示

现在，系统在产品详细信息页面上正确显示与计划目录价格规则关联的动态内容。 以前，在计划目录价格规则时加载动态内容失败。

_ACP2E-2979_

### 客户/客户

#### 前端 — 客户创建页面中的出生日期验证失败

请确保在将moment.js系统依赖关系升级到最新的次要版本后所有验证都能正常工作

_AC-12162 - [GitHub代码贡献](https://github.com/magento/magento2/commit/de4dfb8e)_

#### 客户区段>条件>产品历史记录* >“已查看产品”不起作用

现在，当满足条件时，系统将在“客户区段”下的“已查看产品”条件中正确显示匹配的注册客户。 以前，即使满足条件，匹配的注册客户数仍为零。

_AC-13060_

#### 更改国家/地区下拉列表时，不会重置区域文本字段

现在，当下拉菜单中的国家/地区发生更改时，系统会重置区域文本字段，以确保以前的值不会保留。 以前，从下拉列表中更改国家/地区不会重置“区域”字段，从而导致保留最后保存的值。

_AC-8499 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3ea26621)_

#### 删除客户不会清除Storefront上所有已登录和删除客户的浏览器会话数据

删除客户现在会按预期清理店面中所有已登录和删除客户的浏览器会话数据。 购物者可以继续购物，他们的浏览器将他们的会话视为访客会话。 以前，当从管理员中删除登录购物者的客户帐户时，购物者的浏览器会引发JavaScript错误。

_AC-9240 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7d5e3906)_

### 框架

#### [问题] `app/code/Magento/Translation/etc/di.xml`中未使用的类型配置

系统现在可以删除配置中未使用的依赖项，从而提高整体代码干净度和效率。 以前，配置中存在未使用的依赖项，这些依赖项不会对任何功能产生影响。

_AC-10037 - [GitHub问题](https://github.com/magento/magento2/issues/38030) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38064)_

#### V1/customers/password端点问题/问题

现在，当通过API处理密码更改请求时，系统遵循管理GUI内设置的约束，防止了潜在的滥用密码重置功能。 以前，API可以在管理GUI中定义的规则之外处理密码更改请求，在已知有效电子邮件时，可能会允许不断重置电子邮件。

_AC-10654 - [GitHub问题](https://github.com/magento/magento2/issues/38238) - [GitHub代码贡献](https://github.com/magento/magento2/commit/0c53bbf7)_

#### 清漆配置不排除所有营销参数

现在，系统正确排除了Varnish配置中的所有常见营销参数，从而确保准确跟踪和分析。 以前，某些营销参数（如gad_source、srsltid和msclkid）不被排除，导致数据收集的潜在不准确性。

_AC-10738 - [GitHub问题](https://github.com/magento/magento2/issues/38298) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39188)_

#### 目录搜索索引过程错误索引过程

无论使用PHP编译的libxml版本如何，系统现在都能成功完成重新索引命令，而不会遇到任何错误。 以前，当使用特定版本的libxml编译PHP时，运行“重新索引”命令会导致“索引过程中出现目录搜索索引过程错误”错误。

_AC-10838 - [GitHub问题](https://github.com/magento/magento2/issues/38254) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38553) - [GitHub代码贡献](https://github.com/magento/magento2/commit/0574ac23)_

#### 向客户“订单”查询添加了created_at、status和grand_total筛选器，并修复了多个筛选器故障

系统现在支持在客户订单查询中使用created_at、status和grand_total筛选器，并且解决了多个筛选器未正确应用的问题。 以前，系统不支持这些过滤器，并且在查询中使用多个过滤器时，将无法应用所有过滤器。

_AC-10941 - [GitHub问题](https://github.com/magento/magento2/issues/38392) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36949)_

#### 从相关/追加销售/交叉销售块和价格索引随机获得大量查询

系统现在可以优化来自相关、追加销售和交叉销售数据块的查询，从而提高性能并防止网站由于过多的查询而停机。 以前，系统可能会因这些块中的查询而过载，从而导致速度显着减慢，并可能使网站停机。

_AC-10991 - [GitHub问题](https://github.com/magento/magento2/issues/36667) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38050)_

#### 例外：警告：正在尝试访问升级到ICU 74.1 (PHP Intl)之后的Calendar.php中的数组偏移…… ->

每当购物者或商家访问店面或管理员时，Commerce不再在exception.log中记录以下异常： `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`。 [GitHub-38214](https://github.com/magento/magento2/issues/38214)

_AC-11423 - [GitHub问题](https://github.com/magento/magento2/issues/38214) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38364)_

#### [问题]修复了表单包含名为`method`的元素时客户数据的问题

现在，即使表单中存在名为“method”的元素，系统也会在表单提交中正确识别“method”属性。 这可确保准确处理客户数据。 以前，如果某个表单元素命名为“method”，则会干扰表单提交中“method”属性的识别，从而导致客户数据处理出现潜在问题。

_AC-11476 - [GitHub问题](https://github.com/magento/magento2/issues/38484) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38449)_

#### [问题]修复\Magento\Framework\Data\Collection：：getItemById的PHPDocs

\Magento\Framework\Data\Collection：：getItemById方法的PHPDocs已更新为包含null作为可能的返回类型，从而解决了静态分析工具的问题。 以前，该方法的PHPDocs不指定null作为可能的返回类型，导致在条件语句中使用该方法时进行静态分析时出现警告或错误。

_AC-11489 - [GitHub问题](https://github.com/magento/magento2/issues/38485) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38439)_

#### [问题]仅允许在`setup:di:compile`期间使用有效的首选项

现在，如果为不存在或明确排除的类创建了首选项，则系统将在`setup:di:compile`命令期间引发错误，确保仅允许有效的首选项。 以前，这些方案将以静默方式失败，潜在地使与原始类关联的任何插件变得无用。

_AC-11592 - [GitHub问题](https://github.com/magento/magento2/issues/38517) - [GitHub代码贡献](https://github.com/magento/magento2/pull/33161)_

#### Magento尝试在LoggerProxy的__wakeUp方法中修改只读属性

现在，该系统允许修改LoggerProxy的__唤醒方法中以前为只读的属性，从而确保顺利操作而不强制用户采用解决方法。 以前，尝试在LoggerProxy的__wakeUp方法中重新分配只读属性的值会导致出现问题。

_AC-11651 - [GitHub问题](https://github.com/magento/magento2/issues/38526) - [GitHub代码贡献](https://github.com/magento/magento2/commit/c8f87c25)_

#### [问题] AC-2039 AC-1667升级TinyMCE参考

更新了composer.json中的tinymce最新版本

_AC-11681 - [GitHub问题](https://github.com/magento/magento2/issues/38533) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36543) - [GitHub代码贡献](https://github.com/magento/magento2/commit/b34c0a75)_

#### ChangelogBatchWalker无法在多个线程中工作

系统现在支持MView索引的进程分支，以防止在多个线程上执行索引器时出现错误。 以前，在多个线程上运行ChangelogBatchWalker会导致删除其他线程使用的表，从而导致索引器执行期间出错。

_AC-11696 - [GitHub问题](https://github.com/magento/magento2/issues/38246) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38248)_

#### [问题]重命名命名错误的变量

现在，系统正确命名了包含仍可退款的金额的变量，以防止在调试期间出现混淆。 以前，此变量错误地命名为totalRefute，这可能导致开发人员误解。

_AC-11781 - [GitHub问题](https://github.com/magento/magento2/issues/38609) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36205)_

#### [问题]通过XML将自定义属性传递到当前链接

现在，系统允许通过XML将自定义属性传递到当前链接，以确保即使链接是当前页面，也能正确显示这些属性。 以前，由于当前链接未使用getAttributesHtml()方法，因此不会显示当前页面链接的自定义属性。

_AC-11809 - [GitHub问题](https://github.com/magento/magento2/issues/38500) - [GitHub代码贡献](https://github.com/magento/magento2/pull/30070)_

#### 对于某些配置，内置FPC缓存在2.4.7中损坏

现在，在设置MAGE_RUN_CODE参数时，系统会正确缓存页面，从而确保最佳性能。 以前，在这些情况下不会缓存页面，这会导致潜在的性能问题。

_AC-11819 - [GitHub问题](https://github.com/magento/magento2/issues/38626) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38646) - [GitHub代码贡献](https://github.com/magento/magento2/commit/0c53bbf7)_

#### [问题]修复了开发模式和生产模式之间的异常处理不一致

现在，系统始终如一地处理开发人员和生产模式之间的异常，防止在引发异常时意外重定向到登录页面。 以前，异常处理的不一致性可能会导致在生产模式下重定向到登录页面，而不是显示异常消息。

_AC-11829 - [GitHub问题](https://github.com/magento/magento2/issues/38639) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37712)_

#### 替换token_list.phtml中的“PayPal帐户”翻译

现在，系统在“存储的支付方式”页面中将可令牌化的帐户支付方式的部分标记为“帐户”，而不是“PayPal帐户”，使其更能代表其功能。 以前，此部分被特别标记为“PayPal帐户”，当添加其他可令牌化的帐户支付方法时，这会产生误导。

_AC-11852 - [GitHub问题](https://github.com/magento/magento2/issues/35622) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37959)_

#### Magento\Catalog\Model\ProductRepository类上已失去向后兼容性

ProductRepository类现在通过将Initialization Helper类恢复为第二个参数来保持向后兼容性，确保从此类扩展的模块按预期运行。 以前，从ProductRepository类中的构造函数中删除初始化帮助程序会导致向后兼容性丢失，从而迫使用户采用解决方法。

_AC-11874 - [GitHub问题](https://github.com/magento/magento2/issues/38669)_

#### [问题]静态内容部署 — 类型错误

系统现在可以在静态内容部署期间正确处理空的LESS文件，并显示“LESS文件为空”错误消息。 以前，在部署期间遇到空LESS文件时抛出不正确的类型错误。

_AC-11905 - [GitHub问题](https://github.com/magento/magento2/issues/38682) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38683)_

#### [问题] [视图]删除了链接和脚本标记中的额外空间

现在，系统可确保链接和脚本标记中没有额外的空格，从而提供更干净和更高效的代码。 以前，链接和脚本标记中的属性之间会存在双空格。

_AC-12002 - [GitHub问题](https://github.com/magento/magento2/issues/32920) - [GitHub代码贡献](https://github.com/magento/magento2/pull/32919)_

#### [问题]避免配置错误的无限循环

系统现在通过防止虚拟类型配置中的自引用映射来避免无限循环。 这可确保应用程序在尝试取消引用自引用节点时不会陷入无休止循环。 以前，如果虚拟类型配置是自引用的，则会导致应用程序无限期旋转。

_AC-12127 - [GitHub问题](https://github.com/magento/magento2/issues/38822) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38794)_

#### Object Manager不用于Magento\Csp\Model\Mode\Data\ModeConfigured

现在，系统在创建ModeConfigured对象时可正确使用对象管理器，从而允许在此对象上使用插件。 以前，未使用Object Manager，导致插件无法应用于ModeConfigured对象。

_AC-12299 - [GitHub问题](https://github.com/magento/magento2/issues/38875) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38886)_

#### 产品库存和价格警报中的文档块注释不准确

产品库存和价格预警中deleteCustomer方法的文档块注释已得到更正，以准确反映该方法删除与给定客户和网站（而非网站上的客户）关联的所有库存产品或价格预警。 以前，评论不准确地指出该方法用于从网站中删除客户。

_AC-12540 - [GitHub问题](https://github.com/magento/magento2/issues/38939) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39001)_

#### [问题]对生成的数据使用已编译配置而非常规配置

系统现在使用已编译配置来生成数据，而不是使用常规配置，从而减少依赖于特定代码版本的网络传输和数据开销。 此更改可防止在容器交换期间覆盖共享实例中的缓存，从而提高稳定性并减少停机时间。 以前，某些核心类使用共享配置类型，由于多个服务器上的代码版本不同，这可能会导致缓存覆盖或应用程序停机。

_AC-12594 - [GitHub问题](https://github.com/magento/magento2/issues/38785) - [GitHub代码贡献](https://github.com/magento/magento2/pull/29954)_

#### [问题]从e1ccdb中删除的extjs中删除对文件的引用……

系统现在会从先前删除的extjs中删除对文件的引用，从而消除浏览器控制台和系统日志文件中的错误。 以前，由于缺少引用的文件，这些引用会导致错误。

_AC-12597 - [GitHub问题](https://github.com/magento/magento2/issues/38960) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38951)_

#### [问题]次要清理：修复了sprintf的错误用法，此处只需要2个占位符，并且……

现在，系统正确使用了sprintf函数以及适当数量的占位符，增强了代码干净度和一致性。 以前，sprintf函数与额外的参数一起使用时不正确，这不会导致任何重大问题，但用法不正确。

_AC-12778 - [GitHub问题](https://github.com/magento/magento2/issues/39062) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38628)_

#### PHP 8.2.15删除了FTP扩展

现在，系统将FTP扩展作为依赖项包含在composer.json文件中，以确保通过FTP成功配置CSV导入。 以前，由于PHP包中缺少FTP扩展，尝试通过FTP配置CSV导入时引发错误。

_AC-12857 - [GitHub问题](https://github.com/magento/magento2/issues/39083) - [GitHub代码贡献](https://github.com/magento/magento2/commit/47b448e2)_

#### [问题]修复了Magento模块中引用的不正确的类。

系统现在可以正确引用模块中的类，从而确保更顺畅的操作并防止因不存在类而崩溃。 这包括Indexer和Creditmemo模块中的错误修复，以及PrintAction类中HttpGetActionInterface的实现。 以前，错误的类引用会导致错误和潜在的系统崩溃，并且某些功能(如creditmemo PDF文件的文件名和股票重新索引)无法按预期工作。

_AC-12869 - [GitHub问题](https://github.com/magento/magento2/issues/39126) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37784)_

#### 能够为`dev:di:info` CLI命令定义区域

系统现在允许开发人员定义`dev:di:info` CLI命令的区域，从而增强开发和调试过程。 以前，此命令只能显示GLOBAL区域的信息。

_AC-12964 - [GitHub问题](https://github.com/magento/magento2/issues/38758) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38759)_

#### [问题]将isMultipleFiles属性添加到图像表单元素模板

此修复可防止“在此查找或拖动图像”按钮在多文件图像表单元素中添加图像时消失。

_AC-13149 - [GitHub问题](https://github.com/magento/magento2/issues/39219) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36325)_

#### 由于字符集和归类更改，安装:upgrade在MariaDB 11.4版本中失败

_AC-13247_

#### [问题]移除所有营销获取参数以最小化缓存

系统现在会删除所有营销获取参数，以优化缓存利用率，镜像使用Varnish时所使用的逻辑。 以前，这些参数可能会导致缓存溢出和性能降低。

_AC-13279 - [GitHub问题](https://github.com/magento/magento2/issues/39266) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39099)_

#### [问题] [PHPDOC]修复错误的phpdoc Magento\Directory\Model\AllowedCountries：：getAllowedCountries()

对AllowedCountries：：getAllowedCountries()方法的PHPDoc进行了修正，以提供准确的信息，从而提高文档的清晰度和实用性。 以前，此方法的PHPDoc包含不正确的信息，这可能导致混淆或误用方法。

_AC-13345 - [GitHub问题](https://github.com/magento/magento2/issues/39246) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39241)_

#### [问题]删除我们不再支持的PHP版本的一些代码。

删除了Magento不再支持的PHP版本的代码

_AC-13348 - [GitHub问题](https://github.com/magento/magento2/issues/39361) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39202)_

#### [问题]使ImageMagick适配器与php8兼容（从浮点到int的隐式转换）

系统现在通过在计算图像尺寸时正确处理浮点数来确保与PHP8的兼容性，从而防止由于从浮点到整数的隐式转换而出现任何错误。 以前，计算图像尺寸可能会导致浮点数，这种情况下，隐式舍入可能会导致错误。

_AC-13417 - [GitHub问题](https://github.com/magento/magento2/issues/39402) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37362)_

#### [问题] [PHPDOC]修复错误的phpdoc Magento\Framework\App\Config\ScopeConfigInterface

此更新更正了Magento\Framework\App\Config\ScopeConfigInterface中的PHPDoc注释，以准确反映getValue和isSetFlag方法的$scopeCode参数的类型。

_AC-13537 - [GitHub问题](https://github.com/magento/magento2/issues/39492) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39199)_

#### Magento\Framework\Filesystem\Driver\Http取决于原因短语OK

从Magento\Framework\Filesystem\Driver\Http：：isExists中删除了“OK”短语检查

_AC-13725 - [GitHub问题](https://github.com/magento/magento2/issues/39546) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39558)_

#### 在“按计划更新”模式下，客户网格索引器无法正常工作

早期的客户网格会立即更新，但在修复之后，客户网格会在cron运行后更新，但不会立即反映。

_AC-13810 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1da9ba6f)_

#### js文件出现拼写错误。

现在，系统在JavaScript文件中正确使用了术语“订阅者”，从而确保相关功能正常运行。 以前，JavaScript文件中的输入错误会导致术语“subscribers”的使用不正确。

_AC-6754 - [GitHub问题](https://github.com/magento/magento2/issues/36163) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36171)_

#### [问题]删除禁止的`@author`标记

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，确保代码更干净和标准化。 以前，`@author`标记存在于某些模块中，这违反了既定的编码标准。

_AC-8353 - [GitHub问题](https://github.com/magento/magento2/issues/37253) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37003)_

#### [问题]从`@author`中删除禁止的`Magento_Customer`标记（第2部分）

系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，确保代码更干净和标准化。 以前，`@author`标记存在于某些模块中，这违反了既定的编码标准。

_AC-8356 - [GitHub问题](https://github.com/magento/magento2/issues/37250) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37000)_

#### editorconfig语法中的空格中断`[&lbrace;composer,auth&rbrace;.json]`的规则

在修复了editorconfig中的语法错误后，系统现在可以正确将4空格缩进应用于composer和auth.json文件。 以前，由于editorconfig语法中存在空格，因此这些文件使用2空格缩进的格式不正确。

_AC-8659 - [GitHub问题](https://github.com/magento/magento2/issues/37394) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37395)_

#### [问题]改进cron错误日志记录

系统现在捕获并记录STDERR和STDOUT以用于cron流程，在cron流程失败的情况下提供有价值的诊断信息。 以前，cron进程内的任何错误消息都不会被记录，并且在不同的进程中运行的cron组的STDERR和STDOUT将会丢失。

_AC-8662 - [GitHub问题](https://github.com/magento/magento2/issues/37453) - [GitHub代码贡献](https://github.com/magento/magento2/pull/32690)_

#### [问题]向某些安装cli命令的输出中添加了一些颜色

系统现在为某些设置命令行界面(CLI)命令的输出添加了更多颜色，增强了可读性和用户体验。 以前，由于缺少颜色区分，这些命令的输出更难读取。

_AC-8984 - [GitHub问题](https://github.com/magento/magento2/issues/29335) - [GitHub代码贡献](https://github.com/magento/magento2/pull/29298)_

#### 当添加具有所需州/地区的新国家/地区时，升级Magento会重置general/region/state_required。

现在，系统仅在添加具有所需状态的新国家/地区时，才会将修改后的国家/地区添加到“general/region/state_required”配置，以防止假定地区已禁用的自定义代码出现任何中断。 以前，添加具有所需状态的新国家/地区会将“general/region/state_required”配置重置为具有所需状态的默认国家/地区，这可能会中断业务。

_AC-9630 - [GitHub问题](https://github.com/magento/magento2/issues/37796) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38076)_

#### 具有复杂`calc`表达式的php &amp; nodejs库(grunt)之间较少编译的差异

在更新wikimedia/less.php：^5.x后，修复了php &amp; nodejs库(grunt)之间少编译的差异

_AC-9712 - [GitHub问题](https://github.com/magento/magento2/issues/37841) - [GitHub代码贡献](https://github.com/magento/magento2/commit/b34c0a75)_

#### 执行部分索引时出现“未找到基表或视图”错误

现在，在辅助数据库连接的情况下，部分重新索引在大更改日志中正常工作

_ACP2E-2692 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ba25af8a)_

#### 将MariaDB升级到10.5.1或更高版本后出现问题

修复了在Mysql升级后，数据库中的日期时间值将转换为0000-00-00 00:00:00的问题

_ACP2E-2844 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a12063bd)_

#### 检查数据是否有更改时，数据比较中的类型不匹配

以前，每次在没有任何数据更改的情况下调用save对象（对于任何数值数据字段，如int/float/double）。 它会触发将_hasDataChanges标志设置为true并调用save函数。 进行此修复后，仅当数据发生更改时，才会调用save函数。 int/float/double-check的数据值，其值传递给函数并执行严格的类型匹配。

_ACP2E-2855 - [GitHub代码贡献](https://github.com/magento/magento2/commit/57a32313)_

#### [云]导入不能与目录变量一起使用

无论文件名如何，产品都可以成功导入。

_ACP2E-2959 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3a7c4d17)_

#### 在ipad mini中，菜单和标题以移动设备形式加载，而应以桌面形式加载。

系统现在将宽度为768px的设备视为桌面，以确保菜单和标题正确加载。 以前，宽度为768像素的设备被视为移动设备，从而导致菜单和标题在移动视图中加载。

_ACP2E-2966 - [GitHub代码贡献](https://github.com/magento/magento2/commit/35b1b1da) - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### 执行DDL操作时运行mview cron时未找到基表或视图错误

现在，当在后台运行mview更新时，系统可正确处理数据库更新操作，从而防止出现“找不到基表或视图”错误。 以前，如果同时运行视图更新，某些数据库更新操作可能会导致“未找到基表或视图”错误。

_ACP2E-3046_

#### 在外键的情况下无法通过db_schema.xml修改列长度

现在，通过声明性架构修改带有外键的列时，不会在MariaDB中引发错误

_ACP2E-3230 - [GitHub代码贡献](https://github.com/magento/magento2/commit/581b7ef1)_

#### 在保存订单记录时，将部分关系记录保存到DB中

在触发修复之前不必要的UPDATE查询，这可能会对性能产生影响。 修复后，消除了不必要的UPDATE查询。

_ACP2E-3361 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1366ae5e)_

#### [CLOUD]管理员控制台中有许多Javascript错误

以前，在管理面板中，控制台中存在多个javascript错误。 现在，在管理面板中，控制台中没有JavaScript错误，所有默认的JavaScript功能都将成功执行且不会出现任何问题。

_ACP2E-3375 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d75cff27)_

#### [Cloud] Magento：已删除队列消息

现在可以正确清除队列消息。 在修复之前，假定正在使用SQL队列系统，如果清除队列消息同时运行，则可能会删除新消息。

_ACP2E-3387 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d50f6b5d)_

#### 缓存标记中没有相应的缓存键条目，因此缓存清理无法正常工作

Redis缓存垃圾回收器现在默认启用LUA模式以防止出现争用情况

_ACP2E-3537 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a52ff98f)_

#### Magento_DC_INDEXER__USE_APPLICATION_LOCK值将被忽略

修复后，设置为“false”的ENV变量将被视为bool false，而不是字符串“false”。

_ACP2E-3681 - [GitHub代码贡献](https://github.com/magento/magento2/commit/982b1c42)_

### 框架，GraphQL

#### [问题]已引入对GraphQL架构的自定义标量类型的支持

系统现在支持GraphQL架构的自定义标量类型，允许开发人员定义自定义标量类型和实施。 此功能对于表示可能需要验证的值(例如HTML、电子邮件、URL、日期等)以及更高级的情况（例如EAV属性）特别有用。 以前，系统不支持在GraphQL中处理自定义标量类型。

_AC-7976 - [GitHub问题](https://github.com/magento/magento2/issues/36877) - [GitHub代码贡献](https://github.com/magento/magento2/pull/34651) - [GitHub代码贡献](https://github.com/magento/magento2/commit/0574ac23)_

### 框架、产品

#### 2.4.8-beta1 EE报告因magento异常未生成

_AC-13011_

### 框架、UI框架

#### 即使配置值已锁定，仍有可能覆盖配置值

以前，无法通过bin/magento config:set命令设置设计配置，并且可以通过操作显示它们的表单来更改锁定的值。 修复后，无法再更新从cli使用 — lock-env或 — lock-conf设置的锁定值。

_ACP2E-3324 - [GitHub代码贡献](https://github.com/magento/magento2/commit/55615e61)_

### GraphQL

#### Magento_GraphQl执行标头处理，即使标头值未通过验证

现在，系统确保仅在标头值通过验证时只执行一次标头处理，从而增强安全性并防止潜在漏洞。 以前，即使标头值未通过验证，也会执行标头处理，这会由于两次处理标头值而导致潜在漏洞和意外行为。

_AC-11729 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c8f87c25)_

#### 物理Giftcard选项没有正确的排序顺序

现在，在通过GraphQL查询时，该系统可以对实物礼品卡产品的选项进行正确排序，确保呈现的与Luma主题一致。 以前，根据Luma主题排序顺序不正确，导致显示和排序选项不正确，例如发件人姓名、收件人姓名和金额。

_AC-8951 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1bafc571)_

#### 创建/编辑/移动/删除暂存更新时，[GraphQL]解析器缓存失效

现在，系统在创建、编辑、移动或删除暂存更新时确保解析器缓存不会失效，但仅当将暂存更新应用于实体时才会失效。 以前，解析程序缓存过早失效，甚至在应用暂存更新之前就失效，这导致不必要的缓存失效。

_AC-9157 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0c53bbf7)_

#### 没有为内容暂存更新清除快速缓存

现在，当更新PageBuilder内容相关的实体时，带有PageBuilder内容响应缓存的GraphQL将失效。

_ACP2E-2642 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ba25af8a)_

#### 禁用分层导航 — 不从Graphql中删除聚合

修复了在使用“目录>分层导航>显示类别过滤器”的管理员配置设置通过GraphQL查询请求具有类别聚合的产品搜索时应用检查后的问题。

_ACP2E-2653 - [GitHub代码贡献](https://github.com/magento/magento2/commit/12e071c3)_

#### 包含价格过滤器`&lbrace;from:&quot;0&quot;&rbrace;`的GraphQL产品调用未返回任何结果

以前，使用零价格过滤器的graphql产品搜索由于抛出异常，根本没有返回任何结果。 现在，搜索会按预期返回结果。

_ACP2E-2928 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c971859e)_

#### 客户返回属性的翻译未反映在相应StoreView的GraphQL API中

客户回访属性的翻译反映在相应StoreView的GraphQL API中。
以前，各个StoreView的客户返回属性不会反映在GraphQL API中。

_ACP2E-2974 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ec7e32a9)_

#### 带有节点引号的getPurchaseOrder的[Cloud]中断GraphQL调用

采购订单GraphQL调用将能够执行任务，而不会遇到任何内部服务器错误。

_ACP2E-3128 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6f4805f8)_

#### 如果未在“所有存储视图”中启用[Cloud]可配置产品，则生产站点中未显示这些产品

现在，即使产品未在“所有商店视图”中启用，但在特定商店视图范围内启用，系统仍可在站点中正确显示可配置产品。
以前，如果在“所有商店视图”中禁用某个产品，并且仅在特定商店视图范围内启用该产品，则产品属性在GraphQL响应中将无法正确显示，从而导致产品无法正确显示。

_ACP2E-3184 - [GitHub代码贡献](https://github.com/magento/inventory/commit/3f300077)_

#### [Cloud]产品graphql在相同的简单产品分配给多个可配置产品时出现错误

以前，对于具有相同简单产品的单独可配置产品，grapQL会返回错误。 应用此修复后，不同的可配置产品具有相同的简单产品，grapQL会返回无错误的结果。

_ACP2E-3190 - [GitHub代码贡献](https://github.com/magento/magento2/commit/148c3ead)_

#### 多站点设置中的用户身份验证和跨站点令牌访问存在[云]问题

多站点设置中的GraphQl客户信息和购物车查询会检查非默认网站上的客户是否存在。
以前，在多站点设置中，查询不起作用，不能确保客户存在于非默认网站上。

_ACP2E-3215 - [GitHub代码贡献](https://github.com/magento/magento2/commit/581b7ef1)_

#### GraphQL购物车项目V2分页无法正常工作

通过在集合查询中传递当前页面参数的正确值，已修复此问题。 以前，传递错误值来设置当前页面，从而导致出现问题。

_ACP2E-3253 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8459b17d)_

#### 在获取customerCart时应指定[GRAPHQL]模型值

GraphQL“customerCart”查询现在可以创建空购物车，即使报价在数据库中不可用也是如此。 以前，此操作在创建空购物车时由于国家/地区验证问题而失败。

_ACP2E-3255 - [GitHub代码贡献](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [GraphQl]愿望清单项通过GraphQl可见，但在店面中不可见

通过GraphQL请求时未正确列出的愿望清单产品。 现在，会根据提供的商店上下文过滤愿望清单产品。

_ACP2E-3380 - [GitHub代码贡献](https://github.com/magento/magento2/commit/55615e61)_

#### [GraphQL]重置内容与主题/链接之间的密码电子邮件不一致

通过模拟在发送密码重置请求时客户帐户注册的正确商店（与网站商店无关），该问题已得到解决。

_ACP2E-3404 - [GitHub代码贡献](https://github.com/magento/magento2/commit/5184c067)_

#### [Cloud]产品GraphQL查询返回未分配到当前网站的相关产品

以前，对于graphQL查询，与多商店相关的产品无法正确显示在产品查询中。 应用此修复后，对于产品，graphQL会查询多商店相关产品并相应地显示。

_ACP2E-3419 - [GitHub代码贡献](https://github.com/magento/magento2/commit/078c387e)_

#### 在GraphQL标头中使用错误的Store ID会导致内存错误

在GraphQL请求中发送错误的存储代码不会再导致内存消耗过多。

_ACP2E-3447 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d50f6b5d)_

#### [Cloud] 500响应2.4.7上的空Graphql响应

修复后，无效的graphql请求将不会记录到exception.log文件中。

_ACP2E-3467 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1984c61c)_

#### Graphql API存在[Cloud]问题

在使用Graphql应用程序服务器进行修复之前，客户地址请求未返回最新数据。

_ACP2E-3492 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3f12d152)_

#### 已禁用的产品仍显示在graphQL查询中的相关、向上销售、交叉销售商品中

Graphql现在为禁用的相关、追加销售和交叉销售产品提供了正确的响应

_ACP2E-3505 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d4de4726)_

#### [CLOUD]： GraphQl错误内部服务器错误placeOrder突变

请求中包含优惠券代码信息的“placeOrder”突变不再引发内部错误异常，订单已成功下达。 以前，它失败并出现“内部服务器错误”。

_ACP2E-3647 - [GitHub代码贡献](https://github.com/magento/magento2/commit/982b1c42)_

#### 不会为具有动态价格的捆绑产品计算discount_percentage

为product.price_details的discount_percentage添加了修复程序，该程序无法显示已启用动态价格并应用折扣优惠券的捆绑产品的正确值。

_LYNX-426_

#### 当捆绑产品的某个捆绑产品缺货时，捆绑产品仍会显示“IN_STOCK”

解决了捆绑产品即使在其捆绑产品之一缺货时仍显示“IN_STOCK”的问题。

_LYNX-485_

#### not_available_message和only_x_left_in_stock不显示相同的可用库

解决了not_available_message和only_x_left_in_stock显示库存可用性不一致的问题

_LYNX-486_

#### original_row_total字段返回了错误值

解决了original_row_total字段的问题，在选择自定义选项时，该字段会返回不正确的值

_LYNX-488_

#### 应根据配置显示已分组的产品缩略图     .

解决了确保根据配置设置显示分组产品缩略图的问题

_LYNX-503_

#### 在OrderAddress中查询selected_options时出错

在订单地址GraphQL响应中将AttributeSelectedOptions更新为custom_attributesV2。

_LYNX-510_

#### original_item_price不包含折扣

更新了original_item_price以包含折扣。

_LYNX-512_

#### “不可用”消息未显示可用库存数量

解决了AddProductsToCart突变的错误消息和错误代码以与“不可用”消息配置一致

_LYNX-530_

#### “OUT_OF_STOCK”状态返回“简单，带有自定义选项”产品具有多选选项

更新了库存包中的StockStatusProvider解析程序，以修复具有自定义选项的简单产品的stock_status。

_LYNX-532_

#### 错误(GQL)： cart.itemsV2.items.product.custom_attributesV2返回服务器错误

通过添加不含任何自定义属性的产品，解决了当购物车查询包含产品的自定义属性时发生的服务器错误。

_LYNX-533_

#### orders/date_of_first_order始终返回null

解决了订单> date_of_first_order始终返回null的问题。

_LYNX-536_

#### 客户不能取消部分发运的订单

添加了验证，以限制客户取消部分发运的订单。

_LYNX-544_

#### 基于错误消息的订单取消的错误代码

现在，订单取消的错误代码基于特定的错误消息。

_LYNX-548_

#### 将与该Cookie相关的属性从私有移回受保护属性

将Magento\Framework\App\PageCache\Version类构造函数属性的可见性从private还原为protected

_LYNX-581_

#### 将默认GraphQL查询的最大复杂性增加到1000

将默认最大GraphQL查询复杂性从300提高到了1000。

_LYNX-600_

#### GQL - itemsV2 >原始行总计，对于具有单独价格的文件选项的可下载产品，价格范围价格返回为$0.00。

解决了启用了单独链接购买选项的可下载产品在itemsV2 >原始行总计时返回$0的问题，对于具有单独价格的文件选项的产品，价格范围返回为$0.00。

_LYNX-620_

#### 创建时表的模式与升级时不同的全新模式

解决了由于新安装和升级之间的模式差异而导致向现有表添加新的VARCHAR列导致测试失败的问题。 modifyColumn()方法现在通过设置默认字符集和排序规则来正确处理VARCHAR列。

_LYNX-711_

#### PHP-8.4版本的GraphQl兼容性

修复了跨多个解析器的GraphQL与PHP 8.4的兼容性问题，以确保流畅的功能。 更新了CatalogRule、Customer、GiftMessage、GiftCard和GiftWrapping模块中受影响的文件。

_LYNX-772_

### GraphQL、库存/MSI

#### 当源购物车和目标购物车具有相同的捆绑项目时，MergeCart突变会引发异常

&#39;-

_ACP2E-2607 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c971859e) - [GitHub代码贡献](https://github.com/magento/inventory/commit/db0620da)_

### GraphQL、库存/MSI、性能

#### 升级后站点已关闭

提高了通过GraphQl获取捆绑产品的性能。

_ACP2E-1716 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ba25af8a) - [GitHub代码贡献](https://github.com/magento/inventory/commit/bdbf97ea)_

### GraphQL，性能

#### [GraphQL解析程序]客户解析程序数据未从导入中失效

现在，在通过导入编辑或删除客户时，GraphQL客户解析器缓存会按预期失效。 以前，缓存不会失效，并且可以在导入期间编辑或删除客户数据。

_AC-9569 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0574ac23)_

### GraphQL，搜索

#### 按多个参数排序的GraphQL产品列表不起作用

GraphQl中按多个字段对产品排序现在按文档中的说明工作

_ACP2E-2809 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c971859e)_

#### 产品列表GraphQL查询仅限于total_count 10,000个产品

修复后，搜索结果不再局限于10000个产品，即使计数超过10000，也可以获得所有符合搜索条件的产品。

_ACP2E-948 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a4cf5e62)_

### GraphQL，测试框架

#### Magento\GraphQl\App\GraphQlCustomerMutationsTest.php集成测试失败

&#39;-

_ACP2E-3363 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a4cf5e62)_

### 导入/导出

#### 在产品导入时的问题，当提供了自定义选项类型时： file（创建的产品不包含自定义选项的价格，并且仅显示提供的第一个文件类型扩展名）

现在，系统可正确导入包含“文件”类型自定义选项的产品数据，从而确保显示所有提供的文件扩展名并包含自定义选项的价格。 以前，在产品导入过程中，如果为“file”类型的自定义选项提供了多个文件扩展名，则只显示第一个扩展名，并且缺少自定义选项的价格。

_AC-12172 - [GitHub问题](https://github.com/magento/magento2/issues/38805) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38926)_

#### 导入历史记录网格中导入操作的执行时间错误

导入报表执行时间正确显示，与管理员区域设置无关。

_ACP2E-2710 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ea79f7dd)_

#### 正在使用导入的同一电子邮件地址创建重复客户

在帐户共享设置为全局时导入客户，更新系统中存在的导入客户。
之前导入的客户重复。

_ACP2E-2737 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c971859e)_

#### 产品添加/更新导入复制可自定义选项

通过在产品选项CSV导入过程中将正确的存储分配给产品选项，该问题已得到解决。
以前，分配给管理员存储，而不是其各自的存储。

_ACP2E-2902 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3a7c4d17)_

#### 客户“created_at”日期未在导出时转换为存储时区

“created_at”列的日期值会根据客户导出CSV部分中的存储时区转换为正确的日期格式。

_ACP2E-2990 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3056e9cb)_

#### 使用CSV检查导入数据中的数据时出现[云]获取错误

在CSV导入期间检查数据时没有错误。 以前，使用管理员的CSV检查导入部分中的数据时显示的错误消息是：“我们在以下行中找不到与此电子邮件和网站代码匹配的客户： 1”。

_ACP2E-3165 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8459b17d)_

#### 导入按钮缺失

解决在对CSV中正确和不正确记录的数据进行检查后导入按钮缺失的问题。 以前，在对CSV中正确和不正确记录的数据进行检查后，导入按钮不会显示。

_ACP2E-3172 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1819fe73)_

#### 无法导入导出的客户地址

客户地址导入将按预期进行。 以前，如果共享客户帐户=全局，客户地址导入文件将不会通过验证，并且有两个网站（默认网站有一个受限制的国家/地区列表）的导入地址适用于另一个允许国家/地区不同的网站

_ACP2E-3382 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [云] CSV文件中的错误数量未产生错误

现在，导入库存源将引发对数量列中的非数字值的验证错误。 以前，在数量列中导入具有非数字值的库存源会导致数量设置为0。

_ACP2E-3448 - [GitHub代码贡献](https://github.com/magento/inventory/commit/5b21b7af)_

#### 导入产品时生成的URL密钥重复错误消息在URL密钥已属于某个类别时不正确

在产品导入检查期间显示正确的错误消息（当客户尝试导入产品时，产品的url密钥已属于类别）。

_ACP2E-3455 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d4de4726)_

#### 产品导出导致OOM，即使内存限制为4G

在此修复之前，如果产品属性具有数千个选项值（即使具有4G可用内存），则产品导出失败。 进行此修复后，产品导出应会完成导出csv文件。

_ACP2E-3475 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1984c61c)_

#### [云]导入进程相互干扰

如果同一管理员用户使用同一用户会话执行两项或更多导入操作，则会显示正确的消息。

_ACP2E-3527 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d4de4726)_

### 导入/导出，性能

#### [云]产品导入时间显着增加

在此修复之前，包含超过10,000个条目的目录产品导入会显着降低时间。 修复后，及时执行目录产品导入。

_ACP2E-3476 - [GitHub代码贡献](https://github.com/magento/magento2/commit/87d012e5)_

### 安装和管理

#### Magento在MariaDB 11.4 + 2.4.8-beta1上升级失败

升级应该没有发生任何错误。

_AC-13242 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7b336d0a)_

#### 管理面板中的“No Export VCL for Varnish 7”按钮

“Export VCL for Varnish 7”按钮已添加到“管理”面板中。

_ACP2E-2102 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a4fbf702)_

### 库存/MSI

#### 当数据库使用前缀时，可配置产品的清单更新失败

现在，当数据库使用前缀时，系统可正确更新可配置产品的清单，防止出现任何错误消息并确保保存正确的数量。 以前，如果数据库使用前缀，则在尝试保存可配置产品中简单产品的库存数量时会出错。

_AC-10750 - [GitHub问题](https://github.com/magento/magento2/issues/38045)_

#### 添加带有属性的映射时，Google google API密钥不起作用

系统现在支持最新的Google Maps API版本3.56，使用户能够成功地将PageBuilder菜单中的Map内容块添加到舞台，而不会遇到任何错误。 以前，由于Google地图API版本存在兼容性问题，用户无法添加地图内容块，从而导致“出现问题”错误消息。

_AC-11593 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0574ac23)_

#### 无法为具有多个来源且SKU已损坏的订单项目创建装运

以前，通过数据库错误地在SKU中添加空格会导致发货页面出错，该错误现已修复，并且自动修剪被视为人性化的错误，未发现任何影响。因此，已成功创建发货。

_AC-13922 - [GitHub代码贡献](https://github.com/magento/inventory/commit/c18eb5fa)_

#### [测试]在商店前端显示库存为0的捆绑产品

捆绑产品未使用其他库存显示在其他网站上。

_ACP2E-1411_

#### [Cloud]产品列表存在严重问题，但空格为空

现在，当产品设置为“缺货”时，系统可正确显示产品清单，且不含空格，从而确保一致、准确地显示可用产品。 以前，将产品设置为“缺货”会导致产品列表中显示空白，中断布局并可能使客户感到困惑。

_ACP2E-2794 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ea79f7dd) - [GitHub代码贡献](https://github.com/magento/inventory/commit/b59e48ca)_

#### 启用MSI提货存储时无法装运订单

提高了库存性能，可在存在许多店内取货来源的情况下创建送货

_ACP2E-3335 - [GitHub代码贡献](https://github.com/magento/inventory/commit/9f3e63d1)_

#### Cron重新索引无法更新前端产品可用性

以前，通过REST API更新延交状态后，产品在前端保持缺货。 现在，通过REST API更新延交状态后，产品将显示为有货。

_ACP2E-3355 - [GitHub代码贡献](https://github.com/magento/inventory/commit/e6fe0aa7)_

#### 启用MSI时，将图像添加到可配置项无法正常工作。

现在，当使用库存模块时，可配置产品的图像上传将按预期工作。 以前，图像上传不起作用

_ACP2E-3357 - [GitHub代码贡献](https://github.com/magento/inventory/commit/fdf409aa)_

#### 清理M2.4.7-p3中的捆绑产品+ MSI问题

以前，对于与同一简单产品重复后的库存捆绑产品，无法保存该简单产品。 应用此修复后，简单产品可顺利保存，不会出现任何异常。

_ACP2E-3470 - [GitHub问题](https://github.com/magento/magento2/issues/39358) - [GitHub代码贡献](https://github.com/magento/inventory/commit/0208e433)_

### 库存/MSI、搜索

#### 当SKU未设置为可搜索属性时，所有产品都使用[is_out_of_stock] = 1编制索引

修复后，即使在sku不可搜索的情况下，目录搜索索引中的“is_out_of_stock”也是正确的。

_ACP2E-3413 - [GitHub代码贡献](https://github.com/magento/inventory/commit/5b21b7af)_

### 订购

#### 后端订单概览屏幕：在订单物料层上看不到延交数量

现在，系统在后端订单概览屏幕的数量列中显示延交项目数。 这可确保用户能够准确地跟踪按顺序排列的所有项目的状态。 以前，“数量”列只显示已订购、开票和发运的项目数，而不显示延交项目数。

_AC-10828 - [GitHub问题](https://github.com/magento/magento2/issues/38252) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38320)_

#### [问题]订单地址呈现器中使用了错误的存储ID

现在，系统在呈现订单地址时，可正确使用与订单关联的商店ID，从而确保根据相应的商店ID正确格式化地址。 以前，系统错误地使用当前商店ID，在需要发送来自不同商店的多份订单电子邮件时，可能会导致地址格式不正确。

_AC-10994 - [GitHub问题](https://github.com/magento/magento2/issues/38412) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37932)_

#### JoinProcessor缓存问题

现在，系统可正确地将联接处理器应用于每个迭代（即使连续调用），从而确保准确的数据检索。 以前，JoinProcessor被错误地标记为已在连续迭代中应用，导致数据检索出错。

_AC-11690 - [GitHub问题](https://github.com/magento/magento2/issues/27504) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37550)_

#### [问题]发货价格显示打印的PDF中的差异

现在，系统会根据税务配置设置以打印的PDF正确显示发运价格，从而确保销售订单发票视图页与打印发票之间的一致性。 以前，无论税配置设置如何，打印的PDF中显示的运费不含税。

_AC-11798 - [GitHub问题](https://github.com/magento/magento2/issues/38608) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38595) - [GitHub代码贡献](https://github.com/magento/magento2/commit/1bafc571)_

#### 使用已删除的父可配置产品重新排序

现在，使用已删除的产品重新订购时，系统不会显示要重新订购的重新订购按钮

_AC-13839 - [GitHub问题](https://github.com/magento/magento2/issues/39568) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39601)_

#### [问题]修复错误\Magento\Sales\Model\Order\Email\Container\Template：：$id属性

这修复了\Magento\Sales\Model\Order\Email\Container\Template：：$id的错误phpdoc，实际上$id是type int，但实际上是string。

_AC-13924 - [GitHub问题](https://github.com/magento/magento2/issues/39151) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39150)_

#### 无法在现有订单详细信息中保存对电话号码的更改

现在，用户可以在订购地址的电话字段中添加国际前缀00

_ACP2E-2622 - [GitHub问题](https://github.com/magento/magento2/issues/38201) - [GitHub代码贡献](https://github.com/magento/magento2/commit/12e071c3)_

#### 电子邮件无法发送

系统现在包括一个配置选项async_sending_attempts ，用于指定在停止前尝试发送电子邮件的次数，从而改进在启用“异步发送”时处理失败的电子邮件发送的方式。 以前，如果电子邮件发送失败，系统将不断尝试重新发送，导致系统日志中出现无休止的错误消息循环。

_ACP2E-2734 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b2286ecf)_

#### 部分退回部分发运的订单时，[云]订单状态更改为完成

在发放贷项通知单时，如果存在尚未发运的项目，则订单状态不再更改为“已完成”。

_ACP2E-2756 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7e0e5582)_

#### [CLOUD]无法禁用从管理员UI发送电子邮件，如开发文档所示

现在，系统可正确防止在电子邮件通信被禁用时发送销售电子邮件。 重新启用电子邮件通信后，将不再发送这些电子邮件。 以前，在电子邮件通信被禁用时发起的销售电子邮件，在电子邮件通信重新启用后仍会发送。

_ACP2E-3002 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c8931218)_

#### 未全额退款的订单已结

当具有未捕获付款的订单已创建发运时，系统现在将订单状态正确维护为“正在处理”，将发票状态正确维护为“待定”。 这可确保在全额退款后只将订单标记为“已结”。 以前，为具有待定发票的订单创建发运会错误地将订单状态更改为“已关闭”。

_ACP2E-3045 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6a185204)_

#### [Cloud]如果仅未设置默认帐单地址，则无法在一个商店的管理员中创建订单

现在，相关的错误消息“关联网站中已存在具有相同电子邮件地址的客户”。 如果客户没有默认帐单地址，但尝试在其他商店中创建订单，则会显示。

_ACP2E-3311 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d75cff27)_

#### 已发送管理员重复下单请求

以前，您可以多次单击管理面板中的“提交订单”按钮，或通过反复按“Enter”键来激活该按钮，从而导致重复提交或提交订单时出现错误。 现在，会阻止执行其他操作，直到完全处理完订单，从而确保仅提交一个订单。

_ACP2E-3416 - [GitHub代码贡献](https://github.com/magento/magento2/commit/5184c067)_

#### 即使没有付款方式，管理员仍然可以下订单

现在，当付款方法重新出现在可用付款列表中时，将保留以前选择的付款方法。

_ACP2E-3425 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d50f6b5d)_

#### 在从Mozilla Firefox浏览器的“管理员”创建订单后，项目重复

在admin中创建订单时，在Firefox中不再重复使用“按SKU添加产品”添加的产品。

_ACP2E-3518_

### 订单，支付

#### 即使没有付款方式，管理员仍然可以下订单

以前，商家可以从管理员面板下订单，而无需选择支付方式。 现在，商家需要一种支付方式才能继续下订单。

_ACP2E-3233 - [GitHub代码贡献](https://github.com/magento/magento2/commit/fd5cf3af)_

### 订单，退货

#### 订单退款导致贷项通知单重复

在同时执行两个相同的请求时通过REST API发出退款将不再创建重复的贷项通知单。

_ACP2E-2982 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a4fbf702)_

### 订单，税金

#### [CLOUD]启用跨境交易并应用优惠券折扣时，RESTFUL订单API中的base_row_total不正确

现在，在启用跨境交易并应用了优惠券折扣的情况下，从RESTFUL订单API返回正确的base_row_total。

_ACP2E-3003 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9af794a4)_

### 其他

#### [Braintree]退款联机存储事务为transactionid-refall

_BUNDLE-3394_

#### [Braintree] + [CLOUD] Braintree（信用卡）订单无法分摊费用

_包–3421_

#### [Braintree] [Cloud]Braintree SSL证书将于6月30日前过期

_BUNDLE-3422_

#### GQL查询中返回的private_content_version Cookie

修复了在GraphQL查询中返回private_content_version Cookie（即使会话Cookie已禁用）的问题。 当会话按预期禁用时，GraphQL响应中将不再包含该Cookie。

_LYNX-339_

#### 物理礼品卡查询中电子邮件prop的服务器错误

修复了在物理礼品卡上查询sender_email和recipient_email时导致服务器错误的问题。 现在，这些prop可正确返回虚拟礼品卡，并且查询行为保持一致。

_LYNX-366_

#### 对于可配置产品，CartItemInterface中的is_available属性始终返回false

修复了CartItemInterface中的is_available属性对于库存中的可配置产品始终返回false的问题。 现在，在适用的情况下，它正确地将可用性反映为true。

_LYNX-380_

#### 即使可销售库存低于产品的数量，CartItemInterface中的is_available属性也会返回true

修复了即使在购物车项目数量超过可销售库存时，CartItemInterface中的is_available属性也会错误地返回true的问题。

_LYNX-382_

#### ProductInterface中的only_x_left_in_stock属性在可配置产品上不准确

修复了ProductInterface中的only_x_left_in_stock属性无法准确反映购物车中可配置产品变体的可用库存的问题。 现在， only_x_left_in_stock值正确对应于实际变型库存水平，从而确保在Cart GQL查询中返回准确的库存数据。

_LYNX-395_

#### 将简单产品添加到分组产品中的购物车时，会返回占位符缩略图

修复了将简单产品（分组产品的一部分）添加到购物车时返回占位符缩略图图像的问题，即使产品已分配图像。
修复详细信息：
- 现在，产品缩略图可正确显示分配的图像（如果可用）。
- 缩略图选择遵循下的管理员配置：
商店>配置>销售>结账>购物车>分组的产品图像。
这可确保根据商店设置对分组产品执行一致的缩略图行为。

_LYNX-399_

#### 客户的自定义选项属性不适用于整数值

修复了在返回值为整数时，客户的自定义选项属性不起作用的问题。 现在，自定义选项可正确处理并按预期返回整数值。

_LYNX-400_

#### 尝试获取具有动态价格的捆绑产品的价格详细信息时出现内部服务器错误

解决了通过GraphQL查询具有动态定价的捆绑产品的price_details时导致内部服务器错误的问题。 此增强功能可在使用配置有动态定价的捆绑产品时确保稳定的购物车查询。

_LYNX-402_

#### 对于可配置产品，only_x_left_in_stock始终返回0

解决了使用带有选项的父SKU添加时，对于可配置产品，only_x_left_in_stock属性始终返回0的问题。
修复详细信息：
- only_x_left_in_stock值现在可准确反映所选子变体的库存，而不是父SKU的库存。
- 这确保在购物车和产品页面中正确显示可配置产品变体的库存水平。

_LYNX-403_

#### GraphQL错误：可自定义选项查询中不支持的“file”类型

修复了GraphQL在购物车项目中对类型为“file”的可自定义选项返回错误的问题。 现在，查询可正确返回所有可自定义选项类型的详细信息（包括基于文件的选项），而不会导致错误。

_LYNX-405_

#### GraphQL查询未返回可自定义产品的正确计算常规价格

修复了GraphQL未针对可自定义产品返回正确计算的正常价格的问题。 现在，查询会在prices属性中正确包含计算出的正常价格以及应用的自定义值（例如$125），这既反映了基本价格，也反映了任何其他自定义成本。

_LYNX-411_

#### AppliedTaxes（通过EstimatedTotals计算）会随着更新的突变而保留

修复了EstimatedTotals突变的问题，该问题导致即使在更新区域或邮政编码后，购物车中仍保留已应用的税种。 现在，当在区域和邮政编码值之间更改时，此突变可正确更新应用的税种，从而确保仅根据当前购物车数据应用正确的税则。

_LYNX-412_

#### 即使可销售库存低于产品的数量，CartItemInterface中的is_available属性也会返回true

修复了即使可销售库存低于请求的产品数量，CartItemInterface中的is_available属性也会错误地返回true的问题。 现在，当产品的数量超过可用库存时，is_available字段会正确返回false 。

_LYNX-420_

#### 无法将优惠券添加到购物车，仅提供配送折扣

修复了无法为购物车应用优惠券以获得仅配送折扣的问题。 现在，当使用不含产品条件的销售规则时，优惠券将正确应用于装运金额，从而确保将预期折扣应用于装运成本。

_LYNX-421_

#### 带12位小数和错误值的产品正常价格

修复了在应用多个税率时，product.price_range.maximum_price和minimum_price GraphQL路径中的regular_price值与目录价格不匹配的问题。 regular_price现在可以始终如一地反映所有税务配置的目录价格，从而确保购物车汇总中准确的单价、总行成本计算和折扣检查。

_LYNX-425_

#### 捆绑产品缺货的购物车出现GraphQL服务器错误

修复了以下问题：在获取包含捆绑产品以及缺货项目的购物车时，GraphQL返回了内部服务器错误，尤其是当查询包含itemsV2属性时。 GraphQL现在可以按预期正确返回项目列表，并在捆绑的产品项目条目中附加相关错误消息。

_LYNX-430_

#### 无法创建具有自定义属性的地址

修复了createCustomerAddress突变的问题，该问题阻止使用所需的自定义属性创建地址。 现在，当提供相应的有效负载时，该突变可正确处理自定义地址属性。

_LYNX-441_

#### 捆绑产品上仅带有only_x_left_in_stock的购物车上出现GraphQL服务器错误

修复了获取购物车时导致内部服务器错误的问题，该购物车包含GraphQL查询中具有only_x_left_in_stock字段的捆绑产品。 GraphQL现在可以正确为only_x_left_in_stock字段返回浮点值或空值，而不会出现错误。

_LYNX-447_

#### 删除购物车中可配置产品不足的其他产品时GraphQL出错

修复了以下问题：如果购物车还包含库存不足的可配置产品，则尝试从购物车中删除库存产品会导致“请求的数量不可用”GraphQL错误。 现在，删除操作可按预期运行，而不会触发错误。

_LYNX-464_

#### 由于突变中的SKU区分大小写，因此无法添加产品

解决了在使用具有不同大小写的SKU时，addProductsToCart突变返回“PRODUCT_NOT_FOUND”错误的问题。 该突变现在处理SKU不区分大小写，确保与目录服务查询和PDP行为一致。

_LYNX-469_

#### 产品属性>商标简短形式&amp;amp；trade；返回为&amp;amp；trade；

解决了GraphQL API的产品名称存在的字符编码问题

_LYNX-603_

#### updateCustomerEmail突变问题

解决了updateCustomerEmail突变的问题，该问题导致没有所需自定义属性（在创建帐户后添加）的客户无法更新其电子邮件。

_LYNX-619_

#### 使用pickup_location_code时，突变setShippingAddressesOnCart引发错误

修复了在使用pickup_location_code但未指定customer_address_id或address时，setShippingAddressesOnCart突变返回错误的问题。 现在，此突变可正确设置仅包含pickup_location_code的配送地址。

_LYNX-626_

#### CustomerOrder.items_eligible_for_return列表必须与订单项目一致

解决了订单中退货资格不一致的问题：
1. CustomerOrder.items_eligible_for_return列表现在与实际订单项目一致。
2. 如果已经返回了全部数量，则OrderItemInterface.eligible_for_return字段会正确返回false。
3. 现在，CustomerOrder.items_eligible_for_return只包括尚未在退货流程中的物料。

_LYNX-627_

#### 添加quantity_return_requested字段

向OrderItemInterface添加了quantity_return_requested字段，使您可以确定已提交退货的物料数量。 这样可以增强现有quantity_returned字段的退货跟踪。

_LYNX-628_

#### 在为全部数量物料创建退货之后，可用订单操作不得包含RETURN

修复了在为所有物料创建完全退货之后，GraphQL customer.orders查询中的available_actions字段错误地包含RETURN的问题。 现在，返回过程完成后，将正确删除RETURN操作。

_LYNX-634_

#### 店面兼容性 — 更新逻辑以获取带前缀的表名称以及其他一些小的改进

更新了用于检索带有前缀的表名的逻辑（与SCP更改相关）。

_LYNX-637_

#### 使用setBillingAddressOnCart GQL的same_as_shipping字段时，“保存在通讯簿中”不起作用

修复了在将same_as_shipping字段设置为true的情况下使用setBillingAddressOnCart GraphQL突变时，配送地址未保存到客户通讯簿中的问题。 现在，送货地址已按预期正确存储。

_LYNX-643_

#### 标准化突变中的order_id

突变地标准化了order_id输入，并更新了订单取消确认电子邮件模板，以公开增量id而不是订单id。

_LYNX-650_

#### 客户订单未显示订单注释

解决了CustomerOrder在来宾和客户订单GraphQL查询中包含订单注释的问题。

_LYNX-651_

#### original_item_price不得包含任何折扣

更新了GraphQL购物车项目价格中original_item_price的逻辑以排除折扣。

_LYNX-652_

#### 当捆绑产品的某个捆绑产品缺货时，捆绑产品仍会显示“IN_STOCK”

解决了即使某个捆绑产品缺货，捆绑产品的product.stock_status仍显示“IN_STOCK”的问题。

_LYNX-681_

#### 如果某个客户存在已删除自定义属性的值，则客户查询返回内部服务器错误

修复了以下问题：当删除的自定义属性仍然具有存储值时，客户查询返回内部服务器错误。 现在，如果请求不存在的属性，则会返回正确的错误消息。 删除客户自定义属性时，必要的缓存将失效。

_LYNX-686_

#### 用于返回和取消确认链接的操作参数

为返回和取消确认电子邮件相关链接添加了操作参数

_LYNX-687_

#### 访客用户确认URL被重定向到订单状态页面，因为它缺少orderRef（对于GuestRMA）

向来宾RMA确认电子邮件中的链接添加了orderRef参数

_LYNX-688_

#### 访客用户确认URL被重定向到订单状态页面，因为它缺少orderRef

向来宾订单取消确认电子邮件中的链接添加了orderRef参数

_LYNX-689_

#### 禁用RMA时客户查询出现问题

更新了GraphQL逻辑，以确保即使全局禁用RMA，以前创建的返回结果仍然可访问。 错误消息已移除，以改进店面UX，确保客户仍然可以查看其过去的退货。

_LYNX-690_

#### 应用冲突优惠券时，GraphQL未返回更新的购物车数据

修复了应用具有更高优先级的冲突优惠券时导致出现错误消息而不返回更新后的购物车数据的问题。 现在，当新的优惠券使现有优惠券失效时，该突变会正确返回应用了有效优惠券的购物车。

_LYNX-696_

#### 无法为placeOrder GQL上的不可为空字段“TaxItem.title”返回null

修复了由于不可为空的字段TaxItem.title的值为null而导致placeOrder突变失败并出现内部服务器错误的问题。 现在，字段始终会返回有效值，以确保成功下订单。

_LYNX-699_

#### 估计总数：虚拟产品类型的折扣为Null

解决了将折扣代码应用于包含虚拟产品的购物车时，estimateTotal突变为折扣返回null的问题。

_LYNX-702_

#### 捆绑产品未返回正确的折扣百分比和金额

目录项目价格的新属性“catalog_discount”和“row_catalog_discount”已引入，以便在行层和单个项目层显示正确的折扣金额和百分比。

_LYNX-703_

#### 产品级别的礼品消息配置

修复了全局禁用时，未在产品级别应用礼品消息的问题。 现在，如果为特定产品启用了礼品消息，则可使用updateCartItems突变成功添加这些消息，并且可以正确保存并反映这些消息。

_LYNX-714_

#### 从购物车项目中删除礼品包装时出现问题

修复了使用updateCartItems突变从购物车项目中删除礼品包装无法按预期工作的问题。 现在，正确应用和删除礼品包装功能且没有错误。

_LYNX-717_

#### 匹配的注册客户功能在Boilerplate中不起作用，需要为来宾启用trackViewedProduct突变。

公开trackViewedProduct突变以跟踪客户和嘉宾的产品查看事件

_LYNX-751_

#### 如果没有应用活动的购物车规则，cart.rules查询返回错误而不是空数组

修复了cart.rules查询的问题，该查询在没有应用活动购物车规则时返回空数组而不是错误。

_LYNX-757_

#### 检索购物车物料的礼品包装时出现问题

更新了检索逻辑，以便在全局禁用但在产品级别启用时返回购物车项目的礼品包装选项

_LYNX-758_

#### 安装adobe-commerce/storefront-compatibility包后，使用OPTIONS方法的GraphQL调用返回500响应代码

修复了在安装adobe-commerce/storefront-compatibility包时，使用OPTIONS方法的GraphQL调用返回500内部服务器错误的问题。 现在，端点可按预期正确返回200/204响应。

_LYNX-778_

### 其他开发人员工具

#### [问题]修复visual.phtml中的HTML语法错误

现在，系统会正确关闭visual.phtml文件中的开始标记，从而确保HTML语法正确。 以前，start标记未正确关闭，从而导致HTML语法错误。

_AC-10658 - [GitHub问题](https://github.com/magento/magento2/issues/38247) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37457)_

#### [问题]在bin/magento维护:status命令中将“活动”更改为“已启用”

系统现在为维护模式命令提供更准确的状态消息，将状态从“活动”更改为“已启用”，从“非活动”更改为“已禁用”。 以前，维护模式命令的状态消息显示为“活动”或“非活动”，这可能会导致混淆。

_AC-11474 - [GitHub问题](https://github.com/magento/magento2/issues/38486) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38410)_

#### 导航到类别树会导致Redis中出现错误：“Redis会话超出并发连接数”

_AC-12571 - [GitHub问题](https://github.com/magento/magento2/issues/38851) - [GitHub代码贡献](https://github.com/magento/magento2/commit/0611e750)_

#### 与dev/css/use_css_critical_path结合使用的CSP问题

现在，即使启用了&quot;dev/css/use_css_critical_path&quot;设置，系统也会在签出页面上正确异步加载CSS文件，从而确保这些页面使用正确的CSS样式呈现。 以前，受限制的内容安全策略(CSP)阻止执行内联JavaScript，这导致CSS文件无法按预期加载。

_AC-12731 - [GitHub问题](https://github.com/magento/magento2/issues/39020) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39040)_

#### 使用虚拟类型配置插件，无法在`setup:di:compile`命令中正确生成侦听器方法

现在，当使用虚拟类型配置插件时，系统可正确生成拦截器方法，从而确保无论是预编译的结果还是运行时编译的结果都一致。 以前，与运行时编译相比，在预编译时，系统会产生不正确的结果。

_AC-13398 - [GitHub问题](https://github.com/magento/magento2/issues/33980) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38141)_

#### Adobe Commerce 2.4.7-p3单元测试失败

无需发行说明。

_ACP2E-3631 - [GitHub代码贡献](https://github.com/magento/magento2/commit/982b1c42)_

### 付款/付款方式、订单

#### 付款流保存以供以后使用的信用卡详细信息未显示在存储的付款方法页面上

以前的纸质付款流保存供以后使用的信用卡详情未显示在存储的付款方式页面上，而现在固定的信用卡详情则显示在存储的付款方式页面上。

_AC-13699 - [GitHub代码贡献](https://github.com/magento/magento2/commit/96dec499)_

### 支付

#### 信用卡（Payflow链接）付款不起作用

较早获取错误（付款被拒绝）在成功下固定订单后使用信用卡下订单。

_AC-13414 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a68324bc)_

#### 每次单击“查看事务处理”屏幕上的提取按钮时，Payflow都会创建新事务处理

现在，每次在查看交易屏幕上单击提取按钮时，系统都能正确提取交易信息，而无需创建新的支付交易。 以前，单击“提取”按钮会错误地为已支付的订单创建新的支付交易记录。

_ACP2E-2841 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b2286ecf)_

#### 加拿大Paypal商家帐户的Paylater报文未显示在PDP中

现在，当可以根据帐户帐单地址或发运确定买方的国家/地区时，系统会在产品详细信息页(PDP)上正确显示加拿大PayPal商家帐户的PayLater消息。 以前，由于缺少参数，不会显示PayLater消息，这会导致浏览器控制台中出现错误。

_ACP2E-3028 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6a185204)_

#### PayPal订单退款导致重复的贷项通知单

修复了IPN为PayPal付款服务创建的贷项通知单并发问题。

_ACP2E-3143 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d01ee51e)_

#### 购物车价格规则不适用于Paypal

当通过付款方式应用折扣时，正确的金额显示在PayPal端

_ACP2E-3163 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7377de59)_

#### [Cloud]具有特定角色的用户无法登录

现在，其角色仅包含PayPal部分访问权限的管理员用户可登录，且不会出现错误

_ACP2E-3208 - [GitHub代码贡献](https://github.com/magento/magento2/commit/66dea0de)_

### 性能

#### 默认产品属性设置问题

现在，系统允许用户取消选择产品属性的默认选项，确保该属性并不总是有默认设置。 以前，一旦为产品属性设置了默认值，就无法取消选择它，从而导致该属性始终具有默认设置。

_AC-11932 - [GitHub问题](https://github.com/magento/magento2/issues/38703) - [GitHub代码贡献](https://github.com/magento/magento2/commit/7d5e3906)_

#### [问题]代码清理并添加新的关键标题块并将关键css移动到资产之前

该系统现在包括新的关键头块，并将关键CSS移动到资产之前，允许在前端进行更多自定义和性能优化。 以前，关键CSS不放在资产之前，从而限制了自定义和优化机会。

_AC-12000 - [GitHub问题](https://github.com/magento/magento2/issues/38748) - [GitHub代码贡献](https://github.com/magento/magento2/pull/35580)_

#### 当mysql主机包含端口信息时，主题编译中断

系统现在可以正确处理包含端口信息的MySQL主机配置，确保主题编译成功。 以前，如果数据库连接中的MySQL主机配置包含端口信息，则主题编译将失败。

_AC-12176 - [GitHub问题](https://github.com/magento/magento2/issues/38799) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38842)_

#### 在Magento CLI中支持Symfony的CommandLoaderInterface

此项更改允许延迟初始化命令，直到需要这些命令为止，从而缩短了Magento CLI应用程序的初始化时间。

_AC-13471 - [GitHub问题](https://github.com/magento/magento2/issues/29266) - [GitHub代码贡献](https://github.com/magento/magento2/pull/29355)_

#### 在购物车规则中加载产品属性时的性能问题

改进了销售规则的查询性能 — 从大约150毫秒提高到一位数ms。

_ACP2E-2494 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ba25af8a)_

#### 价格部分索引性能

通过优化索引过程中使用的一些删除查询，改进了价格部分索引性能。

_ACP2E-2673 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ba25af8a)_

#### 使用异步订单处理+条款和条件时，在多商店设置中订单被拒绝

现在，将会处理从启用了条款和条件的非默认网站下达的订单。
在它们被自动拒绝之前。

_ACP2E-2850 - [GitHub代码贡献](https://github.com/magento/magento2/commit/57a32313)_

#### Order Rest API调用需要很长时间才能执行

现在，系统在合理的时间范围内执行Order Rest API调用，从而提高获取大量订单时的性能。 以前，Order Rest API调用执行时间较长，导致在检索大量订单时出现延迟。

_ACP2E-2910 - [GitHub代码贡献](https://github.com/magento/magento2/commit/001e5188)_

### 绩效、提升

#### 销售规则索引器已停止运行

现在，即使有大量合并的过滤器组，系统也能成功完成销售规则索引器，从而确保购物车规则条件按预期应用于购物车。 以前，当存在大量合并的过滤器组时，销售规则索引器将无法完成，从而导致出现错误消息并阻止应用购物车规则条件。

_ACP2E-2617_

### 定价

#### Magento2.4.6-p4订单API简单项目缺少价格

现在，系统在通过Order API查询时可正确显示简单产品的价格，从而确保准确的数据呈现。 以前，简单产品的价格在API响应中错误地显示为零。

_AC-11810 - [GitHub问题](https://github.com/magento/magento2/issues/38603)_

#### 目录规则中的尾数舍入错误

_AC-13855 - [GitHub代码贡献](https://github.com/magento/magento2/commit/276e0acd)_

### 产品

#### 可配置关联产品名称中的特殊字符正在转换为HTML实体。

现在，系统在编辑可配置产品时，会在关联产品的名称中正确保留特殊字符，以防止将这些字符转换为HTML实体。 以前，在编辑可配置产品时，关联产品名称中的特殊字符会转换为HTML实体。

_AC-10535 - [GitHub问题](https://github.com/magento/magento2/issues/38146) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38447)_

#### ProductRepository函数GetById未创建正确的缓存密钥

现在，无论存储ID是以字符串还是整数形式传递，系统都会在ProductRepository的函数GetById中正确创建缓存键。 这样可以确保在后续调用时从内存中检索产品，从而提高性能。 以前，每次调用函数时，系统都会从数据库中检索产品，即使参数相同，这是由于创建缓存键不正确造成的。

_AC-10947 - [GitHub问题](https://github.com/magento/magento2/issues/38384) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38433)_

#### [问题] [MFTF]已添加AdminClickAddOptionForBundleItemsActionGroup

系统现在包含AdminClickAddOptionForBundleItemsActionGroup，增强了管理面板的功能。 以前，此操作组不可用。

_AC-11992 - [GitHub问题](https://github.com/magento/magento2/issues/30857) - [GitHub代码贡献](https://github.com/magento/magento2/pull/30838)_

#### [问题]修复PHPDoc块中的拼写错误

系统现在可以正确删除PHPDoc中用于$helper变量声明的未知引用变量，从而提高代码清晰度和准确性。 以前，PHPDoc中这个未知的引用变量会导致代码中出现混淆和潜在的不准确性。

_AC-13173 - [GitHub问题](https://github.com/magento/magento2/issues/38961) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38940)_

#### [问题]修复了Magento >= 2.4.7中损坏的捆绑包和可下载的产品页面布局

捆绑包和可下载产品页面的布局已固定，确保所有设备显示的一致性和正确性。 以前，由于重新排列产品信息媒体块，这些页面遇到布局问题。

_AC-13423 - [GitHub问题](https://github.com/magento/magento2/issues/39403) - [GitHub代码贡献](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### AlertProcessor — 参数#2 ($storeId)必须是int类型，并且给定字符串

系统现在通过确保商店标识符属于正确的数据类型，正确触发产品警报电子邮件。 以前，由于商店标识符中的类型不匹配，不会发送产品警报电子邮件。

_AC-5969 - [GitHub问题](https://github.com/magento/magento2/issues/35602) - [GitHub代码贡献](https://github.com/magento/magento2/commit/0574ac23)_

#### [Cloud] addFilterToMap函数无法用于某些列

现在，可以在顺序网格中使用自定义模块。 以前，使用自定义模块时出现错误。

_ACP2E-2944 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3a7c4d17)_

#### 类别中的[Cloud]产品 — 添加产品 — 分配 — 全选

用户现在可以使用切换开关选择或取消选择产品。

_ACP2E-3471_

### 促销活动

#### 通过邀请创建帐户时客户属性不可见

在通过邀请创建帐户时，可以使用客户属性。

_ACP2E-2602 - [GitHub代码贡献](https://github.com/magento/magento2/commit/39d54c2d)_

#### 未释放每个优惠券使用次数限制的优惠券代码以进行付款失败，订单被取消

现在，系统会在创建或取消订单后立即更新优惠券使用情况，并将规则使用情况添加到队列中，以防止潜在的死锁。 这可确保释放具有“每张优惠券的使用次数”限制的优惠券代码，并且可在因付款失败而取消订单时重复使用。 以前，系统不会发布优惠券代码以供在此类情况下重用，从而导致出现错误消息，指出优惠券代码无效。

_ACP2E-2627 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c971859e)_

#### [Cloud]重新索引目录规则产品索引器引发SQLSTATE[HY000]：常规错误： 2006 MySQL服务器已消失。

现在，系统可正确处理“Magento\CatalogRule\Model\Indexer\IndexBuilder”的di.xml中的自定义“batchCount”值，从而防止在重新索引目录规则产品索引器期间由于大型目录的批次大小不正确而出现SQL错误，如“常规错误：2006 MySQL服务器已消失”

_ACP2E-2811 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b2286ecf)_

#### 访客客户区段的[CLOUD]购物车价格规则未对购物车应用折扣

现在，即使规则未使用优惠券，系统仍正确地为访客客户区段应用购物车价格规则，从而确保将适当的折扣应用到购物车。 以前，除非购物车价格规则使用优惠券，否则不会将折扣应用于访客客户区段的购物车。

_ACP2E-2926_

#### 相关产品规则的“要匹配的产品”选项卡中缺少“类型”属性

“类型”属性现在作为“相关产品规则”模块的“要匹配的产品”选项卡中的筛选选项提供，从而允许更精确的规则定义。 以前，“要匹配的产品”选项卡中缺少此属性，从而限制了创建准确匹配条件的能力。

_ACP2E-3024_

#### 具有“折扣数量步骤（购买X）”属性的销售规则导致不应用其它规则

如果购物车中的产品数量不足以应用规则，则购物车价格规则不会取消以前应用的规则。

_ACP2E-3139 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d01ee51e)_

#### 购物车价格规则 — 高级销售规则模块出现性能问题

为AdvancedSalesRule筛选器添加了缺少的数据库索引

_ACP2E-3331_

#### 具有固定金额折扣和“最大数量折扣应用于”的问题销售规则

修复了购物车规则折扣的问题，当购物车配置为对有限数量的产品应用固定金额折扣时。 以前，“应用的最大数量折扣”值用于计算购物车中当前项目的价格，而不仅仅用于计算规则的折扣。

_ACP2E-3332 - [GitHub代码贡献](https://github.com/magento/magento2/commit/581b7ef1)_

#### [CLOUD] Magento升级导致优惠券区分大小写

在修复之前，您需要键入与配置完全相同的优惠券代码，并需要考虑使用大写或小写。 现在，无论代码配置是大写还是小写，都将在后端验证优惠券。

_ACP2E-3342_

#### 购物车规则“整个购物车的固定金额折扣”  操作错误地应用折扣

在从管理区域创建订单时使用优惠券代码时，无论使用大写还是小写，都会正确进行验证。 以前，如果优惠券代码与配置的购物车规则代码的字母大小写不符，则不会验证优惠券代码。

_ACP2E-3349 - [GitHub代码贡献](https://github.com/magento/magento2/commit/581b7ef1)_

#### 在后端，默认存储产品属性的值（而不是预期的管理员值）

现在，在后端，使用管理员值而不是产品属性的默认商店值。

_ACP2E-3374 - [GitHub代码贡献](https://github.com/magento/magento2/commit/5184c067)_

#### 添加捆绑包产品时，购物车规则“整个购物车的固定金额折扣”操作错误地应用折扣

捆绑产品未正确应用固定数量的购物车规则。 现在，在计算总折扣金额时，会考虑捆绑子产品，从而生成正确的折扣计算。

_ACP2E-3377 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1366ae5e)_

#### 购物车价格规则计算折扣时出错

目前正在正确计算固定金额折扣。 在修复之前，无法正确计算捆绑产品的固定金额折扣。

_ACP2E-3403 - [GitHub代码贡献](https://github.com/magento/magento2/commit/0b488dd1)_

#### 规则条件中的嵌套类别未显示

修复了当级别3类别下的嵌套类别未显示在类别条件的营销规则中时的问题

_ACP2E-3406 - [GitHub代码贡献](https://github.com/magento/magento2/commit/88660e79)_

#### usage_limit和uses_per_customer未在salesrule_coupon表中更新

现在，更新购物车价格规则中的每张优惠券使用情况和每客户使用情况将影响现有的自动生成优惠券。 以前，新值只影响新优惠券

_ACP2E-3432 - [GitHub代码贡献](https://github.com/magento/magento2/commit/88660e79)_

#### 当购物车使用“等于或大于”条件时，购物车价格规则不考虑父类别。

现在，当在高级条件下使用购物车价格规则时，可以正确考虑父类别

_ACP2E-3456 - [GitHub代码贡献](https://github.com/magento/magento2/commit/93359343)_

#### 优先级折扣计算无效

在适用于整个购物车折扣类型的固定金额的情况下，无法正确计算先前促销已折扣的购物车商品的金额。 现在，折扣总和恰当。

_ACP2E-3463 - [GitHub代码贡献](https://github.com/magento/magento2/commit/078c387e)_

#### [云]配送计算未考虑购物车规则

在修复之前，具有区域条件的购物车规则无法一致应用。 修复后，正确应用包含区域条件的购物车规则。

_ACP2E-3472 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d4de4726)_

#### 发票的购物车规则SKU条件失败。

具有动态价格的Bundle产品的折扣现在正确反映在发票中。 以前，折扣不会反映在发票上。

_ACP2E-3491 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3f12d152)_

#### 当对已折扣/特价的产品同时应用多个购物车价格规则时，折扣值不正确

在修复之前，如果应用了多个购物车规则，则整个购物车规则的固定金额将无法正确应用。 现在，可以正确应用固定金额折扣购物车规则。

_ACP2E-3498 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1984c61c)_

### 返回

#### [CLOUD]受限管理员用户可以看到返回菜单和按钮

受限管理员用户现在无权访问与RMA相关的控件（菜单和按钮）。
以前受限制的管理员用户可以看到返回菜单和按钮。

_ACP2E-3330_

#### 刷新屏幕时，返回屏幕出现混乱

用户可以刷新页面而不会出现屏幕失真。

_ACP2E-3443_

### SEO

#### 添加带有重音符号的URL重写会导致无限加载

现在，系统已成功创建并处理带有重音的URL重写，从而防止在保存过程中进行无限加载。 以前，添加带有重音符号的URL重写会导致无限加载问题。

_AC-11907 - [GitHub问题](https://github.com/magento/magento2/issues/38692) - [GitHub代码贡献](https://github.com/magento/magento2/commit/44cef3a9)_

#### 三级类别的多存储错误类别URL重写

使用自定义作用域URL键为具有父级的子级生成正确的URL重写

_ACP2E-2641 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ea79f7dd)_

#### 产品名称字段中的双字节字符（特殊字符）会阻止在后端创建产品

添加了新设置，通过该设置，您可以将音译应用于产品URL，也可以不应用于产品URL。 可在以下位置进行设置：存储>配置>目录>目录>搜索引擎优化：“为产品URL应用音译”

_ACP2E-2770 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b2286ecf)_

#### 在一个存储组中创建多个存储的url_rewrite条目不正确

在修复之前，您只能在编辑产品时生成网站级别的URL重写。 修复后，引入了一个新设置（存储>配置>目录>目录>搜索引擎优化，包含选项“存储视图”、“网站”的“产品URL重写范围”），允许您在存储视图或网站级别生成URL重写。

_ACP2E-3383 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2d627301)_

### 销售

#### 如果已应用第一个购物车规则，则不会应用第二个购物车价格规则

_AC-13751_

### Search

#### 正在获取“输入搜索词并重试”。 2.4.8-beta1中storefront的“高级搜索”页面出错

现在，当产品属性设置为“否”时，系统会在“高级搜索”页面上正确显示搜索结果。 以前，将产品属性设置为“否”并执行搜索会导致出现错误消息“输入搜索词并重试”。

_AC-13053 - [GitHub代码贡献](https://github.com/magento/magento2/commit/3ea26621)_

#### magento/module-open-search依赖于不存在的opensearch-php分支

_AC-13721 - [GitHub代码贡献](https://github.com/magento/magento2/commit/05dc0bbf)_

#### 搜索查询表大时，对加载时间前端影响较大

改进了搜索列表页面加载时间。 在修复之前，搜索列表页面因未优化查询而延迟。

_ACP2E-3362 - [GitHub代码贡献](https://github.com/magento/magento2/commit/55615e61)_

### 安全性

#### [问题]缺少字体CSP Paylater弹出窗口

现在，系统允许在不违反内容安全策略指令的情况下加载字体“https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39;”，从而确保正确显示Paylater弹出窗口。 以前，由于违反Content Security Policy指令而拒绝加载字体，这会导致Paylater弹出窗口的显示问题。

_AC-11855 - [GitHub问题](https://github.com/magento/magento2/issues/38624) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37401)_

#### [问题]更新js.js DOM文本将重新解释为HTML

通过使用innerText，可以避免注入HTML的风险，因为这些属性会自动转义提供的文本中的任何HTML特殊字符。 此修复将输入视为纯文本而不是解释的HTML，有助于防止跨站点脚本(XSS)漏洞。

_AC-12035 - [GitHub问题](https://github.com/magento/magento2/issues/38767)_

#### 在签出德语时，ReCaptcha V2显示不正确

以前，对于长单词语言（如德语），签出时电子邮件地址下方的recaptcha显示为无样式。 之后，recaptcha看起来与其他区域中的所有recaptcha元素相同。

_ACP2E-3273 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7377de59)_

#### 对于某些用户，管理员登录验证码不需要进行交互

用于管理员登录的ReCaptcha已按预期进行验证

_ACP2E-3300 - [GitHub代码贡献](https://github.com/magento/security-package/commit/8f64ab3c)_

### 配送

#### [问题]修复了tracking.phtml中的拼写错误 — 将JS函数的“currier”重命名为“carrier”

现在，系统在订单跟踪模板中使用的JavaScript处理程序函数中正确使用了术语“carrier”（而不是拼写错误的“currier”），从而确保了正确的函数命名和代码清晰度。 以前，使用拼写错误的术语“currier”，这可能导致代码库中的混淆和不一致。

_AC-10757 - [GitHub问题](https://github.com/magento/magento2/issues/34523) - [GitHub代码贡献](https://github.com/magento/magento2/pull/33414)_

#### UPS REST “装运不能以KGS/IN、LBS/CM或OZS/CM作为其度量单位”

确保在结帐和购物车中显示UPS费率。

_AC-11938 - [GitHub问题](https://github.com/magento/magento2/issues/38618) - [GitHub代码贡献](https://github.com/magento/magento2/commit/493e01f5)_

#### UPS REST“沙盒”和“prod”在devdoc中安装说明更新

_AC-12938_

#### [问题]客户地址的变量拼写正确

系统现在可以正确拼写客户地址的变量，确保前端帐户区域的准确显示。 以前，这些变量的拼写错误可能会导致本地代码审查期间出错。

_AC-13172 - [GitHub问题](https://github.com/magento/magento2/issues/32817) - [GitHub代码贡献](https://github.com/magento/magento2/pull/32815)_

#### 跟踪窗口显示错误的预期交货日期

显示联邦快递承运人的正确交货日期。

_ACP2E-2738 - [GitHub代码贡献](https://github.com/magento/magento2/commit/57a32313)_

#### 即使应用了免运费，仍显示表费率

现在，即使应用优惠券后免费配送变得可用，仍会显示表费率配送方式

_ACP2E-2763 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b2286ecf)_

#### 由于未在Jenkins环境中添加凭据，MFTF测试AdminCreatingShippingLabelTest失败

mftf测试修复

_ACP2E-2765 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ea79f7dd)_

#### FedEx跟踪API不适用于REST凭据

以前，FedEx集成不需要额外的API密钥即可跟踪API。 现在添加了新配置以支持跟踪API密钥。

_ACP2E-3340 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [云] FedEx协商利率未在REST上返回

在修正之前，联邦快递针对具体利率的回应没有发送，即使根据联邦快递的文档，它们本应该发送。 修复后，通过更改我们方的请求，在响应中发送特定于帐户的费率。

_ACP2E-3354 - [GitHub代码贡献](https://github.com/magento/magento2/commit/55615e61)_

### 暂存和预览

#### 如果最初是通过运行update添加的，则未保存计划的更新设置

现在，当在当前运行的更新中修改此类属性时，系统会在后续计划更新中正确清除产品属性值。 以前，当通过运行的计划更新修改产品属性时，无法在创建新的计划更新时清除此类属性值，从而要求用户在创建后重新编辑它们。

_ACP2E-2901_

#### 起始日期和终止日期购物车价格规则未与暂存更新同步

根据购物车价格规则暂存的更新保存日期。

_ACP2E-2999_

#### 暂存预览中出现JS错误

现在，form-mini-stub.js文件已成功加载，并且开发人员工具中没有出现任何Js语法错误。

_ACP2E-3104_

#### 无法更新产品特殊价格暂存内容

现在，系统允许在价格更新促销活动启动后编辑其结束日期，以确保用户可以对其促销活动进行必要的调整。 以前，在尝试更新活动营销活动的结束日期时引发错误，从而阻止用户进行更改。

_ACP2E-3162_

#### 使用唯一的自定义类别属性时无法更新计划更新

修复了在类别具有唯一属性时无法更新类别的计划更新的问题

_ACP2E-3453 - [GitHub代码贡献](https://github.com/magento/magento2/commit/078c387e)_

### 定位

#### [问题]允许在维护允许列表中使用CIDR范围

系统现在支持在维护模式允许IP列表中使用CIDR范围，使一系列IP地址绕过维护模式。 以前，维护模式允许IP列表仅允许单个IP地址绕过维护模式。

_AC-9432 - [GitHub问题](https://github.com/magento/magento2/issues/37943) - [GitHub代码贡献](https://github.com/magento/magento2/pull/30699)_

### 税金

#### [问题] Feature/php8.1构造函数属性升级wee图形ql

用图ql中的模块中的构造函数属性升级替换所有属性：

_AC-13295 - [GitHub问题](https://github.com/magento/magento2/issues/39309) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36975)_

#### 固定产品税(FPT)不适用于可配置产品

可配置产品变体的FPT可正常运行。

_ACP2E-3193 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ec7e32a9)_

### 测试框架

#### 由于JSON列类型，集成测试未通过testDbSchemaUpToDate

现在，系统在集成测试期间可正确识别数据库模式中的JSON列类型，从而防止因数据库模式与声明模式不匹配而导致测试失败。 以前，系统错误地将JSON列类型识别为MariaDB中的LONGTEXT，从而导致集成测试失败。

_AC-11654 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ef81f5a2)_

#### [问题] PHPDoc更正拼写

由于PHPDoc中的拼写更正问题，系统现在可以正确识别IDE中已弃用的方法。 以前，PHPDoc中的拼写错误会导致IDE无法识别已弃用的某些方法。

_AC-13362 - [GitHub问题](https://github.com/magento/magento2/issues/31399) - [GitHub代码贡献](https://github.com/magento/magento2/pull/31398)_

#### MAGETWO-95118：检查会话过期后永久购物车的行为

_AC-13478 - [GitHub代码贡献](https://github.com/magento/magento2/commit/7d5e3906)_

#### 集成测试失败Magento\NegotiableQuote\Controller\Quote\DownloadTest：：testCompanyManagerDownloadWithNQSubPermission

_AC-13716_

#### [数据库比较]如果数据库包含无条件的Target规则相关记录，则出现严重错误

以前，如果数据库包含有关目标规则的记录，且没有任何条件，则会出现致命错误，但在修复数据库比较工具成功通过且没有致命错误之后，出现此情况。

_AC-13722_

#### 修复静态测试以支持3d方扩展使用

_AC-13848 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9e383b4d)_

#### 在执行期间或日志中未显示[内部]夹具应用失败

&#39;-

_ACP2E-3334 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d4de4726)_

#### [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest

固定mftfs

_ACP2E-3458 - [GitHub代码贡献](https://github.com/magento/magento2/commit/078c387e)_

### UI框架

#### Prototype.js安全漏洞修复CVE-2020-27511

更新了系统，以解决Prototype.js 1.7.3中的安全漏洞CVE-2020-27511，从而提高系统的整体安全性。 在此更新之前，系统通过删除精心编制的HTML标签容易遭受正则表达式拒绝服务(ReDOS)攻击。

_AC-12128 - [GitHub代码贡献](https://github.com/magento/magento2/commit/de4dfb8e)_

#### Grunt Less使用pub/前缀作为sourcemap

在使用grunt时，系统现在为路径生成不带/pub前缀的更少/css源地图，从而无需在Web服务器配置中进行变通办法。 以前，在sourcemaps路径中使用/pub前缀需要Web服务器中的特定配置才能正常工作。

_AC-12189 - [GitHub问题](https://github.com/magento/magento2/issues/38837) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38840)_

#### Ui组件文件字段

现在，系统可正确验证UI组件表单中的文件字段，从而在选择文件时提交表单而不出错。 以前，即使选择了文件，验证也会失败，导致表单无法提交。

_AC-12432 - [GitHub问题](https://github.com/magento/magento2/issues/38908) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39004)_

#### [问题] js控制台中的日期格式已得到改进：从12小时切换到24小时……

改进了js控制台中的日期格式：从12小时切换到24小时

_AC-12645 - [GitHub问题](https://github.com/magento/magento2/issues/38983) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38972)_

#### [问题]在开发人员模式下为较少的文件添加sourceMap生成

现在，当处于开发人员模式时，系统为较少的文件生成源映射，从而更容易识别样式的源。 以前，在服务器端编译较少的开发者模式下运行系统时，要识别样式的来源非常困难。

_AC-12650 - [GitHub问题](https://github.com/magento/magento2/issues/38982) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38977)_

#### 正在为禁用的模块部署静态内容

现在，系统将从最终CSS输出文件中排除与已禁用模块相关的CSS，从而确保不加载不必要的样式。 以前，与禁用的模块相关的CSS包含在最终的CSS输出文件中，这会导致加载多余的不必要样式。

_AC-1306 - [GitHub问题](https://github.com/magento/magento2/issues/24666) - [GitHub代码贡献](https://github.com/magento/magento2/pull/32922)_

#### 最小库存阈值“缺货”排序中的行为不一致

现在，系统根据库存水平正确地对目录中的产品进行排序，遵循设置的最低库存阈值，并始终将缺货商品移至列表底部。 以前，排序行为不一致，根据库存水平，项目并非始终以正确的顺序显示，并且在保存、刷新或修改类别层次结构后，排序可能会发生意外更改。

_AC-13459 - [GitHub代码贡献](https://github.com/magento/magento2/commit/47b448e2)_

#### 关于改进require.js加载问题错误报告的建议

此PR可改进必需组件加载失败时的错误消息。

_AC-13472 - [GitHub问题](https://github.com/magento/magento2/issues/36761) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38971)_

#### PHP 8.4弃用错误导致2.4-develop中的生成失败

_AC-14004 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1da9ba6f)_

#### [问题]不在前端加载后端块上下文

系统现在确保前端上未加载后端块上下文，从而防止创建不必要的后端会话和潜在的会话锁定。 以前，系统在前端错误地加载后端块上下文，导致创建后端会话和潜在的会话锁定。

_AC-9007 - [GitHub问题](https://github.com/magento/magento2/issues/37617) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36368)_

#### [问题]删除不必要的脚本审核摘要

现在，系统通过从评级部分中删除不必要的JavaScript脚本来优化页面加载时间，而不是使用内联CSS样式来获取更高效和可读的代码。 以前，将JavaScript脚本用于评级部分可能会减慢页面加载时间。

_AC-9168 - [GitHub问题](https://github.com/magento/magento2/issues/37776) - [GitHub代码贡献](https://github.com/magento/magento2/pull/34643)_

#### 启用Recaptcha后检查礼品卡余额时出现异常

用户将可以在查看和编辑购物车屏幕中获取礼品卡余额。 以前，启用reCAPTCHA时，不会显示这些详细信息。

_ACP2E-2529 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/4a2795ea)_

#### [说明]功能请求ADA合规性

系统现在通过删除不支持的CSS属性并将其替换为print.css文件中支持的属性来确保ADA合规性。 以前，使用不支持的CSS属性会导致浏览器兼容性问题。

_ACP2E-2729 - [GitHub代码贡献](https://github.com/magento/magento2/commit/57a32313)_

#### [Cloud] AC 2.4.4-p8的effect-drop.js中的混淆库代码

系统现在可以正确实施effect-drop.js库，从而确保jQuery UI效果的正常运行。 以前，effect-drop.js库错误地被effect-clip.js库覆盖，导致jQuery UI效果出现潜在问题。

_ACP2E-3061 - [GitHub代码贡献](https://github.com/magento/magento2/commit/35b1b1da)_

#### 网站页眉 | 特殊字符破坏了客户欢迎部分

修复后，特殊字符会在客户欢迎部分中正确显示。

_ACP2E-3367 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1366ae5e)_

#### 客户区段编辑失败，出现日期范围

如果只编辑了一个日期，则可能会使用日期范围条件保存客户区段。

_ACP2E-3561 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a52ff98f)_
