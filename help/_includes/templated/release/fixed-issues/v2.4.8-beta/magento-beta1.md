---
source-git-commit: b3059a262fe6144bca47fc9fb1b4d201b38af3ba
workflow-type: tm+mt
source-wordcount: '14735'
ht-degree: 0%

---
# Magento Open Source发行说明(v2.4.8-beta1)

## v2.4.8-beta1中的亮点

以下49项功能亮点适用于Magento Open Source 2.4.8版本。

### 框架

* _AC-10721_：将league/flysystem Composer依赖项升级到最新版本
   * _修复说明_：将2.x league/flysystem Composer依赖项升级到最新版本3.x
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/91cb4d46>
* _AC-11495_： 2.4.8-beta1平台组件升级
* _AC-11673_：调查php-amqplib/php-amqplib最新版本
   * _修复说明_：更新了php-amqplib/php-amqplib的最新版本：^3.x
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-11723_：为phpunit 10兼容性重构集成测试框架 — 未找到IntegrationTest.php
   * _修复注释_： PHPUnit 9已升级到PHPUnit 10，并且更改了Adobe Commerce的集成和WebAPI测试框架。 PHPUnit 10更改向后兼容。
   * _GitHub代码贡献_： &lt;https://github.com/magento/magento2/ （内部，未合并）>
* _AC-11813_：用于phpunit 10兼容性的WebApi测试框架 — 与SOAP和B2B模块的RabbitMQ连接相关的问题
   * _修复注释_： PHPUnit 9已升级到PHPUnit 10，并且更改了Adobe Commerce的集成和WebAPI测试框架。 PHPUnit 10更改向后兼容。
   * _GitHub代码贡献_： &lt;https://github.com/magento/magento2/ （内部，未合并）>
* _AC-11816_：添加与MySQL 8.4 LTS的兼容性
* _AC-11911_：迁移到上传库后，jQuery/fileuploader css清理
   * _修复注释_：已移除jQuery/fileUploader库，因为它已迁移到Uppy库
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-11995_：添加与MySQL 8.4 LTS for Magento CE的兼容性
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12014_：将elasticsearch 8模块标记为已弃用
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
   * _修复注释_：将moment.js系统依赖关系升级到最新的次要版本2.30.1
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12032_：添加与MySQL 8.4 LTS for EE的兼容性
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12034_：添加与MySQL 8.4 LTS for B2B的兼容性
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
* _AC-12268_：将League/Flysystem Composer依赖项升级到最新版本
   * _修复说明_：将2.x league/flysystem Composer依赖项升级到最新版本3.x
* _AC-12576_：调查MySQL 8.4 LTS的自动化测试失败
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12595_：添加与MariaDB 11.4 LTS For EE的兼容性
   * _修复注释_：添加了对Adobe Commerce和扩展的MariaDB 11.4支持
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12693_：使用MySQL 8.4 LTS调查数据迁移工具(DMT)
* _AC-12715_：更新升级到最新版本的Laminas编辑器依赖项
   * _修复注释_：系统现在支持最新版本的Laminas编辑器依赖项：
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validator
确保兼容性和最新功能。 以前，更新到这些依赖项的最新版本可能会导致向后不兼容问题和测试失败。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12752_：添加与MariaDB 11.4 LTS For Data Migration工具的兼容性
   * _修复注释_：添加了对Adobe Commerce和扩展的MariaDB 11.4支持
* _AC-12823_：调查在组件升级期间由于phpunit修补程序更新而导致的单元测试失败
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12897_： SVC和EAT工具与MySQL 8.4的兼容性
* _AC-12898_： UCT工具与MySQL 8.4的兼容性
   * _修复说明_：升级兼容性工具(UCT)现在与MySQL 8.4兼容，从而确保在此版本上运行的实例的顺利操作和兼容性检查。 之前，UCT工具未测试和验证是否与MySQL 8.4兼容。
* _AC-9749_： PHPUnit 10升级
   * _修复说明_：已将phpunit/phpunit编辑器依赖项更新为兼容版本 — “phpunit/phpunit”：“10.x”

### 安装和管理

* _AC-6819_：默认情况下将索引器设置为“按计划更新”

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
* _AC-12480_： Elasticsearch 7和8选项应在管理配置中随附已弃用。
   * _修复注释_：“管理员配置”选项中的Elasticsearch 8选项将显示已弃用的文本，以告知用户不再建议使用Elasticsearch 8选项。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0611e750>
* _AC-12481_：在管理员配置中选择Elasticsearch选项时添加文本注释
   * _修复说明_：添加了文本说明，以便Adobe Commerce管理员用户知道Adobe不再支持elasticsearch，并且已弃用。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0611e750>
* _AC-12870_： SVC和EAT工具与MariaDB 11.4的兼容性
   * _修复注释_： SVC和EAT工具与MariaDB 11.4的兼容性
* _AC-12876_： UCT工具与MariaDB 11.4的兼容性
* _LYNX-374_：通过GraphQL进行文档电子邮件确认
* _LYNX-376_：记录在GraphQL中获取reCAPTCHA的配置
* _LYNX-409_：更新购物车项目突变的数据库查询优化

### 安全性

* _AC-11041_：从2024年6月版本开始，对2.4.8-beta1版的安全性进行了改进
* _AC-11864_：从2024年8月版本开始，对2.4.8-beta1版的安全性进行了改进
* _AC-12346_：从2024年10月发行版开始，对2.4.8-beta1版的安全性进行了改进
* _AC-12691_： [2.4.8-beta1]客户更新REST API终结点无法正常工作
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4102373>，<https://github.com/magento/magento2/commit/a4102373>

### UI框架

* _AC-12726_： [2.4.8-beta1] TinyMCE 5迁移到TinyMCE 7
   * _修复说明_：已将TinyMCE 5迁移到TinyMCE 7.3.0以作为Adobe Commerce的支持版本，以前的系统使用的是5.10.2，该版本已过时并报告了安全漏洞
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12825_： [2.4.8-beta1] TinyMCE 5迁移到TinyMCE 7页面生成器
   * _修复说明_：已将TinyMCE 5迁移到TinyMCE 7.3.0以作为Adobe Commerce的支持版本，以前的系统使用的是5.10.2，该版本已过时并报告了安全漏洞
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12844_： [2.4.8-beta1] TinyMCE 5迁移到TinyMCE 7 - Magento2-infra — 禁止使用的字词
   * _修复说明_：已将TinyMCE 5迁移到TinyMCE 7.3.0以作为Adobe Commerce的支持版本，以前的系统使用的是5.10.2，该版本已过时并报告了安全漏洞
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12901_： Require.js升级到最新版本2.3.7(安全漏洞CVE-2024-38999)
   * _修复注释_：已将require.js更新到最新版本2.3.7。在以前的版本中报告了安全漏洞
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b34c0a75>

## 修复了v2.4.8-beta1中的问题

我们已在Magento Open Source 2.4.8核心代码中修复了253个问题。 此版本中包含的已修复问题的子集如下所述。

### API

* _AC-10042_： /V1/transactions REST API在parent_txn_id = txn_id时返回错误
   * _修复注释_：系统现在可以正确处理父交易ID与交易ID相同的父概念交易和子概念交易，从而防止在查询/V1/transactions REST API端点时发生无限循环。 以前，由于超出最大执行时间，此方案会导致致命错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_： 2.4.7中的[Graphql]类型问题
   * _修复注释_：在执行GraphQL查询时，系统现在可以正确处理GetCustomSelectedOptionAttributes函数中的整数值，从而防止出现任何与类型相关的错误。 以前，启动使用具有整数参数的GetCustomSelectedOptionAttributes的GraphQL查询会导致类型错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38662>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38663>
