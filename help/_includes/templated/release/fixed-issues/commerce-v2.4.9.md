---
source-git-commit: 21da8a0133c3c70c2c37851aca79e2d5d8f82905
workflow-type: tm+mt
source-wordcount: '3327'
ht-degree: 0%

---
# Adobe Commerce已修复问题(v2.4.9)

## 修复了v2.4.9中的问题

我们已在Adobe Commerce 2.4.9核心代码中修复了84个问题。 此版本中包含的已修复问题的子集如下所述。

### API

* __对于async.magento.configurableproduct.api.optionrepositoryinterface.save.post__，异步批量操作仍处于打开状态
如果请求正文不是Array，则批量API端点现在将引发错误，因此需要批量项目键是从0开始的连续数字。 以前，由于批量请求中提交的任意项目键，无法更新批量项目状态。
  _ACP2E-3544 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/9608ca21>)_
* 未使用searchCriteria __从当前存储考虑is_subscribed值上的__[ CLOUD] API REST错误
API REST客户查询使用searchCriteria从正确的存储中提取正确的“is_subscribed”值
以前，API REST客户查询在提取is_subscribed”值时不考虑存储。
  _ACP2E-3621 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/9608ca21>)_
* __async.operations.all可以为1个SKU创建多个条目__
现在，保存和更新相同产品的并发请求会被序列化，以防止可能导致数据不一致或产品重复的竞争情况
  _ACP2E-3744 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/520f9e30>)_

### 帐户

* 在客户帐户创建期间，__[云]删除操作因当前区域错误而被禁止__
修复程序保存地址无效的客户后，会返回一条描述无效原因的消息，而不是相关的“当前区域禁止执行删除操作”。
  _ACP2E-3791 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/6ea61121>)_

### 管理员UI

* __[问题]改进用户使用角色树__的体验
此拉取请求会添加按钮，以折叠所有项、展开所有项以及展开包含选定项的分支。 此功能类似于类别树（目录 — >库存 — >类别）中提供的功能
  _AC-14020 - [GitHub问题](https://github.com/magento/magento2/issues/39654) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/36511>)_
* __Symfony\Component\Mime\Exception\LogicException：“Sender”标头必须为“Symfony\Component\Mime\Header\MailboxHeader”的实例(得到“Symfony\Component\Mime\Header\MailboxListHeader”)__
  _AC-14520 - [GitHub问题](https://github.com/magento/magento2/issues/39823) - [GitHub代码贡献](<https://github.com/magento/magento2/commit/1e14bd72>) - [GitHub代码贡献](<https://github.com/magento/magento2/commit/1514117f>)_
* __提供使用网格批量删除税率的功能__
管理员用户现在可以同时从“管理员税率”网格中删除多个税率。  [GitHub-33399](https://github.com/magento/magento2/issues/33399)
  _AC-2238 - [GitHub问题](https://github.com/magento/magento2/issues/33399) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/33484>) - [GitHub代码贡献](<https://github.com/magento/magento2/commit/5cd64dd0>)_
* __条件SKU的购物车价格规则未考虑SKU中的“前导零”(sku： 01234与1234相同)__
系统现在可以正确处理购物车价格规则，其中条件SKU会考虑SKU中的“前导零”
  _AC-9428 - [GitHub问题](https://github.com/magento/magento2/issues/37919) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39525>)_
* __多选的默认属性选项值行为问题__
在修复多个选项属性的默认值之前，未正确保存。 现在，修复之后，值将正确地存储在数据库中。
  _ACP2E-3523 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/9608ca21>)_
* __后端管理菜单字幕未显示__
现在将正确显示主菜单组的所有标题。 以前，如果主菜单的第二列或第三列只包含一组链接，则不会显示该组的标题。
  _ACP2E-3540_
* __将产品数量从管理员移至购物车时出现问题__
从管理员创建订单时，侧边栏上的客户购物车中的产品在添加到订单时不会消失。
  _ACP2E-3563 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/c8ba4ab1>)_

### 管理员UI，B2B

* 作为客户标题登录的&#x200B;__B2B仍具有Magento品牌__
早些时候，店面标题显示“您现在作为&lt;store name>上的&lt;customer name>连接”与Magento品牌化。 现已修复，并且标题会显示为ADOBE品牌。
  _AC-14361 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/fadcfa8b>)_

### 管理员UI，内容

* 在图像插入期间&#x200B;__出现异常“无法为媒体资源路径创建演绎版”__
删除媒体库图像优化配置的“最大宽度”和“最大高度”的值后，在图像优化过程中不再发生错误。
  _ACP2E-3781 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/520f9e30>)_

### 管理员UI、安全性

* __弱密码管理__
使用相同密码时无法保存管理员用户。 以前，在没有进行正确验证的情况下成功保存了它。
  _ACP2E-3657 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/df92debe>)_

