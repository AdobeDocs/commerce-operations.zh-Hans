---
source-git-commit: cfaa71f84f7d27d41c9d991aceef0087ee3d8ec0
workflow-type: tm+mt
source-wordcount: '8487'
ht-degree: 0%

---
# Magento Open Source发行说明(v2.4.8-beta2)

## v2.4.8-beta2中的亮点

以下30项功能亮点适用于Magento Open Source 2.4.8版本。

### Braintree

* _BUNDLE-3400_：删除不支持的LPM
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3401_： Google支付标记
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3402_： Apple支付标记
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3403_： Google付款送货回拨
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3404_：稍后付费消息
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3405_： JS-SDK按钮
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3406_：优化Braintree扩展中的代码
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3407_：更新Braintree PHP和JS SDK
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3408_：行项目(GooglePay)
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3409_：行项目(Apple支付)
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/208>
* _BUNDLE-3420_：包跟踪
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/208>

### 框架

* _AC-12012_：将Nginx版本从1.24更新为1.26
* _AC-12028_：添加与2.4.8和2.4.7的最新版本Composer 2.8的兼容性
* _AC-12029_：检查与Varnish 7.6兼容性
* _AC-12970_： PHPUnit 10升级第2部分 — 删除弃用
   * _修复说明_：已将phpunit/phpunit编辑器依赖项更新为兼容版本 — “phpunit/phpunit”：“10.x”
* _AC-13076_：使用最新可用版本更新所有js库和npm依赖项
   * _修复注释_：编辑器版本支持仅更新到编辑器版本2.2.x。 现在，支持也扩展到了2.4.x版本。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/19844aa0>
* _AC-13077_：所有捆绑的扩展和集成组件都与PHP 8.4兼容
* _AC-13078_：所有Adobe Commerce工具都与PHP 8.4兼容
* _AC-13079_：所有Adobe Commerce项目laminas/dependencies都与PHP 8.4兼容
* _AC-13256_：将TinyMCE依赖项从版本7降级到版本6.8.5
* _AC-13276_： PHP 8.4的弃用要求对Adobe Commerce进行重大更改
* _AC-8828_：将MySQL的默认归类设置为utf8mb4

### 其他

* _AC-12133_： Adobe Commerce 2.4.8核心代码与PHP 8.4兼容
* _AC-12972_： 2.4.8-beta2核心质量改进
* _AC-13038_：从composer.json中删除PHP 8.1和所有相关支持
* _AC-13448_：为2.4.8提供了一级价格运营性能改进修补程序
   * _修复注释_：在使用“/V1/products/tier-prices”REST API端点时，系统现在允许更高效地批量更新层价格，而不会导致性能问题或站点无响应。 以前，使用此端点更新大量价格可能会导致性能问题和网站无响应。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/082d981c>
* _AC-13550_：从Adobe存储库中删除所有Magento Open Source机密版权声明
   * _修复说明_：已从开源存储库中删除所有Adobe机密版权声明，确保仅使用Adobe版权的简化形式。 以前，公共存储库中的某些文件包含Adobe机密版权声明，这会导致社区上报。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39493>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/4bca5dfe>

### 安全性

* _AC-10982_： [2FA]与Duo Web SDK集成以支持通用提示
   * _修复注释_：待定

### 测试框架

* _AC-9037_：能够为Adobe Commerce源代码使用Adobe版权

### UI框架

* _AC-12944_：从adobe commerce中删除TinyMCE 5

## 修复了v2.4.8-beta2中的问题

我们已在Magento Open Source 2.4.8核心代码中修复了159个问题。 此版本中包含的已修复问题的子集如下所述。

### API

* _ACP2E-3236_：有效负载中缺少SKU时，异步操作失败
   * _修复注释_：如果有效负载中缺少sku，则异步和同步操作以前由于产品保存错误而失败。 修复后，异步和同步产品保存rest api操作失败，并显示相关的异常消息。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_： [CLOUD]无法使用REST API更新基价（“catalog_product_entity_decimal”中的“value_id”值未正确递增。）
   * _修复说明_：在此修复之前，调用rest api /rest/default/V1/products/base-prices时，增量ID错误地增加，使值之间出现间隙。 修复后，增量ID将按预期递增。 此外， value_id字段范围也增加了。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3486_：未对产品RestAPI的日期和时间属性设置默认值
   * _修复注释_：现在通过RestAPI为日期、日期和时间属性正确设置了默认值
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1984c61c>

### API、购物车和结账

* _ACP2E-3343_：严重500错误：Magento\Framework\Webapi\Exception与接受HTTP标头相关
   * _修复注释_：修复后，指定“接受”标头没有问题。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1366ae5e>

### 帐户