* _ACP2E-2927_： [REST API]：为可配置产品添加配置后，在存储视图中使用默认值不会保持选中状态
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
   * _修复注释_：通过允许更改顺序状态（如果该状态仅来自当前状态），该问题已得到解决。 以前，它不会遵循订单状态并阻止任何订单状态中的更改，即使订单状态来自同一状态也是如此。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/93d50f8d>

### 帐户

* _AC-10782_：客户地址表单允许在名称字段中使用随机代码
   * _修复注释_：系统现在验证客户地址表单中“名字”和“姓氏”字段的输入，以防止使用随机代码。 以前，系统允许在这些字段中使用随机代码，而不会引发错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38331>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38345>
* _AC-10990_：我的帐户在保存时添加地址崩溃
   * _修复注释_：系统现在可以正确保存客户地址，即使未显示区域字段也是如此，从而防止在保存过程中崩溃。 以前，尝试添加或编辑没有显示区域字段的地址会导致异常错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38406>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38407>
* _AC-11919_：管理员：页面操作按钮向左浮动而不是向右浮动
   * _修复注释_：系统现在可以将“页面操作”按钮正确对齐管理面板中粘性标题的右侧，从而增强专业外观。 以前，这些按钮错误地浮动到粘性标题的左侧。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38701>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_： magento 2.4.7中的dev:di:info错误
   * _修复注释_：系统现在在执行dev:di:info命令时可正确显示构造函数参数，从而防止出现任何错误。 以前，执行此命令会导致错误，因为参数中的类型不匹配。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38740>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-6071_：客户已登录，但在前端显示404错误。
   * _修复注释_：现在，当客户登录时，店面客户仪表板页面会按预期加载。 以前，客户可以登录，但此页面显示404错误。 [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _GitHub问题_： <https://github.com/magento/magento2/issues/35838>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_：无法在管理员编辑客户部分中保存客户属性信息；
   * _修复注释_：现在已按管理员客户编辑表单的网站范围正确实施客户的商店ID。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/488c1034>

### 管理员UI

* _AC-11588_：在导入具有替换行为的产品时，数据验证成功且存在导入按钮
   * _修复注释_：系统现在可以正确验证数据，并在产品导入过程中使用“替换”行为隐藏“导入”按钮，以防止任何意外的数据替换。 以前，系统会错误地验证数据并显示“导入”按钮，从而导致潜在的数据不一致。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_： [错误] Magento 2.4.7不允许使用大写字母文件扩展名的产品照片。
   * _修复注释_：系统现在接受带大写字母文件扩展名的产品图像上载，从而确保产品创建过程顺畅。 以前，使用大写字母文件扩展名的图像上传被拒绝，从而迫使用户将文件扩展名更改为小写。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38831>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-6975_： [问题]将默认索引器模式设置为“计划”
   * _修复注释_：所有新索引器默认处于&#x200B;**[!UICONTROL Update by Schedule]**&#x200B;模式。  以前，默认模式为&#x200B;**[!UICONTROL Update on Save]**。 现有的索引器不受影响。 [GitHub-36419](https://github.com/magento/magento2/issues/36419)
   * _GitHub问题_： <https://github.com/magento/magento2/issues/36419>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0b410856>
* _AC-7700_： [问题]在mview取消订阅时删除索引器更改日志表
   * _修复注释_：当索引从“按计划更新”切换为“保存时更新”时，系统现在会自动删除未使用的changelog表，并将索引标记为无效，以确保不会丢失任何条目。 以前，将索引切换为“保存时更新”会在系统中保留未使用的changelog表，并将所有更改的索引标记为“有效”。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/29789>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/25859>
* _AC-9843_： i18n：collect-phrases破坏翻译完整性
   * _修复注释_： `bin/magento i18n:collect-phrases -o`命令现在可以从JavaScript和.phtml文件中正确收集和添加新短语，确保翻译文件能准确反映翻译。 以前，系统无法在翻译文件中包含来自JavaScript文件的多行翻译短语以及来自.phtml文件的短语，从而导致翻译不完整或不正确。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2787_：存储视图名称中的撇号已替换为&#39;
   * _修复注释_：网格的存储视图筛选器现在正确显示撇号
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38395>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_： Favicon上传无法验证.ico文件
   * _修复注释_：文件验证错误已更新为“文件验证失败。 请验证存储配置中的图像处理设置。” 以前，它只是“文件验证失败”。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_： PageBuilder中的图库显示的是旧的图像缩略图，而不是新上传的图像
   * _修复注释_：为通过页面生成器内容中的媒体集删除并重新上传的具有相同名称的图像，重新生成图像预览。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/001e5188>，<https://github.com/magento/magento2-page-builder/commit/60140cd2>
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

### 管理员UI，性能

* _ACP2E-3169_：更新到2.4.5-p8后，从管理员创建订单时出现500错误
   * _修复注释_：以前，启用HTML缩小功能时，无法下达管理员的订单。 现在，启用HTML缩小功能后，管理员的订单就可以成功下达。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b21e5d91>

### 管理员UI，配送

* _ACP2E-2519_：优惠券代码计数不会在   如果订单是多次发运的，则“管理优惠券代码”选项卡中的“已用时间”列。
   * _修复注释_：以前，在多次发运下订单时，在“管理优惠券代码”选项卡的“使用时间”列中，优惠券代码计数不会更新。 现在，正确计数会同时显示在“使用时间”中，以反映多次配送的所需值。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/4745100c>

### Analytics/报表

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

### Analytics/报表，B2B

* _ACP2E-2300_： B2B - Sitemap包括未分配给共享目录的产品/类别
   * _修复注释_：将Sitemap生成的类别和产品限制为仅分配给公共共享目录和/或目录类别权限设置的类别和产品。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics/报表、云

* _ACP2E-3067_： Magento放弃大部分New Relic cron交易#34108
   * _修复注释_： AC正在向NewRelic正确报告cron作业相关的事务。 以前，某些cron作业相关事务在NR中显示为“OtherTransaction/Action/unknown”
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/35b1b1da>

### B2B

* _ACP2E-3044_：“我的订单”部分上有不必要的边框
   * _修复注释_：以前创建了一个附加容器（订单引用），该容器应用了附加的CSS类，这会导致“我的订单”部分中的订单编号下方出现不必要的边框行，而现在该订单编号不可见。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/9af794a4>

### B2B，框架

* _AC-9607_：筛选公司网格，然后尝试网格CSV导出将失败并引发异常
   * _修复注释_：系统现在允许成功CSV导出管理面板中的公司网格数据，即使应用了“未付余额”和“公司类型”等过滤器也是如此。 以前，应用某些过滤器并尝试导出网格数据会导致失败并引发异常。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/44cef3a9>

### Braintree

* _BUNDLE-3367_：通过LPM付费
   * _修复说明_：系统现在会在首次加载时正确呈现本地支付方式(LPM)，即使登录客户的送货地址和帐单地址不匹配也是如此，从而确保结账过程顺利进行。 以前，客户的送货地址和账单地址不匹配会导致LPM无法呈现，进而在结账期间导致潜在中断。
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3368_：可使用Virtual作为子产品进行配置
   * _修复注释_：系统现在允许对具有虚拟子产品的可配置产品使用快速付款方法，以确保顺利的结账过程。 以前，当将带有虚拟子产品的可配置产品添加到购物车时，快速付款方法不可用。
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3369_： CVV验证失败错误
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3370_：通过帐户区域进行保险存储问题247
   * _修复注释_：系统现在允许客户跨多个网站保存新卡或PayPal帐户信息，而不会遇到授权错误。 以前，客户无法跨不同网站保存新的支付方式，并收到授权错误消息。
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3371_：从其他国家发送到地址
   * _修复注释_：系统现在允许处理从其他国家发往某个地址的交易记录，而不会出错，从而确保结账过程顺利进行。 以前，尝试从其他国家/地区发送地址会导致控制台错误，尽管前端没有明显错误。
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3372_： Credit Card - Teardown函数
   * _修复注释_：现在，当客户从付款页导航回送货页时，系统会正确处理Braintree PayPal组件的拆卸，从而防止任何错误并确保PayPal Express按钮正确呈现。 以前，在尝试拆卸Braintree PayPal组件时，从付款页面导航回送货页面有时会导致错误。
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3373_： PayPal Express的配送回拨
   * _修复说明_：系统现在可在PayPal Express模式中正确显示可用的配送方式，允许客户在继续查看页面或完成交易之前选择其首选配送方式。 以前，在PayPal Express模式中无法选择配送方式，这要求客户在完成交易之前，在单独的审核页面上选择配送方式。
   * _GitHub代码贡献_： <https://github.com/magento/ext-braintree/pull/204>

### 购物车和结帐

* _AC-10660_：在比较产品页面中将产品添加到购物车时，未正确处理异常
   * _修复注释_：现在，在从比较产品页将产品添加到购物车时，系统可正确处理异常，并在控制器中显示消息管理器消息。 以前，异常会导致返回JSON编码页面，而不是正确捕获和处理该页面。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38200>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38257>，<https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_： GTag未发送交易价格和总计。
   * _修复注释_：启用GTag后，系统现在可正确地向Google标记发送交易价格和总计，从而确保对电子商务数据的准确跟踪。 以前，该货币作为“所有”订单的一部分错误地发送，而不是与单个订单相关联。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37348>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37504>，<https://github.com/magento/magento2/pull/37349>
* _AC-11641_： [问题] [签出] Depend指令已在失败的付款电子邮件模板中更新
   * _修复注释_：系统现在会从虚拟产品的付款电子邮件模板中正确忽略送货地址和送货方式，确保电子邮件中仅包含相关信息。 以前，虚拟产品付款失败的电子邮件错误地包含送货地址和送货方法。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/32781>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/32511>
* _AC-11876_：[问题] 2.4.7中的销售规则回归
   * _修复注释_：系统现在可以正确验证销售规则，防止在产品条件与任何产品名称不匹配时将优惠券代码应用到购物车。 以前，即使产品条件与任何产品名称不匹配，也可以应用销售规则并根据运费金额提供折扣。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38671>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11993_： [问题]更改邮政编码后，加载程序将阻止配送方式，配送费率验证规则
   * _修复注释_：系统现在可以正确处理自定义配送方式，而不使用运费验证规则，从而确保在结帐期间在配送地址中更改邮编后，加载程序不会阻止配送方式。 以前，在结帐期间更改装运地址中的邮政编码会导致加载程序阻止装运方法，并且在使用没有装运费率验证规则的自定义装运方法时不会消失。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38742>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_：优惠券代码功能在Magento 2.4.7上的签出页面中无法正常工作
   * _修复注释_：系统现在为虚拟和可下载产品在结账页面上启用折扣代码/优惠券输入字段，允许用户按预期应用折扣代码。 以前，折扣代码/优惠券输入被禁用，并且按钮标题文本显示为“取消优惠券”，阻止用户应用折扣代码。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38826>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/1bafc571>
* _AC-8103_：地址呈现器中的翻译VAT
   * _修复注释_：系统现在允许地址渲染器中文本“VAT”、“T”、“F”的翻译，使用户可以将这些术语翻译为商店的特定语言。 以前，这些术语无法翻译，因此用户必须采用解决方法。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/36942>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36943>
* _ACP2E-2055_：具有相同报价ID的重复订单，时间差很小
   * _修复注释_：修复了Adobe Commerce客户遇到使用相同QuoteID下重复订单的问题
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2470_：在结帐步骤中清理了永久购物车
   * _修复说明_：修复后，在未登录时结账期间选择付款方式不会终止永久会话。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_：重新排序将未分配的产品添加到购物车
   * _修复注释_：以前，对于不同的商店，可以从其他商店对产品重新排序。 仅应用此修复后，在启用客户帐户共享时，可对同一范围产品重新排序
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_：在admin中，从右侧选择商品和“移至购物车”时，左侧的“购物车”未更新
   * _修复注释_：选择项目时，左侧的“购物车”将更新，而管理员右侧的“移至购物车”将更新。 以前，此功能不起作用，因为转换后的购物车项目不会从会话中清空。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2646_： [Cloud]销售规则未应用于第一笔多发订单
   * _修复注释_：修复之后，将正确显示同一多送货报价单中每个订单的折扣。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_： [Cloud]将相同产品添加到购物车的生产并行请求在购物车REST API中产生了两个不同的项目
   * _修复注释_：系统现在可正确处理多个并行请求，以将同一产品添加到购物车中，并添加到单个行项目，从而防止为同一SKU创建单独的行项目。 以前，并行请求通过REST API将同一产品添加到购物车会导致同一SKU出现多个行项目。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2704_：获取无法发送Cookie。 尝试重新排序时“图像消息”的大小
   * _修复注释_：重新排序过程现在不会生成自己的错误。 它将依赖购物车列表的内置项目检查。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_：结帐时未选择默认送货地址
   * _修复注释_：在启用的地址搜索的上下文中正在选择默认送货地址事件。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_：[CLOUD] graphql addProductsToCart api问题，带有自定义选项
   * _修复注释_： GraphQL使用不同的自定义选项将相同的产品正确地添加到购物车
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2923_：签出为新客户时，向帐户添加了多个地址
   * _修复注释_：现在，系统仅在创建订单失败时保存一次新客户地址，从而防止在出现订单放置错误时创建多个相同的地址。 以前，每次尝试下订单时，无论是否成功创建了订单，系统都会保存一个新地址。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/001e5188>，<https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_：通过访客订单重新订购客户订单导致购物车为空
   * _修复注释_：以前，通过“订单和退货”页面重新订购时，客户被重定向到登录页面。 应用此修复后，进行重新订购时，注册的客户会被正确重定向到“查看购物车”页面。 该流的工作方式与访客客户相同。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_：角色资源有限的管理员用户无法查看购物车
   * _修复注释_：以前，受限制的管理员无法从相关网站的管理员面板中看到放弃的购物车。 应用此修复后，受限管理员可以从管理员面板中看到放弃的购物车。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d1f7dc95>

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
   * _修复注释_：现在，当产品从简单产品转换为可配置产品时，系统会正确移除产品的层价格，从而确保前端准确显示价格。 以前，当产品从简单产品转换为可配置产品时，不会删除可配置产品的层价格，从而导致显示的价格不匹配。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38390>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38427>
* _AC-11804_：非默认存储审阅中的类别描述WYSIWYG为空
   * _修复注释_：在商店视图级别编辑类别时，系统现在会在WYSIWYG编辑器中正确保存并显示类别描述。 以前，在商店视图级别保存类别描述后，WYSIWYG编辑器将显示为空。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38622>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38623>
* _AC-12076_： [问题]修复分层导航上筛选器项的措辞
   * _修复注释_：系统现在正确使用了分层导航筛选器项中的“item”和“items”两词，从而增强了筛选器描述的清晰度和准确性。 以前，这些词语使用不正确，这可能导致导航过滤器选项的用户混淆。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38789>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37852>
* _AC-12164_：自定义选项的日期和时间格式不起作用
   * _修复注释_：系统现在可以将配置的日期格式正确应用于类型为“日期”的产品自定义选项，确保日期格式在前端正确显示。 以前，对日期格式配置的更改不会反映在日期类型的产品自定义选项的前端。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/32990>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38925>
* _AC-6738_：eav_attribute_option_value表上缺少唯一键
   * _修复注释_：系统现在在“eav_attribute_option_value”表的“option_id”和“store_id”列中包含唯一键，以防止可能有一个选项具有同一存储视图的多个值。 以前，错误代码可能会导致同一商店视图的选项具有多个值，从而导致在编辑产品或属性时出现问题。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/24718>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/28796>
* _AC-8297_： [问题]使用类别产品索引器的可见性类，而不是硬编码值
   * _修复注释_：系统现在使用类别产品索引器的可见性类，而不是硬编码值，增强了模块性。 以前，在类别产品索引器中使用硬编码值，限制了灵活性和适应性。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37200>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37199>
* _AC-9375_：新产品小部件中的货币代码未更改
   * _修复注释_：现在，当货币在前端发生更改时，系统可正确更新新产品小组件中的货币代码，从而确保网站中货币显示的一致性。 以前，更改前端中的货币不会影响新产品小部件中显示的货币代码。
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
* _ACP2E-2874_：使用捆绑包产品时，前端类别页面显示空插槽
   * _修复注释_：在当前存储上下文中不可销售的捆绑产品不再编制索引。
   * _GitHub代码贡献_： <https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2905_：[Cloud]多网站架构中的报价问题
   * _修复注释_：以前，使用不同货币和客户组的多网站架构无法正确为商店应用折扣。 实施此修复后，具有不同客户组价格折扣的多网站架构将成功应用于不同的商店。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38506>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_： dynamic-rows.js：658编辑捆绑产品时未捕获的TypeError： dataRecord.slice
   * _修复注释_：从捆绑包产品中删除选项时，浏览器控制台中没有Javascript错误。
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
* _ACP2E-3100_： New Relic错误日志中不存在[Cloud]图像文件
   * _修复注释_：系统现在将自定义占位符图像同步到本地存储，以确保在使用远程存储(如AWS S3)时正确呈现这些图像。 以前，自定义占位符图像在使用远程存储时无法渲染，从而导致图像显示中断和错误日志。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3126_： [Cloud]产品媒体集GQL响应未按图像位置排序
   * _修复注释_：系统现在可以在GraphQL响应中按位置正确排列媒体集中的项目，确保显示顺序准确。 以前，媒体集中的项目不按位置排序，从而导致显示顺序不正确。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37671>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_：[Cloud]子类别项未显示在管理员后端的小组件编辑中
   * _修复注释_：加载级别5以上的类别时，新构件页面上的类别树不会再出现问题。 以前，在加载树以超过5级类别时缺少某些类别。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/148c3ead>

### 目录、框架

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

### 目录、定价、暂存和预览

* _ACP2E-2672_： [Cloud]特殊价格API端点在同时更新大量产品时返回错误
   * _修复说明_：现在，特价批量更新API将为每个日期范围创建一个促销活动，而不是为每个产品和日期范围创建多个计划更新。 此外，它支持并发API请求，以更快地处理大量SKU。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/f89a447e>

### 目录、产品

* _AC-7050_：编辑产品中的类别选择树与目录 — >类别中的设置顺序不同
   * _修复注释_：系统现在会按照在目录 — >类别中设置的相同顺序，在产品编辑部分中正确显示类别选择树，从而使产品在大目录中的管理更加容易。 以前，产品编辑部分中的类别树按类别创建顺序显示，而不管在目录 — >类别中设置的显示顺序如何。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/36101>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36104>

### 目录，搜索

* _ACP2E-2757_：产品未在类别和搜索中显示，但直接链接正常工作
   * _修复注释_：以前，带price_* attribute_code的Yes/No自定义属性不适用于索引。 进行此修复后，“是/否”自定义属性会按预期工作。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_： [Cloud]某些类别页面上的弹性搜索错误
   * _修复注释_：以前，在提及配置票证后，当我们为多个产品定价0时，会在前端类别页面引发异常。 应用此修复后，当多个产品价格0并且我们在前端加载类别页面时，它不会引发任何异常，并且将成功加载类别页面。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c8931218>

### 云

* _ACP2E-3010_： [Cloud] PHPSESSID正在更改每个POST请求
   * _修复注释_：如果启用了L2 Redis缓存并且客户已从后端更新，则不再为登录的客户在前端区域上重新生成PHPSESSID的POST请求
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6a185204>

### 内容

* _AC-10539_：[问题]，最近查看的小组件中显示价格
   * _修复注释_：系统现在可在“最近查看的产品”构件中正确显示缺货的简单产品的价格，确保所有构件和产品列表页面的一致性。 以前，由于价格加载模板中的条件，缺货的简单产品的价格不会显示在“最近查看的产品”小部件中。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38167>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38159>
* _AC-10596_： [问题] acl.xsd文件中的拼写错误和语法正确
   * _修复注释_：系统现在更正了acl.xsd文件中的拼写错误和语法错误，提高了文档的清晰度和准确性。 以前， acl.xsd文件包含拼写错误和语法错误，这可能会导致混淆。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38061>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38046>
* _AC-10845_： Pagebuilder横幅图像在图库中不可见
   * _修复注释_：系统现在可以正确显示在Pagebuilder图库中新创建的文件夹中上传的横幅图像，从而消除以前的控制台错误。 在此修复之前，如果横幅图像上载到新文件夹中，则不会在图库中显示这些图像，从而导致控制台错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_：更新到2.4.5-p8后“未设置区号”
   * _修复注释_：现在，在启用Magento_CSP模块并将“dev/js/translate_strategy”设置为“embedded”时，系统可成功完成静态内容部署过程，而不会触发“未设置区码”错误。 以前，在这些情况下，静态内容部署过程会失败，并出现“未设置区码”错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38845>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38922>
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
* _ACP2E-2842_：切换到单存储模式 — 全局内容不再出现
   * _修复注释_：在启用单商店模式时，系统现在将商店视图设计配置与网站设计配置同步，确保内容更新在前端可见。 以前，切换到单商店模式会阻止内容更新反映在店面上。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_：页面生成器在尝试添加链接和其他可用性问题时替换图像。
   * _修复注释_：现在单击图像，页面生成器文本元素的wysiwyg编辑器中的链接将在图像、链接配置对话框中加载正确的数据。 现在，在编辑器中添加指向图像的链接也可正常使用。 以前，图像会被替换为链接。
   * _GitHub代码贡献_： <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_：将0字节的图像放在目录中时，旧媒体集无法呈现图像
   * _修复注释_：系统现在可以在不中断功能的情况下处理媒体集中的0字节图像，从而允许按预期显示和选择目录中的其他图像。 以前，如果媒体集中存在0字节图像，则会阻止显示或选择目录中的所有图像。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_：编辑CMS块时页面生成器出错
   * _修复注释_：系统现在可以使用页面生成器正确地保存管理区域中所做的更改，而不会引发错误“页面生成器呈现了5秒钟，并且未释放锁定”。 在浏览器控制台中。 以前，在尝试保存更改时会发生此错误，从而阻止内容成功更新。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/35b1b1da>，<https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_： [CLOUD]购物车分区中没有结帐或编辑购物车的按钮
   * _修复注释_：现在通过小组件将捆绑包产品添加到购物车，并且没有出现错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b21e5d91>，<https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3127_： imagecreatetruecolor()：参数#2 ($height)必须大于0。 无法上传特定图像
   * _修复注释_：解决了通过媒体集上载高度为0的图像时，导致管理员出现错误的问题，并使用sync命令成功同步资产。 以前无法通过媒体集上传图像，并且当特定图像位于媒体集内时，同步命令也会失败。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_： Prototype.js Array.from与Google映射API冲突
   * _修复注释_：Google映射现在可在PageBuilder编辑器中正确呈现。 以前，Javascript错误会导致Google映射无法正确呈现。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/148c3ead>

### 客户/客户

* _AC-12162_：客户创建页面中的“前端 — 出生日期”验证失败
   * _修复注释_：确保在将moment.js系统依赖关系升级到最新的次要版本后，所有验证都应正常工作
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/de4dfb8e>

### 框架

* _AC-10654_： V1/customers/密码端点问题/问题
   * _修复注释_：现在，在通过API处理密码更改请求时，系统会遵守管理GUI中设置的约束，从而防止可能滥用密码重置功能。 以前，API可以在管理GUI中定义的规则之外处理密码更改请求，在已知有效电子邮件时，可能会允许不断重置电子邮件。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38238>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10721_：
   * _修复说明_：将league/flysystem Composer依赖项升级到最新版本
   * _GitHub问题_： &lt;<https://github.com/magento/magento2/commit/91cb4d46>>
   * _GitHub代码贡献_：将2.x league/flysystem Composer依赖项升级到最新版本3.x
* _AC-10838_：目录搜索索引过程错误索引过程
   * _修复注释_：无论使用PHP编译的libxml版本如何，系统现在都能成功完成重新索引命令，而不会遇到任何错误。 以前，当使用特定版本的libxml编译PHP时，运行“重新索引”命令会导致“索引过程中出现目录搜索索引过程错误”错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38254>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38553>，<https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_：已将created_at、status和grand_total筛选器添加到客户订单查询，并修复了多个筛选器失败
   * _修复注释_：系统现在支持在客户订单查询中使用created_at、status和grand_total筛选器，并且解决了多个筛选器未正确应用的问题。 以前，系统不支持这些过滤器，并且在查询中使用多个过滤器时，将无法应用所有过滤器。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38392>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36949>
* _AC-10971_： https://github.com/magento/magento2/issues/38415
   * _修复注释_： PHP 8.2/8.3，此时只有一个依赖项失败php linter： league/flysystem
   * _GitHub问题_： &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _GitHub代码贡献_：系统现在通过将league/flysystem包更新到版本3.0.20来支持PHP 8.2/8.3，从而确保不会发生PHP Linting错误。 以前，通过带有PHP 8.3的PHP Linter运行PHP文件会导致league/flysystem包出现Linting错误。
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
   * _修复说明_： \Magento\Framework\Data\Collection：：getItemById方法的PHPDocs已更新，可能包含null作为返回类型，从而解决了静态分析工具的问题。 以前，该方法的PHPDocs不指定null作为可能的返回类型，导致在条件语句中使用该方法时进行静态分析时出现警告或错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38485>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38439>
* _AC-11651_： Magento尝试在LoggerProxy的__wakeUp方法中修改只读属性
   * _修复注释_：系统现在允许修改LoggerProxy的__唤醒方法中以前的只读属性，从而确保顺利操作而不强制用户采用解决方法。 以前，尝试在LoggerProxy的__wakeUp方法中重新分配只读属性的值会导致出现问题。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38526>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11673_：
   * _修复注释_：调查php-amqplib/php-amqplib最新版本
   * _GitHub问题_： &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub代码贡献_：更新了最新版本php-amqplib/php-amqplib ：^3.x
* _AC-11681_： [问题] AC-2039 AC-1667升级TinyMCE参考
   * _修复注释_：更新了composer.json中的tinymce最新版本
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38533>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36543>，<https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_： ChangelogBatchWalker在多个线程中不起作用
   * _修复注释_：系统现在支持MView索引的进程分支，以防止在多个线程上运行索引器时出现错误。 以前，在多个线程上运行ChangelogBatchWalker会导致删除其他线程使用的表，从而导致索引器执行期间出错。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38246>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38248>
* _AC-11781_： [问题]重命名命名错误的变量
   * _修复注释_：系统现在可以正确命名包含仍可退款的金额的变量，以防止在调试期间出现混淆。 以前，此变量错误地命名为totalRefute，这可能导致开发人员误解。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38609>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36205>
* _AC-11808_：
   * _修复注释_：调查和升级Adobe Commerce核心依赖项列表
   * _GitHub代码贡献_：需要升级Adobe Commerce核心依赖项列表 
* _AC-11819_：某些配置的内置FPC缓存在2.4.7中损坏
   * _修复注释_：现在，在设置MAGE_RUN_CODE参数时，系统会正确缓存页面，从而确保最佳性能。 以前，在这些情况下不会缓存页面，这会导致潜在的性能问题。
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
* _AC-11905_： [问题]静态内容部署 — 类型错误
   * _修复注释_：系统现在可以在静态内容部署期间正确处理空的LESS文件，并显示“LESS文件为空”错误消息。 以前，在部署期间遇到空LESS文件时抛出不正确的类型错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38682>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38683>
* _AC-11911_：
   * _修复注释_：迁移至uppy库后，jQuery/fileuploader css清理
   * _GitHub问题_： &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _GitHub代码贡献_：已删除jQuery/fileUploader库，因为它已迁移到Uppy库
* _AC-12002_： [问题] [视图]删除了链接和脚本标记中的额外空间
   * _修复注释_：系统现在可确保链接和脚本标记中没有额外的空格，从而提供更干净和更高效的代码。 以前，链接和脚本标记中的属性之间会存在双空格。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/32920>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/32919>
* _AC-12015_：
   * _修复注释_：迁移到jsTree库后，清理ExtJs文件夹
   * _GitHub问题_： &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _GitHub代码贡献_：删除了extJs文件夹，因为相关功能已迁移到jsTree
* _AC-12022_：
   * _修复注释_：将独白/独白系统依赖项升级到最新的主版本
   * _GitHub问题_： &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub代码贡献_：系统已更新为使用“monolog/monolog：^3.x”库的最新主要版本，从而确保兼容性和改进的性能。 以前，系统使用的是“monolog/monolog”库的过时版本，这可能导致潜在的问题和限制。
* _AC-12023_：
   * _修复注释_：将wikimedia/less.php依赖项升级到最新的主版本
   * _GitHub问题_： &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub代码贡献_：系统已更新为使用“wikimedia/less.php”库的最新主要版本5.x，从而确保兼容性和最新功能。 以前，系统使用的库版本过时，这可能导致安全问题。
* _AC-12024_：
   * _修复注释_：将jquery/validate库依赖项升级到最新的次要版本
   * _GitHub问题_： &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub代码贡献_：将jquery/validate库依赖关系升级到最新的次要版本1.20.0
* _AC-12025_：
   * _修复注释_：将moment.js系统依赖关系升级到最新的次要版本
   * _GitHub问题_： &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub代码贡献_：将moment.js系统依赖关系升级到最新的次要版本2.30.1
* _AC-12267_：
   * _修复注释_：支持Redis会话的连接重试并与colimollenhour/php-redis-session-abstract v2.0.0兼容
   * _GitHub问题_： &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _GitHub代码贡献_：更新了与adobe commerce兼容的最新版本的colimmollenhour/php-redis-session-abstract v2.0.0
* _AC-12268_：
   * _修复注释_：将league/flysystem Composer依赖项升级到最新版本
   * _GitHub代码贡献_：将2.x league/flysystem Composer依赖项升级到最新版本3.x
* _AC-12594_： [问题]对生成的数据使用已编译配置而不是常规配置
   * _修复注释_：系统现在对生成的数据使用编译的配置，而不是常规配置，从而减少依赖于特定代码版本的网络传输和数据开销。 此更改可防止在容器交换期间覆盖共享实例中的缓存，从而提高稳定性并减少停机时间。 以前，某些核心类使用共享配置类型，由于多个服务器上的代码版本不同，这可能会导致缓存覆盖或应用程序停机。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38785>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/29954>
* _AC-12597_： [问题]从e1ccdb中删除的extjs中删除对文件的引用……
   * _修复注释_：系统现在会从以前删除的extjs中删除对文件的引用，从而消除浏览器控制台和系统日志文件中的错误。 以前，由于缺少引用的文件，这些引用会导致错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38960>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38951>
* _AC-12715_：
   * _修复注释_：更新升级到最新版本的Laminas编辑器依赖项
   * _GitHub问题_： &lt;<https://github.com/magento/magento2/commit/b34c0a75>>
   * _GitHub代码贡献_：系统现在支持最新版本的Laminas编辑器依赖项：
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validator
确保兼容性和最新功能。 以前，更新到这些依赖项的最新版本可能会导致向后不兼容问题和测试失败。
* _AC-12778_： [问题]次要清理：修复了sprintf的错误用法，此处只需要2个占位符，然后……
   * _修复注释_：系统现在正确使用sprintf函数以及适当数量的占位符，从而提高代码清洁度和一致性。 以前，sprintf函数与额外的参数一起使用时不正确，这不会导致任何重大问题，但用法不正确。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39062>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38628>
* _AC-12866_：
   * _修复注释_：删除弃用项 — PhpUnit10集成测试
   * _GitHub问题_： &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub代码贡献_：解决PHPUnit弃用问题
* _AC-12868_：
   * _修复注释_：删除弃用项 — PhpUnit10 WebApi测试
   * _GitHub问题_： &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub代码贡献_：解决PHPUnit弃用问题
* _AC-12869_： [问题]修复了Magento模块中引用的不正确的类。
   * _修复注释_：系统现在可以正确引用模块中的类，从而确保操作更顺畅，并防止由于不存在类而导致崩溃。 这包括Indexer和Creditmemo模块中的错误修复，以及PrintAction类中HttpGetActionInterface的实现。 以前，错误的类引用会导致错误和潜在的系统崩溃，并且某些功能(如creditmemo PDF文件的文件名和股票重新索引)无法按预期工作。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/39126>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37784>
* _AC-6754_： js文件出现拼写错误。
   * _修复注释_：系统现在可以在JavaScript文件中正确使用“订阅者”一词，从而确保相关功能正常运行。 以前，JavaScript文件中的输入错误会导致术语“subscribers”的使用不正确。
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
* _AC-8984_： [问题]在某些安装cli命令的输出中添加了一些颜色
   * _修复注释_：系统现在为某些安装命令行界面(CLI)命令的输出添加了更多颜色，增强了可读性和用户体验。 以前，由于缺少颜色区分，这些命令的输出更难读取。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/29335>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/29298>
* _AC-9630_：当添加具有所需州/地区的新国家/地区时，升级Magento将重置general/region/state_required。
   * _修复注释_：现在，当添加具有所需状态的新国家/地区时，系统仅会将修改后的国家/地区添加到“general/region/state_required”配置中，以防止假定地区已禁用的自定义代码出现任何中断。 以前，添加具有所需状态的新国家/地区会将“general/region/state_required”配置重置为具有所需状态的默认国家/地区，这可能会中断业务。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37796>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38076>
* _AC-9712_：具有复杂`calc`表达式的php &amp; nodejs库(grunt)之间编译较少的差异
   * _修复注释_：在更新wikimedia/less.php：^5.x后，修复php &amp; nodejs库(grunt)之间较少编译的差异
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37841>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_：执行部分索引时出现“未找到基表或视图”错误
   * _修复注释_：现在，在辅助数据库连接的情况下，部分重新索引可以与大更改日志一起正常工作
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_：将MariaDB升级到10.5.1或更高版本后出现问题
   * _修复注释_：修复了Mysql升级后，数据库中的日期时间值转换为0000-00-00 00:00:00的问题
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_：检查数据是否有更改时，数据比较中的类型不匹配
   * _修复注释_：以前，每次在没有任何数据更改的情况下调用save对象（对于任何数值数据字段，如int/float/double）。 它会触发将_hasDataChanges标志设置为true并调用save函数。 进行此修复后，仅当数据发生更改时，才会调用save函数。 int/float/double-check的数据值，其值传递给函数并执行严格的类型匹配。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_： [云]导入不能与目录var一起使用
   * _修复注释_：无论文件名如何，都可以成功导入产品。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_：在ipad mini中，菜单和标题以移动设备加载，而应以桌面加载。
   * _修复注释_：系统现在将宽度为768像素的设备视为桌面，以确保菜单和标题正确加载。 以前，宽度为768像素的设备被视为移动设备，从而导致菜单和标题在移动视图中加载。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/35b1b1da>，<https://github.com/magento/magento2-page-builder/commit/4d5db10a>

### 框架，GraphQL

* _AC-7976_： [问题]引入了GraphQL架构的自定义标量类型支持
   * _修复注释_：系统现在支持GraphQL架构的自定义标量类型，允许开发人员定义自定义标量类型和实现。 此功能对于表示可能需要验证的值(例如HTML、电子邮件、URL、日期等)以及更高级的情况（例如EAV属性）特别有用。 以前，系统不支持在GraphQL中处理自定义标量类型。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/36877>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/34651>，<https://github.com/magento/magento2/commit/0574ac23>

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
* _ACP2E-3253_： GraphQL cart itemsV2分页无法正常工作
   * _修复注释_：通过为集合查询中的当前页面参数传递正确的值，已修复该问题。 以前，传递错误值来设置当前页面，从而导致出现问题。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/8459b17d>

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
   * _修复注释_：通过导入编辑或删除客户时，GraphQL客户解析程序缓存现在会按预期失效。 以前，缓存不会失效，并且可以在导入期间编辑或删除客户数据。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL，搜索

* _ACP2E-2809_： GraphQL产品列表按多个参数排序不起作用
   * _修复注释_： GraphQl中按多个字段排序的产品现在按文档中的说明工作
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c971859e>

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
之前导入的客户重复。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_：添加/更新产品导入重复可自定义选项
   * _修复注释_：通过在产品选项CSV导入期间将正确的存储分配给产品选项，该问题已得到解决。
以前，分配给管理员存储，而不是其各自的存储。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_：客户的“created_at”日期未在导出时转换为存储时区
   * _修复注释_：根据客户导出CSV分区中的存储时区，列“created_at”日期值将转换为适当的日期格式。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_： [Cloud]使用CSV检查导入数据中的数据时出现错误
   * _修复注释_：在CSV导入期间检查数据时没有错误。 以前，使用管理员的CSV检查导入部分中的数据时显示的错误消息是：“我们在以下行中找不到与此电子邮件和网站代码匹配的客户： 1”。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/8459b17d>

### 安装和管理

* _ACP2E-2102_：管理面板中没有用于清漆7按钮的导出VCL
   * _修复说明_：“Export VCL for Varnish 7”按钮已添加到“管理”面板中。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4fbf702>

### 库存/MSI

* _AC-11593_：添加具有属性的映射时，Google google API密钥不起作用
   * _修复注释_：系统现在支持最新的Google Maps API版本3.56，使用户能够成功地将映射内容块从PageBuilder菜单添加到舞台中，而不会遇到任何错误。 以前，由于Google地图API版本存在兼容性问题，用户无法添加地图内容块，从而导致“出现问题”错误消息。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2794_：[Cloud]产品列表的关键问题为空白
   * _修复注释_：现在，当产品设置为“缺货”时，系统可正确显示产品清单，且不含空格，从而确保一致、准确地显示可用产品。 以前，将产品设置为“缺货”会导致产品列表中显示空白，中断布局并可能使客户感到困惑。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ea79f7dd>，<https://github.com/magento/inventory/commit/b59e48ca>

### 订购

* _AC-10828_：后端订单概览屏幕：在订单物料级别上看不到延期交货数量
   * _修复注释_：系统现在会在后端订单概述屏幕的数量列中显示延期交货项目数。 这可确保用户能够准确地跟踪按顺序排列的所有项目的状态。 以前，“数量”列只显示已订购、开票和发运的项目数，而不显示延交项目数。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38252>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38320>
* _AC-10994_： [问题]订单地址呈现器中使用了错误的存储ID
   * _修复注释_：现在，系统在呈现订单地址时，正确使用了与订单关联的商店ID，从而确保根据相应的商店ID正确格式化地址。 以前，系统错误地使用当前商店ID，在需要发送来自不同商店的多份订单电子邮件时，可能会导致地址格式不正确。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38412>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37932>
* _AC-11798_： [问题]装运价格在打印的PDF中显示差异
   * _修复备注_：系统现在可根据税务配置设置以打印的PDF正确显示发运价格，确保销售订单发票视图页与打印发票之间的一致性。 以前，无论税配置设置如何，打印的PDF中显示的运费不含税。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38608>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38595>，<https://github.com/magento/magento2/commit/1bafc571>
* _ACP2E-2622_：无法在现有订单详细信息中保存对电话号码的更改
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

### 订单，退货

* _ACP2E-2982_：订单退款导致贷项通知单重复
   * _修复注释_：同时执行两个相同的请求时通过REST API发出退款将不再创建重复的贷项通知单。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/a4fbf702>

### 订单，税金

* _ACP2E-3003_： [CLOUD] RESTFUL订单API中的base_row_total在启用跨国交易和应用优惠券折扣时不正确
   * _修复注释_：现在，在启用跨境交易并应用优惠券折扣的情况下，从RESTFUL订单API返回正确的base_row_total。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/9af794a4>

### 其他开发人员工具

* _AC-10658_： [问题]修复visual.phtml中的HTML语法错误
   * _修复注释_：系统现在可以正确关闭visual.phtml文件中的开始标记，从而确保HTML语法正确。 以前，start标记未正确关闭，从而导致HTML语法错误。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38247>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37457>
* _AC-11474_： [问题]在bin/magento maintenance：status命令中将“活动”更改为“已启用”
   * _修复注释_：系统现在为维护模式命令提供更准确的状态消息，状态从“活动”更改为“已启用”，从“非活动”更改为“已禁用”。 以前，维护模式命令的状态消息显示为“活动”或“非活动”，这可能会导致混淆。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38486>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38410>
* _AC-12571_：在类别树中导航会导致Redis中出现错误：“Redis会话超出并发连接数”
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38851>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0611e750>

### 支付

* _ACP2E-2841_：每次单击“查看事务”屏幕上的“提取”按钮时，Payflow都会创建新事务
   * _修复注释_：现在，每次单击“查看交易”屏幕上的提取按钮时，系统都会正确提取交易信息，而不会创建新的付款交易。 以前，单击“提取”按钮会错误地为已支付的订单创建新的支付交易记录。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_：加拿大Paypal商家帐户的PDP中未显示Paylater消息
   * _修复说明_：当可以根据帐户帐单地址或装运确定买方所在国家/地区时，系统现在会在产品详细信息页面(PDP)上正确显示加拿大PayPal商家帐户的PayLater消息。 以前，由于缺少参数，不会显示PayLater消息，这会导致浏览器控制台中出现错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/6a185204>

### 性能

* _AC-12000_： [问题]代码清理并添加新的关键标题块并将关键css移动到资产之前
   * _修复注释_：系统现在包含新的关键头块并将关键CSS移动到资产之前，允许在前端进行更多自定义和性能优化。 以前，关键CSS不放在资产之前，从而限制了自定义和优化机会。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38748>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/35580>
* _AC-12176_： mysql主机包含端口信息时主题编译中断
   * _修复注释_：系统现在可以正确处理包含端口信息的MySQL主机配置，确保主题编译成功。 以前，如果数据库连接中的MySQL主机配置包含端口信息，则主题编译将失败。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38799>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38842>
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
   * _修复注释_：系统现在会在合理的时间范围内执行Order Rest API调用，从而提高获取大量订单时的性能。 以前，Order Rest API调用执行时间较长，导致在检索大量订单时出现延迟。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/001e5188>

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
* _AC-5969_： AlertProcessor — 参数#2($storeId)必须是int类型，并且给定字符串
   * _修复注释_：系统现在通过确保商店标识符的数据类型正确来正确触发产品警报电子邮件。 以前，由于商店标识符中的类型不匹配，不会发送产品警报电子邮件。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/35602>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_： [Cloud] addFilterToMap函数无法用于某些列
   * _修复注释_：现在，可以在订单网格中使用自定义模块。 以前，使用自定义模块时出现错误。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/3a7c4d17>

### 促销活动

* _ACP2E-2602_：从邀请创建帐户时客户属性不可见
   * _修复注释_：从邀请创建帐户时，客户属性可用。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2627_：未释放每个优惠券限制使用次数的优惠券代码以进行取消订单的付款
   * _修复注释_：系统现在会在创建或取消订单后立即更新优惠券使用情况，并将规则使用情况添加到队列中，以防止潜在的死锁。 这可确保释放具有“每张优惠券的使用次数”限制的优惠券代码，并且可在因付款失败而取消订单时重复使用。 以前，系统不会发布优惠券代码以供在此类情况下重用，从而导致出现错误消息，指出优惠券代码无效。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2811_： [Cloud]重新索引目录规则产品索引器引发SQLSTATE[HY000]：常规错误： 2006 MySQL服务器已消失。
   * _修复注释_：系统现在可以正确处理“Magento\CatalogRule\Model\Indexer\IndexBuilder”的di.xml中的自定义“batchCount”值，从而防止在重新索引目录规则产品索引器期间由于大型目录的批处理大小不正确而出现SQL错误，如“常规错误： 2006 MySQL服务器已消失”
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b2286ecf>

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

### 安全性

* _AC-11762_：
   * _修复注释_：在BiC更改后，使用正确的描述和默认值更新2FA OTP窗口字段
   * _GitHub代码贡献_：更新了命令，说明如何从现在bin/magento config：set twofactorauth/google/otp_window VALUE输入otp_window周期
至bin/magento config：set twofactorauth/google/leeway VALUE
* _AC-11855_： [问题]缺少字体CSP播放器弹出窗口
   * _修复注释_：系统现在允许加载字体“https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39;”，而不违反内容安全策略指令，从而确保正确显示Paylater弹出窗口。 以前，由于违反Content Security Policy指令而拒绝加载字体，这会导致Paylater弹出窗口的显示问题。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38624>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/37401>
* _AC-11937_：
   * _修复注释_：在BiC更改后，使用正确的描述和默认值更新2FA OTP窗口字段
   * _GitHub代码贡献_：更新了命令，说明如何从现在bin/magento config：set twofactorauth/google/otp_window VALUE输入otp_window周期
至bin/magento config：set twofactorauth/google/leeway VALUE
* _AC-12309_：
   * _修复注释_：更新双重身份验证(2FA)的用户文档以更改otp_window命令
   * _GitHub代码贡献_：更新双重身份验证(2FA)的用户文档以更改OTP_WINDOW设置命令，如下所示： https://jira.corp.adobe.com/browse/AC-11762

### 配送

* _AC-10757_： [问题]修复了tracking.phtml中的拼写错误 — 已将JS函数“currier”重命名为“carrier”
   * _修复注释_：现在，系统在订单跟踪模板中使用的JavaScript处理程序函数中正确使用了术语“carrier”，而不是拼写错误的“currier”，从而确保函数命名正确且代码清晰明了。 以前，使用拼写错误的术语“currier”，这可能导致代码库中的混淆和不一致。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/34523>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/33414>
* _AC-11811_：
   * _修复说明_： UPS REST“装运不能以KGS/IN、LBS/CM或OZS/CM作为其度量单位”
   * _GitHub问题_： &lt;<https://github.com/magento/magento2/commit/9b1713d8>>
   * _GitHub代码贡献_： UPS费率在结帐和购物车中可见。
* _AC-11916_：
   * _修复说明_： [QPT] UPS REST“装运不能以KGS/IN、LBS/CM或OZS/CM作为其度量单位”
   * _GitHub代码贡献_： UPS费率在结帐和购物车中可见。
* _AC-11938_： UPS REST “装运不能以KGS/IN、LBS/CM或OZS/CM作为其度量单位”
   * _修复注释_：确保在结帐和购物车中显示UPS费率。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38618>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/493e01f5>
* _AC-11983_：
   * _修复说明_： [QPT] UPS REST“装运不能以KGS/IN、LBS/CM或OZS/CM作为其度量单位”
   * _GitHub代码贡献_： UPS费率在结帐和购物车中可见。
* _AC-11984_：
   * _修复说明_： [QPT] UPS REST“装运不能以KGS/IN、LBS/CM或OZS/CM作为其度量单位”
   * _GitHub代码贡献_： UPS费率在结帐和购物车中可见。
* _ACP2E-2738_：跟踪窗口显示错误的预期投放日期
   * _修复注释_：显示Fedex承运人的正确交货日期。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_：即使应用免运费，仍显示表费率
   * _修复注释_：即使优惠券应用后免费送货变为可用，现在仍显示表费率送货方法
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_：由于未在Jenkins环境中添加凭据，MFTF测试AdminCreatingShippingLabelTest失败
   * _修复注释_： mftf测试修复
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ea79f7dd>

### 目标选择

* _AC-9432_： [问题]允许在维护允许列表中使用CIDR范围
   * _修复注释_：系统现在支持在维护模式允许IP列表中使用CIDR范围，使一系列IP地址绕过维护模式。 以前，维护模式允许IP列表仅允许单个IP地址绕过维护模式。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37943>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/30699>

### 测试框架

* _AC-11491_：
   * _修复注释_： [跳过]需要再次取消跳过集成测试
   * _GitHub问题_： &lt;<https://github.com/magento/magento2/commit/493e01f5>>
   * _GitHub代码贡献_：取消跳过此PR中跳过的所有集成测试 — https://github.com/magento-commerce/magento2ce/pull/8811/
* _AC-11654_：由于JSON列类型，集成测试未通过testDbSchemaUpToDate
   * _修复注释_：在集成测试期间，系统现在可以正确识别数据库架构中的JSON列类型，从而防止由于数据库架构与声明性架构不匹配而导致的测试失败。 以前，系统错误地将JSON列类型识别为MariaDB中的LONGTEXT，从而导致集成测试失败。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/ef81f5a2>

### UI框架

* _AC-12128_： Prototype.js安全漏洞修复CVE-2020-27511
   * _修复说明_：系统已更新，以解决Prototype.js 1.7.3中的安全漏洞CVE-2020-27511，从而提高系统的整体安全性。 在此更新之前，系统通过删除精心编制的HTML标签容易遭受正则表达式拒绝服务(ReDOS)攻击。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_： Grunt Less使用pub/前缀作为sourcemaps
   * _修复注释_：在使用grunt时，系统现在为路径生成不带/pub前缀的较少/css源地图，从而无需在Web服务器配置中进行变通处理。 以前，在sourcemaps路径中使用/pub前缀需要Web服务器中的特定配置才能正常工作。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/38837>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/38840>
* _AC-1306_：正在为禁用的模块部署静态内容
   * _修复注释_：系统现在会从最终CSS输出文件中排除与已禁用模块相关的CSS，从而确保不加载不必要的样式。 以前，与禁用的模块相关的CSS包含在最终的CSS输出文件中，这会导致加载多余的不必要样式。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/24666>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/32922>
* _AC-9007_： [问题]不在前端加载后端块上下文
   * _修复注释_：系统现在确保前端上未加载后端块上下文，从而防止创建不必要的后端会话和潜在的会话锁定。 以前，系统在前端错误地加载后端块上下文，导致创建后端会话和潜在的会话锁定。
   * _GitHub问题_： <https://github.com/magento/magento2/issues/37617>
   * _GitHub代码贡献_： <https://github.com/magento/magento2/pull/36368>
* _ACP2E-2529_：启用Recaptcha时检查礼品卡余额时出现异常
   * _修复注释_：用户将能够在查看和编辑购物车屏幕中获取礼品卡余额。 以前，启用reCAPTCHA时，不会显示这些详细信息。
   * _GitHub代码贡献_： <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_：[说明]功能请求ADA合规性
   * _修复注释_：系统现在通过删除不支持的CSS属性并将其替换为print.css文件中支持的属性来确保ADA合规性。 以前，使用不支持的CSS属性会导致浏览器兼容性问题。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_： [Cloud] AC 2.4.4-p8的effect-drop.js中的混淆库代码
   * _修复注释_：系统现在可以正确实施effect-drop.js库，从而确保jQuery UI效果的正常运行。 以前，effect-drop.js库错误地被effect-clip.js库覆盖，导致jQuery UI效果出现潜在问题。
   * _GitHub代码贡献_： <https://github.com/magento/magento2/commit/35b1b1da>
