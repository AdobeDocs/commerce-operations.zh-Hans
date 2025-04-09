---
source-git-commit: 62b6501fc2ba595146bf7f38a7d3352ef02be1a0
workflow-type: tm+mt
source-wordcount: '26051'
ht-degree: 0%

---
# Magento Open Source发行说明(v2.4.8)

## 高亮

以下31项重点内容适用于Magento Open Source2.4.8版本。

### 框架

* _AC-10721_：将league/flysystem Composer依赖项升级到最新版本
   * _修复说明_：将2.x league/flysystem Composer依赖项升级到最新版本3.x
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/91cb4d46>
* _AC-11673_：调查php-amqplib/php-amqplib最新版本
   * _修复说明_：更新了php-amqplib/php-amqplib的最新版本：^3.x
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-11911_：迁移到上传库后，jQuery/fileuploader css清理
   * _修复注释_：已移除jQuery/fileUploader库，因为它已迁移到Uppy库
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-11995_：添加与MySQL 8.4 LTS for Magento CE的兼容性
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12015_：迁移到jsTree库后，清理ExtJs文件夹
   * _修复注释_：删除了extJs文件夹，因为相关功能已迁移到jsTree
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-12022_：将独白/独白系统依赖项升级到最新的主版本
   * _修复说明_：系统已更新为使用“monolog/monolog：^3.x”库的最新主要版本，从而确保兼容性和改进的性能。 以前，系统使用的是“monolog/monolog”库的过时版本，这可能导致潜在的问题和限制。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12023_：将wikimedia/less.php依赖关系升级到最新主版本
   * _修复说明_：系统已更新为使用“wikimedia/less.php”库的最新主要版本5.x，从而确保兼容性和最新功能。 以前，系统使用的库版本过时，这可能导致安全问题。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12024_：将jquery/validate库依赖关系升级到最新的次要版本
   * _修复注释_：将jquery/validate库依赖项升级到最新的次要版本1.20.0
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12025_：将moment.js系统依赖关系升级到最新的次要版本
   * _修复注释_：将Moment.js系统依赖关系升级到最新的次要版本2.30.1
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12032_：添加与MySQL 8.4 LTS for EE的兼容性
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12034_：为B2B添加与MySQL 8.4 LTS的兼容性
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12074_：为包扩展添加与MySQL 8.4 LTS的兼容性
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12085_：添加与MariaDB 11.4 LTS For CE的兼容性
   * _修复注释_：添加了对Adobe Commerce和扩展的MariaDB 11.4支持
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12165_：订阅者优化 — PhpUnit10
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/90e25b6b>
* _AC-12267_：支持Redis会话的连接重试并与colimollenhour/php-redis-session-abstract v2.0.0兼容
   * _修复注释_：更新了与adobe commerce兼容的最新版本的colimollenhour/php-redis-session-abstract v2.0.0
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12576_：调查MySQL 8.4 LTS的自动化测试失败
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12595_：添加与MariaDB 11.4 LTS For EE的兼容性
   * _修复注释_：添加了对Adobe Commerce和扩展的MariaDB 11.4支持
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12715_：更新升级到最新版本的Laminas编辑器依赖项
   * _修复注释_：系统现在支持最新版本的Laminas编辑器依赖项：
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validator
确保兼容性和最新功能。 以前，更新到这些依赖项的最新版本可能会导致向后不兼容问题和测试失败。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12823_：调查在组件升级期间由于phpunit修补程序更新而导致的单元测试失败
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-13076_： [第1部分] — 使用最新可用版本更新所有js库和npm依赖项
   * _修复注释_：编辑器版本支持仅更新到编辑器版本2.2.x。 现在，支持也扩展到了2.4.x版本。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/19844aa0>

### 订购

* _ACP2E-2709_： [功能请求]客户建议“订单详细信息”页面上的“提交评论”按钮混乱，应将其更改为其他内容
   * _修复注释_：为了最大程度地减少混淆，订单详细信息页面中的“提交注释”按钮标签已更改为“更新”。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/488c1034>

### 其他

* _AC-11420_：安装新版本的Adobe Commerce时，设置的索引器默认显示为就绪状态
   * _修复注释_：安装Magento后，索引器的状态默认必须处于&#x200B;*就绪*&#x200B;状态。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/71432aeb>
* _AC-11421_：在现有Magento安装中，当按计划安装第三方索引器模块时默认设置更新中的索引器。
   * _修复注释_：默认情况下，所有新索引器都处于[按计划更新]模式。 以前，默认模式为[保存时更新]。 自定义索引器也是如此。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/71432aeb>
* _AC-12480_：Elasticsearch7和8选项应随附管理员配置中弃用的。
   * _修复注释_：“管理员配置”选项中的“Elasticsearch8”选项将显示已弃用的文本，以通知用户不再建议使用“Elasticsearch8”选项。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0611e750>
* _AC-12481_：在管理员配置中选择Elasticsearch选项时添加文本注释
   * _修复注释_：添加了文本注释，以让Adobe Commerce管理员用户知道elasticsearch不再受Adobe支持且已弃用。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0611e750>
* _AC-13448_：在2.4.8版中提供层级价格运营性能改进修补程序
   * _修复说明_：在使用“/V1/products/tier-prices”REST API端点时，系统现在允许更高效地批量更新层价格，而不会导致性能问题或站点无响应。 以前，使用此端点更新大量价格可能会导致性能问题和网站无响应。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/082d981c>
* _AC-13550_：从Adobe存储库中删除所有Magento Open Source机密版权声明
   * _修复说明_：已从开源存储库中删除所有Adobe机密版权声明，确保仅使用Adobe版权的简化形式。 以前，公共存储库中的某些文件包含Adobe机密版权声明，这会导致社区上报。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39493>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/4bca5dfe>

### UI框架

* _AC-12726_： [2.4.8-beta1] TinyMCE 5迁移到TinyMCE 7
   * _修复说明_：已将TinyMCE 5迁移到TinyMCE 7.3.0以作为Adobe Commerce的支持版本，以前的系统使用的是5.10.2，该版本已过时并报告了安全漏洞
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12825_： [2.4.8-beta1] TinyMCE 5迁移到TinyMCE 7页面生成器
   * _修复说明_：将TinyMCE 5迁移到TinyMCE 7.3.0以成为Adobe Commerce支持的版本，以前的系统使用的是5.10.2，该版本已过时并报告了安全漏洞
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12844_： [2.4.8-beta1] TinyMCE 5迁移到TinyMCE 7 - Magento2-infra — 禁止使用的字词
   * _修复说明_：已将TinyMCE 5迁移到TinyMCE 7.3.0以作为Adobe Commerce的支持版本，以前的系统使用的是5.10.2，该版本已过时并报告了安全漏洞
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12901_： Require.js升级到最新版本2.3.7(安全漏洞CVE-2024-38999)
   * _修复注释_：已将require.js更新到最新版本2.3.7。在以前的版本中报告了安全漏洞
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b34c0a75>

## 修复的问题

我们已在Magento Open Source 2.4.8核心代码中修复了497个问题。 此版本中包含的已修复问题的子集如下所述。

### API

* _AC-10042_： /V1/transactions REST API在parent_txn_id = txn_id时返回错误
   * _修复注释_：系统现在可以正确处理父交易ID与交易ID相同的父概念交易和子概念交易，从而防止在查询/V1/transactions REST API端点时发生无限循环。 以前，由于超出最大执行时间，此方案会导致致命错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_： 2.4.7中的[Graphql]类型问题
   * _修复注释_：在执行GraphQL查询时，系统现在可以正确处理GetCustomSelectedOptionAttributes函数中的整数值，从而防止出现任何与类型相关的错误。 以前，启动使用具有整数参数的GetCustomSelectedOptionAttributes的GraphQL查询会导致类型错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38662>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38663>
* _AC-3223_：类别url_key中的特殊字符（通过REST API创建时）
   * _修复注释_：早期的category_url_key中的特殊字符在修复后不存在，它在category_url_key中显示特殊字符
   * _GitHub问题_： <https://github.com/magento/magento2/issues/35577>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c699c206>
* _ACP2E-2755_：启用2FA Duo后rest api出现问题
   * _修复注释_： 2FA with Duo安全选项现在可为Rest API生成正确的签名
   * _GitHub代码贡献_： <https://github.com/magento/security-package/commit/412fa642>
* _ACP2E-2927_： [REST API]：为可配置产品添加配置后，商店视图中的使用默认值不会保持选中状态
   * _修复注释_：通过确保非默认存储的可自定义选项具有正确的数据库条目，该问题已得到修复。 由于数据库条目不准确，因此以前在“管理员>目录>产品编辑>可自定义选项”部分中针对自定义商店的复选框处于未选中状态，即使自定义商店的选项标题与默认商店的标题保持相同也是如此。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-2969_：使用Oauth1时，REST API无法在SKU中使用斜杠(/)发出请求
   * _修复注释_：在修复之前，您无法成功调用其SKU中具有“/”的产品API。 现在，即使其SKU中存在正斜杠，您仍可以成功发出API GET请求以获取产品详细信息。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3079_：如果启用“validateDefaultAddress”，则通过REST API更新客户地址时失败
   * _修复注释_：在解决API有效负载中缺少ID密钥的问题后，API终结点现在可以按预期运行。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3091_： [Cloud]在层价格Api中创建重复的网站组价格客户组。
   * _修复注释_：现在，层价格重置Api不允许创建重复的网站组价格客户组。
以前，可以在层价格Api中创建重复的网站组价格客户组，以免在产品保存期间通过管理员验证。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3130_：无法通过REST API添加具有状态的订单注释
   * _修复注释_：该问题已解决，如果订单状态仅来自当前状态，则允许更改订单状态。 以前，它不遵循订单状态并防止任何订单状态中的更改，即使它来自同一状态。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3236_：有效负载中缺少SKU时，异步操作失败
   * _修复注释_：如果有效负载中缺少sku，则异步和同步操作以前由于产品保存错误而失败。 修复后，异步和同步产品保存rest api操作失败，并显示相关的异常消息。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_： [CLOUD]无法使用REST API更新基价（“catalog_product_entity_decimal”中的“value_id”值未正确递增。）
   * _修复说明_：在此修复之前，调用rest api /rest/default/V1/products/base-prices时，增量ID错误地增加，使值之间出现间隙。 修复后，增量ID将按预期递增。 此外， value_id字段范围也增加了。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3460_：订单项在API POST V1/order/：orderId/refall的贷项通知单电子邮件中不可见
   * _修复注释_：以前，在本次修复之前，当客户通过通知send_email的API请求创建贷项通知单时，它不包含产品详细信息网格。 进行此修复后，客户发送了贷项通知单API请求，并将发现电子邮件中显示了产品项目详细信息。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3486_：未对产品RestAPI的日期和时间属性设置默认值
   * _修复注释_：现在通过RestAPI为日期、日期和时间属性正确设置了默认值
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1984c61c>

### API、购物车和结账

* _ACP2E-3343_：严重500错误：Magento\Framework\Webapi\Exception与接受HTTP标头相关
   * _修复注释_：修复后，指定“接受”标头没有问题。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1366ae5e>

### 帐户

* _AC-10782_：客户地址表单允许在名称字段中使用随机代码
   * _修复注释_：系统现在验证客户地址表单中“名字”和“姓氏”字段的输入，以防止使用随机代码。 以前，系统允许在这些字段中使用随机代码，而不会引发错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38331>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38345>
* _AC-10886_：管理员密码更新。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38352>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-10990_：我的帐户在保存时添加地址崩溃
   * _修复注释_：系统现在可以正确保存客户地址，即使未显示区域字段也是如此，从而防止在保存过程中崩溃。 以前，尝试添加或编辑没有显示区域字段的地址会导致异常错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38406>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38407>
* _AC-11718_：当URL大写时重定向循环
   * _修复注释_：系统现在会自动将URL中的大写字符转换为小写，从而防止在访问主页时出现重定向循环。 以前，如果安全基础URL中包含大写字符，则在尝试访问主页时会引发连续的重定向循环。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38538>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38539>