* _AC-10886_：管理员密码更新。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38352>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-11718_：当URL大写时重定向循环
   * _修复注释_：系统现在会自动将URL中的大写字符转换为小写，从而防止在访问主页时出现重定向循环。 以前，如果安全基础URL中包含大写字符，则在尝试访问主页时会引发连续的重定向循环。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38538>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38539>
* _AC-13000_：“以客户选择加入身份登录”复选框不可翻译
   * _修复说明_：系统现在允许在“商店视图”范围中设置“以客户身份登录选择加入复选框”和“以客户身份登录”复选框工具提示”字段，从而为不同的商店视图启用翻译。 以前，这些字段仅在“网站”范围中设置，导致无法翻译各个商店视图。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/32329>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/32359>
* _ACP2E-3329_：登录后，未显示以访客用户身份添加到比较列表的产品。
   * _修复注释_：以客户身份登录之前添加到产品比较列表的产品现在会在登录后保留。
以前，在登录后，以访客用户身份添加到比较列表的产品不可见。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_：允许国家/地区配置导致客户地址配置出现问题
   * _修复注释_：现在选择“允许国家/地区”配置不会影响为给定范围之外显示的国家/地区。 以前，允许国家/地区配置会影响给定范围之外的客户地址属性
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/078c387e>

### 帐户、API、GraphQL

* _ACP2E-3246_：客户API — 成功登录后无法重置为0的登录失败数
   * _修复注释_：现在，客户通过API端点成功登录后，客户实体表中的故障编号将重置为零。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ec7e32a9>

### 帐户、管理员UI、B2B

* _ACP2E-3038_：受限管理员用户无法始终查看自定义共享目录
   * _修复注释_：受限管理员用户现在可以始终查看和管理客户以及为其分配产品的所有共享目录，前提是他们有权访问特定商店。 以前，具有特定商店访问权限的受限管理员用户无法始终查看分配给产品的所有共享目录，或者无法查看客户，从而导致系统中出现不一致的情况。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7377de59>

### 管理员UI

* _AC-10705_： [问题]为“重新加载数据”数据按钮添加权限检查
   * _修复注释_：系统现在包含对“重新加载数据”按钮的权限检查，以确保该按钮仅向具有相应权限的用户显示和访问。 以前，“重新加载数据”按钮对所有用户可见和可点击，导致在没有必要权限的用户单击时出现“不允许”页面。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38283>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38279>
* _AC-13131_： [问题]修复警告：未定义数组键“筛选器”
   * _修复注释_：系统现在处理新用户尚未与书签交互的情况，从而阻止记录未定义的数组键“筛选器”警告。 以前，当新用户未与书签交互时，将记录此警告。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39013>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38996>
* _AC-13529_：由于Validate.php文件中的代码更改，产品导入带有特殊字符的csv文件失败
   * _修复注释_：系统现在可以正确验证和导入包含特殊字符的产品CSV文件，从而允许成功传输数据。 以前，尝试导入包含特殊字符的产品CSV文件会导致错误，从而阻止导入过程。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-7962_：在手机视图中结帐付款时，没有指向送货的链接
   * _修复注释_：系统现在可以确保在移动视图中的页面顶部始终显示签出标题/链接“送货”和“审核和付款”，从而使用户能够轻松地在步骤之间导航并进行必要的更正。 以前，这些标题/链接在移动视图中隐藏，使用户难以了解其当前步骤或返回之前的步骤。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/36856>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36982>
* _AC-8109_：客户订单查询装运注释created_at在+0时区中返回，不在商店配置的时区中
   * _修复注释_：使用客户订单查询时，系统现在会在客户配置的时区中正确显示来自装运注释的“created_at”字段。 以前，“created_at”字段以+0时区显示，无论客户配置的时区如何。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/36947>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37642>
* _ACP2E-3294_：送货地址状态不是自动更新
   * _修复说明_：在修复之前，送货地址区域（或区域ID）与地址帐单信息不同步。 现在，当帐单地址信息更改时，送货地址区域和区域ID都会正确更新。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_：“重置”按钮对添加/编辑管理员用户不起作用
   * _修复注释_：以前，在“添加/编辑管理员用户”页面上，“重置”按钮不起作用。 现在，在“管理员”面板中“系统” — >“权限” — >“所有用户”下，“重置”按钮将在“添加/编辑管理员用户”页面上正常工作。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/5184c067>
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
   * _修复注释_：以前，在“管理”面板的生产模式下启用JavaScript缩小功能会导致浏览器控制台中出现与TinyMCE 7相关的JavaScript错误，从而影响功能和用户体验。 现在，此问题已得到解决，从而确保TinyMCE 7平稳运行，不会生成任何错误，即使启用了JS缩小也是如此。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_：请求进行其他更改以完全完成ACP2E-3375修复
   * _修复注释_： &#39;-
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d50f6b5d>