### 管理UI、安全性、暂存和预览

* 内容暂存的&#x200B;__操作日志__
现在，操作日志将显示暂存更新活动。 以前，暂存更新日志不会记录在管理员操作日志中。
  _ACP2E-3679_

### B2B

* __下单无效“通过可转让报价进行结帐”，付款方式为PayFlow Pro信用卡付款方式__
  _AC-11973_
* 引用重命名后的&#x200B;__成功消息间歇性消失__
  _AC-13447_
* __总计计算不包括税额__
在启用了跨境贸易的情况下，订单包含来自现有采购订单的订单的正确总计。
  _ACP2E-3727_
* __通过REST API取消分配B2B共享目录中的类别缓慢__
现在，在B2B中取消分配类别时，性能显着提高。 以前，取消分配B2B共享目录中的类别需要很长时间。
  _ACP2E-3796_
* B2B中的新安装程序修补程序存在&#x200B;__性能问题__
修复了在更新到B2B 1.5.2后升级Magento_Company模块时，在company_structure表中处理大量记录(~100,000+)花费过多时间的性能问题。
  _ACP2E-3850_

### 购物车和结帐

* __Magento 2.4.7更新（迷你）购物车不允许小数位数__
现在，当我们从小型购物车更新具有小数的数量时(区域设置为NL（荷兰语）)，Magento可正确处理
  _AC-13238 - [GitHub问题](https://github.com/magento/magento2/issues/39236) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39669>)_
* __[问题]更新subtotal.phtml__
系统以正确的间距更新subtotal.phtml
  _AC-13907 - [GitHub问题](https://github.com/magento/magento2/issues/39619) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39612>)_
* __无法向来宾下订单__
  _AC-14241 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/27217d0e>)_
* __已过期的永久引号未由cron作业sales_clean_quotes清理__
现在，当“persistent_clear_expired”cron作业运行时，将清除过期的持久引号。 以前，过期的持久引号不会被任何其他cron作业清除。
  _ACP2E-3493 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/11be3dff>)_
* 签出非活动公司时，__出现“出现错误”错误__
在修复之前，如果长期登录用户公司不再启用，则无法在购物车页面上正确完成注销操作。 现在，如果公司不再可用，则正确执行注销。
  _ACP2E-3541 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/df92debe>)_
* 当我们“使用多个地址签出”时，__地址选择未保存__
在取消多送选项时进行修复之前，在恢复为多送时不会预先选择地址。 现在，默认地址将替换为多送货屏幕中所做的选择之一。
  _ACP2E-3646 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/6ea61121>)_

### 购物车和结帐、SEO

* 从辅助网站购买时，__电子邮件中的礼品卡代码URL不正确__
以前，非默认商店的多商店设置和礼品卡始终将礼品卡报销申请重定向到默认网站。 应用此修复后，电子邮件会将礼品卡报销申请链接重定向到正确的范围或网站。
  _ACP2E-3699_

### 购物车和结帐、送货