* _AC-11755_：没有为来宾帐户保存middlename(&#39;s)
   * _修复注释_：系统现在会在签出期间正确保存来宾帐户的中间名，使其可在电子邮件模板中访问。 以前，中间名未保存在报价表中，并且无法在来宾帐户的电子邮件模板中访问。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38593>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39067>
* _AC-11919_：管理员：页面操作按钮向左浮动而不是向右浮动
   * _修复注释_：系统现在可以将“页面操作”按钮正确对齐管理面板中粘性标题的右侧，从而增强专业外观。 以前，这些按钮错误地浮动到粘性标题的左侧。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38701>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_： magento 2.4.7中的dev:di:info错误
   * _修复注释_：系统现在在执行dev:di:info命令时可正确显示构造函数参数，从而防止出现任何错误。 以前，执行此命令会导致错误，因为参数中的类型不匹配。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38740>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-13000_：“以客户选择加入身份登录”复选框不可翻译
   * _修复说明_：系统现在允许在“商店视图”范围中设置“以客户选择加入复选框身份登录”和“以客户复选框身份登录”工具提示字段，从而支持针对不同商店视图的翻译。 以前，这些字段仅在“网站”范围中设置，无法针对单个商店视图进行翻译。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/32329>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/32359>
* _AC-6071_：客户已登录，但在前端显示404错误。
   * _修复注释_：现在，当客户登录时，店面客户仪表板页面会按预期加载。 以前，客户可以登录，但此页面显示了404错误。 [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _GitHub问题_： <https://github.com/magento/magento2/issues/35838>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_：无法在管理员编辑客户部分中保存客户属性信息；
   * _修复注释_：现在已按管理员客户编辑表单的网站范围正确实施客户的商店ID。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/488c1034>
* _ACP2E-3329_：登录后，以访客用户身份添加到比较列表中的产品不可见。
   * _修复说明_：以客户身份登录之前添加到产品比较列表中的产品，现在会在登录后保留。
以前，在登录后，不会显示以访客用户身份添加到比较列表中的产品。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_：允许国家/地区配置导致客户地址配置出现问题
   * _修复说明_：现在，选择“允许国家/地区”配置不会影响为给定范围之外的国家/地区显示的国家/地区。 以前允许受配置影响的客户地址属性超出给定范围
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3501_： VAPT：业务逻辑错误 — 将来日期作为客户出生日期
   * _修复注释_：客户的出生日期不能设置为晚于今天
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d4de4726>

### 帐户、API、GraphQL

* _ACP2E-3246_： Customer API - Login Failures Number Cannot Able to Reset To 0 After Successful Login （客户API — 登录成功后，登录失败数字无法重置为0）
   * _修复注释_：现在，客户通过API端点成功登录后，客户实体表中的失败编号将重置为零。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ec7e32a9>

### 帐户，管理员UI，B2B

* _ACP2E-3038_：受限管理员用户无法始终查看自定义共享目录
   * _修复注释_：受限管理员用户现在可以始终如一地查看和管理客户以及产品分配到的所有共享目录，前提是他们有权访问特定商店。 以前，有权访问特定商店的受限管理员用户不可能始终看到产品分配到的所有共享目录，或者可能看到无法保存的客户，从而导致系统不一致。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7377de59>

### 帐户、购物车和结帐

* _AC-2341_：“select”自定义客户地址属性不会为新客户地址渲染
   * _GitHub问题_： <https://github.com/magento/magento2/issues/34950>

### 管理员UI

* _AC-10705_： [问题]为“重新加载数据”数据按钮添加权限检查
   * _修复注释_：系统现在包含对“重新加载数据”按钮的权限检查，以确保该按钮仅向具有相应权限的用户显示和访问。 以前，“重新加载数据”按钮对所有用户可见和可点击，导致在没有必要权限的用户单击时出现“不允许”页面。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38283>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38279>
* _AC-11427_： [问题]营销规则中属性的标签不一致
   * _修复注释_：系统现在可以正确填充购物车价格规则中类别和属性选项的标签
   * _GitHub问题_： <https://github.com/magento/magento2/issues/31232>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/31231>
* _AC-11588_：在导入具有替换行为的产品时，数据验证成功且存在导入按钮
   * _修复注释_：系统现在可以正确验证数据，并在产品导入过程中使用“替换”行为隐藏“导入”按钮，以防止任何意外的数据替换。 以前，系统会错误地验证数据并显示“导入”按钮，从而导致潜在的数据不一致。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_： [错误] Magento 2.4.7不允许使用大写字母文件扩展名的产品照片。
   * _修复注释_：系统现在接受带大写字母文件扩展名的产品图像上载，从而确保产品创建过程顺畅。 以前，使用大写字母文件扩展名的图像上传被拒绝，从而迫使用户将文件扩展名更改为小写。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38831>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12319_：具有选择操作的网格中的隐藏下拉列表（例如“内容”>“元素”>“页面”）
   * _修复注释_：现在系统已修复所有网格的所有类似下拉列表。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38891>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39371>
* _AC-13131_： [问题]修复警告：未定义数组键“筛选器”
   * _修复注释_：系统现在处理新用户尚未与书签交互的情况，从而阻止记录未定义的数组键“筛选器”警告。 以前，当新用户未与书签交互时，将记录此警告。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39013>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38996>
* _AC-13529_：由于Validate.php文件中的代码更改，产品导入带有特殊字符的csv文件失败
   * _修复注释_：系统现在可以正确验证和导入包含特殊字符的产品CSV文件，从而允许成功传输数据。 以前，尝试导入包含特殊字符的产品CSV文件会导致错误，从而阻止导入过程。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13850_：必填电话号码字段没有红色星号
   * _修复注释_：电话号码未显示早期的红色星号，但是  电话号码是必填项。 现在，已修复红色星号的电话号码可视为必填字段。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c699c206>
* _AC-6975_： [问题]将默认索引器模式设置为“计划”
   * _修复注释_：所有新索引器默认处于&#x200B;**[!UICONTROL Update by Schedule]**&#x200B;模式。  以前，默认模式为&#x200B;**[!UICONTROL Update on Save]**。 现有索引器不受影响。 [GitHub-36419](https://github.com/magento/magento2/issues/36419)
   * _GitHub问题_： <https://github.com/magento/magento2/issues/36419>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0b410856>
* _AC-7700_： [问题]删除mview取消订阅上的索引器更改日志表
   * _修复注释_：当索引从“按计划更新”切换为“保存时更新”时，系统现在会自动删除未使用的changelog表，并将索引标记为无效，以确保不会丢失任何条目。 以前，将索引切换为“保存时更新”会在系统中保留未使用的changelog表，并将所有更改的索引标记为“有效”。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/29789>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/25859>
* _AC-7962_：在手机视图中结帐付款时，没有指向送货的链接
   * _修复注释_：系统现在可以确保在移动视图中的页面顶部始终显示签出标题/链接“送货”和“审核和付款”，从而使用户能够轻松地在步骤之间导航并进行必要的更正。 以前，这些标题/链接在移动视图中隐藏，使用户难以了解其当前步骤或返回之前的步骤。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/36856>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36982>
* _AC-8109_：客户订单查询装运注释created_at在+0时区中返回，不在商店配置的时区中
   * _修复注释_：使用客户订单查询时，系统现在会在客户配置的时区中正确显示来自装运注释的“created_at”字段。 以前，“created_at”字段以+0时区显示，无论客户配置的时区如何。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/36947>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37642>
* _AC-9843_： i18n：collect-phrases破坏翻译完整性
   * _修复注释_： `bin/magento i18n:collect-phrases -o`命令现在可以正确收集和添加JavaScript和.phtml文件中的新短语，确保翻译准确反映在翻译文件中。 以前，系统无法在翻译文件中包含JavaScript文件的多行翻译短语和.phtml文件的短语，从而导致翻译不完整或不正确。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2787_：存储视图名称中的撇号已替换为&#39;
   * _修复注释_：网格的存储视图筛选器现在正确显示撇号
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38395>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_： Favicon上传无法验证.ico文件
   * _修复注释_：文件验证错误已更新为“文件验证失败。 请验证存储配置中的图像处理设置。” 以前，它只是“文件验证失败”。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_： PageBuilder中的库显示旧图像缩略图，而不是新上传的图像
   * _修复注释_：为通过页面生成器内容中的媒体集删除并重新上传的具有相同名称的图像，重新生成图像预览。
   * _GitHub代码贡献_： <https://github.com/magento/magento2-page-builder/commit/60140cd2>，<https://github.com/magento/magento2/commit/001e5188>
* _ACP2E-2978_：由角色范围不同的管理员用户保存产品将覆盖/删除产品中现有的相关产品信息
   * _修复注释_：以前，在修复之前，当辅助管理员用户单击“保存”按钮时，相关产品会重置并变为空，而不会更改相关产品。 进行此修复后，辅助管理员用户单击“保存”按钮，产品未重置且保存成功。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_：无法导出200个以上的订单
   * _修复注释_：通过将GET中的HTTP请求更改为POST，已忽略先前提交的选定ID的请求大小的服务器限制，以便修复此问题。 以前，由于GET请求大小的服务器限制，遇到问题。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_：签出页验证消息不正确。
   * _修复注释_：如果任何必填字段留空（如“地址”），则服务器端验证将不会显示消息。 客户端验证将确保显示必填字段错误通知，说明“这是必填字段”。 以前，如果任何必填字段留空，除了客户端验证消息之外，还会显示“地址为必填项”消息。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_：管理员用户的密码重置模板问题
   * _修复注释_：问题已通过使用正确的密钥得到解决，该密钥现在包含电子邮件模板中的管理员用户名并正确填写主题。 以前，问题源自正在使用的过时键。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3149_：客户区段URL中有双斜杠
   * _修复注释_：在网格中单击“重置筛选器”时，URL中未出现双斜杠。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3171_： COD不可用于允许的特定国家/地区
   * _修复注释_：现在，当需要并且允许特定国家/地区时，“货到付款”可用   AC-3216按预期工作。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3178_：无法更新自定义创建的订单状态
   * _修复注释_： &#39;
我们现在可以更新自定义创建的订单状态，而以前，仅当当前状态为“正在处理”或“欺诈”时，才能更改状态。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38659>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3294_：送货地址状态不是自动更新
   * _修复说明_：在修复之前，送货地址区域（或区域ID）与地址帐单信息不同步。 现在，当帐单地址信息更改时，送货地址区域和区域ID都会正确更新。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_：“重置”按钮对添加/编辑管理员用户不起作用
   * _修复注释_：以前，在“添加/编辑管理员用户”页面上，“重置”按钮不起作用。 现在，在“管理员”面板中“系统” — >“权限” — >“所有用户”下，“重置”按钮将在“添加/编辑管理员用户”页面上正常工作。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3373_： Magento管理员URL路由错误检测和CORS错误
   * _修复说明_：修复后，如果自定义管理域是主域的子域，则只能从配置的子域访问管理员。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37663>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3392_：“购物车中允许的最大数量”的验证损坏
   * _修复注释_：以前，当我们将`Maximum Qty Allowed in Shopping Cart`设置为空时，它不会引发任何异常，尽管此处不接受空值。 进行此修复后，输入空字符串将会引发异常，并且不允许保存产品。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_：[Pagebuilder预览UI问题]页面生成器列中的按钮未正确对齐
   * _修复注释_：页面生成器列中的按钮现在正确对齐。 以前，它们在页面生成器列中不会对齐。
   * _GitHub代码贡献_： <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_：未导出订购的产品报表。 而是404错误。
   * _修复注释_：产品订购报表导出为CSV和XML时现在可按预期运行
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_：在生产模式下启用Js缩小后，控制台中出现TinyMCE JS错误
   * _修复注释_：以前，在“管理”面板的生产模式下启用JavaScript缩小功能会导致浏览器控制台中出现与TinyMCE 6相关的JavaScript错误，从而影响功能和用户体验。 现在，此问题已得到解决，从而确保TinyMCE 6平稳运行，不会生成任何错误，即使启用了JS缩小也是如此。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_：请求进行其他更改以完全完成ACP2E-3375修复
   * _修复注释_： &#39;-
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3503_：自动启用新ACL权限
   * _修复注释_：除非明确配置，否则添加到自定义模块的新权限将不再自动授予对所有现有用户角色的访问权限。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3509_：管理员操作日志用户报告未显示admin_user_delete的详细信息
   * _修复注释_： adminhtml_user_delete现在可正确记录重要详细信息。 以前，不会为用户删除生成日志。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/4de008a9>
* _ACP2E-3536_：从管理员下订单时未应用配送条件的购物车规则
   * _修复注释_：以前，如果购物车价格规则具有附带优惠券的配送方式折扣，则无法通过管理员UI应用该价格规则。 应用此修复后，将从Admin UI成功应用带有特定配送方式优惠券的购物车价格规则折扣。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a52ff98f>，<https://github.com/magento/inventory/commit/11ce816b>
* _ACP2E-3559_： [FRESH]十六进制代码未在样本中正确更新
   * _修复注释_：用户在Visual Swatch拾色器中手动输入的十六进制代码不再由系统更改。 以前，某些十六进制代码由于颜色模型之间的转换错误而经历细微调整。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/344fce23>，<https://github.com/magento/inventory/commit/1ef984c0>

### 管理员UI、B2B

* _AC-13628_：作为客户标头的B2B登录仍具有Magento品牌
   * _修复注释_：以前，店面标题显示“您现在已作为&lt;store name>上的&lt;customer name>连接”，并带有Magento品牌。 此问题现已修复，并且标题将以ADOBE品牌化显示。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/96dec499>

### 管理员UI、付款/付款方式、订单

* _AC-13520_：PayPal智能按钮排序后，“交易”选项卡中未显示交易授权
   * _修复注释_：现在，在使用PayPal智能按钮下达订单后，系统可在“交易”选项卡中正确显示交易授权。 以前，单击“授权”按钮后，授权交易未显示在Transaction选项卡中，并且未创建“授权”类型的新交易。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6cfb9b6b>

### 管理员UI，性能

* _ACP2E-3169_：更新到2.4.5-p8后，从管理员创建订单时出现500错误
   * _修复注释_：以前，启用HTML最小化时，无法向管理员下达订单。 现在，在启用HTML缩减功能的情况下，可以成功下达管理员的订单。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b21e5d91>

### 管理员UI，配送

* _ACP2E-2519_：优惠券代码计数不会在   如果订单是多次发运的，则“管理优惠券代码”选项卡中的“已用时间”列。
   * _修复注释_：以前，在多次发运下订单时，在“管理优惠券代码”选项卡的“使用时间”列中，优惠券代码计数不会更新。 现在，正确计数会同时显示在“使用时间”中，以反映多次配送的所需值。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/4745100c>

### 管理员UI、暂存和预览

* _ACP2E-3424_： [Cloud]移除包含缺失图像的模板时导致pub/media被删除
   * _修复注释_：以前进行过此修复，如果pagebuilder模板缺少预览图像名称，则会删除pub/media文件夹。 修复后，将仅删除模板并预览图像（如果找到）。
   * _GitHub代码贡献_： <https://github.com/magento/magento2-page-builder/commit/0986853b>

### 分析/报告

* _AC-9922_：Google AnalyticsCSP错误https://region1.analytics.google.com
   * _修复注释_：启用Google Analytics后，系统现在可正确允许连接到“https://region1.analytics.google.com&#39;”，从而防止出现内容安全策略(CSP)错误。 以前，由于拒绝连接到&#39;https://region1.analytics.google.com&#39;，从欧盟启用Google Analytics和查看网站会导致CSP控制台错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37750>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38991>
* _ACP2E-2570_：高级报告无法正常工作
   * _修复注释_：系统现在支持通过以10,000个批次加载和写入报表，为超大型数据集生成高级报表数据文件。 以前，高级报告模块无法为超大型数据集生成数据文件，导致在执行analytics_collect_data cron作业期间出现“MySQL服务器已消失”错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_：管理员订购的产品报告日期范围可见性问题。
   * _修复说明_：用户将能够从“订购的产品”报表中选择任何日期。 以前，在刷新表后，选择“起始”日期将重置“截止”日期。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_： curl标头不正确，导致newrelic:create:deploy-marker无法正常工作
   * _修复注释_：系统现在可以正确设置curl标头的格式，从而允许newrelic:create:deploy-marker命令在New Relic中成功创建部署标记。 以前，错误的curl标头会阻止在New Relic中创建部署标记。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37641>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3183_： NewRelic浏览器监视内联JS脚本导致CSP错误
   * _修复注释_：应用程序现在插入NewRelic浏览器监视脚本，而不是APM代理，以符合CSP（内容安全策略）。 以前，由APM代理插入的NewRelic浏览器监控脚本与CSP不兼容，并导致脚本无法执行。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_：对sales_bestsellers_aggregated_daily表的INSERT查询在销售订单量大的项目上变得缓慢
   * _修复注释_：以前，如果下订单量很大，则要生成畅销商品汇总的每日报表会花费大量时间。 现在，报告已及时生成。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_：订单报表显示错误的货币符号
   * _修正说明_：订单报告中订单金额的货币符号错误地取自货币/选项/基数。 现已更正，使用货币/选项/默认进行准确报告。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_：优惠券使用情况报告中的[云]计算不正确
   * _固定注释_：现在，通过合并“折扣税补偿金额”和“装运折扣税补偿金额”，可准确计算优惠券报表网格中的销售总额。 以前，计算中缺少这些金额，导致销售总额与销售订单数据之间出现差异。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_：共享“&lt;project_id>/var/tmp”时出现问题
   * _修复注释_： Analytics DataExport临时文件将使用sys tmp目录，该目录更适合频繁访问和更改。 为了避免在同一服务器上运行多个实例时发生冲突，更新了tmp路径以使用实例的唯一id
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4cf5e62>

### Analytics/报表，B2B

* _ACP2E-2300_： B2B - Sitemap包括未分配给共享目录的产品/类别
   * _修复注释_：将Sitemap生成的类别和产品限制为仅分配给公共共享目录和/或目录类别权限设置的类别和产品。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics/报表、云

* _ACP2E-3067_：Magento放弃大部分New Relic cron交易#34108
   * _修复注释_： AC正在向NewRelic正确报告cron作业相关事务。 以前，某些与cron作业相关的事务在NR中显示为“OtherTransaction/Action/unknown”
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3187_：NR中的指标可能会对背景交易造成误导 — ACP2E-3067的跟进
   * _修复注释_：后台事务(cron)将使用在配置设置中定义的New Relic应用程序名称
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _ACP2E-2139_：执行部分索引时，分配给共享目录的产品不会反映在前端
   * _修复说明_：完成部分索引后，通过REST API分配给共享目录的产品现在可以立即显示在店面上。 以前，产品仅在完全重新编制索引后才可见。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3044_：“我的订单”部分中存在不必要的边框
   * _修正注释_：以前曾创建应用了其他CSS类的额外容器（订单引用），这导致“我的订单”部分中的订单编号下方出现不必要的边框行，现在不可见。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3247_： sales_clean_quotes cron从尚未批准的采购订单中删除报价
   * _修复注释_： sales_clean_quotes cron作业不会删除采购订单中使用的报价
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/581b7ef1>

### B2B，框架

* _AC-9607_：筛选公司网格，然后尝试网格CSV导出将失败并引发异常
   * _修复注释_：系统现在允许成功CSV导出管理面板中的公司网格数据，即使应用了“未付余额”和“公司类型”等过滤器也是如此。 以前，应用某些过滤器并尝试导出网格数据会导致失败并引发异常。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/44cef3a9>

### 捆绑

* _AC-10826_：店面包复选框验证错误消息计数大于1
   * _修复注释_：现在，单击“添加到购物车”按钮时，系统只显示一条验证错误消息，而没有为捆绑产品选择任何复选框选项。 以前，系统会为每个未选复选框显示多个验证错误消息。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3ea26621>

### 购物车和结帐

* _AC-10660_：在比较产品页中将产品添加到购物车时，未正确处理异常
   * _修复注释_：现在，当从比较产品页将产品添加到购物车时，系统可正确处理异常，并在控制器中显示消息管理器消息。 以前，异常将导致返回JSON编码的页面，而不是正确捕获和处理。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38200>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38257>，<https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_： GTag未发送交易价格和总计。
   * _修复注释_：启用GTag后，系统现在可正确地向Google标记发送交易价格和总计，从而确保对电子商务数据的准确跟踪。 以前，该货币作为“所有”订单的一部分错误地发送，而不是与单个订单相关联。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37348>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37504>，<https://github.com/magento/magento2/pull/37349>
* _AC-11641_： [问题] [签出] Depend指令已在失败的付款电子邮件模板中更新
   * _修复注释_：系统现在会从失败的虚拟产品付款电子邮件模板中正确忽略运送地址和运送方式，从而确保电子邮件中仅包含相关信息。 以前，虚拟产品付款失败的电子邮件未正确包含运送地址和运送方式。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/32781>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/32511>
* _AC-11717_： Magento 2在现有客户的签出内登录，在Firefox浏览器中引发控制台错误
   * _修复注释_：系统现在允许用户在结账过程中登录，而不会在Firefox浏览器中遇到任何控制台错误。 以前，在签出期间尝试以现有客户身份登录会导致Firefox中出现控制台错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38557>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39509>
* _AC-11876_：[问题] 2.4.7中的销售规则回归
   * _修复注释_：系统现在可以正确验证销售规则，防止在产品条件与任何产品名称不匹配时将优惠券代码应用到购物车。 以前，即使产品条件与任何产品名称不匹配，也可以应用销售规则并根据运费金额提供折扣。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38671>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11914_： [问题]销售规则CartFixed计算：折扣金额不正确
   * _修复注释_：系统现在可以正确计算具有购物车固定金额的销售规则的折扣金额，从而确保无论购物车项目发生什么更改，都能应用准确的折扣。 以前，当购物车项目更改时，折扣金额可能会错误地变化，有时会导致折扣显着高于预期。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38694>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-11993_： [问题]更改邮政编码后，加载程序将阻止配送方式，配送费率验证规则
   * _修复注释_：系统现在可以正确处理自定义配送方式，而不使用运费验证规则，从而确保在结帐期间在配送地址中更改邮编后，加载程序不会阻止配送方式。 以前，在结帐期间更改装运地址中的邮政编码会导致加载程序阻止装运方法，并且在使用没有装运费率验证规则的自定义装运方法时不会消失。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38742>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_：优惠券代码功能在Magento 2.4.7上的签出页面中无法正常工作
   * _修复注释_：系统现在为虚拟和可下载产品在结账页面上启用折扣代码/优惠券输入字段，允许用户按预期应用折扣代码。 以前，折扣代码/优惠券输入被禁用，并且按钮标题文本显示为“取消优惠券”，阻止用户应用折扣代码。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38826>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12479_：“条款和条件”复选框不允许店面上的HTML
   * _修复说明_：系统现在支持店面的“条款和条件”复选框文本中的HTML格式，从而增强自定义和可读性。 以前，复选框文本以纯文本格式显示，忽略使用的任何HTML标记。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-12541_：为已登录用户创建的购物车价格规则错误地应用于未登录用户
   * _修复注释_：现在，系统会在登录用户因Cookie过期而自动注销时正确删除购物车价格规则，确保折扣不适用于非登录用户。 以前，即使用户已注销，购物车价格规则仍会应用，从而导致将错误的折扣应用于非登录用户。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38944>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13302_： [问题] [功能]通过阻止……
   * _修复注释_：系统现在通过防止重复的getActions调用、提高购物车操作的速度和效率，优化大型购物车的性能。 以前，对于包含多个项目的购物车，会多次调用getActions函数，这会降低系统的性能。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39292>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39290>
* _AC-8103_：地址渲染器中的翻译增值税
   * _修复说明_：系统现在允许翻译地址呈现器中的文本“VAT”、“T”、“F”，使用户能够将这些条款翻译为商店的特定语言。 以前，这些术语无法翻译，从而迫使用户采用解决方法。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/36942>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36943>
* _ACP2E-2055_：具有相同报价ID但存在少量时间差异的重复订单
   * _修复注释_：修复了Adobe Commerce客户遇到使用相同QuoteID下达重复订单的问题
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2470_：结帐步骤中永久清除购物车
   * _修复注释_：修复后，如果在结帐时选择付款方式而没有登录，将不会终止永久会话。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_：重新排序将未分配的产品添加到购物车
   * _修复注释_：以前，对于不同的商店，可以从其他商店对产品重新排序。 仅应用同一商店应用此修复后，启用客户帐户共享时，可以重新排序同一范围的产品
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_：在Admin中，选择项目时左侧的购物车未更新，从右侧选择“移至购物车”时未更新
   * _修复注释_：选择项目时，左侧的“购物车”会更新；选择管理端右侧的“移动到购物车”时，左侧的“移动到购物车”会更新。 以前，此功能不起作用，因为转换后的购物车项目不会从会话中清空。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2646_： [Cloud]销售规则未应用于第一笔多发订单
   * _修复注释_：修复之后，将正确显示同一多送货报价单中每个订单的折扣。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_： [Cloud]将相同产品添加到购物车的生产并行请求在购物车REST API中产生了两个不同的项目
   * _修复注释_：系统现在可正确处理多个并行请求，以将同一产品添加到购物车中的单个行项目，从而防止为同一SKU创建单独的行项目。 以前，并行请求通过REST API将同一产品添加到购物车将导致同一SKU包含多个行项目。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2704_：无法发送Cookie。 尝试重新排序时“图像消息”的大小
   * _修复注释_：重新排序过程现在不会生成自己的错误。 它将依赖购物车列表的内置项目检查。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_：结帐时未选择默认送货地址
   * _修复注释_：在启用的地址搜索的上下文中正在选择默认送货地址事件。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_：[CLOUD] graphql addProductsToCart api问题，带有自定义选项
   * _修复注释_： GraphQL使用不同的自定义选项将相同的产品正确地添加到购物车
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2923_：签出为新客户时，向帐户添加了多个地址
   * _修复说明_：现在，如果未能创建订单，系统只会保存一次新的客户地址，从而防止在出现订单下达错误的情况下创建多个相同的地址。 以前，系统会在每次尝试下单时保存一个新地址，而不管订单是否成功创建。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/001e5188>，<https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_：通过访客订单重新订购客户订单导致购物车为空
   * _修复注释_：以前，通过“订单和退货”页面重新订购时，客户被重定向到登录页面。 应用此修复后，进行重新订购时，注册的客户会被正确重定向到“查看购物车”页面。 该流的工作方式与访客客户相同。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_：角色资源有限的管理员用户无法查看购物车
   * _修复注释_：以前，受限制的管理员无法从相关网站的管理员面板中看到放弃的购物车。 应用此修复后，受限管理员可以从管理员面板中看到放弃的购物车。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3176_： [云]快速订购大量SKU性能
   * _修复注释_：当购物车价格规则条件中使用的属性对于所有产品均不存在，并且启用了MAP（最低广告价格）功能时，结账性能已得到改进。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_：购物车中重复的项目
   * _修复注释_：系统现在可正确处理多个并行请求，以将同一产品添加到购物车中，并添加到单个行项目，从而防止为同一SKU创建单独的行项目。 以前，并行请求将同一产品添加到店面的购物车会导致同一SKU有多个行项目。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_：结帐订单电子邮件确认会发送到以名字/姓氏输入的电子邮件中
   * _修复说明_：结帐单电子邮件确认不再发送，之前在“名字”和“姓氏”字段中输入类似电子邮件的模式时曾发送过该确认电子邮件。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_：签出送货地址表单更新为错误的地址
   * _修复注释_：现在已将shippingAddressFromData保存到每个网站的本地存储中。 以前，如果在URL中使用商店代码，并且在同一访客会话期间从多个网站启动了结账，则来自错误网站的地址可能会在结账期间自动填充到送货地址表单中。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3407_：礼品卡产品 | 购物车合并正在合并礼品卡
   * _修复注释_：Giftcard产品现已正确合并到购物车中
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3415_：注销时未遵循购物车持久性
   * _修复注释_：添加了缺失的功能从客户登录到身份验证弹出窗口和签出登录，请记住我。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/344fce23>
* _ACP2E-3488_：现有报价数据未更新/不可见，而是在trigger_recollect = 1时创建新的报价记录
   * _修复注释_：客户的购物车项目在添加到购物车后不再因产品被删除而消失。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3618_：[CLOUD]重新排序按钮功能
   * _修复注释_：现在，从管理员区域重新排序的订单会将具有Stock的产品添加到报价中，即使原始订单中的某些产品不再具有Stock。 修复之前，如果原始订单中没有库存产品，则不会将任何产品添加到新报价中。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3622_：搜索存储无法按邮政编码工作
   * _修复注释_：按邮政编码搜索取车位置对于荷兰本地化无法正常工作。 修复后，取车地点搜索将根据邮政编码提供结果。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/344fce23>

### 购物车和结帐、结帐/单页结帐

* _AC-9386_： [随机错误]电子邮件字段未呈现，或需要很长时间才能在结帐送货或付款页面中显示
   * _修复注释_： Commerce现在会按预期在结账送货和付款页面上渲染&#x200B;**[!UICONTROL Email]**&#x200B;字段。 以前，此字段不存在或呈现缓慢。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/e1babcfd>

### 购物车和结帐、订购

* _ACP2E-3097_：从管理员下订单时，具有多个日期字段无效的可自定义选项的产品日期选取器
   * _修复注释_：在管理订单创建过程中配置具有多个可自定义日期选项的产品时，系统现在可以正确显示所有日期字段的日期选取器。 以前，仅为第一个日期字段显示日期选取器，而其余字段没有日期选取器。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b21e5d91>

### 购物车和结帐、送货

* _AC-12119_：可配置产品的即时购买“最便宜的送货”中断
   * _修复注释_：即时购买功能错误地为可配置产品选择了更昂贵的店内交付选项，而不是最便宜的统一费率方法。 这一修复措施可确保根据实际价格选择正确的配送方式。”
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38811>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38819>，<https://github.com/magento/magento2/commit/29fe9097>

### 目录

* _AC-10910_： cron_schedule数据库表的清理未清理非现有作业
   * _修复注释_：系统现在会自动清理cron_schedule数据库表，删除系统中不再存在的作业的条目。 这通过保持表中的最小行数来确保最佳性能。 以前，不清理非活动模块或已移除模块中作业的条目，导致cron_schedule表中出现不必要的数据积累。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38217>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38693>
* _AC-10953_：未从可配置产品中删除层价格
   * _修复注释_：现在，当产品从简单产品转换为可配置产品时，系统会正确移除产品的层价格，从而确保前端准确显示价格。 以前，将产品从简单产品转换为可配置产品时，不会删除可配置产品的层价格，从而导致显示的价格不匹配。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38390>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38427>
* _AC-11804_：非默认存储审阅中的类别描述WYSIWYG为空
   * _修复注释_：在商店视图级别编辑类别时，系统现在会在WYSIWYG编辑器中正确保存并显示类别描述。 以前，在商店视图级别保存类别描述后，WYSIWYG编辑器将显示为空。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38622>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38623>
* _AC-11970_：无法通过选中自定义选项的一个复选框来重新排序可配置产品
   * _修复注释_：系统现在使用单个选定的复选框自定义选项正确处理可配置产品的重新排序，从而允许成功创建购物篮。 以前，尝试重新排序此类产品会导致错误，并阻止将商品添加到购物车。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38736>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1d144bce>
* _AC-12076_： [问题]修复分层导航上筛选器项的措辞
   * _修复注释_：系统现在可正确使用分层导航筛选器项中的“item”和“items”两词，从而增强筛选器描述的清晰度和准确性。 以前，这些词语使用不正确，这可能导致导航过滤器选项的用户混淆。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38789>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37852>
* _AC-12164_：自定义选项的日期和时间格式不起作用
   * _修复注释_：系统现在可以将配置的日期格式正确应用于类型为“日期”的产品自定义选项，确保日期格式在前端正确显示。 以前，对日期格式配置的更改不会反映在日期类型的产品自定义选项的前端。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/32990>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38925>
* _AC-13068_：下拉列表选项缺失
   * _修复注释_：现在，在创建具有超过20个值的新属性时，系统会在下拉列表中正确显示所有值。 以前，仅显示前20个值或其他选定的页面值，从而导致其余值缺失。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_： [问题]将当前存储ID用于类别运行时缓存
   * _修复注释_：系统现在可正确使用类别运行时缓存的当前存储ID，从而防止在使用仿真时覆盖数据，或防止自定义代码将类别保存到不同的存储中。 以前，运行时中存储的对象可能来自错误的存储，从而导致数据覆盖。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39310>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36394>
* _AC-13324_： bin/magento sampledata：deploy —no-update引发异常
   * _修复注释_：现在，在使用sampledata：deploy命令中的 — no-update选项时，系统可正确接受布尔值，从而防止在示例数据部署期间出现任何错误。 以前，使用此命令时引发错误，因为系统错误地期望整数值。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39344>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39345>
* _AC-13355_： [问题]修复EAV缓存类型的用法
   * _修复注释_：系统现在在所有相关位置正确使用EAV缓存类型，确保一致且高效的数据缓存。 以前，EAV缓存类型使用不一致，这可能导致数据缓存效率低下和不一致。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/32322>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/31264>
* _AC-13596_：包含空数据的目录高级搜索将转到搜索结果页[2.4.dev branch]
   * _修复注释_：系统现在可以正确保留“高级搜索”页面上的用户，并在用户尝试在不输入任何数据的情况下执行搜索时显示错误消息。 以前，执行空搜索会将用户重定向到“目录高级搜索”页面，并会显示一条消息，提示用户修改其搜索。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13622_： [问题]基于attribute_set的产品布局
   * _修复注释_：系统现在允许根据属性集调整产品布局，从而为管理前端商店中的产品显示提供了一种更实用和更高效的方法。 以前，布局只能根据SKU或产品类型进行调整，这对于许多产品或特定文章并不总是可行的。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38790>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36244>
* _AC-6738_：eav_attribute_option_value表上缺少唯一键
   * _修复注释_：系统现在在“eav_attribute_option_value”表的“option_id”和“store_id”列中包含唯一键，以防止可能有一个选项具有同一存储视图的多个值。 以前，错误代码可能会导致同一商店视图的选项具有多个值，从而导致在编辑产品或属性时出现问题。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/24718>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/28796>
* _AC-8297_： [问题]使用类别产品索引器的可见性类，而不是硬编码值
   * _修复注释_：系统现在使用类别产品索引器的可见性类，而不是硬编码值，增强了模块性。 以前，在类别产品索引器中使用硬编码值，限制了灵活性和适应性。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37200>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37199>
* _AC-9375_：新产品小组件中的货币代码未更改
   * _修复注释_：现在，在前端更改货币时，系统可正确更新新产品小组件中的货币代码，从而确保整个站点显示的货币一致。 以前，更改前端中的货币不会影响新产品小组件中显示的货币代码。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37898>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37899>
* _ACP2E-2224_：可配置产品的PLP上不显示常规价格
   * _修复注释_：对于具有具有特价子产品的可配置产品，产品列表页面上现在显示常规价格。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2478_：库存信息未直接显示在可视化促销网格上
   * _修复注释_：现在根据选定的商店显示库存。
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_：构件内容未在cms页面上更新
   * _修复注释_：现在，当产品设置为新产品且已保存时，系统会更新CMS页面上的构件内容，以确保该页面显示更新的产品集合。 以前，由于缓存中用于小部件的缓存标识不正确，页面未更新以显示新产品。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2630_：在捆绑产品上保存高级定价时出现问题
   * _修复注释_：捆绑产品保存性能改进。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2652_： [内部部署]重新索引进程在创建目录价格规则时效率低下
   * _修复注释_：现在保存目录价格规则将不会使索引器失效，而是只为受影响的产品重新编制索引
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2679_：正在通过CSV导入更新日期和时间类型产品属性的时间
   * _修复注释_：现在，日期时间属性在导出的数据中将具有时间部分。 也可以使用导入来更新此类属性的时间。 此外，如果启用了“Fields Enclosure”，则“additional_attributes”列中的属性值将用双引号括起来。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38306>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2689_：请求中的网站ID错误时，没有相应的错误消息
   * _修复注释_：现在，当请求中的网站ID错误时，添加了要显示的相应错误消息。 以前，当请求中的网站ID错误时，不会进行验证。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2785_：删除不会影响映像的现有计划更新后，产品映像丢失
   * _修复注释_：删除暂存更新时未删除产品映像。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2799_： [Cloud]与层级价格一起使用时捆绑产品的价格错误
   * _固定备注_：以前，在计算四舍五入到2个小数点的某些百分比折扣时，将会为购物车和产品列表页面/产品详细信息页面生成不同的最终价格。 应用此修复后，捆绑包产品的最终价格与产品详细信息页面、产品列表页面和迷你购物车页面中的价格相同。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38091>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2805_：目录促销规则不适用于quantity_and_stock_status属性
   * _修复注释_：目录促销规则现在将考虑quantity_and_stock_status属性，以前在从管理员端生成新产品时未考虑该属性。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/35627>
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/cf34971d>
* _ACP2E-2837_：通过REST API更新价格时，产品实体updated_at列值未更新
   * _修复注释_：通过REST API更新现有产品时，管理员的产品“上次更新时间”列将在适当的日期时间更新。 以前，列“上次更新时间”未正确更新。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2840_：可以通过产品导入设置非唯一值
   * _修复注释_：现在，系统会在产品导入期间为唯一的产品属性正确实施唯一值约束，从而防止此类属性的值重复。 以前，对于通过产品导入配置为具有唯一值的产品属性，可以设置非唯一值。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38445>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2843_：启用单存储模式时，前端上的产品使用存储特定数据
   * _修复注释_：以前，当我们为默认商店视图启用单商店模式时，更改未迁移到网站级别的范围。 应用此修复后，当我们启用单商店模式时，默认商店视图特定的数据将与网站级别特定的数据同步，并将解决产品和类别可能存在的冲突。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2857_：无法使用rest API在类别中设置“默认排序依据”
   * _修复注释_：通过REST/SOAP APi请求正确更新类别上的default_sort_by
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_： [Cloud]商家面临愿望清单计数问题
   * _修复注释_：在一个商店中将产品添加到愿望清单不会再增加在同一浏览器中打开的其他商店中的愿望清单计数。 以前，如果两个存储都加载到同一浏览器中，则另一个存储中的愿望清单计数也会增加。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_：使用捆绑产品时，前端的类别页面显示空插槽
   * _修复注释_：在当前存储上下文中不可销售的捆绑产品不再编制索引。
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2905_：[Cloud]多网站架构中的报价问题
   * _修复注释_：以前，使用不同货币和客户组的多网站架构无法正确为商店应用折扣。 实施此修复后，具有不同客户组价格折扣的多网站架构将成功应用于不同的商店。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38506>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_： dynamic-rows.js：658编辑捆绑产品时未捕获的TypeError： dataRecord.slice
   * _修复注释_：从捆绑产品中删除选项时，浏览器控制台中没有JavaScript错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38505>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_： [Cloud]捆绑产品在订单确认中定价错误
   * _修复注释_：当使用基础货币以外的货币时，将按顺序在Storefront上为捆绑选项显示正确的数量。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2956_： YouTube视频添加错误
   * _修复注释_：产品图像和视频是在全局范围内配置的。 鉴于您无法在一个范围中拥有产品视频，而不能在另一个范围中拥有产品视频，因此Youtube API密钥设置已设置为全局范围。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_：仅对store_id=0进行[Cloud] URL更新
   * _修复注释_：“URL路径”现在使用正确的存储ID存储。 以前，商店ID不正确，导致在移动类别时数据库中保留不正确的URL路径。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_： async.operations.all已执行并创建错误。
   * _修复注释_： REST API调用中的产品链接数据不正确不再导致严重错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_： [Cloud]移动问题仅无法在PDP图像上夹紧
   * _修复注释_：系统现在支持在Chrome上的移动设备视图中缩放产品详细信息页面图像的功能，从而增强移动设备用户体验。 以前，在Chrome上的移动视图中双击图像时，无法按预期放大图像。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_：选项名称为0的LayeredNavigation中缺少标签
   * _修复注释_：通过跳过属性值0的空值检查器，该问题已得到解决。 以前，它被视为空并导致问题。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_：客户看到其他客户组的价格
   * _修复注释_：修复了由于请求中的X-Magento-Vary的旧值而导致客户组相关信息保存在错误区段的问题
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_：删除捆绑包选项时出错
   * _修复注释_：系统现在可以正确删除捆绑包选项，而不会触发错误或导致页面无响应。 以前，尝试删除捆绑包选项会导致“页面无响应”错误并阻止保存产品。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3100_： [New Relic错误日志中不存在]图像文件
   * _修复注释_：现在，系统会将自定义占位符图像同步到本地存储，从而确保在使用远程存储(如AWS S3)时正确渲染这些图像。 以前，自定义占位符图像在使用远程存储时无法渲染，从而导致图像显示和错误日志损坏。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3103_：由于缓存问题，未使用新产品更新新产品RSS源
   * _修复注释_：现在，当产品设置为新产品并保存时，新产品的Rss源已更新
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3126_： [Cloud]产品媒体集GQL响应未按图像位置排序
   * _修复注释_：系统现在可以正确排序GraphQL响应中按位置的媒体集中的项目，确保准确显示顺序。 以前，媒体集中的项目未按位置排序，导致显示顺序不正确。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37671>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_：[Cloud]子类别项未显示在管理员后端的小组件编辑中
   * _修复注释_：加载级别5以上的类别时，新构件页面上的类别树不会再出现问题。 以前，在加载树以超过5级类别时缺少某些类别。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3198_： [云]实际移动设备上的双指缩放和移动问题
   * _修复注释_：系统现在确保移动设备上具有一致的图像缩放功能，从而提供流畅且可预测的用户体验。 以前，图像缩放功能不一致，并且在通过移动设备查看特定点后突然缩小。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3282_：从共享目录取消分配产品时，未清除愿望清单产品
   * _修复注释_：现在，如果共享目录中没有产品，则愿望清单中不会显示任何项目。 以前，即使愿望清单中实际上没有项目，愿望清单页面也会错误地显示“1个项目”的计数。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3286_：相关产品全选/取消全选
   * _修复注释_：以前，如果手动选择了产品，则相关产品的“全选”/“取消全选”按钮无法正常工作。 修复后，这些按钮现在可以正常工作（即使手动选择按钮也是如此），确保所有产品都已正确选择或取消选择。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3336_： [Cloud] Stock警报电子邮件翻译为错误的语言
   * _修复注释_：当使用不同语言发送具有多个商店视图的网站的库存/价格警报时，将在电子邮件上使用创建警报的商店视图所用的语言。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4cf5e62>，<https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3350_：已禁用类别的名称在类别树中不再灰显
   * _修复注释_：以前，已禁用的类别在类别树中不会显示为灰色。 现在，它们以灰显效果显示。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_：可配置产品编辑表单加载导致超时和内存耗尽
   * _修复注释_：在修复可配置产品变体之前，基于所有可能的属性选项组合来构建。 如果属性具有许多选项，这将导致冗长且耗费资源的操作。 现在，可配置产品变体是基于现有的子产品属性构建的。 这大大减少了计算，从而改进了资源的使用。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_：使用样本时，Fotorama无法正确加载视频，已通过URL预先选择选项
   * _修复注释_：如果URL包含选定的选项，产品视频现在将在可配置的产品详细信息页面上正确呈现。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_： PageBuilder轮播构件显示不符合条件的产品
   * _修复注释_：构件中使用的产品列表现在遵循类别条件
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_：当一个产品的数量无效时，将触发组中所有产品的验证错误
   * _修复注释_：现在，当一个产品的数量无效时（以前未发生这种情况），将正确触发组中所有产品的验证错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3513_：可配置产品中未显示[CLOUD]特价
   * _修复说明_：修复后，更改特殊价格属性的“在产品列表中使用”值不会影响显示可配置产品的特殊价格。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3516_：如果进程终止，则不清理索引器临时表
   * _修复注释_：如果索引器进程终止，现在将清除CatalogRule索引器临时表
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_： 2.4.7-p3中的[QUANS]核心单元测试失败
   * _修复说明_：此测试不需要发行说明，因为它是一项单元测试改进。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3533_：多来源分组产品的库存量检索性能问题
   * _修复说明_：当分配的产品具有大量库存来源时，分组产品和捆绑包产品编辑页面现在已优化。
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/0208e433>
* _ACP2E-3641_：重新修复https://jira.corp.adobe.com/browse/ACP2E-3389
   * _修复注释_：在锚点类别数量较大时，提高了管理类别页面的性能
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/982b1c42>

### 目录，内容

* _ACP2E-3063_： [Cloud]缓存未失效。
   * _修复注释_：以前，保存包含更新设计布局的CMS页面时，它没有正确反映在前端。 应用此修复后，当更改设计布局并保存CMS页面时，将在前端看到合适的设计布局。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_：[云]锚点/非锚点类别在内容小组件中反转
   * _修复注释_：以前，当我们选择“显示于 — >锚点类别”时，它显示所有不反映锚点和非锚点之间的父子关系的类别。 应用此修复后，“显示于 — >锚点类别”仅显示锚点类别（可选），“显示于 — >非锚点类别”显示非锚点类别（可选）
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_：类别无法使用小组件
   * _修复注释_：以前，如果我们为不同的锚点/非锚点类别保存CMS块，那么当该块显示在前端时，它不适用于子类别。 应用此修复后，块会显示在不同类别的前端。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d01ee51e>

### 目录、框架

* _AC-9111_：订单获取(Shipments|Creditmemos|Invoice)集合 — 不应加载集合
   * _修复备注_：系统现在可以确保在从订单中检索时不会预装装运和贷项通知单收款，从而允许对这些收款应用额外的过滤条件或订单。 以前，会自动加载这些收藏集，从而防止进行任何进一步的修改。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37561>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37562>
* _ACP2E-2949_： [Cloud]跟进：检查数据是否有更改时数据比较不匹配
   * _修复注释_：以前，每次在没有任何数据更改的情况下调用save对象（对于任何数值数据字段，如int/float/double）。 它会触发将_hasDataChanges标志设置为true并调用save函数。 它也不会检查由字符串封装的浮动数字。 进行此修复后，仅当数据发生更改时，才会调用save函数。 int/float/double-check的数据值，其值传递给函数并执行严格的类型匹配
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c8931218>

### 目录，GraphQL

* _ACP2E-3090_：在GraphQL中处理类别筛选器： includeDirectChildrenOnly和category_uid
   * _修复注释_：按category_uid进行筛选时，仅获取直接子类别。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_： [Cloud] Graphql产品排序不起作用
   * _修复注释_：在变量中传递字段时，GraphQl产品按多个字段排序现在可按预期工作。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3312_：层价格在GraphQL产品中返回了错误的值（与Storefront相比）
   * _修复注释_：修复后，为graphql请求返回的产品层价格具有每一项的价格。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1366ae5e>

### 目录、定价、暂存和预览

* _ACP2E-2672_： [Cloud]特殊价格API端点在同时更新大量产品时返回错误
   * _修复说明_：现在，特价批量更新API将为每个日期范围创建一个促销活动，而不是为每个产品和日期范围创建多个计划更新。 此外，它支持并发API请求，以更快地处理大量SKU。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/f89a447e>

### 目录、产品

* _AC-7050_：编辑产品中的类别选择树与目录 — >类别中的设置顺序不同
   * _修复注释_：系统现在会按照在目录 — >类别中设置的相同顺序，在产品编辑部分中正确显示类别选择树，从而使产品在大目录中的管理更加容易。 以前，产品编辑部分中的类别树按类别创建顺序显示，而不管在目录 — >类别中设置的显示顺序如何。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/36101>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36104>

### 目录，SEO

* _ACP2E-3653_：页面> 1时类别的规范URL不正确
   * _修复注释_：以前，多页面内容的规范URL无法正常运行，始终显示基本URL。 但是，在实施此修复后，多页面内容的规范URL现在可以正确显示具有页面ID的URL。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/982b1c42>

### 目录，搜索

* _ACP2E-2757_：产品未在类别和搜索中显示，但直接链接正常工作
   * _修复注释_：以前，带price_* attribute_code的Yes/No自定义属性不适用于索引。 进行此修复后，“是/否”自定义属性会按预期工作。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_： [Cloud]某些类别页面上的弹性搜索错误
   * _修复注释_：以前，在提及配置票证后，当我们为多个产品定价0时，会在前端类别页面引发异常。 应用此修复后，当多个产品价格0且我们在前面加载类别页面时，它不会引发任何异常，并将成功加载类别页面。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3345_：创建对象时出现类型错误： Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor异常
   * _修复注释_：修复后，无需指定$data即可创建Magento\CatalogSearch\Model\Indexer\Fulltext类的实例。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_：在Magento Admin中保存后，产品的[CLOUD]问题在前端不可见
   * _修复注释_：修复了具有长名称子产品的可配置产品后，店面不会丢失这些产品。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1984c61c>

### 云

* _ACP2E-3010_： [Cloud] PHPSESSID正在更改每个POST请求
   * _修复注释_：如果启用了L2 Redis缓存并且客户已从后端更新，则不再为登录的客户在前端区域上重新生成PHPSESSID的POST请求
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3532_： Sitemap生成警告
   * _修复注释_：修复后，将在系统tmp目录中生成Sitemap并复制到最终目标。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d4de4726>

### 内容

* _AC-10539_：“最近查看”小组件中的价格显示出现[问题]
   * _修复说明_：系统现在可以在“最近查看的产品”小组件中正确显示现成的简单产品的价格，确保所有小组件和产品列表页面的一致性。 以前，由于价格加载模板中存在条件，缺货简单产品的价格不会显示在“最近查看的产品”小组件中。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38167>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38159>
* _AC-10596_： [问题] acl.xsd文件中的拼写错误和语法正确
   * _修复注释_：系统现在更正了acl.xsd文件中的拼写错误和语法错误，提高了文档的清晰度和准确性。 以前， acl.xsd文件包含拼写错误和语法错误，这可能会导致混淆。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38061>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38046>
* _AC-10845_：页面生成器横幅图像在图库中不可见
   * _修复注释_：系统现在可正确显示页面生成器库中新创建的文件夹中上传的横幅图像，从而消除了以前的控制台错误。 在此修复之前，如果横幅图像上传到新文件夹中，则不会在图库中看到这些横幅图像，这会导致控制台错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_：更新到2.4.5-p8后“未设置区号”
   * _修复注释_：现在，在启用Magento_CSP模块并将“dev/js/translate_strategy”设置为“embedded”时，系统可成功完成静态内容部署过程，而不会触发“未设置区码”错误。 以前，在这些情况下，静态内容部署过程将失败，并显示“未设置区码”错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38845>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38922>
* _AC-12692_：构件类别树未正确渲染
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39008>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_：在设计配置页面中更改主题时，无法看到“使用默认值”消息
   * _修复注释_：系统现在包含一个单独的列，以根据设计配置页面中选择的主题显示“使用默认值”消息。 这确保默认值状态清晰可见。 以前，不会显示“使用默认值”消息，这会导致对所选主题状态的混淆。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13569_： [问题]再次恢复与TinyMCE插件的向后兼容性(之后……
   * _修复注释_：系统现在恢复与TinyMCE插件的向后兼容性，允许从其他位置使用小组件时调用插件中定义的函数。 以前，由于TinyMCE版本中的更改，插件不会将构件作为对象返回，从而导致在尝试调用构件实例上的某些函数时出错。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39262>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39258>
* _AC-9638_：[问题]产品页面上的WYSIWYG编辑器中的文件上传问题
   * _修复注释_：系统现在可以正确显示文件夹树，并允许在产品页面上的WYSIWYG编辑器中上传图像，即使先展开“图像和视频”选项卡后也是如此。 以前，先展开“图像和视频”选项卡，导致文件夹树无法显示，以及尝试在WYSIWYG编辑器中上传图像时出现错误消息。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38026>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_：[内部部署]动态块问题
   * _修复注释_：在动态块中，小组件现在正正确呈现。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2693_： [Cloud]前端因新闻稿模板中的问题未加载
   * _修复注释_：通过CMS页面内容部分添加块不再导致异常
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_： ACP2E-2836： [Cloud]调查日志中发现的异常： InvalidArgumentException：类在vendor/magento/module-rule/Model/ConditionFactory.php中不存在
   * _修复注释_：删除PageBuilder产品内容设置的条件不会再导致在日志文件中记录异常。 以前，删除PageBuilder产品内容设置上的条件会导致在日志中记录严重异常，即使不会导致前端出现任何问题。
   * _GitHub代码贡献_： <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_：切换到单一商店模式 — 不再显示全局内容
   * _修复注释_：现在，在启用单一商店模式时，系统会将商店视图设计配置与网站设计配置同步，确保内容更新在前端可见。 以前，切换到单一商店模式会阻止在店面反映内容更新。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_：页面生成器在尝试添加链接和其他可用性问题时替换图像。
   * _修复注释_：现在单击图像，页面生成器文本元素的wysiwyg编辑器中的链接将在图像、链接配置对话框中加载正确的数据。 现在，在编辑器中添加指向图像的链接也可正常使用。 以前，图像会被替换为链接。
   * _GitHub代码贡献_： <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_：将0字节的图像放入目录时，旧媒体库无法渲染图像
   * _修复注释_：系统现在可以在不中断功能的情况下处理媒体集中的0字节图像，从而允许按预期显示和选择目录中的其他图像。 以前，媒体集中存在0字节的图像会阻止显示或选择目录中的所有图像。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_：编辑CMS块时页面生成器出错
   * _修复注释_：系统现在可以正确保存使用页面生成器所做的管理区域更改，而不会引发错误“页面生成器渲染了5秒钟，但未释放锁定”。 在浏览器控制台中。 以前，在尝试保存更改时发生此错误，从而阻止成功更新内容。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/35b1b1da>，<https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_： [CLOUD]购物车部分中没有结帐或编辑购物车的按钮
   * _修复注释_：捆绑产品现已通过Widget添加到购物车中，且未出现错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b21e5d91>，<https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3122_： [CLOUD]上传图像按钮不起作用
   * _修复注释_：在PageBuilder中“横幅”和“滑块”的“上传图像”按钮未按预期工作之前，现在按该按钮时会打开本地文件管理器以选择要上传的图像。
   * _GitHub代码贡献_： <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3127_： imagecreatetruecolor()：参数#2 ($height)必须大于0。 无法上传特定图像
   * _修复注释_：解决了通过媒体集上载高度为0的图像时，导致管理员出现错误的问题，并使用sync命令成功同步资产。 以前无法通过媒体集上传图像，并且当特定图像位于媒体集内时，同步命令也会失败。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_： Prototype.js Array.from与Google映射API冲突
   * _修复注释_：Google映射现在可在PageBuilder编辑器中正确呈现。 以前，Javascript错误会导致Google映射无法正确呈现。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3275_： [Cloud] - CMS滑块未反映最新更改
   * _修复注释_：通过在编辑幻灯片屏幕上触发保存事件时确保刷新滑块列表，此问题已修复。 以前，它会触发并导致问题。
   * _GitHub代码贡献_： <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_：使用页面生成器按特定顺序插入CMS块时，CSM页面中出错
   * _修复说明_：以前，在某些版本的PHP和OS (Linux)上，通过PageBuilder引用其他cms块的块的块呈现会失败，并出现“发生未知错误。 请重试。” 现在，cms块的内容在PageBuilder控制的内容中正确呈现。
   * _GitHub代码贡献_： <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3428_：大型内容的Pagebuilder模板预览失败
   * _修复注释_：大型内容导致画布元素超出浏览器的限制，并返回不正确的值，这会破坏后端代码（无法正确解码图像）。 修正了将画布大小限制为通用浏览器的限制。
   * _GitHub代码贡献_： <https://github.com/magento/magento2-page-builder/commit/adfb1747>
* _ACP2E-3430_：缺少字体大小的TinyMCE 7的最新安全更新
   * _修复注释_：字体大小和字体系列选择器现在可在WYSIWYG编辑器中使用。 在此修复之前，使用TinyMCE 7时，编辑器界面中没有这些功能。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d50f6b5d>，<https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>
* _ACP2E-3483_：管理员中的TinyMCE 7编辑器字体大小为PT，而不是PX，请说明
   * _修复注释_：在修复之前，无法在WYSIWYG区域的px中指定字体大小。 现在，您可以用px而不是pt来设置字体大小。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3f12d152>，<https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3490_：页面生成器中的产品内容类型已折叠，没有正确的消息
   * _修复注释_：在修复之前，当小部件中没有产品时，预览HTML无法正确生成。 现在，可以正确生成空响应，并在预览中正确显示产品小部件。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3f12d152>，<https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3534_： [页面生成器]将产品列表添加到块会导致错误
   * _修复注释_：现在通过页面生成器将捆绑包产品列表添加到阻止将不会导致错误
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/344fce23>

### 客户/客户

* _AC-12162_：客户创建页面中的“前端 — 出生日期”验证失败
   * _修复注释_：确保在将moment.js系统依赖关系升级到最新的次要版本后，所有验证都应正常工作
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-8499_：更改国家/地区下拉列表时，未重置区域文本字段
   * _修复注释_：现在，在下拉菜单中更改国家/地区时，系统会重置区域文本字段，以确保以前的值不会保留。 以前，从下拉列表中更改国家/地区不会重置“区域”字段，从而导致保留最后保存的值。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_：删除客户时不会清除Storefront上所有已登录和删除客户的浏览器会话数据
   * _修复注释_：删除客户现在会按预期清理店面中所有已登录和删除客户的浏览器会话数据。 购物者可以继续购物，他们的浏览器将他们的会话视为访客会话。 以前，当从管理员中删除登录购物者的客户帐户时，购物者的浏览器会引发JavaScript错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7d5e3906>

### 框架

* _AC-10037_： [问题]在`app/code/Magento/Translation/etc/di.xml`中未使用的类型配置
   * _修复注释_：系统现在会删除配置中未使用的依赖项，从而提高整体代码干净度和效率。 以前，配置中存在未使用的依赖项，这些依赖项不会对任何功能产生影响。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38030>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38064>
* _AC-10654_： V1/customers/密码端点问题/问题
   * _修复注释_：现在，在通过API处理密码更改请求时，系统会遵守管理GUI中设置的约束，从而防止可能滥用密码重置功能。 以前，API可以在管理GUI中定义的规则之外处理密码更改请求，在已知有效电子邮件时，可能会允许不断重置电子邮件。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38238>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10738_：清漆配置不排除所有营销参数
   * _修复注释_：系统现在正确排除了Varnish配置中的所有常见营销参数，从而确保准确跟踪和分析。 以前，某些营销参数（如gad_source、srsltid和msclkid）不被排除，导致数据收集的潜在不准确性。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38298>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39188>
* _AC-10838_：目录搜索索引过程错误索引过程
   * _修复注释_：无论使用PHP编译的libxml版本如何，系统现在都能成功完成重新索引命令，而不会遇到任何错误。 以前，当使用特定版本的libxml编译PHP时，运行“重新索引”命令会导致“索引过程中出现目录搜索索引过程错误”错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38254>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38553>，<https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_：已将created_at、status和grand_total筛选器添加到客户订单查询，并修复了多个筛选器失败
   * _修复注释_：系统现在支持在客户订单查询中使用created_at、status和grand_total筛选器，并且解决了多个筛选器未正确应用的问题。 以前，系统不支持这些过滤器，并且在查询中使用多个过滤器时，将无法应用所有过滤器。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38392>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36949>
* _AC-10991_：从相关/追加销售/交叉销售区块和价格索引中随机获取大量查询
   * _修复注释_：系统现在优化来自相关、追加销售和交叉销售块的查询，从而提高性能并防止网站因过多的查询而停机。 以前，系统可能会因这些块中的查询而过载，从而导致速度显着减慢，并可能使网站停机。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/36667>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38050>
* _AC-11423_：异常：警告：正在尝试访问ICU 74.1 (PHP Intl)升级后的Calendar.php中的数组偏移…… ->
   * _修复注释_：每当购物者或商家访问店面或管理员时，Commerce不再在exception.log中记录以下异常： `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`。 [GitHub-38214](https://github.com/magento/magento2/issues/38214)
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38214>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38364>
* _AC-11476_： [问题]修复了表单包含名为`method`的元素时客户数据的问题
   * _修复注释_：系统现在可以在表单提交中正确识别“method”属性，即使表单中存在名为“method”的元素也是如此。 这可确保准确处理客户数据。 以前，如果某个表单元素命名为“method”，则会干扰表单提交中“method”属性的识别，从而导致客户数据处理出现潜在问题。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38484>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38449>
* _AC-11489_： [问题]修复\Magento\Framework\Data\Collection：：getItemById的PHPDocs
   * _修复注释_： \Magento\Framework\Data\Collection：：getItemById方法的PHPDocs已更新，以包括null作为可能的返回类型，从而解决了静态分析工具的问题。 以前，该方法的PHPDocs不指定null作为可能的返回类型，导致在条件语句中使用该方法时进行静态分析时出现警告或错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38485>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38439>
* _AC-11592_： [问题]在安装期间仅允许有效的首选项:di:编译
   * _修复注释_：如果为不存在或明确排除的类创建首选项，系统现在会在安装:di:编译命令期间引发错误，确保只允许使用有效的首选项。 以前，这些方案将以静默方式失败，潜在地使与原始类关联的任何插件变得无用。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38517>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/33161>
* _AC-11651_： Magento尝试在LoggerProxy的__wakeUp方法中修改只读属性
   * _修复注释_：系统现在允许修改LoggerProxy的__唤醒方法中以前的只读属性，从而确保顺利操作而不强制用户采用解决方法。 以前，尝试在LoggerProxy的__wakeUp方法中重新分配只读属性的值会导致出现问题。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38526>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11681_： [问题] AC-2039 AC-1667升级TinyMCE参考
   * _修复注释_：更新了composer.json中的tinymce最新版本
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38533>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36543>，<https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_： ChangelogBatchWalker无法在多个线程中运行
   * _修复注释_：系统现在支持MView索引的进程分支，从而防止在多个线程上操作索引器时在执行索引器时出现错误。 以前，在多个线程上运行ChangelogBatchWalker会导致删除其他线程使用的表，从而导致索引器执行期间出错。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38246>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38248>
* _AC-11781_： [问题]重命名命名错误的变量
   * _修复注释_：系统现在可以正确命名包含仍可退款的金额的变量，从而防止在调试过程中混淆。 之前，此变量被错误地命名为totalRefund，这可能会导致开发人员产生误解。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38609>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36205>
* _AC-11809_： [问题]通过XML将自定义属性传递到当前链接
   * _修复注释_：系统现在允许通过XML将自定义属性传递到当前链接，确保即使链接是当前页面也能正确显示这些属性。 以前，由于当前链接未使用getAttributesHtml()方法，因此不会显示当前页面链接的自定义属性。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38500>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/30070>
* _AC-11819_：对于某些配置，内置FPC缓存在2.4.7中损坏
   * _修复注释_：在设置MAGE_RUN_CODE参数后，系统现在可以正确缓存页面，从而确保最佳性能。 以前，在这些情况下不会缓存页面，这会导致潜在的性能问题。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38626>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38646>，<https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11829_： [问题]修复了开发模式和生产模式之间的异常处理不一致
   * _修复注释_：系统现在可以始终处理开发模式和生产模式之间的异常，从而防止在引发异常时意外重定向到登录页面。 以前，异常处理的不一致性可能会导致在生产模式下重定向到登录页面，而不是显示异常消息。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38639>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37712>
* _AC-11852_：替换token_list.phtml中的“PayPal帐户”翻译
   * _修复注释_：系统现在在“存储的支付方式”页面中将可令牌化的帐户支付方式的部分标记为“帐户”而不是“PayPal帐户”，使其更具有代表性。 以前，此部分被特别标记为“PayPal帐户”，当添加其他可令牌化的帐户支付方法时，这会产生误导。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/35622>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37959>
* _AC-11874_： Magento\Catalog\Model\ProductRepository类上已失去向后兼容性
   * _修复注释_： ProductRepository类现在通过将Initialization Helper类还原为第二个参数来保持向后兼容性，确保从此类扩展的模块按预期运行。 以前，从ProductRepository类中的构造函数中删除初始化帮助程序会导致向后兼容性丢失，从而迫使用户采用解决方法。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38669>
* _AC-11905_： [问题]静态内容部署 — 类型错误
   * _修复注释_：系统现在可以在静态内容部署期间正确处理空的LESS文件，并显示“LESS文件为空”错误消息。 以前，在部署期间遇到空LESS文件时抛出不正确的类型错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38682>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38683>
* _AC-12002_： [问题] [视图]删除了链接和脚本标记中的额外空间
   * _修复注释_：系统现在可确保链接和脚本标记中没有额外的空格，从而提供更干净和更高效的代码。 以前，链接和脚本标记中的属性之间会存在双空格。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/32920>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/32919>
* _AC-12127_： [问题]避免配置错误的无限循环
   * _修复注释_：系统现在通过阻止虚拟类型配置中的自引用映射，避免了无限循环。 这可确保应用程序在尝试取消引用自引用节点时不会陷入无休止循环。 以前，如果虚拟类型配置是自引用的，则会导致应用程序无限期旋转。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38822>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38794>
* _AC-12299_：对象管理器未用于Magento\Csp\Model\Mode\Data\ModeConfigured
   * _修复注释_：系统现在在创建ModeConfigured对象时正确使用对象管理器，从而允许在此对象上使用插件。 以前，未使用Object Manager，导致插件无法应用于ModeConfigured对象。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38875>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38886>
* _AC-12540_：产品库存和价格警报中的文档块注释不准确
   * _修复说明_：产品库存和价格预警中deleteCustomer方法的文档块注释已得到更正，以准确反映该方法删除了与给定客户和网站（而非网站中的客户）关联的所有库存产品或价格预警。 以前，评论不准确地指出该方法用于从网站中删除客户。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38939>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39001>
* _AC-12594_： [问题]对生成的数据使用已编译配置而不是常规配置
   * _修复注释_：系统现在对生成的数据使用编译的配置，而不是常规配置，从而减少依赖于特定代码版本的网络传输和数据开销。 此更改可防止在容器交换期间覆盖共享实例中的缓存，从而提高稳定性并减少停机时间。 以前，某些核心类使用共享配置类型，由于多个服务器上的代码版本不同，这可能会导致缓存覆盖或应用程序停机。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38785>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/29954>
* _AC-12597_： [问题]从e1ccdb中删除的extjs中删除对文件的引用……
   * _修复注释_：系统现在会从以前删除的extjs中删除对文件的引用，从而消除浏览器控制台和系统日志文件中的错误。 以前，由于缺少引用的文件，这些引用会导致错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38960>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38951>
* _AC-12778_： [问题]次要清理：修复了sprintf的错误用法，此处只需要2个占位符，然后……
   * _修复注释_：系统现在正确使用sprintf函数以及适当数量的占位符，从而提高代码清洁度和一致性。 以前，sprintf函数与额外的参数一起使用时不正确，这不会导致任何重大问题，但用法不正确。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39062>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38628>
* _AC-12857_： PHP 8.2.15删除了FTP扩展
   * _修复注释_：系统现在将FTP扩展作为依赖项包含在composer.json文件中，从而确保通过FTP成功配置CSV导入。 以前，由于PHP包中缺少FTP扩展，尝试通过FTP配置CSV导入时引发错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39083>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12869_： [问题]修复了Magento模块中引用的不正确的类。
   * _修复注释_：系统现在可以正确引用模块中的类，从而确保操作更顺畅，并防止由于不存在类而导致崩溃。 这包括Indexer和Creditmemo模块中的错误修复，以及PrintAction类中HttpGetActionInterface的实现。 以前，错误的类引用会导致错误和潜在的系统崩溃，并且某些功能(如creditmemo PDF文件的文件名和股票重新索引)无法按预期工作。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39126>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37784>
* _AC-12964_：能够为dev:di:info CLI命令定义区域
   * _修复注释_：系统现在允许开发人员定义dev:di:info CLI命令的区域，从而增强开发和调试过程。 以前，此命令只能显示GLOBAL区域的信息。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38758>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38759>
* _AC-13149_： [问题]将isMultipleFiles属性添加到图像表单元素模板
   * _修复注释_：此修复会阻止在多个文件图像表单元素中添加图像时，“浏览以查找或拖动图像到此处”按钮消失。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39219>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36325>
* _AC-13279_： [问题]移除所有营销获取参数以最小化缓存
   * _修复注释_：系统现在将删除所有Marketing Get参数以优化缓存利用率，镜像使用Varnish时所使用的逻辑。 以前，这些参数可能会导致缓存溢出和性能降低。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39266>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39099>
* _AC-13345_： [问题] [PHPDOC]修复错误的phpdoc Magento\Directory\Model\AllowedCountries：：getAllowedCountries()
   * _修复说明_：已更正AllowedCountries：：getAllowedCountries()方法的PHPDoc，以提供准确的信息，从而提高文档的清晰度和实用性。 以前，此方法的PHPDoc包含不正确的信息，这可能导致混淆或误用方法。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39246>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39241>
* _AC-13348_： [问题]删除了我们不再支持的PHP版本的一些代码。
   * _修复注释_：删除了Magento中不再支持的PHP版本的代码
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39361>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39202>
* _AC-13417_： [问题]使ImageMagick适配器与php8兼容（从浮点到整点的隐式转换）
   * _修复注释_：系统现在通过在计算图像尺寸时正确处理浮点数，从而确保与PHP8的兼容性，从而防止因从浮点到int的隐式转换而出现任何错误。 以前，计算图像尺寸可能会导致浮点数，这种情况下，隐式舍入可能会导致错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39402>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37362>
* _AC-13537_： [问题] [PHPDOC]修复错误的phpdoc Magento\Framework\App\Config\ScopeConfigInterface
   * _修复注释_：此更新更正了Magento\Framework\App\Config\ScopeConfigInterface中的PHPDoc注释，以准确反映getValue和isSetFlag方法的$scopeCode参数的类型。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39492>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39199>
* _AC-13725_： Magento\Framework\Filesystem\Driver\Http取决于原因短语“确定”
   * _修复注释_：已从Magento\Framework\Filesystem\Driver\Http：：isExists中删除“确定”短语检查
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39546>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39558>
* _AC-13810_：客户网格索引器在“按计划更新”模式下无法正常工作
   * _修复说明_：早期的客户网格已立即更新，但修复后的客户网格在cron运行后更新，但未立即反映。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-6754_：js文件出现拼写错误。
   * _修复注释_：系统现在可正确使用JavaScript文件中的术语“订阅者”，从而确保相关功能的正确功能。 以前，JavaScript文件中的印刷错误导致术语“subscriptibers”使用不正确。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/36163>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36171>
* _AC-8353_： [问题]删除禁止的`@author`标记
   * _修复注释_：系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，确保代码更干净且更标准化。 以前，`@author`标记存在于某些模块中，这违反了既定的编码标准。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37253>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37003>
* _AC-8356_： [问题]从`Magento_Customer`中删除禁止的`@author`标记（第2部分）
   * _修复注释_：系统现在通过从某些模块中删除禁止的`@author`标记来遵守编码标准，确保代码更干净且更标准化。 以前，`@author`标记存在于某些模块中，这违反了既定的编码标准。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37250>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37000>
* _AC-8659_： editorconfig中的空格破坏了[{composer，auth}.json]的规则
   * _修复注释_：在修复了editorconfig中的语法错误后，系统现在可以对composer和auth.json文件正确应用4空格缩进。 以前，由于editorconfig语法中存在空格，因此这些文件使用2空格缩进的格式不正确。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37394>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37395>
* _AC-8662_： [问题]改进cron错误日志记录
   * _修复注释_：现在，系统会捕获并记录cron进程的STDERR和STDOUT，在cron进程失败的情况下提供有价值的诊断信息。 以前，cron进程内的任何错误消息都不会被记录，并且在单独的进程中运行的cron组的STDERR和STDOUT将会丢失。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37453>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/32690>
* _AC-8984_： [问题]向某些设置cli命令的输出添加更多颜色
   * _修复说明_：系统现在会将更多颜色添加到某些安装命令行界面(CLI)命令的输出中，从而增强可读性和用户体验。 以前，由于缺少颜色区分，这些命令的输出更难读取。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/29335>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/29298>
* _AC-9630_：当添加具有所需州/地区的新国家/地区时，升级Magento将重置general/region/state_required。
   * _修复说明_：现在，在添加具有所需状态的新国家/地区时，系统仅将修改后的国家/地区添加到“general/region/state_required”配置，从而防止假定区域已禁用的自定义代码出现任何中断。 以前，添加具有所需状态的新国家/地区会将“general/region/state_required”配置重置为具有所需状态的默认国家/地区，从而可能会破坏正常使用。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37796>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38076>
* _AC-9712_：具有复杂`calc`表达式的php &amp; nodejs库(grunt)之间编译较少的差异
   * _修复注释_：在更新wikimedia/less.php：^5.x后，修复php &amp; nodejs库(grunt)之间较少编译的差异
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37841>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_：执行部分索引时出现“未找到基表或视图”错误
   * _修复注释_：在辅助数据库连接的情况下，部分重新索引现在可正确与大更改日志配合使用
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_：将MariaDB升级到10.5.1或更高版本后出现问题
   * _修复注释_：修复了Mysql升级后，数据库中的日期时间值转换为0000-00-00 00:00:00的问题
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_：检查数据是否更改时，数据比较中的类型不匹配
   * _修复注释_：以前，每次在没有任何数据更改的情况下调用save对象（对于任何数值数据字段，如int/float/double）。 它会触发将_hasDataChanges标志设置为true并调用save函数。 进行此修复后，仅当数据发生更改时，才会调用save函数。 int/float/double-check的数据值，其值传递给函数并执行严格的类型匹配。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_： [云]导入不能与目录var一起使用
   * _修复注释_：无论文件名如何，都可以成功导入产品。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_：在ipad mini中，菜单和标题以移动设备加载，而应以桌面加载。
   * _修复注释_：系统现在将宽度为768像素的设备视为桌面，以确保菜单和标头正确加载。 以前，宽度768像素的设备被视为移动设备，导致菜单和标头在移动视图中加载。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/35b1b1da>，<https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3230_：在外键的情况下无法通过db_schema.xml修改列长度
   * _修复注释_：现在通过声明性架构修改带有外键的列不会在MariaDB中引发错误
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3361_：在保存订单记录时，会将某些关系记录保存到DB
   * _修复注释_：触发修复之前不必要的UPDATE查询，这可能会影响性能。 修复后，消除了不必要的UPDATE查询。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3375_： [CLOUD]在admin中，控制台中有许多javascript错误
   * _修复注释_：以前，在管理面板中，控制台中存在多个javascript错误。 现在，在管理面板中，控制台中没有JavaScript错误，所有默认的JavaScript功能都将成功执行且不会出现任何问题。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3387_： [Cloud] Magento：已删除队列消息
   * _修复注释_：队列消息现在正在被正确清除。 在修复之前，假设正在使用SQL队列系统，如果清除队列消息同时运行，则新消息可能已被删除。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3537_：缓存标记中没有相应的缓存键项，因此缓存清理无法正常工作
   * _修复注释_：现在默认情况下为Redis缓存垃圾回收器启用LUA模式，以防止出现争用情况
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3681_：已忽略MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK值
   * _修复注释_：修复之后，设置为“false”的ENV变量将被视为bool false，而不是字符串“false”。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/982b1c42>

### 框架，GraphQL

* _AC-7976_： [问题]引入了GraphQL架构的自定义标量类型支持
   * _修复注释_：系统现在支持GraphQL架构的自定义标量类型，允许开发人员定义自定义标量类型和实现。 此功能对于表示可能需要验证的值(例如HTML、电子邮件、URL、日期等)以及更高级的情况（例如EAV属性）特别有用。 以前，系统不支持在GraphQL中处理自定义标量类型。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/36877>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/34651>，<https://github.com/magento/magento2/commit/0574ac23>

### 框架、UI框架

* _ACP2E-3324_：即使配置值已锁定，仍有可能覆盖配置值
   * _修复注释_：以前对于此修复，无法通过bin/magento config：set命令设置设计配置，并且可以通过操作显示这些配置信息的表单来更改锁定的值。 修复后，无法再更新从cli使用 — lock-env或 — lock-conf设置的锁定值。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _AC-11729_：即使标头值未通过验证，Magento_GraphQl也会执行标头处理
   * _修复注释_：系统现在确保仅在标头值通过验证时只执行一次标头处理，从而增强安全性并防止潜在漏洞。 以前，即使标头值未通过验证，也会执行标头处理，这会由于两次处理标头值而导致潜在漏洞和意外行为。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-8951_：物理Giftcard选项没有正确的排序顺序
   * _修复注释_：在通过GraphQL查询时，系统现在可以正确排序实际礼品卡产品的选项，确保与Luma主题一致的呈现。 以前，根据Luma主题排序顺序不正确，导致显示和排序选项不正确，例如发件人姓名、收件人姓名和金额。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1bafc571>
* _AC-9157_： [GraphQL]解析器缓存在创建/编辑/移动/删除临时更新时失效
   * _修复注释_：系统现在确保在创建、编辑、移动或删除临时更新时不会使解析程序缓存失效，但仅当将临时更新应用于实体时才会使解析程序缓存失效。 以前，解析程序缓存过早失效，甚至在应用暂存更新之前就失效，这导致不必要的缓存失效。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2642_：没有为内容暂存更新清除快速缓存
   * _修复注释_：现在，当更新PageBuilder内容相关的实体时，带有PageBuilder内容响应缓存的GraphQL将失效。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_：禁用分层导航 — 不从Graphql中删除聚合
   * _修复注释_：当管理员配置设置为“目录>分层导航>显示类别过滤器”时，在通过GraphQL查询请求具有类别聚合的产品搜索时应用检查后，问题已修复。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_：包含价格过滤器{from：&quot;0&quot;}的GraphQL产品调用未返回任何结果
   * _修复注释_：以前，使用零价格筛选条件的graphql产品搜索由于抛出异常而根本没有返回任何结果。 现在，搜索会按预期返回结果。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2974_：客户返回属性的翻译未反映在相应StoreView的GraphQL API中
   * _修复注释_：客户返回属性的翻译反映在相应StoreView的GraphQL API中。
以前，各个StoreView的客户返回属性不会反映在GraphQL API中。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3128_： [带有节点引号的getPurchaseOrder的GraphQL调用已中断]
   * _修复注释_：采购订单GraphQL调用将能够执行任务，而不会遇到任何内部服务器错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3184_：如果未在“所有商店视图”中启用产品，生产站点中未显示[Cloud]可配置产品
   * _修复注释_：系统现在可以正确显示站点中的可配置产品，即使未在“所有商店视图”中启用该产品，但在特定商店视图范围内启用该产品也是如此。
以前，如果在“所有商店视图”中禁用某个产品，并且仅在特定商店视图范围内启用该产品，则产品属性在GraphQL响应中将无法正确显示，从而导致产品无法正确显示。
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/3f300077>
* _ACP2E-3190_： [Cloud]当同一简单产品分配给多个可配置产品时，产品graphql出错
   * _修复注释_：以前，对于具有相同简单产品的单独可配置产品，grapQL会返回错误。 应用此修复后，不同的可配置产品具有相同的简单产品，grapQL会返回无错误的结果。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3215_：多站点设置中存在用户身份验证和跨站点令牌访问的[云]问题
   * _修复注释_：多站点设置中的GraphQl客户信息和购物车查询会检查非默认网站上的客户是否存在。
以前，在多站点设置中，查询不起作用，不能确保客户存在于非默认网站上。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3253_： GraphQL cart itemsV2分页无法正常工作
   * _修复注释_：通过为集合查询中的当前页面参数传递正确的值，已修复该问题。 以前，传递错误值来设置当前页面，从而导致出现问题。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3255_：在获取customerCart时应指定[GRAPHQL]模型值
   * _修复注释_： GraphQL“customerCart”查询现在可以创建空购物车，即使报价在数据库中不可用也是如此。 以前，此操作在创建空购物车时由于国家/地区验证问题而失败。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3380_： [GraphQl]愿望清单项目可通过GraphQl查看，但在店面不可见
   * _修复注释_：通过GraphQL请求时，未正确列出愿望清单产品。 现在，会根据提供的商店上下文过滤愿望清单产品。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/55615e61>
* _ACP2E-3404_： [GraphQL]重置内容与主题/链接之间的密码电子邮件不一致
   * _修复注释_：通过模拟在发送密码重置请求时客户帐户注册的正确商店（无论网站商店如何），该问题已得到解决。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3419_： [Cloud]产品GraphQL查询返回未分配给当前网站的相关产品
   * _修复注释_：以前，对于graphQL查询，多商店相关产品无法正确显示产品查询。 应用此修复后，对于产品，graphQL查询多商店相关产品会相应地显示。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3447_：在GraphQL标头中使用错误的存储ID会导致严重的内存错误
   * _修复注释_：在GraphQL请求中发送错误的存储区代码不再导致内存消耗过多。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3467_： [云] 500响应，针对2.4.7上的空Graphql响应
   * _修复注释_：修复后，无效的graphql请求将不会记录到exception.log文件中。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3492_：[Cloud] Graphql API存在问题
   * _修复注释_：在使用Graphql应用程序服务器进行修复之前，客户地址请求未返回最新数据。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3505_：禁用产品仍显示在grpahQL查询中的相关、追加销售、交叉销售项目中
   * _修复注释_： Graphql现在可为已禁用的related、upsell和cross-sell产品提供正确响应
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3647_： [CLOUD]： GraphQl错误内部服务器错误placeOrder突变
   * _修复注释_：请求中包含优惠券代码信息的“placeOrder”突变不再引发内部错误异常，订单已成功下达。 以前，它失败并出现“内部服务器错误”。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/982b1c42>
* _LYNX-426_：未针对具有动态价格的捆绑产品计算discount_percentage
   * _修复注释_：为product.price_details的discount_percentage添加的修复未显示已启用动态价格并应用折扣优惠券的捆绑产品的正确值。
* _LYNX-485_：当捆绑产品之一缺货时，捆绑产品仍显示“IN_STOCK”
   * _修复注释_：解决了捆绑产品即使其中一个捆绑产品缺货，仍显示“IN_STOCK”的问题。
* _LYNX-486_： not_available_message和only_x_left_in_stock不显示相同的可用库存
   * _修复注释_：解决了not_available_message和only_x_left_in_stock显示stock可用性不一致的问题
* _LYNX-488_： original_row_total字段返回了错误值
   * _修复注释_：解决了original_row_total字段的问题，该字段在选择自定义选项时返回不正确的值
* _LYNX-503_：应根据配置显示分组产品缩略图     .
   * _修复注释_：解决了该问题，以确保根据配置设置显示分组的产品缩略图
* _LYNX-512_： original_item_price不包括折扣
   * _修复注释_：更新了original_item_price以包含折扣。
* _LYNX-530_：未显示可用库存数量的可用消息
   * _修复注释_：解决了AddProductsToCart变异的错误消息和错误代码，使其与“不可用”消息配置保持一致
* _LYNX-532_：“OUT_OF_STOCK”状态返回带多个选择选项的Simple with custom选项产品
   * _修复注释_：更新了库存包中的StockStatusProvider解析程序，以修复具有自定义选项的简单产品的stock_status。
* _LYNX-533_：错误(GQL)： cart.itemsV2.items.product.custom_attributesV2返回服务器错误
   * _修复注释_：通过添加不含任何自定义属性的产品解决了当购物车查询包含产品的自定义属性时发生的服务器错误。
* _LYNX-536_： orders/date_of_first_order始终返回null
   * _修复注释_：解决了orders > date_of_first_order始终返回null的问题。
* _LYNX-544_：客户不能取消部分发运的订单
   * _修复说明_：已添加验证，以限制客户取消部分发运的订单。
* _LYNX-548_：根据错误消息取消订单的错误代码
   * _修复注释_：订单取消的错误代码现在基于特定错误消息。
* _LYNX-581_：将Cookie相关属性从私有移回受保护属性
   * _修复注释_：将Magento\Framework\App\PageCache\Version类构造函数属性的可见性从私有还原为受保护
* _LYNX-600_：将默认GraphQL查询的最大复杂度增加到1000
   * _修复注释_：将默认最大GraphQL查询复杂性从300提高到了1000。
* _LYNX-620_： GQL - itemsV2 >原始行总计，对于具有单独价格的文件选项的可下载产品，价格范围价格返回为$0.00。
   * _修复说明_：解决了启用了单独链接购买选项的可下载产品对itemsV2 >原始行总计返回$0的问题，对于具有单独价格的文件选项的产品，价格范围返回为$0.00。
* _LYNX-772_： PHP-8.4版本的GraphQl兼容性
   * _修复注释_：修复了跨多个解析器的GraphQL与PHP 8.4的兼容性问题，确保顺利地工作。 更新了CatalogRule、Customer、GiftMessage、GiftCard和GiftWrapping模块中受影响的文件。

### GraphQL、库存/MSI

* _ACP2E-2607_：当源购物车和目标购物车具有相同的捆绑项目时，MergeCart变异引发异常
   * _修复注释_： &#39;-
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c971859e>，<https://github.com/magento/inventory/commit/db0620da>

### GraphQL、库存/MSI、性能

* _ACP2E-1716_：升级后站点已关闭
   * _修复注释_：提高了通过GraphQl获取捆绑产品的性能。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ba25af8a>，<https://github.com/magento/inventory/commit/bdbf97ea>

### GraphQL，性能

* _AC-9569_： [GraphQL解析程序]未使导入中的客户解析程序数据失效
   * _修复说明_：现在，通过导入编辑或删除客户时，GraphQL客户解析器缓存会按预期失效。 以前，缓存不会失效，并且可以在导入期间编辑或删除客户数据。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL，搜索

* _ACP2E-2809_： GraphQL产品列表按多个参数排序不起作用
   * _修复注释_： GraphQl中按多个字段排序的产品现在按文档中的说明工作
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-948_：产品列表GraphQL查询仅限于total_count 10,000个产品
   * _修复注释_：修复后，搜索结果不限于10000个产品，即使计数超过10000，也可以获取符合搜索条件的所有产品。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL，测试框架

* _ACP2E-3363_： Magento\GraphQl\App\GraphQlCustomerMutationsTest.php集成测试失败
   * _修复注释_： &#39;-
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4cf5e62>

### 导入/导出

* _AC-12172_：随自定义选项类型一起提供时，在产品导入时出现问题： file （创建的产品不包含自定义选项的价格，并且仅显示提供的第一个文件类型扩展名）
   * _修复注释_：系统现在可以正确导入具有“file”类型的自定义选项的产品数据，从而确保显示所有提供的文件扩展名并包含自定义选项的价格。 以前，在产品导入过程中，如果为“file”类型的自定义选项提供了多个文件扩展名，则只显示第一个扩展名，并且缺少自定义选项的价格。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38805>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_：“导入历史记录”网格中导入操作的执行时间错误
   * _修复注释_：导入报表执行时间正确显示，与管理员区域设置无关。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_：正在使用导入的相同电子邮件地址创建重复客户
   * _修复注释_：在“帐户共享”设置为“全局”时导入客户，更新了系统中存在的导入客户。
以前导入的客户已复制。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_：添加/更新产品导入并复制可自定义选项
   * _修复注释_：通过在产品选项CSV导入期间将正确的商店分配给产品选项，解决了此问题。
以前，分配给管理员存储，而不是其各自的存储。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_：客户的“created_at”日期未在导出时转换为存储时区
   * _修复注释_：根据客户导出CSV分区中的存储时区，列“created_at”日期值将转换为适当的日期格式。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_： [Cloud]使用CSV检查导入数据中的数据时出现错误
   * _修复注释_：在CSV导入期间检查数据时没有错误。 以前，使用管理员提供的CSV检查导入部分中的数据时，显示的错误消息为：“我们找不到在行：1中与此电子邮件和网站代码匹配的客户”。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3172_：“导入”按钮缺失
   * _修复注释_：解决CSV中数据检查后导入按钮缺失的问题。 以前，如果在数据检查后使用了CSV中的正确和不正确的记录，则不会显示导入按钮。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_：无法导入导出的客户地址
   * _修复注释_：客户地址导入将按预期继续。 以前，如果共享客户帐户=全局，客户地址导入文件将不会通过验证，并且有两个网站（默认网站有一个受限制的国家/地区列表）的导入地址适用于另一个允许国家/地区不同的网站
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_： [Cloud] CSV文件中的错误数量未给出错误
   * _修复注释_：现在，库存源导入将引发数量列中的非数字值的验证错误。 以前，在数量列中导入具有非数字值的库存源会导致数量设置为0。
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3455_：当URL密钥已属于某个类别时，导入产品时生成的URL密钥重复错误消息不正确
   * _修复注释_：当客户尝试在产品的URL密钥已属于某个类别的情况下导入产品时，在产品导入检查期间显示正确的错误消息。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3475_：产品导出导致内存限制为4G的OOM
   * _修复注释_：在此修复之前，如果产品属性具有数千个选项值（即使具有4G可用内存），则产品导出失败。 进行此修复后，产品导出应会完成导出csv文件。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3527_： [云]导入进程相互干扰
   * _修复注释_：如果同一管理员用户使用同一用户会话执行两个或多个导入操作，则显示正确的消息。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d4de4726>

### 导入/导出，性能

* _ACP2E-3476_： [Cloud]产品导入时间已显着增加
   * _修复注释_：在修复之前，包含超过10,000个条目的目录产品导入会显着降低时间。 修复后，及时执行目录产品导入。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/87d012e5>

### 安装和管理

* _AC-13242_：Magento升级在MariaDB 11.4 + 2.4.8-beta1上失败
   * _修复注释_：升级应该没有任何错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7b336d0a>
* _ACP2E-2102_：管理面板中没有用于清漆7按钮的导出VCL
   * _修复说明_：“Export VCL for Varnish 7”按钮已添加到“管理”面板中。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4fbf702>

### 库存/MSI

* _AC-10750_：当数据库使用前缀时，可配置产品的清单更新失败
   * _修复注释_：当数据库使用前缀时，系统现在可以正确更新可配置产品的清单，从而防止出现任何错误消息并确保保存正确的数量。 以前，如果数据库使用前缀，则在尝试保存可配置产品中简单产品的库存数量时会出错。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38045>
* _AC-11593_：添加具有属性的映射时，Google google API密钥不起作用
   * _修复注释_：系统现在支持最新的Google Maps API版本3.56，使用户能够成功地将映射内容块从PageBuilder菜单添加到舞台中，而不会遇到任何错误。 以前，由于Google地图API版本存在兼容性问题，用户无法添加地图内容块，从而导致“出现问题”错误消息。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0574ac23>
* _AC-13922_：无法为具有多个来源且SKU已损坏的订单项目创建装运
   * _修复注释_：以前，通过数据库错误地在SKU中添加空格会导致装运页面出错，该错误现已修复，并且自动修剪被视为人性化的错误，未找到任何影响。因此，已成功创建装运。
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/c18eb5fa>
* _ACP2E-1411_：[测试]捆绑销售前部显示库存为0的产品
   * _修复注释_：捆绑产品未使用其他库存显示在其他网站上。
* _ACP2E-2794_：[Cloud]产品列表的关键问题为空白
   * _修复注释_：现在，当产品设置为“缺货”时，系统可正确显示产品清单，且不含空格，从而确保一致、准确地显示可用产品。 以前，将产品设置为“缺货”会导致产品列表中显示空白，中断布局并可能使客户感到困惑。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ea79f7dd>，<https://github.com/magento/inventory/commit/b59e48ca>
* _ACP2E-3335_：启用MSI收取存储时无法发送订单
   * _修复注释_：如果存在许多店内提货来源，则提高了创建装运的库存性能
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_： Cron重新索引无法更新前端产品可用性
   * _修复注释_：以前，通过REST API更新延交订单状态后，产品在前端保持缺货。 现在，通过REST API更新延交状态后，产品将显示为有货。
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_：启用MSI时，将图像添加到可配置项无法正常工作。
   * _修复注释_：使用库存模块时，可配置产品的映像上传现在将按预期工作。 以前，图像上传不起作用
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/fdf409aa>
* _ACP2E-3470_：清洁M2.4.7-p3中的捆绑产品+ MSI出现问题
   * _修复说明_：以前，对于与同一简单产品重复之后的库存捆绑产品，无法保存该简单产品。 应用此修复后，简单产品可顺利保存，不会出现任何异常。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39358>
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/0208e433>

### 库存/MSI、搜索

* _ACP2E-3413_：未将SKU设置为可搜索属性时，所有产品都将使用[is_out_of_stock] = 1编制索引
   * _修复注释_：修复后，目录搜索索引中的“is_out_of_stock”是正确的，即使sku不可搜索也是如此。
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/5b21b7af>

### 订购

* _AC-10828_：后端订单概览屏幕：在订单物料级别上看不到延期交货数量
   * _修复注释_：系统现在会在后端订单概述屏幕的数量列中显示延期交货项目数。 这可确保用户能够准确地跟踪按顺序排列的所有项目的状态。 以前，“数量”列只显示已订购、开票和发运的项目数，而不显示延交项目数。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38252>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38320>
* _AC-10994_： [问题]订单地址呈现器中使用了错误的存储ID
   * _修复注释_：现在，在渲染订单地址时，系统可正确使用与订单关联的存储ID，从而确保根据相应的存储ID正确格式化地址。 以前，系统未正确使用当前商店ID，在需要发送来自不同商店的多个订单电子邮件时，这可能会导致地址格式不正确。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38412>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37932>
* _AC-11690_： JoinProcessor缓存问题
   * _修复注释_：系统现在可以正确应用每个迭代的JoinProcessor，即使连续调用也是如此，从而确保准确的数据检索。 以前，JoinProcessor被错误地标记为已在连续迭代中应用，导致数据检索出错。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/27504>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37550>
* _AC-11798_：[问题]装运价格在打印的PDF中显示不同
   * _修复备注_：系统现在可根据税务配置设置以打印的PDF正确显示发运价格，确保销售订单发票视图页与打印发票之间的一致性。 以前，无论税配置设置如何，打印的PDF中显示的运费不含税。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38608>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38595>，<https://github.com/magento/magento2/commit/1bafc571>
* _AC-13839_：使用已删除的父可配置产品重新排序
   * _修复注释_：现在，在使用已删除的产品重新排序时，系统不会显示要重新排序的重新排序按钮
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39568>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39601>
* _AC-13924_： [问题]修复错误的\Magento\Sales\Model\Order\Email\Container\Template：：$id属性
   * _修复注释_：这将修复\Magento\Sales\Model\Order\Email\Container\Template：：$id的错误phpdoc，实际上$id是类型int，但实际上是string。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39151>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39150>
* _ACP2E-2622_：无法保存现有订单详细信息中对电话号码的更改
   * _修复注释_：现在，用户可以在订单地址的电话字段中添加国际前缀00
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38201>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_：电子邮件发送失败
   * _修复注释_：系统现在包含一个配置选项async_sending_attempts ，用于指定在停止前尝试发送电子邮件的次数，从而改进了在启用“异步发送”时处理失败的电子邮件发送的方式。 以前，如果电子邮件发送失败，系统将不断尝试重新发送，导致系统日志中出现无休止的错误消息循环。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_： [Cloud]部分退回部分发运的订单时，订单状态更改为完成
   * _修复备注_：在发出贷项通知单时，如果存在尚未发运的项目，则订单状态不再更改为“已完成”。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_： [CLOUD]无法禁用从管理员UI发送电子邮件，如开发文档所示
   * _修复注释_：系统现在可以正确阻止在禁用电子邮件通信时发送销售电子邮件。 重新启用电子邮件通信后，将不再发送这些电子邮件。 以前，在电子邮件通信被禁用时发起的销售电子邮件，在电子邮件通信重新启用后仍会发送。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3045_：未全额退款的已结订单
   * _修复注释_：当具有未捕获付款的订单已创建装运时，系统现在将订单状态正确维护为“正在处理”，将发票状态正确维护为“待定”。 这可确保在全额退款后只将订单标记为“已结”。 以前，为具有待定发票的订单创建发运会错误地将订单状态更改为“已关闭”。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3311_： [Cloud]如果仅未设置默认帐单地址，则无法在一个商店的admin中创建订单
   * _修复注释_：现在相关的错误消息“关联网站中已存在具有相同电子邮件地址的客户”。 如果客户没有默认帐单地址，但尝试在其他商店中创建订单，则会显示。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_：已发送管理员重复下单请求
   * _修复注释_：以前，管理员面板中的“提交订单”按钮可能会被多次单击或通过反复按“Enter”键而激活，从而导致重复提交订单或提交订单出错。 现在，会阻止执行其他操作，直到完全处理完订单，从而确保仅提交一个订单。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_：即使没有付款方式，管理员仍然可以下订单
   * _修复注释_：当付款方法重新出现在可用付款列表中时，现在将保留以前选择的付款方法。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d50f6b5d>

### 订单，支付

* _ACP2E-3233_：即使没有付款方式，管理员仍然可以下订单
   * _修复注释_：以前，商家可以从管理员面板下订单，而无需选择付款方式。 现在，商家需要一种支付方式才能继续下订单。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/fd5cf3af>

### 订单，退货

* _ACP2E-2982_：订单退款导致贷项通知单重复
   * _修复注释_：同时执行两个相同的请求时通过REST API发出退款将不再创建重复的贷项通知单。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4fbf702>

### 订单，税金

* _ACP2E-3003_： [CLOUD] RESTFUL订单API中的base_row_total在启用跨国交易和应用优惠券折扣时不正确
   * _修复注释_：现在，在启用跨境交易并应用优惠券折扣的情况下，从RESTFUL订单API返回正确的base_row_total。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/9af794a4>

### 其他

* _LYNX-339_： GQL查询中返回的private_content_version Cookie
   * _修复注释_：修复了在GraphQL查询中返回private_content_version Cookie（即使会话Cookie已禁用）的问题。 当会话按预期禁用时，GraphQL响应中将不再包含该Cookie。
* _LYNX-380_： CartItemInterface中的is_available属性对可配置产品始终返回false
   * _修复注释_：修复了CartItemInterface中的is_available属性始终为库存可配置产品返回false的问题。 现在，在适用的情况下，它正确地将可用性反映为true。
* _LYNX-382_： CartItemInterface中的is_available属性返回true，即使可销售库存低于产品的数量也是如此
   * _修复注释_：修复了CartItemInterface中的is_available属性不正确地返回true的问题，即使购物车项目数量超过可销售库存也是如此。
* _LYNX-399_：将简单产品添加到分组产品中的购物车时，会返回占位符缩略图
   * _修复注释_：修复了在将简单产品（分组产品的一部分）添加到购物车时返回占位符缩略图图像的问题，即使该产品已分配图像。
修复详细信息：
·产品缩略图现在可以正确显示分配的图像（如果可用）。
·缩略图选择遵循以下项下的管理员配置：
商店>配置>销售>结账>购物车>分组的产品图像。
这可确保根据商店设置对分组产品执行一致的缩略图行为。
* _LYNX-400_：客户的自定义选项属性不适用于整数值
   * _修复注释_：修复了在返回值为整数时，客户的自定义选项属性不起作用的问题。 现在，自定义选项可正确处理并按预期返回整数值。
* _LYNX-402_：尝试获取具有动态价格的捆绑包产品的价格详细信息时出现内部服务器错误
   * _修复注释_：解决了通过GraphQL查询具有动态定价的捆绑产品的price_details时导致内部服务器错误的问题。 此增强功能可在使用配置有动态定价的捆绑产品时确保稳定的购物车查询。
* _LYNX-403_： only_x_left_in_stock对于可配置产品始终返回0
   * _修复注释_：解决了使用带有选项的父SKU添加可配置产品时，only_x_left_in_stock属性始终返回0的问题。
修复详细信息：
· only_x_left_in_stock值现在可准确反映所选子变体而非父SKU的库存。
·这确保在购物车和产品页面中正确显示可配置产品变体的库存水平。
* _LYNX-411_： GraphQL查询未返回可自定义产品的正确计算常规价格
   * _修复注释_：修复了GraphQL未针对可自定义产品返回正确计算出的正常价格的问题。 现在，查询会在prices属性中正确包含计算出的正常价格以及应用的自定义值（例如$125），这既反映了基本价格，也反映了任何其他自定义成本。
* _LYNX-412_：通过EstimatedTotals应用的ApplicedTaxes随更新的突变而保留
   * _修复注释_：修复了EstimatedTotals突变的问题，该问题导致即使更新区域或邮政编码后，购物车中仍保留已应用的税费。 现在，当在区域和邮政编码值之间更改时，此突变可正确更新应用的税种，从而确保仅根据当前购物车数据应用正确的税则。
* _LYNX-420_： CartItemInterface中的is_available属性返回true，即使可销售库存低于产品的数量也是如此
   * _修复注释_：修复了CartItemInterface中的is_available属性不正确地返回true的问题，即使可销售库存低于请求的产品数量也是如此。 现在，当产品的数量超过可用库存时，is_available字段会正确返回false 。
* _LYNX-425_：产品正常价格为12位小数且值错误
   * _修复注释_：修复了在应用多个税率时product.price_range.maximum_price和minimum_price GraphQL路径中的regular_price值与目录价格不匹配的问题。 regular_price现在可以始终如一地反映所有税务配置的目录价格，从而确保购物车汇总中准确的单价、总行成本计算和折扣检查。
* _LYNX-430_：捆绑产品缺货的购物车出现GraphQL服务器错误
   * _修复注释_：修复了在获取购物车时GraphQL返回内部服务器错误的问题，该购物车包含带有缺货项目的捆绑产品，尤其是当查询包含itemsV2属性时。 GraphQL现在可以按预期正确返回项目列表，并在捆绑的产品项目条目中附加相关错误消息。
* _LYNX-441_：无法创建具有自定义属性的地址
   * _修复说明_：修复了createCustomerAddress变异导致无法创建具有所需自定义属性的地址的问题。 现在，当提供适当的负载时，突变可以正确处理自定义地址属性。
* _LYNX-447_：捆绑产品上仅具有_x_left_in_stock的购物车上的GraphQL服务器错误
   * _修复注释_：修复了获取购物车时导致内部服务器错误的问题，该购物车包含在GraphQL查询中带有only_x_left_in_stock字段的捆绑产品。 GraphQL现在可正确返回only_x_left_in_stock字段的浮点值或空值，且不会出现错误。
* _LYNX-464_：删除购物车中可配置产品不足的其他产品时，GraphQL出错
   * _修复说明_：修复了如果购物车还包含库存不足的可配置产品，则尝试从购物车中移除库存产品会导致“请求的数量不可用”GraphQL错误的问题。 删除操作现在可按预期方式工作，而不会触发错误。
* _LYNX-469_：由于突变中的SKU区分大小写，无法添加产品
   * _修复说明_：解决了使用不同大小写的SKU时，addProductsToCart突变返回“PRODUCT_NOT_FOUND”错误的问题。 此突变现在可以不区分大小写地处理SKU，从而确保与目录服务查询和PDP行为一致。
* _LYNX-603_：产品属性>商标简短形式™以™形式返回
   * _修复注释_：解决了GraphQL API的产品名称存在的字符编码问题
* _LYNX-619_： updateCustomerEmail突变问题
   * _修复注释_：解决了updateCustomerEmail突变的问题，该问题导致没有所需自定义属性（在创建帐户后添加）的客户无法更新其电子邮件。
* _LYNX-626_：使用pickup_location_code时突变setShippingAddressesOnCart引发错误
   * _修复注释_：修复了在使用pickup_location_code但未指定customer_address_id或address时，setShippingAddressesOnCart突变返回错误的问题。 现在，此突变可正确设置仅包含pickup_location_code的配送地址。
* _LYNX-637_： Storefront兼容性 — 更新逻辑以获取带前缀的表名和其他细微改进
   * _修复注释_：更新了逻辑以检索带有前缀的表名（与SCP更改相关）。
* _LYNX-643_：使用setBillingAddressOnCart GQL的same_as_shipping字段时，无法保存在通讯簿中
   * _修复注释_：修复了在将setBillingAddressOnCart GraphQL突变的same_as_shipping字段设置为true时，未将送货地址保存到客户通讯簿中的问题。 现在，送货地址已按预期正确存储。
* _LYNX-650_：标准化突变中的order_id
   * _修复注释_：标准化了突变中的order_id输入，并更新了订单取消确认电子邮件模板，以显示增量id而不是订单id。
* _LYNX-651_：客户订单未显示订单注释
   * _修复注释_：解决了CustomerOrder的问题，从而在来宾查询和客户订单GraphQL查询中包含订单注释。
* _LYNX-652_： original_item_price不得包含任何折扣
   * _修复注释_：更新了GraphQL购物车项目价格中original_item_price的逻辑以排除折扣。
* _LYNX-681_：当捆绑产品的某个缺货时，捆绑产品仍显示“IN_STOCK”
   * _修复注释_：解决了即使其中一个捆绑产品缺货，捆绑产品的product.stock_status仍显示“IN_STOCK”的问题。
* _LYNX-686_：如果客户存在已删除自定义属性的值，则客户查询返回内部服务器错误
   * _修复注释_：修复了在已删除的自定义属性仍具有存储值时，客户查询返回内部服务器错误的问题。 现在，如果请求不存在的属性，则会返回正确的错误消息。 删除客户自定义属性时，必要的缓存将失效。
* _LYNX-687_：返回和取消确认链接的操作参数
   * _修复注释_：为返回和取消确认电子邮件相关链接添加了操作参数
* _LYNX-689_：访客用户确认URL被重定向到订单状态页面，因为它缺少orderRef
   * _修复注释_：已将orderRef参数添加到来宾订单取消确认电子邮件中的链接
* _LYNX-699_：无法为placeOrder GQL上不可为空的字段“TaxItem.title”返回null
   * _修复注释_：修复了由于不可为空的字段TaxItem.title的值为null，导致placeOrder突变失败并出现内部服务器错误的问题。 现在，字段始终会返回有效值，以确保成功下订单。
* _LYNX-702_： EstimateTotals：虚拟产品类型的折扣为Null
   * _修复注释_：解决了将折扣代码应用于包含虚拟产品的购物车时，estimateTotal突变为折扣返回null的问题。
* _LYNX-703_：捆绑产品未返回正确的折扣百分比和金额
   * _修复注释_：为目录项目价格引入了“catalog_discount”和“row_catalog_discount”新属性，以便在行和单个项目级别显示正确的折扣金额和百分比。
* _LYNX-714_：产品级别的礼品消息配置
   * _修复注释_：修复了全局禁用时未在产品级别应用礼品消息的问题。 现在，如果为特定产品启用了礼品消息，则可使用updateCartItems突变成功添加这些消息，并且可以正确保存并反映这些消息。
* _LYNX-757_：如果没有应用活动的购物车规则，cart.rules查询返回错误而不是空数组
   * _修复注释_：修复了cart.rules查询以返回空数组，而不是在没有应用活动购物车规则时返回错误。
* _LYNX-778_：安装adobe-commerce/storefront-compatibility软件包时，使用OPTIONS方法的GraphQL调用返回500响应代码
   * _修复注释_：修复了在安装adobe-commerce/storefront-compatibility包时，使用OPTIONS方法的GraphQL调用返回500内部服务器错误的问题。 现在，端点可按预期正确返回200/204响应。

### 其他开发人员工具

* _AC-10658_： [问题]修复visual.phtml中的HTML语法错误
   * _修复注释_：系统现在可正确关闭visual.phtml文件中的启动标记，从而确保HTML语法正确。 以前，未正确关闭启动标记，从而导致HTML语法错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38247>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37457>
* _AC-11474_： [问题]在bin/magento maintenance：status命令中将“活动”更改为“已启用”
   * _修复注释_：系统现在为维护模式命令提供更准确的状态消息，状态从“活动”更改为“已启用”，从“非活动”更改为“已禁用”。 以前，维护模式命令的状态消息显示为“活动”或“非活动”，这可能会导致混淆。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38486>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38410>
* _AC-12571_：在类别树中导航会导致Redis中出现错误：“Redis会话超出并发连接数”
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38851>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0611e750>
* _AC-12731_：与dev/css/use_css_critical_path合并的CSP问题
   * _修复注释_：现在，即使启用了“dev/css/use_css_critical_path”设置，系统也会在签出页面上以异步方式正确加载CSS文件，从而确保这些页面呈现正确的CSS样式。 以前，限制的内容安全策略(CSP)阻止执行内联JavaScript，这会导致无法按预期加载CSS文件。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39020>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39040>
* _AC-13398_：使用虚拟类型配置插件，无法在安装程序:di:compile命令中正确生成侦听器方法
   * _修复注释_：系统现在在使用虚拟类型配置插件时正确生成侦听器方法，从而确保无论是预编译的结果还是运行时编译的结果都一致。 以前，与运行时编译相比，在预编译时，系统会产生不正确的结果。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/33980>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38141>
* _ACP2E-3631_： Adobe Commerce 2.4.7-p3单元测试失败
   * _修复说明_：不需要发行说明。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/982b1c42>

### 付款/付款方式、订单

* _AC-13699_：保存的付款方式页面上未显示保存供以后使用的付款方式信用卡详细信息
   * _修复便笺_：以前保存的付款流程信用卡详细信息供以后使用，未显示在存储的付款方式页面上，而现在修复的信用卡详细信息显示在存储的付款方式页面上。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/96dec499>

### 支付

* _AC-13414_：信用卡（Payflow链接）付款不起作用
   * _修复备注_：在成功完成修复订单后，使用信用卡下订单时出现早期获取错误（付款被拒绝）。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a68324bc>
* _ACP2E-2841_：每次单击“查看事务”屏幕上的“提取”按钮时，Payflow都会创建新事务
   * _修复注释_：现在，每次单击“查看交易”屏幕上的提取按钮时，系统都会正确提取交易信息，而不会创建新的付款交易。 以前，单击“提取”按钮会错误地为已支付的订单创建新的支付交易记录。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_：加拿大Paypal商家帐户的PDP中未显示Paylater消息
   * _修复说明_：当可以根据帐户帐单地址或装运确定买方所在国家/地区时，系统现在会在产品详细信息页面(PDP)上正确显示加拿大PayPal商家帐户的PayLater消息。 以前，由于缺少参数，不会显示PayLater消息，这会导致浏览器控制台中出现错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3143_： PayPal订单退款导致重复的贷项通知单
   * _修复注释_：修复了PayPal付款服务的IPN创建的贷项通知单的并发问题。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3163_：购物车价格规则不适用于Paypal
   * _固定注释_：通过付款方式应用折扣时，PayPal端会显示正确的金额
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3208_： [Cloud]具有特定角色的用户无法登录
   * _修复注释_：角色仅包含PayPal分区访问权限的管理员用户现在可以登录而不会出现错误
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/66dea0de>

### 性能

* _AC-11932_：默认产品属性设置问题
   * _修复注释_：系统现在允许用户取消选择产品属性的默认选项，确保该属性并不总是有默认设置。 以前，一旦为产品属性设置了默认值，就无法取消选择它，从而导致该属性始终具有默认设置。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38703>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-12000_： [问题]代码清理并添加新的关键标题块并将关键css移动到资产之前
   * _修复注释_：系统现在包括一个新的关键头块，并将关键CSS移至资产之前，允许在前端进行更多自定义和性能优化。 以前，关键CSS没有放在资源之前，这限制了自定义和优化机会。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38748>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/35580>
* _AC-12176_：当mysql主机包含端口信息时，主题编译中断
   * _修复注释_：系统现在可正确处理包含端口信息的MySQL主机配置，从而确保成功进行主题编译。 以前，如果数据库连接中的MySQL主机配置包含端口信息，则主题编译将失败。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38799>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38842>
* _AC-13471_：支持Magento CLI中的Symfony CommandLoaderInterface
   * _修复注释_：此项更改允许延迟初始化命令，直到需要这些命令为止，从而缩短了Magento CLI应用程序的初始化时间。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/29266>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/29355>
* _ACP2E-2494_：在购物车规则中加载产品属性时出现性能问题
   * _修复注释_：改进了销售规则的查询性能 — 从大约150毫秒提高到一位数ms。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_：价格部分索引性能
   * _修复注释_：通过优化索引过程中使用的某些删除查询，价格部分索引性能已得到改进。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_：使用异步订单处理+条款和条件时，在多商店设置中订单被拒绝
   * _修复注释_：现在会处理来自启用了条款和条件的非默认网站的订单。
在它们被自动拒绝之前。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_： Order Rest API调用需要很长时间才能执行
   * _修复注释_：系统现在会在合理的时间范围内执行Order Rest API调用，从而提高了获取大量订单时的性能。 以前，执行Order Rest API调用需要很长时间，导致在检索大量订单时出现延迟。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/001e5188>

### 定价

* _AC-11810_： Magento2.4.6-p4订单API简单项目缺少价格
   * _修复注释_：现在，系统在通过订单API进行查询时，可以正确显示简单产品的价格，从而确保准确的数据呈现。 以前，简单产品的价格在API响应中错误地显示为零。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38603>
* _AC-13855_：目录规则中存在尾数舍入错误
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/276e0acd>

### 产品

* _AC-10535_：正在将可配置关联产品名称中的特殊字符转换为HTML实体。
   * _修复注释_：现在，在编辑可配置产品时，系统会在关联产品的名称中正确保留特殊字符，从而阻止将这些字符转换为HTML实体。 以前，在编辑可配置产品时，关联产品名称中的特殊字符会转换为HTML实体。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38146>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38447>
* _AC-10947_： ProductRepository函数GetById未创建正确的缓存密钥
   * _修复注释_：系统现在可以在ProductRepository的函数GetById中正确创建缓存密钥，无论存储ID是以字符串还是整数形式传递。 这样可以确保在后续调用时从内存中检索产品，从而提高性能。 以前，每次调用函数时，系统都会从数据库中检索产品，即使参数相同，这是由于创建缓存键不正确造成的。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38384>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38433>
* _AC-11992_： [问题] [MFTF]已添加AdminClickAddOptionForBundleItemsActionGroup
   * _修复注释_：系统现在包含AdminClickAddOptionForBundleItemsActionGroup，增强了管理面板的功能。 以前，此操作组不可用。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/30857>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/30838>
* _AC-13173_： [问题]修复PHPDoc块中的拼写错误
   * _修复注释_：系统现在可正确删除PHPDoc中对$helper变量声明的未知引用变量，从而增强代码清晰度和准确性。 以前，PHPDoc中的此未知引用变量在代码中引起混淆和潜在错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38961>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38940>
* _AC-13423_： [问题]修复了Magento中损坏的捆绑包和可下载产品页面布局>= 2.4.7
   * _修复注释_：捆绑包和可下载产品页面的布局已修复，确保在所有设备上显示一致且正确。 以前，这些页面由于重新排列产品信息媒体块而遇到布局问题。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39403>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-5969_： AlertProcessor — 参数#2($storeId)必须是int类型，并且给定字符串
   * _修复注释_：系统现在通过确保存储标识符的数据类型正确来正确触发产品警报电子邮件。 以前，由于商店标识符中的类型不匹配，因此未发送产品警告电子邮件。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/35602>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_： [Cloud] addFilterToMap函数无法用于某些列
   * _修复注释_：现在，可以在订单网格中使用自定义模块。 以前，使用自定义模块时出现错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3a7c4d17>

### 促销活动

* _ACP2E-2602_：从邀请创建帐户时客户属性不可见
   * _修复注释_：从邀请创建帐户时，客户属性可用。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2627_：由于订单取消失败，无法发放具有每个优惠券使用次数限制的优惠券代码，因此无法付款
   * _修复注释_：现在，系统会在创建或取消订单时立即更新优惠券使用情况，并将规则使用情况添加到队列，以防止潜在的死锁。 这可确保发放限制为“按优惠券使用”的优惠券代码，如果订单因付款失败而被取消，则可以重复使用。 以前，系统不会释放该优惠券代码以便在此类情况下重复使用，从而导致一条错误消息，指出该优惠券代码无效。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2811_： [Cloud]重新索引目录规则产品索引器引发SQLSTATE[HY000]：常规错误： 2006 MySQL服务器已消失。
   * _修复注释_：系统现在可以正确处理“Magento\CatalogRule\Model\Indexer\IndexBuilder”的di.xml中的自定义“batchCount”值，从而防止在重新索引目录规则产品索引器期间由于大型目录的批处理大小不正确而出现SQL错误，如“常规错误： 2006 MySQL服务器已消失”
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3139_：具有折扣数量步骤（购买X）属性的销售规则导致不应用其他规则
   * _修复注释_：如果购物车中的产品数量不足以应用规则，则购物车价格规则不会取消以前应用的规则。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3332_：发布具有固定金额折扣和“最大数量折扣应用于”的销售规则
   * _修复注释_：修复了购物车规则折扣的问题，当购物车配置为对有限数量的产品应用固定金额折扣时。 以前，“应用的最大数量折扣”值用于计算购物车中当前项目的价格，而不仅仅用于计算规则的折扣。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3349_：购物车规则“整个购物车的固定金额折扣”  操作错误地应用折扣
   * _修复说明_：在从管理区域创建订单时使用优惠券代码时，无论使用大写还是小写，都会正确验证优惠券代码。 以前，如果优惠券代码与配置的购物车规则代码的字母大小写不符，则不会验证优惠券代码。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3374_：在后端，使用产品属性的默认存储值（而不是预期的管理员值）
   * _修复注释_：现在，在后端中，使用管理员值，而不是产品属性的默认商店值。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3377_：添加捆绑包产品时，购物车规则“整个购物车的固定金额折扣”操作应用折扣不正确
   * _修复注释_：未正确为捆绑包产品应用固定数量的购物车规则。 现在，在计算总折扣金额时，会考虑捆绑子产品，从而生成正确的折扣计算。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3403_：购物车价格规则错误计算折扣
   * _修复注释_：正在正确计算固定金额折扣。 在修复之前，无法正确计算捆绑产品的固定金额折扣。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0b488dd1>
* _ACP2E-3406_：规则条件中的嵌套类别未显示
   * _修复注释_：修复了当级别3类别下的嵌套类别未显示在类别条件的营销规则中时的问题
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3432_： usage_limit和uses_per_customer未在salesrule_coupon表中更新
   * _修复注释_：更新购物车价格规则中每张优惠券的使用次数和每客户的使用次数将影响现有的自动生成优惠券。 以前，新值只影响新优惠券
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3456_：当购物车使用“等于或大于”条件时，购物车价格规则不考虑父类别。
   * _修复注释_：现在，当在高级条件下使用父类别时，购物车价格规则可正确考虑父类别
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/93359343>
* _ACP2E-3463_：优先级折扣计算无效
   * _固定备注_：在适用于整个购物车折扣类型的固定金额的情况下，未正确计算先前促销已折扣的购物车项目的金额。 现在，折扣总和恰当。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3472_： [CLOUD]配送计算未考虑购物车规则
   * _修复注释_：在修复之前，无法一致地应用具有区域条件的购物车规则。 修复后，正确应用包含区域条件的购物车规则。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3491_：发票的购物车规则SKU条件失败。
   * _修复注释_：具有动态价格的捆绑产品折扣现已正确反映在发票中。 以前，折扣不会反映在发票上。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3498_：与折扣/特价产品同时应用多个购物车价格规则时，折扣值不正确
   * _修复注释_：在修复之前，如果应用了多个购物车规则，则无法正确应用整个购物车规则的固定金额。 现在，正在正确应用固定金额折扣购物车规则。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1984c61c>

### SEO

* _AC-11907_：添加带有重音符号的URL重写会导致无限加载
   * _修复注释_：系统现在成功创建并处理带有重音的URL重写，从而防止在保存过程中无限加载。 以前，添加带有重音符号的URL重写会导致无限加载问题。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38692>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/44cef3a9>
* _ACP2E-2641_：第三级类别的多存储错误类别URL重写
   * _修复注释_：使用自定义作用域URL键为父项的子项生成正确的URL重写
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_：“产品名称”字段中的双字节字符（特殊字符）会阻止在后端创建产品
   * _修复注释_：添加了新设置，允许您对产品URL应用音译或不应用音译。 可在以下位置进行设置：存储>配置>目录>目录>搜索引擎优化：“为产品URL应用音译”
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3383_：在一个商店组中创建了多个商店的url_rewrite条目不正确
   * _修复注释_：在修复之前，您只能在编辑产品时生成网站级别的URL重写。 修复后，引入了一个新设置（存储>配置>目录>目录>搜索引擎优化，包含选项“存储视图”、“网站”的“产品URL重写范围”），允许您在存储视图或网站级别生成URL重写。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/2d627301>

### Search

* _AC-13053_：正在获取“输入搜索词并重试”。 2.4.8-beta1中storefront的“高级搜索”页面出错
   * _修复注释_：当产品属性设置为“否”时，系统现在会在“高级搜索”页面上正确显示搜索结果。 以前，将产品属性设置为“否”并执行搜索会导致出现错误消息“输入搜索词并重试”。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13721_： magento/module-open-search依赖于不存在的opensearch-php分支
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/05dc0bbf>
* _ACP2E-3362_： search_query表大时，对加载时间前端影响较大
   * _修复注释_：改进了搜索列表页面加载时间。 在修复之前，搜索列表页面因未优化查询而延迟。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/55615e61>

### 安全性

* _AC-11855_： [问题]缺少字体CSP Paylater弹出窗口
   * _修复说明_：系统现在允许在不违反内容安全策略指令的情况下加载字体“https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39;”，从而确保正确显示Paylater弹出窗口。 以前，该字体因违反“内容安全策略”指令而被拒绝加载，从而导致Paylater弹出窗口出现显示问题。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38624>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37401>
* _AC-12035_： [问题]更新js.js DOM文本将重新解释为HTML
   * _修复注释_：通过使用innerText，可以避免注入HTML的风险，因为这些属性会自动转义提供的文本中的任何HTML特殊字符。 此修复将输入视为纯文本而不是解释的HTML，有助于防止跨站点脚本(XSS)漏洞。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38767>
* _ACP2E-3273_： ReCaptcha V2在德语签出时显示不正确
   * _修复注释_：以前，对于长单词语言（如德语），签出时电子邮件地址下方的recaptcha显示为无样式。 之后，recaptcha看起来与其他区域中的所有recaptcha元素相同。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_：管理员登录时的验证码不需要与某些用户进行交互
   * _修复注释_：管理员登录的ReCaptcha已按预期进行验证
   * _GitHub代码贡献_： <https://github.com/magento/security-package/commit/8f64ab3c>

### 装运

* _AC-10757_： [问题]修复了tracking.phtml中的拼写错误 — 已将JS函数“currier”重命名为“carrier”
   * _修复注释_：现在，系统在订单跟踪模板中使用的JavaScript处理程序函数中正确使用了术语“carrier”，而不是拼写错误的“currier”，从而确保函数命名正确且代码清晰明了。 以前，使用拼写错误的术语“currier”，这可能导致代码库中的混淆和不一致。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/34523>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/33414>
* _AC-11938_： UPS REST “装运不能以KGS/IN、LBS/CM或OZS/CM作为其度量单位”
   * _修复注释_：确保在结帐和购物车中显示UPS费率。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38618>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/493e01f5>
* _AC-13172_： [问题]客户地址的变量拼写正确
   * _修复注释_：系统现在可以正确拼写客户地址的变量，从而确保在前端帐户区域中准确显示。 以前，这些变量的拼写错误可能会导致本地代码审查期间出错。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/32817>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/32815>
* _ACP2E-2738_：跟踪窗口显示错误的预期投放日期
   * _修复注释_：显示Fedex承运人的正确交货日期。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_：即使应用免运费，仍显示表费率
   * _修复注释_：即使优惠券应用后免费送货变为可用，现在仍显示表费率送货方法
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_：由于未在Jenkins环境中添加凭据，MFTF测试AdminCreatingShippingLabelTest失败
   * _修复注释_： mftf测试修复
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-3340_： FedEx轨道API无法处理REST凭据
   * _修复注释_：以前的FedEx集成不需要额外的API密钥即可跟踪API。 现在，添加了新配置以支持跟踪API密钥。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_：[Cloud] FedEx协商利率未返回REST
   * _修复注释_：在修复之前，联邦快递帐户特定的费率未在响应时发送，即使根据FedEx文档它们本应发送也如此。 修复后，通过更改我们方的请求，在响应中发送特定于帐户的费率。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/55615e61>

### 暂存和预览

* _ACP2E-3453_：使用唯一的自定义类别属性时无法更新计划的更新
   * _修复注释_：修复了如果类别具有唯一属性，则无法更新该类别的计划更新的问题
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/078c387e>

### 目标选择

* _AC-9432_： [问题]允许在维护允许列表中使用CIDR范围
   * _修复注释_：系统现在支持在维护模式允许IP列表中使用CIDR范围，使一系列IP地址绕过维护模式。 以前，维护模式允许IP列表仅允许单个IP地址绕过维护模式。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37943>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/30699>

### 税

* _AC-13295_： [问题] Feature/php8.1构造函数属性升级wee图形ql
   * _修复注释_：在图ql的模块中，使用构造函数属性升级替换所有属性：
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39309>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36975>
* _ACP2E-3193_：固定产品税(FPT)不适用于可配置产品
   * _修复注释_： FPT以使可配置产品变体正常工作。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ec7e32a9>

### 测试框架

* _AC-11654_：由于JSON列类型，集成测试未通过testDbSchemaUpToDate
   * _修复注释_：在集成测试期间，系统现在可以正确识别数据库架构中的JSON列类型，从而防止由于数据库架构与声明性架构不匹配而导致的测试失败。 以前，系统错误地将JSON列类型识别为MariaDB中的LONGTEXT，从而导致集成测试失败。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ef81f5a2>
* _AC-13362_： [问题] PHPDoc更正拼写
   * _修复注释_：由于PHPDoc中的拼写更正问题，系统现在可以正确识别IDE中已弃用的方法。 以前，PHPDoc中的拼写错误会导致IDE无法识别已弃用的某些方法。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/31399>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/31398>
* _AC-13478_： MAGETWO-95118：检查会话过期后永久购物车的行为
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13848_：修复静态测试以启用3d方扩展的使用
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/9e383b4d>
* _ACP2E-3334_：在执行期间或日志中未显示[内部]夹具应用失败
   * _修复注释_： &#39;-
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3458_： [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _修复注释_：修复了mftfs
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/078c387e>

### UI框架

* _AC-12128_： Prototype.js安全漏洞修复CVE-2020-27511
   * _修复说明_：系统已更新，可解决Prototype.js 1.7.3中的安全漏洞CVE-2020-27511，从而增强系统的整体安全性。 在此更新之前，通过去除精心编制的HTML标记，系统容易遭受正则表达式拒绝服务(ReDOS)攻击。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_： Grunt Less使用pub/前缀作为sourcemaps
   * _修复注释_：在使用grunt时，系统现在为路径生成不带/pub前缀的较少/css源地图，从而无需在Web服务器配置中进行变通处理。 以前，在sourcemaps路径中使用/pub前缀需要Web服务器中的特定配置才能正常工作。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38837>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38840>
* _AC-12432_： Ui组件文件字段
   * _修复注释_：系统现在可以正确验证UI组件表单中的文件字段，以便在选择文件时提交表单而不会出错。 以前，即使选择了文件，验证也会失败，导致表单无法提交。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38908>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39004>
* _AC-12645_： [问题] js控制台中的日期格式已得到改进：从12小时切换到24小时……
   * _修复注释_：改进了js控制台中的日期格式：从12小时切换为24小时
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38983>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38972>
* _AC-12650_： [问题]在开发人员模式下为更少的文件添加sourceMap生成
   * _修复注释_：现在，系统在开发人员模式下为较少的文件生成源映射，从而更容易识别样式的源。 以前，在服务器端编译较少的开发人员模式下运行系统时，很难确定样式的来源。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38982>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38977>
* _AC-1306_：正在为禁用的模块部署静态内容
   * _修复注释_：系统现在会从最终CSS输出文件中排除与已禁用模块相关的CSS，从而确保不加载不必要的样式。 以前，与禁用的模块相关的CSS包含在最终的CSS输出文件中，这会导致加载多余的不必要样式。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/24666>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/32922>
* _AC-13459_：使用最小库存阈值进行“缺货”排序时的行为不一致
   * _修复注释_：系统现在可以根据库存水平正确地对目录中的产品进行排序，遵循设置的最低库存阈值，并将缺货商品一致地移到列表的底部。 以前，排序行为不一致，根据库存水平，项目并非始终以正确的顺序显示，并且在保存、刷新或修改类别层次结构后，排序可能会发生意外更改。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_：建议改进require.js加载问题的错误报告
   * _修复注释_：此PR可改进必需项加载组件失败时的错误消息。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/36761>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38971>
* _AC-14004_： PHP 8.4弃用错误导致2.4-develop中的生成失败
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-9007_： [问题]不在前端加载后端块上下文
   * _修复注释_：系统现在确保前端上未加载后端块上下文，从而防止创建不必要的后端会话和潜在的会话锁定。 以前，系统在前端错误地加载后端块上下文，导致创建后端会话和潜在的会话锁定。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37617>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36368>
* _AC-9168_： [问题]删除不必要的脚本审阅摘要
   * _修复注释_：系统现在通过从评级部分中删除不必要的JavaScript脚本来优化页面加载时间，而不是使用内联CSS样式来获取更高效和可读的代码。 以前，将JavaScript脚本用于评级部分可能会减慢页面加载时间。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37776>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/34643>
* _ACP2E-2529_：启用Recaptcha时检查礼品卡余额时出现异常
   * _修复注释_：用户将能够在查看和编辑购物车屏幕中获取礼品卡余额。 以前，启用reCAPTCHA时，不会显示这些详细信息。
   * _GitHub代码贡献_： <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_：[说明]功能请求ADA合规性
   * _修复注释_：系统现在通过删除不受支持的CSS属性并将其替换为print.css文件中支持的属性来确保ADA的合规性。 以前，使用不支持的CSS属性会导致浏览器兼容性问题。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_： [Cloud] AC 2.4.4-p8的effect-drop.js中的混淆库代码
   * _修复注释_：系统现在可以正确实施effect-drop.js库，从而确保jQuery UI效果的正常运行。 以前，effect-drop.js库错误地被effect-clip.js库覆盖，导致jQuery UI效果出现潜在问题。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3367_：站点标头 | 特殊字符破坏了客户欢迎部分
   * _修复注释_：修复之后，在客户欢迎部分中正确显示了特殊字符。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3561_：客户区段编辑失败，出现日期范围
   * _修复注释_：如果只编辑了一个日期，则可以保存具有日期范围条件的客户区段。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a52ff98f>