### 管理员UI、支付/支付方式、订单

* _AC-13520_： PayPal智能按钮排序后，交易授权未显示在“交易”选项卡中
   * _修复注释_：使用PayPal智能按钮下订单后，系统现在会在“交易”选项卡中正确显示交易授权。 以前，单击“授权”按钮后，授权交易未显示在Transaction选项卡中，并且未创建“授权”类型的新交易。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6cfb9b6b>

### 管理UI、暂存和预览

* _ACP2E-3424_： [Cloud]删除缺少映像的模板导致pub/media被删除
   * _修复注释_：在此修复之前，如果pagebuilder模板缺少预览图像名称，则会删除pub/media文件夹。 修复后，将仅删除模板和预览图像（如果找到）。
   * _GitHub代码贡献_： <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analytics/报表

* _AC-9922_： Google Analytics CSP错误https://region1.analytics.google.com
   * _修复注释_：启用Google Analytics后，系统现在可正确连接到“https://region1.analytics.google.com&#39;”，从而防止出现内容安全策略(CSP)错误。 以前，由于拒绝连接到“https://region1.analytics.google.com&#39;”，因此启用Google Analytics并从欧盟查看网站会导致CSP控制台错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37750>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38991>
* _ACP2E-3183_： NewRelic浏览器监视内联JS脚本导致CSP错误
   * _修复注释_：应用程序现在插入NewRelic浏览器监视脚本，而不是APM代理，以符合CSP（内容安全策略）。 以前，由APM代理插入的NewRelic浏览器监控脚本与CSP不兼容，并导致脚本无法执行。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_：对sales_bestsellers_aggregated_daily表的INSERT查询在销售订单量大的项目上变得缓慢
   * _修复注释_：以前，如果下订单量很大，则要生成畅销商品汇总的每日报表会花费大量时间。 现在，报告已及时生成。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_：订单报表显示错误的货币符号
   * _修复注释_：订单报表中订单金额的货币符号错误地取自currency/options/base。 现已更正为使用“货币”/“选项”/“默认”报表，以便进行准确的报告。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_： [Cloud]优惠券使用情况报告中的计算不正确
   * _固定注释_：通过将“折扣税补偿金额”和“装运折扣税补偿金额”合并在一起，现在可以准确计算优惠券报表网格中的销售总额。 以前，计算中缺少这些金额，导致销售总额与销售订单数据之间存在差异。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_：共享“&lt;project_id>/var/tmp”时出现问题
   * _修复注释_： Analytics DataExport临时文件将使用sys tmp目录，该目录更适合频繁访问和更改。 为了避免在同一服务器上运行多个实例时发生冲突，更新了tmp路径以使用实例的唯一id
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4cf5e62>

### Analytics/报表、云

* _ACP2E-3187_： NR中的量度可能对后台事务产生误导 — ACP2E-3067的跟进
   * _修复注释_：后台事务(cron)将使用在配置设置中定义的New Relic应用程序名称
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _ACP2E-2139_：执行部分索引时，分配给共享目录的产品未反映在前端
   * _修复注释_：现在，在部分索引完成后，通过REST API分配到共享目录的产品会立即在店面中可见。 以前，产品仅在完全重新索引后可见。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3247_： sales_clean_quotes cron会从尚未批准的采购订单中删除报价
   * _修复注释_： sales_clean_quotes cron作业不会删除采购订单中使用的报价
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/581b7ef1>

### 捆绑

* _AC-10826_：店面包复选框验证错误消息计数大于1
   * _修复注释_：现在，单击“添加到购物车”按钮时，系统只显示一条验证错误消息，而没有为捆绑产品选择任何复选框选项。 以前，系统会为每个未选复选框显示多个验证错误消息。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3ea26621>

### 购物车和结帐