* __[Mainline]购物车价格规则未遵守多发服务__
在实施此更正之前，当应用子选择条件并启用免费配送时，多配送产品的购物车价格规则无法正确应用。 但是，由于应用了校正，因此多件运输购物车的购物车价格规则现在按预期运行。
  _ACP2E-3666 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/b12ffe36>)_

### 目录

* __具有相同查询的相同页面出现重复的缓存fpc__
现在，系统可正确识别并使用相同的全页缓存(FPC)来查找查询参数相同的页面，而不管其顺序或尾随字符如何。 这可以防止页面缓存文件夹大小不必要的增加。 以前，如果查询参数的顺序不同或存在尾随字符，系统会为同一页面创建不同的FPC标识符，从而导致页面缓存文件夹大小增加。
  _AC-10722 - [GitHub问题](https://github.com/magento/magento2/issues/38269) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/38270>)_
* __缺少catalog_product_entity_int表中所需列的索引__
在catalog_product_entity_int表中添加了缺少的所需列的索引
  _AC-10844 - [GitHub问题](https://github.com/magento/magento2/issues/38315) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/38316>)_
* __产品页面因url重写而出错__
现在，当我们重写URL时，产品页面加载成功
  _AC-2950 - [GitHub问题](https://github.com/magento/magento2/issues/35371) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39670>)_
* 将产品添加到类别&#x200B;__时出现__[&#x200B;云]错误
现在，通过弹出网格将产品添加到类别时，分页和记录计数标签可正常工作。 以前，如果仅加载一个页面的项目等于页面大小，则会导致项目选择下拉列表出现问题。
  _ACP2E-3526_
* MAGE_INDEXER_THREADS_COUNT出现&#x200B;__indexer_update_all_views cron错误__
修复了MAGE_INDEXER_THREADS_COUNT > 2和客户区段索引器的问题
  _ACP2E-3538 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/9608ca21>)_
* 在页面生成器产品小组件条件中添加“条件组合”时出现&#x200B;__异常__
通过添加检查以跳过缺失或不完整的条件，此问题已得到修复。 以前，由于处理系统中不完整的条件，这会导致生成错误日志。
  _ACP2E-3545 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/11be3dff>)_
* __加载属性集时浏览器崩溃__
如果产品属性超过4千个，则浏览器不会再在属性集编辑页面上崩溃
  _ACP2E-3633 - [GitHub问题](https://github.com/magento/magento2/issues/38810) - [GitHub代码贡献](<https://github.com/magento/magento2/commit/b12ffe36>)_
* 未为新存储创建&#x200B;__[云]产品URL重写：上线阻止程序__
已成功创建新商店的产品URL重写。
之前操作因内存泄漏或超时而结束。
  _ACP2E-3669 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/df92debe>)_
* __属性默认值不适用于选项__
以前，当我们更改product select属性的默认值时，它会显示为具有先前值的数组元素。 应用此修复后，当我们更新产品属性值时，它将在eav_attribute表中保存为单个元素。
  _ACP2E-3688 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/520f9e30>)_
* 由于千位分隔符，__编辑时礼品卡验证失败__
修复了在礼品卡金额为1000及更高时礼品卡产品类型保存的问题。
  _ACP2E-3704_

### 目录、GraphQL、搜索

* __产品graphql在类别聚合中返回了禁用的类别__
修复后，不会为产品GraphQl请求返回禁用的类别。
  _ACP2E-2885 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/b12ffe36>)_

### 目录、产品

* __[随机错误]未加载Fotorama库__
现在，系统可确保Fotorama库已正确加载，从而允许所有附加的图像按预期显示在图像库中。 以前，由于Fotorama库未正确加载的问题，因此仅显示第一个图像。
  _AC-12124 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/45b51c9c>) - [GitHub代码贡献](<https://github.com/magento/magento2/commit/27217d0e>)_

### 内容

* __将csp_whitelist.xml置于主题中不起作用，并会产生间歇性问题__
按网站区域实施了CSP白名单缓存。
  _AC-13069 - [GitHub问题](https://github.com/magento/magento2/issues/38933) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39672>)_
* __错误：加载产品时管理内容pagebuilder的“Magento_Catalog/js/validate-product”出现脚本错误__
此PR修复了使用products条件编辑pagebuilder时catalogAddToCart出现脚本错误
  _AC-13891 - [GitHub问题](https://github.com/magento/magento2/issues/39604) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39677>)_
* __阻止具有相同标识符的小组件中的选择__
现在，当我们具有相同的标识符块时，系统可以在创建构件时正确处理选择块
  _AC-14132 - [GitHub问题](https://github.com/magento/magento2/issues/39692) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39722>)_
* __未考虑表前缀__
  _AC-14556 - [GitHub问题](https://github.com/magento/magento2/issues/39847) - [GitHub代码贡献](<https://github.com/magento/magento2/commit/1bc2d6d0>)_
* __无法上载宽度相对较小的图像__
系统不再无法以相对于其高度的相对较小的宽度来调整图像大小。
  _ACP2E-3558 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/9608ca21>)_
* __远程存储路径样式配置的配置路径不正确__
修复后，设置远程存储路径样式配置将影响实际的AWS S3路径样式配置。
  _ACP2E-3734 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/df92debe>)_

### 框架

* __正在完成已禁用模块的代码。__
此拉取请求转义在代码编译之前禁用了模块。
  _AC-10933 - [GitHub问题](https://github.com/magento/magento2/issues/38241) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39723>)_
* __Magento_Theme title.phtml模板对于PHP 8.2__无效
此拉取请求修复了使用null标题创建的CMS页的问题，如Php 8.x中的，将null传递给trim()会引发异常：已弃用的功能： trim()：将null传递给string类型的参数#1($string)
  _AC-12856 - [GitHub问题](https://github.com/magento/magento2/issues/39092) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39398>)_
* __在将文件存储用于锁定提供程序时，我们会获得不断增长的文件目录，并且不会进行任何清理__
此拉取请求引入了一个新的cronjob，每天运行一次，并搜索过去24小时内未修改并因此可安全移除的锁定文件。 这将使锁定文件目录的内容处于控制之下。
只有当锁提供程序配置为使用文件时，此cronjob才会执行某些操作，而不是当使用其他文件之一时（数据库 — 默认、zookeeper或缓存）
  _AC-13367 - [GitHub问题](https://github.com/magento/magento2/issues/39369) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39372>)_
* __[问题]清理：不使用方法调用中的void返回值。__
此PR会进行细微的清理。 有时我们调用不会返回任何内容(void)的方法，然后使用该结果值。 其实并不需要。
  _AC-13664 - [GitHub问题](https://github.com/magento/magento2/issues/39524) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39516>)_
* __[问题] [PHPDOC]修复Magento\Framework\Message\ManagerInterface__的错误phpdoc
此PR修复了\Magento\Framework\Message\ManagerInterface的错误phpdoc并删除了\Magento\Framework\Message\Manager中的所有重复phpdoc（使用inheritdoc syntaxe）。
  _AC-14312 - [GitHub问题](https://github.com/magento/magento2/issues/39593) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39153>)_
* __从composer.json中删除了测试版最低稳定性__
从composer.json中删除了测试版最低稳定性
  _AC-14450 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/1cbbf187>)_
* 应通过环境变量&#x200B;__设置__allow_parallel_generation
修复后，“MAGENTO_DC_CACHE_ALLOW__PARALLEL_GENERATION”环境变量可用于设置“allow_parallel_generation”配置。
  _ACP2E-3673 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/b12ffe36>)_
* __[Cloud]在Magento 2中使用db_schema.xml文件将表列类型从Int更改为Decimal会导致错误__
无法正确更改列数据类型。 以前，它会引发错误：不允许使用属性“identity”。
  _ACP2E-3709 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/df92debe>)_
* 在Adobe中支持&#x200B;__新货币(XCG)__
加勒比盾(XCG)被添加到货币列表。
  _ACP2E-3790 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/520f9e30>)_

### GraphQL

* __GraphQL订单响应不包含异常消息__
还原以前以不同格式返回错误的更改。 现在，以一致的方式返回了潜在错误，而不会破坏GraphQL架构。 应将其添加为已知BIC，由PM批准此处：https://jira.corp.adobe.com/browse/ACP2E-3399?focusedId=45248897&amp;page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-45248897
  _ACP2E-3399 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/9608ca21>)_
* 订单投放的&#x200B;__GraphQL响应已部分本地化__
placeOrder GraphQl突变返回的错误未完全本地化。 现在，在多语言上下文中，错误会被正确翻译。
  _ACP2E-3506 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/9608ca21>)_
* __并发调用对GraphQL API重新排序 — 将相同的产品添加到不同的行__
修复了以下问题：同时调用重新排序GraphQL API会导致相同的产品被添加为不同的行，进而导致数据不一致。
  _ACP2E-3774 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/c8ba4ab1>)_
* __updateCustomerEmail GraphQL突变（更改电子邮件地址）未触发电子邮件通知__
以前，成功更新客户帐户中的电子邮件地址后不会向客户发送电子邮件。 应用此修复后，客户现在会在成功更新其电子邮件地址后收到电子邮件通知。
  _ACP2E-3785 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/c8ba4ab1>)_