* _AC-11914_： [问题]销售规则CartFixed计算：折扣金额不正确
   * _修复注释_：系统现在可以正确计算具有购物车固定金额的销售规则的折扣金额，从而确保无论购物车项目发生什么更改，都能应用准确的折扣。 以前，当购物车项目更改时，折扣金额可能会错误地变化，有时会导致折扣显着高于预期。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38694>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/581b7ef1>
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
* _ACP2E-3176_： [云]快速订购大量SKU性能
   * _修复注释_：当购物车价格规则条件中使用的属性对于所有产品均不存在，并且启用了MAP（最低广告价格）功能时，结账性能已得到改进。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_：购物车中重复的项目
   * _修复注释_：系统现在可正确处理多个并行请求，以将同一产品添加到购物车中，并添加到单个行项目，从而防止为同一SKU创建单独的行项目。 以前，并行请求将同一产品添加到店面的购物车会导致同一SKU出现多个行项目。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_：将结账订单电子邮件确认发送给以名字/姓氏输入的电子邮件
   * _修复注释_：不再发送签出订单电子邮件确认，该确认之前在“名字”和“姓氏”字段中输入类似电子邮件的模式时发送。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_：签出送货地址表单更新为错误的地址
   * _修复注释_：现在已将shippingAddressFromData保存到每个网站的本地存储中。 以前，如果在URL中使用商店代码，并且在同一访客会话期间从多个网站启动了结账，则来自错误网站的地址可能会在结账期间自动填充到送货地址表单中。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3407_：礼品卡产品 | 购物车合并正在合并礼品卡
   * _修复注释_：Giftcard产品现已正确合并到购物车中
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3488_：现有报价数据未更新/不可见，而是在trigger_recollect = 1时创建新的报价记录
   * _修复注释_：客户的购物车项目在添加到购物车后不再因产品被删除而消失。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1984c61c>

### 目录

* _AC-11970_：无法通过选中自定义选项的一个复选框来重新排序可配置产品
   * _修复注释_：系统现在使用单个选定的复选框自定义选项正确处理可配置产品的重新排序，从而允许成功创建购物篮。 以前，尝试重新排序此类产品会导致错误，并阻止将商品添加到购物车。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38736>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1d144bce>
* _AC-13068_：下拉列表选项缺失
   * _修复注释_：现在，在创建具有超过20个值的新属性时，系统会在下拉列表中正确显示所有值。 以前，仅显示前20个值或其他选定的页面值，从而导致其余值缺失。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_： [问题]将当前的存储ID用于类别运行时缓存
   * _修复注释_：系统现在可以正确使用类别运行时缓存的当前存储ID，从而防止在使用模拟或自定义代码将类别保存到其他存储时覆盖数据。 以前，存储在运行时的对象可能来自错误的存储，从而导致数据覆盖。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39310>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36394>
* _AC-13324_： bin/magento sampledata：deploy —no-update引发异常
   * _修复注释_：在sampledata：deploy命令中使用 — no-update选项时，系统现在可以正确接受布尔值，从而防止在示例数据部署期间出现任何错误。 以前，使用此命令时引发错误，因为系统错误地期望整数值。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39344>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39345>
* _AC-13355_： [问题]修复EAV缓存类型的用法
   * _修复注释_：系统现在在所有相关位置正确使用EAV缓存类型，确保一致且高效的数据缓存。 以前，EAV缓存类型使用不一致，这会导致数据缓存效率低下和不一致。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/32322>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/31264>
* _AC-13596_：包含空数据的目录高级搜索将转到搜索结果页面[2.4.dev分支]
   * _修复注释_：系统现在可以在“高级搜索”页面上正确保留用户，并在用户尝试执行搜索而不输入任何数据时显示错误消息。 以前，执行空搜索会将用户重定向到“目录高级搜索”页面，并显示一条消息，提示用户修改其搜索。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6cfb9b6b>
* _ACP2E-3103_：由于缓存，未使用新产品更新New Products RSS源
   * _修复注释_：将产品设置为新并保存后，现在将更新“新产品”的Rss源
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d01ee51e>
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
* _ACP2E-3516_：如果进程终止，则不清理索引器临时表
   * _修复注释_：如果索引器进程终止，现在将清除CatalogRule索引器临时表
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_： 2.4.7-p3中的[QUANS]核心单元测试失败
   * _修复说明_：此测试不需要发行说明，因为它是一项单元测试改进。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1984c61c>

### 目录，内容

* _ACP2E-3063_： [云]缓存未失效。
   * _修复注释_：以前，在保存具有更新设计布局的CMS页面时，该页面不会在前端正确反映。 应用此修复后，当我们更改设计布局并保存CMS页面时，会在前端看到相应的设计布局。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_：[云]在内容小部件中反转的锚点/非锚点类别
   * _修复注释_：以前，当我们选择“显示位置” — >“锚点类别”时，它显示的所有类别都没有反映锚点与非锚点之间的父子关系。 应用此修复后，“显示位置 — >锚点类别”仅显示锚点类别（可选），“显示位置 — >非锚点类别”则显示非锚点类别（可选）
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_：类别无法使用小组件
   * _修复注释_：以前，如果我们为不同的锚点/非锚点类别保存CMS块，那么当该块显示在前端时，它不适用于子类别。 应用此修复后，块会显示在不同类别的前端。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d01ee51e>

### 目录，GraphQL

* _ACP2E-3312_：层价格在GraphQL产品中返回了错误的值（与Storefront相比）
   * _修复注释_：修复后，为graphql请求返回的产品层价格具有每一项的价格。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1366ae5e>

### 目录，搜索

* _ACP2E-3345_：创建对象时出现类型错误： Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor异常
   * _修复注释_：修复后，无需指定$data即可创建Magento\CatalogSearch\Model\Indexer\Fulltext类的实例。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_：在Magento Admin中保存后，产品的[CLOUD]问题在前端不可见
   * _修复注释_：修复了具有长名称子产品的可配置产品后，店面不会丢失这些产品。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1984c61c>

### 内容

* _AC-12692_：构件类别树未正确呈现
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39008>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_：在设计配置页面中更改主题时，无法看到“使用默认值”消息
   * _修复注释_：系统现在包含一个单独的列，以根据设计配置页面中选择的主题显示“使用默认值”消息。 这确保默认值状态清晰可见。 以前，不会显示“使用默认值”消息，这会导致对所选主题状态的混淆。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13569_： [问题]再次恢复与TinyMCE插件的向后兼容性(之后……
   * _修复注释_：系统现在恢复与TinyMCE插件的向后兼容性，允许从其他位置使用小组件时调用插件中定义的函数。 以前，由于TinyMCE版本中的更改，插件不会将构件作为对象返回，从而导致在尝试调用构件实例上的某些函数时出错。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39262>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39258>
* _ACP2E-3122_： [CLOUD]上传图像按钮不起作用
   * _修复注释_：在PageBuilder中“横幅”和“滑块”的“上传图像”按钮未按预期工作之前，现在按该按钮时会打开本地文件管理器以选择要上传的图像。
   * _GitHub代码贡献_： <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3275_： [Cloud] - CMS滑块未反映最新更改
   * _修复注释_：通过确保在编辑幻灯片屏幕上触发保存事件时刷新滑块列表，已修复此问题。 以前，它会触发并导致问题。
   * _GitHub代码贡献_： <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_：使用页面生成器按特定顺序插入CMS块时，CSM页面中出错
   * _修复说明_：以前，在某些版本的PHP和OS (Linux)上，通过PageBuilder引用其他cms块的块的块呈现会失败，并出现“发生未知错误。 请重试。” 现在，cms块的内容在PageBuilder控制的内容中正确呈现。
   * _GitHub代码贡献_： <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3430_：缺少TinyMCE 7字体大小的最新安全更新
   * _修复注释_： WYSIWYG编辑器中现在提供字体大小和字体系列选择器。 在此修复之前，使用TinyMCE 7时，这些在编辑器界面中不可用。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d50f6b5d>，<https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>

### 客户/客户

* _AC-8499_：更改国家/地区下拉列表时，未重置区域文本字段
   * _修复注释_：现在，在下拉菜单中更改国家/地区时，系统会重置区域文本字段，以确保以前的值不会保留。 以前，从下拉列表中更改国家/地区不会重置“区域”字段，从而导致保留最后保存的值。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_：删除客户时不会清除Storefront上所有已登录和删除客户的浏览器会话数据
   * _修复注释_：删除客户现在会按预期清理店面中所有已登录和删除客户的浏览器会话数据。 购物者可以继续购物，他们的浏览器将他们的会话视为访客会话。 以前，当从管理员中删除登录购物者的客户帐户时，购物者的浏览器会引发JavaScript错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7d5e3906>

### 框架

* _AC-10738_：清漆配置不排除所有营销参数
   * _修复注释_：系统现在正确排除了Varnish配置中的所有常见营销参数，从而确保准确跟踪和分析。 以前，某些营销参数（如gad_source、srsltid和msclkid）不被排除，导致数据收集的潜在不准确性。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38298>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39188>
* _AC-11592_： [问题]在安装期间仅允许有效的首选项:di:编译
   * _修复注释_：如果为不存在或明确排除的类创建首选项，系统现在会在安装:di:编译命令期间引发错误，确保只允许使用有效的首选项。 以前，这些方案将以静默方式失败，潜在地使与原始类关联的任何插件变得无用。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38517>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/33161>
* _AC-11809_： [问题]通过XML将自定义属性传递到当前链接
   * _修复注释_：系统现在允许通过XML将自定义属性传递到当前链接，确保即使链接是当前页面也能正确显示这些属性。 以前，由于当前链接未使用getAttributesHtml()方法，因此不会显示当前页面链接的自定义属性。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38500>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/30070>
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
* _AC-12857_： PHP 8.2.15删除了FTP扩展
   * _修复注释_：系统现在将FTP扩展作为依赖项包含在composer.json文件中，从而确保通过FTP成功配置CSV导入。 以前，由于PHP包中缺少FTP扩展，尝试通过FTP配置CSV导入时引发错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39083>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12964_：能够为dev:di:info CLI命令定义区域
   * _修复注释_：系统现在允许开发人员定义dev:di:info CLI命令的区域，从而增强开发和调试过程。 以前，此命令只能显示GLOBAL区域的信息。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38758>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38759>
* _AC-13279_： [问题]移除所有营销获取参数以最小化缓存
   * _修复注释_：系统现在将删除所有Marketing Get参数以优化缓存利用率，镜像使用Varnish时所使用的逻辑。 以前，这些参数可能会导致缓存溢出和性能降低。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39266>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39099>
* _AC-13345_： [问题] [PHPDOC]修复错误的phpdoc Magento\Directory\Model\AllowedCountries：：getAllowedCountries()
   * _修复说明_：已更正AllowedCountries：：getAllowedCountries()方法的PHPDoc，以提供准确的信息，从而提高文档的清晰度和实用性。 以前，此方法的PHPDoc包含不正确的信息，这可能导致混淆或误用方法。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39246>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39241>
* _AC-13348_： [问题]删除我们不再支持的PHP版本的一些代码。
   * _修复注释_：删除了Magento不再支持的PHP版本的代码
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39361>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39202>
* _AC-13417_： [问题]使ImageMagick适配器与php8兼容（从浮点数到int的隐式转换）
   * _修复注释_：系统现在通过在计算图像尺寸时正确处理浮点数，从而确保与PHP8的兼容性，从而防止因从浮点到int的隐式转换而出现任何错误。 以前，计算图像尺寸可能会导致浮点数，这种情况下，隐式舍入可能会导致错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39402>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37362>
* _AC-13537_： [问题] [PHPDOC]修复错误的phpdoc Magento\Framework\App\Config\ScopeConfigInterface
   * _修复注释_：此更新更正了Magento\Framework\App\Config\ScopeConfigInterface中的PHPDoc注释，以准确反映getValue和isSetFlag方法的$scopeCode参数的类型。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39492>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39199>
* _AC-8662_： [问题]改进cron错误日志记录
   * _修复注释_：系统现在捕获并记录cron进程的STDERR和STDOUT，在cron进程失败的情况下提供有价值的诊断信息。 以前，cron进程内的任何错误消息都不会被记录，并且在不同的进程中运行的cron组的STDERR和STDOUT将会丢失。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37453>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/32690>
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
   * _修复注释_：正在正确清除队列消息。 在修复之前，假定正在使用SQL队列系统，如果清除队列消息同时运行，则可能会删除新消息。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d50f6b5d>

### 框架、UI框架

* _ACP2E-3324_：即使配置值已锁定，仍有可能覆盖配置值
   * _修复注释_：以前对于此修复，无法通过bin/magento config：set命令设置设计配置，并且可以通过操作显示这些配置信息的表单来更改锁定的值。 修复后，无法再更新从cli使用 — lock-env或 — lock-conf设置的锁定值。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _ACP2E-2974_：客户返回属性的翻译未反映在相应StoreView的GraphQL API中
   * _修复注释_：客户返回属性的翻译反映在相应StoreView的GraphQL API中。
以前，各个StoreView的客户返回属性不会反映在GraphQL API中。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3215_：多站点设置中存在用户身份验证和跨站点令牌访问的[云]问题
   * _修复注释_：多站点设置中的GraphQl客户信息和购物车查询会检查非默认网站上的客户是否存在。
以前，在多站点设置中，查询不起作用，不能确保客户存在于非默认网站上。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3255_：在获取customerCart时应指定[GRAPHQL]模型值
   * _修复注释_： GraphQL“customerCart”查询现在可以创建空购物车，即使报价在数据库中不可用也是如此。 以前，此操作在创建空购物车时由于国家/地区验证问题而失败。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3380_： [GraphQl]愿望清单项目可通过GraphQl查看，但在店面不可见
   * _修复注释_：通过GraphQL请求时，未正确列出愿望清单产品。 现在，会根据提供的商店上下文过滤愿望清单产品。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/55615e61>
* _ACP2E-3404_： [GraphQL]重置内容与主题/链接之间的密码电子邮件不一致
   * _修复注释_：通过模拟在发送密码重置请求时客户帐户注册的正确商店（无论网站商店如何），该问题已得到解决。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3419_： [Cloud]产品GraphQL查询返回未分配到当前网站的相关产品
   * _修复注释_：以前，对于graphQL查询，产品查询无法正确显示与多商店相关的产品。 应用此修复后，对于产品，graphQL会查询多商店相关产品并相应地显示。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3447_：在GraphQL标头中使用错误的Store ID会导致内存错误
   * _修复注释_：在GraphQL请求中发送错误的存储区代码不再导致内存消耗过多。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3467_： [Cloud] 500响应2.4.7上的空Graphql响应
   * _修复注释_：修复后，无效的graphql请求将不会记录到exception.log文件中。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1984c61c>

### GraphQL，搜索

* _ACP2E-948_：产品列表GraphQL查询仅限于total_count 10,000个产品
   * _修复注释_：修复后，搜索结果不限于10000个产品，即使计数超过10000，也可以获取符合搜索条件的所有产品。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL，测试框架

* _ACP2E-3363_： Magento\GraphQl\App\GraphQlCustomerMutationsTest.php集成测试失败
   * _修复注释_： &#39;-
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4cf5e62>

### 导入/导出

* _ACP2E-3172_：缺少导入按钮
   * _修复注释_：解决CSV中数据检查后导入按钮缺失的问题。 以前，在对CSV中正确和不正确记录的数据进行检查后，导入按钮不会显示。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_：无法导入导出的客户地址
   * _修复注释_：客户地址导入将按预期继续。 以前，如果共享客户帐户=全局，客户地址导入文件将不会通过验证，并且有两个网站（默认网站有一个受限制的国家/地区列表）的导入地址适用于另一个允许国家/地区不同的网站
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_： [Cloud] CSV文件中的错误数量未给出错误
   * _修复注释_：现在，库存源导入将引发数量列中的非数字值的验证错误。 以前，在数量列中导入具有非数字值的库存源会导致数量设置为0。
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3475_：产品导出导致内存限制为4G的OOM
   * _修复注释_：在此修复之前，如果产品属性具有数千个选项值（即使具有4G可用内存），则产品导出失败。 进行此修复后，产品导出应会完成导出csv文件。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1984c61c>

### 导入/导出，性能

* _ACP2E-3476_： [Cloud]产品导入时间已显着增加
   * _修复注释_：在修复之前，包含超过10,000个条目的目录产品导入会显着降低时间。 修复后，及时执行目录产品导入。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/87d012e5>

### 安装和管理

* _AC-13242_：Magento升级在MariaDB 11.4 + 2.4.8-beta1上失败
   * _修复注释_：升级应该没有任何错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7b336d0a>

### 库存/MSI

* _ACP2E-3335_：启用MSI收取存储时无法发送订单
   * _修复注释_：如果存在许多店内提货来源，则提高了创建装运的库存性能
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_： Cron重新索引无法更新前端产品可用性
   * _修复注释_：以前，通过REST API更新延交订单状态后，产品在前端保持缺货。 现在，通过REST API更新延交状态后，产品将显示为有货。
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_：启用MSI时，将图像添加到可配置项无法正常工作。
   * _修复注释_：使用库存模块时，可配置产品的映像上传现在将按预期工作。 以前，图像上传不起作用
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/fdf409aa>

### 库存/MSI、搜索

* _ACP2E-3413_：未将SKU设置为可搜索属性时，所有产品都将使用[is_out_of_stock] = 1编制索引
   * _修复注释_：修复后，目录搜索索引中的“is_out_of_stock”是正确的，即使sku不可搜索也是如此。
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/5b21b7af>

### 订购

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

### 其他开发人员工具

* _AC-12731_：与dev/css/use_css_critical_path结合使用的CSP问题
   * _修复注释_：现在，即使启用了“dev/css/use_css_critical_path”设置，系统也会在签出页面上正确异步加载CSS文件，从而确保这些页面使用正确的CSS样式呈现。 以前，受限制的内容安全策略(CSP)阻止执行内联JavaScript，这导致CSS文件无法按预期加载。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39020>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39040>
* _AC-13398_：使用虚拟类型配置插件，无法在安装程序:di:编译命令中正确生成侦听器方法
   * _修复注释_：系统现在在使用虚拟类型配置插件时正确生成侦听器方法，从而确保无论是预编译的结果还是运行时编译的结果都一致。 以前，与运行时编译相比，在预编译时，系统会产生不正确的结果。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/33980>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38141>

### 支付

* _ACP2E-3143_： PayPal订单退款导致贷项通知单重复
   * _修复注释_：修复了PayPal付款服务的IPN创建的贷项通知单并发问题。
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
* _AC-13471_：支持Magento CLI中的Symfony CommandLoaderInterface
   * _修复注释_：此项更改允许延迟初始化命令，直到需要这些命令为止，从而缩短了Magento CLI应用程序的初始化时间。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/29266>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/29355>

### 产品

* _AC-13173_： [问题]修复PHPDoc块中的拼写错误
   * _修复注释_：系统现在可以正确删除PHPDoc中用于$helper变量声明的未知引用变量，从而提高代码清晰度和准确性。 以前，PHPDoc中这个未知的引用变量会导致代码中出现混淆和潜在的不准确性。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38961>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38940>
* _AC-13423_： [问题]修复了Magento中损坏的捆绑包和可下载的产品页布局>= 2.4.7
   * _修复说明_：已修复捆绑包和可下载产品页面的布局，确保所有设备显示一致且正确。 以前，由于重新排列产品信息媒体块，这些页面遇到布局问题。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39403>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6cfb9b6b>

### 促销活动

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
   * _修复注释_：现在在后端，使用管理员值而不是产品属性的默认商店值。
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
* _ACP2E-3498_：与折扣/特价产品同时应用多个购物车价格规则时，折扣值不正确
   * _修复注释_：在修复之前，如果应用了多个购物车规则，则无法正确应用整个购物车规则的固定金额。 现在，可以正确应用固定金额折扣购物车规则。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1984c61c>

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

* _ACP2E-3273_： ReCaptcha V2在德语签出时显示不正确
   * _修复注释_：以前，对于长单词语言（如德语），签出时电子邮件地址下方的recaptcha显示为无样式。 之后，recaptcha看起来与其他区域中的所有recaptcha元素相同。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7377de59>

### 配送

* _ACP2E-3340_： FedEx跟踪API不使用REST凭据
   * _修复注释_：以前，FedEx集成不需要额外的API密钥即可跟踪API。 现在添加了新配置以支持跟踪API密钥。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_： [Cloud] FedEx协商利率未在REST上返回
   * _修复注释_：在修复之前，联邦快递帐户特定的费率未在响应时发送，即使根据FedEx文档它们本应发送也如此。 修复后，通过更改我们方的请求，在响应中发送特定于帐户的费率。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/55615e61>

### 暂存和预览

* _ACP2E-3453_：使用唯一的自定义类别属性时无法更新计划更新
   * _修复注释_：修复了在类别具有唯一属性时无法更新类别的计划更新的问题
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/078c387e>

### 税金

* _ACP2E-3193_：固定产品税(FPT)不适用于可配置产品
   * _修复注释_： FPT以使可配置产品变体正常工作。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ec7e32a9>

### 测试框架

* _AC-13362_： [问题] PHPDoc更正拼写
   * _修复注释_：由于PHPDoc中的拼写更正问题，系统现在可以正确识别IDE中已弃用的方法。 以前，PHPDoc中的拼写错误会导致IDE无法识别已弃用的某些方法。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/31399>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/31398>
* _AC-13478_： MAGETWO-95118：检查会话过期后永久购物车的行为
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7d5e3906>
* _ACP2E-3458_： [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _修复注释_：修复了mftfs
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/078c387e>

### UI框架

* _AC-12432_： Ui组件文件字段
   * _修复注释_：系统现在可以正确验证UI组件表单中的文件字段，以便在选择文件时提交表单而不会出错。 以前，即使选择了文件，验证也会失败，导致表单无法提交。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38908>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/39004>
* _AC-12645_： [问题] js控制台中的日期格式已得到改进：从12小时切换到24小时……
   * _修复注释_：改进了js控制台中的日期格式：从12小时切换为24小时
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38983>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38972>
* _AC-12650_： [问题]在开发人员模式下为较少的文件添加sourceMap生成
   * _修复注释_：在开发人员模式下，系统现在为较少的文件生成源映射，从而更容易识别样式的源。 以前，在服务器端编译较少的开发者模式下运行系统时，要识别样式的来源非常困难。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38982>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38977>
* _AC-13459_：使用最小库存阈值进行“缺货”排序时的行为不一致
   * _修复注释_：系统现在可以根据库存水平正确地对目录中的产品进行排序，遵循设置的最低库存阈值，并将缺货商品一致地移到列表的底部。 以前，排序行为不一致，根据库存水平，项目并非始终以正确的顺序显示，并且在保存、刷新或修改类别层次结构后，排序可能会发生意外更改。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_：建议改进require.js加载问题的错误报告
   * _修复注释_：此PR可改进必需项加载组件失败时的错误消息。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/36761>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38971>
* _AC-9168_： [问题]删除不必要的脚本审阅摘要
   * _修复注释_：系统现在通过从评级部分中删除不必要的JavaScript脚本来优化页面加载时间，而不是使用内联CSS样式来获取更高效和可读的代码。 以前，将JavaScript脚本用于评级部分可能会减慢页面加载时间。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37776>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/34643>
* _ACP2E-3367_：站点标头 | 特殊字符破坏了客户欢迎部分
   * _修复注释_：修复之后，在客户欢迎部分中正确显示了特殊字符。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1366ae5e>