* __动态属性未通过updateGiftRegistry变异在礼品注册表中更新__
以前，在通过updateGiftRegistry突变进行此修复之前，不会通过GraphQL突变来修改或更新礼品注册表的自定义属性。 应用此修复后，可通过updateGiftRegistry变异成功更新礼品注册表的动态属性。
  _ACP2E-3805 - [GitHub问题](https://mcstaging.briscoes.co.nz/)_

### 导入/导出

* __[问题] Copyedit：将“coping”更改为“coping”__
PR修复了次要复制以更正“copying”的拼写
  _AC-13300 - [GitHub问题](https://github.com/magento/magento2/issues/39311) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39307>)_
* __REST端点产品导入Json未验证必填字段__
现在，通过导入流程（管理员或API）创建新产品时，需要填写名称字段。 在修复之前，您可能创建了无名称的新产品，这会破坏管理员界面并创建无效产品。
  _ACP2E-3660 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/df92debe>)_
* __导出过程中缺少网站筛选器选项__
现在，在创建产品导出时可以按网站过滤产品。
  _ACP2E-3720 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/520f9e30>)_
* __AC-13913重复 — 静态属性异步清理。__
修复后，在创建\Magento\CatalogImportExport\Model\Import\Product\Type\AbstractType的众多实例时，不会出现“未定义数组键“apply_to”错误。
  _ACP2E-3752 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/520f9e30>)_

### 库存/MSI

* __结帐时地址更改时，__商店代答未遵循最大搜索半径
现在，如果配送地址发生更改，“店内提货”中预先选定的商店将会更新。 以前，预先选择商店后，即使新送货地址不在所选商店的半径内，商店也不会更改
  _ACP2E-3728 - [GitHub代码贡献](<https://github.com/magento/inventory/commit/07620383>)_

### 订购

* __无法对不可为空的字段\&amp;amp；quot；AppliedCoupon.code\&amp;amp；quot；返回空值；意外问题__
  _AC-14484 - [GitHub问题](https://github.com/magento/magento2/issues/39841) - [GitHub代码贡献](<https://github.com/magento/magento2/commit/97b2ea42>)_
* __[云]升级到magento 2.4.6-p7__后，某些内联Javascript不起作用
单击admin中“Add to Order by SKU”（按SKU添加至订单）中的“delete”（删除）按钮现在会删除SKU。 以前，单击“按SKU添加到订单”中的“删除”按钮不会删除SKU。
  _ACP2E-3515_
* sales_order表&#x200B;__中的__gift_cards序列化数据不一致
sales_order表中的gift_cards数据现在已正确序列化。 以前，每次更新订单时都会序列化。
  _ACP2E-3662_

### 订单，定价

* 创建返回时，__管理员在上显示的货币符号不正确__
在使用不同货币（欧元/美元/英镑）的多网站设置中，管理员的退货产品选择页面现在显示正确的货币符号。 以前，它显示默认货币符号。
  _ACP2E-3658 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/df92debe>)_

### 其他开发人员工具

* __灯塔辅助功能失败__
系统现在通过，辅助功能得分为100
  _AC-12783 - [GitHub问题](https://github.com/magento/magento2/issues/39054) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39164>)_
* __禁用captcha storefont配置仍加载captcha js文件__
在禁用验证码时，系统现在不加载验证码js文件
（存储）
  _AC-14267 - [GitHub问题](https://github.com/magento/magento2/issues/32987) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39154>)_

### 包装

* __[打包]修复magento/magento-coding-standard依赖关系+ page-builder__
  _ACPLTSRV-6383_

### 支付

* __[问题]修复脱机发票捕获(404)__
它修复了从Magento管理员处捕获离线支付方法的发票时出现404页面错误的问题
  _AC-13336 - [GitHub问题](https://github.com/magento/magento2/issues/39298) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39297>)_

### 性能

* __类别权限模块可能阻止缓存__
第三方控制器现在使用客户区段正确缓存
  _ACP2E-3721_

### 产品

* __产品收藏集 — 当收藏集可能加载或将加载时，addMediaGalleryData调用getSize（可以使用count避免额外的DB查询）__
如果在调用Product Graphql时已经加载了产品收藏集，并且其中包含media_gallery字段，则此PR会减少使用count()进行的额外查询调用。
  _AC-13055 - [GitHub问题](https://github.com/magento/magento2/issues/39111) - [GitHub代码贡献](<https://github.com/magento/magento2/pull/39681>)_
* __[2.4.8]未找到cron作业catalog_product_alert__的回调
  _AC-14494 - [GitHub问题](https://github.com/magento/magento2/issues/39800) - [GitHub代码贡献](<https://github.com/magento/magento2/commit/1bc2d6d0>)_
* 当通过pagebuilder包含产品小部件时，__执行缓慢查询__
优化了用于创建产品小部件（包括产品SKU）的查询。
  _ACP2E-3449 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/df92debe>)_
* __产品图像在添加为可配置产品时未调整大小__
以前，通过管理面板中的配置添加的映像不符合最大上传大小限制，这可能导致不一致和管理挑战。 现在，已实施了一项修复，以确保在上传期间自动调整图像大小以符合最大大小限制，从而简化流程和维护系统标准。
  _ACP2E-3504 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/df92debe>)_

### 配送

* __文档应该针对%实施进行更新，这在官方文档__中不正确
更新了有关DHL Rest API支持的devdoc
  _AC-14507_
* __[DHL] — 处理REST与XML API集成之间的常规大小设置和价格差异中的可选维度__
  _AC-14601 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/1e3bde4c>)_
* 创建UPS装运标签时出现&#x200B;__异常__
修复了警告：在UPS配送标签创建期间数组到字符串的转换
  _ACP2E-3676 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/b12ffe36>)_

### 暂存和预览

* __预览计划更新将按字母顺序打开第一个商店视图，而不是感兴趣的商店视图__
在修复之前，计划更新的预览在第一个商店视图中按字母顺序打开，而不是在分配的商店视图中打开。
修复后，预览现在会在分配给CMS块暂存更新的存储视图中正确打开。
  _ACP2E-3671 - [GitHub代码贡献](<https://github.com/magento/magento2/commit/b12ffe36>)_
* __Staging_apply_version Cron行为问题 — 已忽略special_price__
完成此修复后，通过计划的产品更新更改特殊价格后，将重新计算报价总额。
  _ACP2E-3674_

### 税金

* 从购物车中移除礼品包装时，__税额未更新__
  _AC-14637_
