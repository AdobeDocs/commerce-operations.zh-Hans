---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '10868'
ht-degree: 0%
---
# Adobe Commerce修复了问题(v2.4.10-alpha1)

## 修复了v2.4.10-alpha1中的问题

我们已在Adobe Commerce 2.4.10-alpha1核心代码中修复了169个问题。 此版本中包含的已修复问题的子集如下所述。

### API

#### Creditmemo\Validation\QuantityValidator中的[问题] TypeError是由带有字符串数量的min()引起的

为了稳定财务日志管道并防止在批量自动订单退款期间出现API请求失败，在内部销售贷项通知单工厂和验证层中添加了数据类型铸造护栏。

_AC-16056 - [GitHub问题](https://github.com/magento/magento2/issues/40302) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40429) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40303)_

#### 在没有attribute_id的情况下，REST API属性更新失败

修复了未提供attribute_id时通过REST API更新现有产品属性失败的问题。 API现在可以使用URL中的attribute_code正确标识属性并成功对其进行更新。

_AC-16424 - [GitHub问题](https://github.com/magento/magento2/issues/40458) - [GitHub代码贡献](https://github.com/magento/magento2/commit/c10554e1)_

#### 当Adobe Stock凭据无效时显示身份验证错误

当Adobe Stock凭据无效时，管理员现在会看到身份验证错误。

_AC-17123_

#### 通过REST API更新选项时已删除可视化样本

为了保护目录数据完整性并简化自动化集成，已解决EAV样本管理层中的一个错误，该错误导致在标准选项更新期间无意中清除了现有的视觉或文本样本值。

_AC-9199 - [GitHub问题](https://github.com/magento/magento2/issues/37794) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40872)_

#### 当缺少一个SKU时，批量层价格API在整个批次中失败

以前，当有效负载中的任何SKU不存在时，批量层价格更新API(POST /V1/products/tier-prices)会失败整个请求，从而使有效的SKU没有更新。 现在，系统会成功处理有效的SKU，同时将缺少的SKU报告为按项目错误，因此单个错误条目不再中止整个批次。

_ACP2E-4998 - [GitHub代码贡献](https://github.com/magento/magento2/commit/51f6d191)_

#### 属性更新失败，标签值与现有选项值ID匹配

修复了标签与现有选项的ID匹配时，无法通过REST API创建新的下拉/多选产品属性选项的问题。 以前，即使可以通过管理员UI成功创建相同选项，API也会返回“已存在”错误（并且可能返回错误的选项ID）。

_ACP2E-5107 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4d0357d7)_

### API，导入和导出

#### REST API允许负产品价格，而管理员UI会阻止这些产品价格

通过REST API端点导入产品时，现在会拒绝价格类型属性（price、special_price、cost和相关的MSRP字段）的负值，这与Admin UI导入的行为一致。 以前，API静默接受负价格并将其保留。

_ACP2E-4941 - [GitHub代码贡献](https://github.com/magento/magento2/commit/08b91f1a)_

### API、顺序

#### 订单速率限制功能与Valkey缓存后端不兼容

以前，此固定速率限制被静默地绕过，并且无论配置的限制是什么，每个请求都允许通过。 修复后，超过HTTP 429配置限制的请求将被正确拒绝。

_ACP2E-4899 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9b6a8bd9)_

### 帐户

#### [问题]修复：登录表单密码标签不正确

修复了客户登录页面上的“密码”字段的标签关联不正确的问题。 现在，密码标签可正确定向“密码”字段，从而允许自动测试工具正确识别密码。

_AC-16193 - [GitHub问题](https://github.com/magento/magento2/issues/40353) - [GitHub代码贡献](https://github.com/magento/magento2/commit/64eb754d)_

#### [问题]验证文件上载的前端输入类型

客户地址文件上传现在会先验证目标属性的输入类型是文件或图像，然后再进行处理，因此文本和其他非文件属性不能被滥用为上传目标。 无效上载尝试返回了清除验证错误，而不是无法预测地失败或接受不允许的文件类型。

_AC-17076 - [GitHub问题](https://github.com/magento/magento2/issues/40795) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40583)_

#### 在网站A上生成的客户令牌可在网站B上用于网站范围内的客户配置

为了在多网站实例上强制实施严格的客户数据隔离，已在GraphQL身份验证层中消除了一个安全漏洞，该漏洞导致令牌在不同边界上被错误验证。

_AC-17299 - [GitHub问题](https://github.com/magento/magento2/issues/40847) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40858)_

#### [问题]修复PHP 8.5弃用问题：使用null作为array_key_exists()的键参数

修复了PHP 8.5上的一个问题：由于使用null键的已弃用array_key_exists()调用，客户在来宾签出期间登录失败。 现在，客户登录可成功运行，且不会生成弃用错误。

_AC-17395 - [GitHub问题](https://github.com/magento/magento2/issues/40875) - [GitHub代码贡献](https://github.com/magento/magento2/commit/515d3dd3)_

#### [问题] magento/magento2：将i18翻译添加到requestPasswordResetEmail和resetPassword GraphQL突变

为确保完全本地化的Headless店面体验，客户帐户恢复API端点添加了国际化(i18n)翻译功能

_AC-9356 - [GitHub问题](https://github.com/magento/magento2/issues/29658) - [GitHub代码贡献](https://github.com/magento/magento2/pull/28950)_

### 管理员UI

#### 默认情况下，当使用聚合数据时，仪表板应显示过去7天

修复了在启用汇总销售数据时，功能板默认显示今天的问题。 现在，使用聚合数据时，仪表板默认显示过去7天。

_AC-13799 - [GitHub问题](https://github.com/magento/magento2/issues/28152) - [GitHub代码贡献](https://github.com/magento/magento2/commit/29a7cdbe)_

#### 对于简单产品的相同配置，购物车页面和产品页面中的FPT值不同

修复了固定产品税(FPT)值在同一税务配置的产品和购物车页面上显示不同的问题。 现在，FPT值在产品、目录、迷你购物车和购物车页面中的显示方式是一致的。

_AC-17007 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ecbeba3a)_

#### 延迟配置实施

性能优化，通过延迟解析范围系统配置数据，同时保留现有配置行为，从而改善配置加载性能。

_ACP2E-4751 - [GitHub代码贡献](https://github.com/magento/magento2/commit/65f660bd)_

#### GegRTE编辑器阻止表情符号 — javascript验证失败

修复了在PageBuilder内容类型模式（文本、横幅、幻灯片）内编辑时，GegRTE阻止保存包含utf8mb4表情符号（例如🔵⚪🔴）的内容的问题。 以前，这些模式表单的wysiwyg验证配置将`allowUtf8mb4`解析为`false`，导致编辑器拒绝包含4字节UTF-8字符的设置，即使数据库完全支持utf8mb4的安装也是如此。

_ACP2E-4822 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/f2691e17)_

#### 受限管理员在升级后无法删除客户

修复了受限管理员在升级后无法删除客户的问题，该问题会在客户网格的顶部显示一个红色横幅，横幅上写着：“需要更多权限才能查看此项目。”

_ACP2E-4838_

#### 在管理员面板的客户编辑页面中查看具有大型通讯簿的客户时，管理员会注销

修复了当管理员在管理面板的客户编辑页面中查看具有大地址簿的客户时注销的问题

_ACP2E-4875 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b63925d9)_

#### 订单未显示在销售网格中

修复了在启用异步网格索引时，由于协调光标在赶上最新实体时重置，新订单在Sales网格中显示延迟的问题。 新条目现在会在下次cron运行时显示在网格中。

_ACP2E-4893 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b63925d9)_

#### 启用Magento_VisualMerchandiser后，[Cloud]在类别产品网格中缺少分配的产品筛选器

修复了在启用可视化促销器后， Add Products模式搜索All Products网格中缺少“已分配”过滤器的问题。 以前，管理员用户无法按其在相应模式中的已分配/未分配状态筛选产品，因此很难识别哪些产品已属于类别。

_ACP2E-4974_

#### 操作日志不显示与返回相关的操作的返回编号/返回ID

修复了退货编号/退货ID未显示在与退货相关的管理操作的操作日志条目中的问题。 以前，查看或保存RMA等操作会记录在操作日志中，并且不会返回任何标识符，这与正确显示订单编号的订单相关操作不同。

_ACP2E-5050_

#### 对于在商店视图范围中保存的管理员产品的价格和税类，“使用默认值”未选中

受限管理员用户现在可以在商店视图范围保存产品，而不会丢失价格、状态和税类属性的“使用默认值”状态。 以前，将产品另存为受限管理员（拒绝价格和状态编辑）时，系统会静默取消勾选这些字段的“使用默认值”，导致即使没有预期覆盖也会写入存储视图级别的覆盖。

_ACP2E-5081_

### 管理员UI，订单

#### 当两个分组产品共享相同的简单产品时，管理员创建订单中为分组产品显示的价格不正确

修复了以下问题：当共享同一简单产品的两个分组产品都配置而未添加到购物车时，管理员创建订单中分组产品的价格计算不正确。

_ACP2E-4965 - [GitHub代码贡献](https://github.com/magento/magento2/commit/08b91f1a)_

### 管理员UI、UI框架

#### Magento2重定向到主页，而不是显示错误的菜单声明错误

为了优化扩展开发工作流并确保稳定的后端加载，解决了结构化的路由缺陷：无效的管理菜单声明触发了静默浏览器循环故障，而不是显示可操作的诊断消息。

_AC-7543 - [GitHub问题](https://github.com/magento/magento2/issues/36632) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40881)_

### Analytics/报表

#### [QUANS]能否在高级报告下的“客户KPI”表中显示客户电子邮件ID和名称？

Adobe Commerce现在在导出到高级报告的数据中包括客户的名字、中间名和姓氏，允许客户KPI表显示客户名称。 以前，只导出编码的客户标识符，因此商家无法在高级报表中按名称识别客户。

_ACP2E-3928 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4d0357d7)_

#### 对sales_bestsellers_aggregated_monthly执行大量插入

改进了aggregate_sales_report_bestsellers_data cron的性能。

_ACP2E-4559 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8d95ae6e)_

#### 添加到购物车事件有效负载采用的是旧版Universal Analytics增强型电子商务格式，而不是GA4电子商务格式。

在修复之前，通过Google Tag Manager发送到Google Analytics 4的电子商务事件使用旧版Universal Analytics格式，并且缺少多个签出事件。 修复后，所有电子商务事件都使用正确的GA4格式，并跟踪完全签出的funnel。

_ACP2E-5176 - [GitHub代码贡献](https://github.com/magento/magento2/commit/24667df1)_

### B2B

#### placeNegotiableQuoteOrderV2对来自可转让报价的订单返回total.total_shipping = null

修复了placeTransactionalQuoteOrderV2为来自带付运的可协商报价的订单返回空发运合计的问题。 现在，API可正确返回装运金额，与订单总计中包含的装运费用相匹配。

_AC-18083_

#### 将报价转换为订单后，[B2B]报价详细信息中缺少捆绑选项价格

修复了在将报价转换为订单后，可转让报价详细信息页面上缺少捆绑产品选项价格的问题。

_ACP2E-5055_

### B2B，订购

#### 有关清理59M以上报价表的帮助（sales_clean_quotes无法运行）

修复了在具有大报价表的实例上`sales_clean_quotes` cron作业超时的问题。 以前，清理查询从`negotiable_quote`表中不必要地选择了所有列，导致MySQL在数百万行上执行完整的文件排序；并且每个引号都通过PHP模型层单独删除，从而增加了性能成本。

_ACP2E-4891 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b63925d9)_

### 购物车和结帐

#### 添加到相关产品的购物车通知

修复了在将产品及其相关产品添加在一起时，“添加到购物车”通知不包含相关产品的问题。
通知现在会显示添加到购物车的两个产品的名称。

_AC-11976 - [GitHub问题](https://github.com/magento/magento2/issues/27164) - [GitHub代码贡献](https://github.com/magento/magento2/commit/515d3dd3)_

#### [问题]更新CartRepositoryInterface.php

更新了CartRepositoryInterface.php以声明在保存购物车时可能引发的异常。 这可使界面与底层购物车保存实施保持一致。

_AC-13323 - [GitHub问题](https://github.com/magento/magento2/issues/39328) - [GitHub代码贡献](https://github.com/magento/magento2/commit/29a7cdbe)_

#### 在结帐配送步骤中添加新地址时，配送地址中的[错误]公司字段在多商店设置中设置为null

修复了客户在多商店设置中结账期间添加新送货地址时，“公司”字段未保存的问题。 公司值现在正确地保存在报价、下单和客户通讯簿中。

_AC-13456 - [GitHub问题](https://github.com/magento/magento2/issues/39424) - [GitHub代码贡献](https://github.com/magento/magento2/commit/515d3dd3)_

#### Paypal >客户数据不匹配（前缀、名字、姓氏）

修复了PayPal SEPA结账流程期间客户名称详细信息映射不正确的问题。 现在，前缀、名字和姓氏会按正确顺序填充，而不会出现任何不匹配。

_AC-15366 - [GitHub问题](https://github.com/magento/magento2/issues/39061) - [GitHub代码贡献](https://github.com/magento/magento2/commit/ecbeba3a)_

#### 虚拟产品的free_shipping标记不正确

修复了将多个项目添加到购物车时，虚拟产品的free_shipping标志设置不正确的问题。 现在，当应用适用的免费送货规则时，所有项目的标志均正确设置。

_AC-15648 - [GitHub问题](https://github.com/magento/magento2/issues/40184) - [GitHub代码贡献](https://github.com/magento/magento2/commit/c10554e1)_

#### 访客添加到购物车：迷你购物车/客户数据“购物车”部分在报告购物车下显示为空白，尽管项目已正确保留

修复了访客迷你购物车在将产品添加到购物车后未立即反映商品的问题。 迷你购物车计数器和下拉列表现在可以正确更新，并且添加的产品会按预期显示在购物车中。

_AC-17973 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2b218686)_

#### AJAX添加到购物车的内联错误消息丢失role=&quot;alert&quot;语义

修复了在店面显示AJAX添加到购物车错误消息但未由屏幕阅读器公告的问题。 添加到购物车错误现在显示在可访问的role=&quot;alert&quot;区域内，以便提供相应的辅助功能支持。

_AC-18036 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2b218686)_

#### 放弃装运金额的后续规则

为确保促销定价准确且严格遵守配置的折扣规则，解决了购物车价格规则计算器中存在的一个缺陷，即低优先级的送货折扣未正确应用

_AC-9612 - [GitHub问题](https://github.com/magento/magento2/issues/37985) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40869)_

#### 即使触发了错误，仍会创建重复订单

修复了仍然可能使用无效客户地址下订单的问题

_ACP2E-4774 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8d95ae6e)_

#### 可配置产品对结账的性能影响(totals-information、estimate-shipping-modules)

在修复之前，当第一个可销售子项在子列表中显示较晚时，对于包含许多子产品的可配置产品，结账请求（如totals-information和estimate-shipping-methods）可能会显着变慢。 修复后，不再发生此性能下降，并且无论第一个可销售子项的位置如何，响应时间都保持不变。

_ACP2E-4805 - [GitHub代码贡献](https://github.com/magento/inventory/commit/30fbdb0f)_

#### 在每次购物车页面查看时重新计算购物车总数

优化了购物车页面上的购物车总计请求。 每次查看购物车页面时，购物车总计会重新计算两次。

_ACP2E-4817 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b63925d9)_

#### 客户地址属性(EAV)城市和街道验证规则与硬编码验证规则冲突。

修复了以下问题：城市验证器错误地拒绝长度超过100个字符（数据库限制为255个字符）的有效城市名称，并且在数据库中长度超过255个字符的街道地址可能会自动被截断，并且\
返回验证错误。 现在，两个验证器对所有地址表都强制实施与最窄数据库列约束一致的限制。

_ACP2E-4861 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b63925d9)_

#### [店面]添加到购物车的“请求的数量不可用”消息间歇性地未在PDP上呈现

修复了库存不可用消息（“请求的数量不可用，请减少数量。”）的问题。 在尝试添加到购物车失败后，间歇性地未显示在产品详细信息页面上。 以前，当购物者反复单击添加到购物车以获取其购物车中已完全保留可用库存的产品时，页面可能会静默刷新，且没有错误反馈。

_ACP2E-5071 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8d70f246)_

#### 在注销时清除持久性时，在自然会话到期时清除持久性购物车=是

修复了浏览器会话过期时清除永久购物车的问题。 以前，启用“注销时清除持久性”后，过期的会话清空购物车并删除永久性Cookie，即使购物者未注销。

_ACP2E-5088 - [GitHub代码贡献](https://github.com/magento/magento2/commit/597c7211)_

#### 重试结帐时，restoreQuote()后未从帐单地址重新同步来宾报价customer_email

修复了重试失败的访客结帐时，使用之前输入的电子邮件而非更新的电子邮件下达订单的问题。

_ACP2E-5188 - [GitHub代码贡献](https://github.com/magento/magento2/commit/597c7211)_

### GraphQL购物车和结账

#### 报价GraphQL API可能会将货币对象而不是ISO货币代码分配给报价字段

更新了Quote GraphQL API以将ISO货币代码分配给报价的存储和报价货币字段，而不是分配货币对象。

_ACP2E-5229 - [GitHub代码贡献](https://github.com/magento/magento2/commit/24667df1)_

### 目录

#### 针对Magento_ConfigurableProductGraphQl、Magento_MsrpConfigurableProduct、Magento_NewRelicReporting和Magento_Swatches模块的[问题] module.xml文件改进。

通过从四个核心子模块中删除多余的Magento_Catalog依赖项，优化了模块声明架构。 此清理解决了依赖关系树中不必要的重复问题，简化了模块加载顺序计算，并改进了长期框架可维护性而没有引入中断性更改。

_AC-10762 - [GitHub问题](https://github.com/magento/magento2/issues/30675) - [GitHub代码贡献](https://github.com/magento/magento2/pull/30638)_

#### 可配置的getUsedProducts函数中可能出现的内存泄漏

修复了处理多个可配置产品导致执行时间和内存使用量随时间增加的问题。
现在可以处理可配置的产品而不需要渐进的减速和内存增加。

_AC-10942 - [GitHub问题](https://github.com/magento/magento2/issues/37639) - [GitHub代码贡献](https://github.com/magento/inventory/commit/8c058c2e)_

#### 在非锚点类别上可见的“按类别购买”筛选器

修复了在“管理员”中禁用类别过滤器后，按类别购物过滤器仍会在非锚点类别上显示的问题。
现在，根据配置的设置，该过滤器在店面中处于隐藏状态。

_AC-10945 - [GitHub问题](https://github.com/magento/magento2/issues/38379) - [GitHub代码贡献](https://github.com/magento/magento2/commit/64eb754d)_

#### 报价和报价项目中applied_rule_ids的数据类型不同

为了确保绝对数据库架构的一致性并防止大批量促销商店上的关键购物车数据不匹配，跟踪活动促销定义的数据列已在父结账结构中展开。

_AC-14518 - [GitHub问题](https://github.com/magento/magento2/issues/39838) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40540)_

#### 如果价格是全局范围的，则无法获取产品收藏集范围的`decimal`属性

为确保在国际设置中准确呈现店面定价和属性，解决了因存储特定的小数值被默认全局值错误地替换而导致的核心数据收集错误。

_AC-15806 - [GitHub问题](https://github.com/magento/magento2/issues/40218) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40419)_

#### GET参数的处理不正确

为了提高平台稳定性并保护结账funnel，添加了块级别的输入验证层，以防止格式错误的URL查询导致店面产品页面崩溃。

_AC-16262 - [GitHub问题](https://github.com/magento/magento2/issues/40405) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40433)_

#### Magento\SalesRule\Model\Plugin\QuoteConfigProductAttributes：：afterGetProductAttributes在所有购物车查询中被触发

为了减少数据库执行压力并消除客户结账期间未优化的数据库命中，已优化销售规则产品配置插件，以便有条件地执行并利用缓存结构。

_AC-16559 - [GitHub问题](https://github.com/magento/magento2/issues/40226) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40251)_

#### [问题] [PHPDOC]修复函数Magento\Sales\Model\Order中的orderComment

为了消除严格的键入限制、提高静态分析准确性并改善开发人员在严格内联引擎(如PHPStan（级别5或更高版本）)下的体验，在销售订单核心子系统中对内联结构文档块进行了标准化。

_AC-16759 - [GitHub问题](https://github.com/magento/magento2/issues/39575) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39572)_

#### [问题] [错误] GraphQL SearchCriteriaValidator未加载 — 由module-graph-ql di.xml数组覆盖删除

为了保留强大的查询验证并强制执行平台护栏，解决了意外禁用SearchCriteriaValidator层的依赖项注入(DI)配置缺陷。

_AC-16959 - [GitHub问题](https://github.com/magento/magento2/issues/40762) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40742)_

#### strpos()要求参数1为字符串，给定数组 | magento/module-eav

为了保护店面的稳定性并提供无中断的客户发现体验，高级目录搜索处理引擎中解决了一个关键的类型不匹配缺陷。

_AC-1706 - [GitHub问题](https://github.com/magento/magento2/issues/33588) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40422)_

#### 客户访问页面时正在创建空的报价记录

在某些情况下，访问店面的产品页面不会创建空的报价记录。
以前，当客户访问店面的产品页面时，会创建一个空的报价记录

_ACP2E-4682 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8d95ae6e)_

#### 产品详细信息页面的“权重”属性在“其他信息”部分中未显示单位后缀

修复了Storefront产品页面上的“重量”属性在“其他信息”或“更多信息”部分中仅显示原始数值而没有配置度量单位（磅或千克）的问题。

_ACP2E-4808 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b63925d9)_

#### [Cloud]目录价格规则激活直到下次强制重新同步才会反映在Live Search中 — 价格信息源同步延迟

修复了激活目录价格规则时，在稍后强制重新同步之前未在Live Search中更新价格的问题。 价格信息源索引器可以在它所依赖的目录规则索引器完成之前运行，因此会导出过时的价格。 依赖项未完成的索引器现在会延迟到下一次cron运行，因此价格馈送始终针对最新价格运行。

_ACP2E-5029 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ec436b10)_

#### [CLOUD] Adobe Commerce Cloud类别规则或运算符逻辑问题

Contains运算符现在接受多个逗号分隔值，以OR匹配形式进行计算。 因此，单个规则行可以与多个术语中的任意术语匹配，而不是只匹配一个术语。

_ACP2E-5061_

#### 对于新添加的产品图像，不会保存替换文本（标签）

修复了由于媒体库中的文件名冲突，上传的文件在保存时重命名后，新上传的产品图像的替换文本（标签）未保存的问题。 以前，图像角色属性(image、small_image、thumbnail)存储正确，但是它们对应的*_label属性会被静默删除，导致店面搜索和列表页面上的替换文本为空。 图库创建处理程序现在将重命名文件解析回其原始图像条目，因此标签将保留给所有分配的图像角色。 因此，在创建产品时输入的替换文字将可靠地保存并呈现在整个店面。

_ACP2E-5216 - [GitHub代码贡献](https://github.com/magento/magento2/commit/24667df1)_

#### 当用户缺少“编辑产品状态”资源时，在admin中打开“添加产品”页时，PHP 8.5“null as array offset”弃用错误

以前，没有“编辑产品状态”权限的管理用户在打开“添加产品”页面时可能会遇到“null as array offset”弃用错误。 此问题已得到修复，因此无论用户的产品状态权限如何，页面都会正确加载。

_ACP2E-5248 - [GitHub代码贡献](https://github.com/magento/magento2/commit/24667df1)_

### 目录，GraphQL

#### 在adminhtml中输入了净价的[GraphQl]产品查询价格筛选器问题

修复了GraphQL产品查询在应用价格过滤器时未考虑征税的问题。
价格过滤器现在会使用显示的含税价格，因此仅返回指定价格范围内的产品。

_AC-6883 - [GitHub问题](https://github.com/magento/magento2/issues/36337) - [GitHub代码贡献](https://github.com/magento/magento2/commit/8b67e8ed)_

### 目录、性能

#### 目录权限索引管道不允许[CLOUD] customer_group_excluded_website

目录权限索引现在排除了从客户组中排除的网站。

_ACP2E-5223_

### 目录，SEO

#### 所有商店视图的url_key更改时未同步类别url_path

以前，在“所有商店视图”范围更改类别的URL键时，可能会使商店范围的后代类别保留具有过时或前缀不正确的url_path，而使用类别自己的商店特定url_path覆盖来编辑类别时，可能会采用其预编辑URL键，而不是新输入的URL键。 此问题现在已修复 — URL键更改会以正确的分层顺序正确地级联到所有存储范围内的子代以及正确的父级路径，并且类别自己的存储范围内的url_path覆盖会使用其刚刚更改的URL键重新计算，因此存储范围内的URL在保存后会立即保持准确。

_ACP2E-5113 - [GitHub代码贡献](https://github.com/magento/magento2/commit/597c7211)_

### 云、框架

#### 启用SymfonyL2后，性能下降和缓存存储不正确

修复了将L1缓存存储路径配置为绝对路径（例如/dev/shm）导致其被静默重定向到var/目录的问题，以及由于阻止Redis操作而导致使大型目录上的缓存标记失效可能导致显着响应时间延迟的单独性能问题。

_ACP2E-4989 - [GitHub代码贡献](https://github.com/magento/magento2/commit/51f6d191)_

### 内容

#### 为不同网站创建的CMS页面在前端显示错误的页面

以前，在多网站设置中，如果没有为每个网站设置Website Restriction登陆页面缓存键值的范围，则会导致在二级网站店面中提供错误的CMS页面。 WebsiteRestriction/Controller/Index/Stub.php中的缓存键现在正确包含通过商店管理器解析的当前网站ID。

_ACP2E-4593_

#### 启用全局客户共享后，客户区段评估仅返回第一个网站的客户，而不是所有分配的网站

修复了在启用全局客户共享的情况下，“客户区段”评估仅从第一个网站返回客户，而不是从所有分配的网站返回客户的问题。

_ACP2E-5079_

#### 在禁用翻译缓存的情况下，页面生成器ajax预览请求返回500错误

现在，无论已启用还是禁用翻译缓存，PageBuilder预览均可正确呈现。 以前，在禁用翻译缓存时，无法呈现PageBuilder预览。

_ACP2E-5118 - [GitHub代码贡献](https://github.com/magento/magento2-page-builder/commit/606e12fd)_

#### 启用“启用旧媒体集”后，动画GIF上传内容会转换为PNG

修复了在启用旧版媒体集后，通过媒体集上传的GIF动画图像转换为PNG的问题。 以前，启用“前端调整大小”时，通过旧媒体集上传的动画GIF会丢失其动画，并另存为静态PNG文件。 动画GIF现在以其原始格式上传和存储。

_ACP2E-5232 - [GitHub代码贡献](https://github.com/magento/magento2/commit/24667df1)_

### 内容/CMS

#### [问题]当图像属性标签包含单引号时，修复产品库选项卡

为了确保管理面板中的目录管理体验可靠且无中断，已解决一个JavaScript格式缺陷，该缺陷完全中断了后端产品工作区界面

_AC-16474 - [GitHub问题](https://github.com/magento/magento2/issues/40519) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40870)_

#### [问题]当访问已调整大小的图像URL但该URL不存在时，提高性能。

为了最大化资产交付响应速度，显着减少服务器磁盘I/O，并防止严重的服务器处理器峰值，目录图像生成子系统已得到优化，可严格按需处理缺失的媒体URL。

_AC-16547 - [GitHub问题](https://github.com/magento/magento2/issues/40399) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40388)_

#### 回归：非UTF-8编码的URI组件仍在2.4.7-p5的CatalogWidget中引发“无法序列化值”

为了消除因生产Web流量错误而导致的严重渲染故障，已增强目录小部件块，以正常处理所请求URL中的非UTF-8数据序列。

_AC-17264 - [GitHub问题](https://github.com/magento/magento2/issues/40824) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40825)_

#### 编辑全局设计配置范围时`Using null as an array offset is deprecated, use an empty string instead`

修复了以下问题：在“内容”>“设计”>“配置”下编辑全局范围时，由于存在已弃用的null数组偏移，导致在PHP 8.5上返回HTTP 500错误。 全局设计配置现在已成功打开，并且没有出现错误。

_AC-17456 - [GitHub问题](https://github.com/magento/magento2/issues/40886) - [GitHub代码贡献](https://github.com/magento/magento2/commit/515d3dd3)_

### 框架

#### 当媒体数据库存储未使用或禁用时，从media_storage_file_storage中选择

为了减少不必要的数据库查询开销并消除噪音系统异常，媒体文件同步层已经过优化，当系统明确配置为使用本地文件系统时，可以绕过数据库存储检查

_AC-10586 - [GitHub问题](https://github.com/magento/magento2/issues/38116) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40480)_

#### 当Cookie存储为数组时，异常构造函数引发致命错误

修复了无效的存储Cookie值导致PHP严重错误的问题。
当存储Cookie包含无效值时，Magento现在会正确引发“存储参数无效”异常。

_AC-10888 - [GitHub问题](https://github.com/magento/magento2/issues/38365) - [GitHub代码贡献](https://github.com/magento/magento2/commit/7aecc9f1)_

#### [问题] Magento\Customer\Model\Address\Config中使用静态常量

修复了自定义地址配置类必须复制getFormats()才能使用自定义地址模板路径的问题。 自定义地址配置现在可以使用静态常量定义自己的模板路径，而无需复制方法。

_AC-12906 - [GitHub问题](https://github.com/magento/magento2/issues/39135) - [GitHub代码贡献](https://github.com/magento/magento2/commit/29a7cdbe)_

#### 无法在产品收藏集上使用processFilter

修复了使用FilterProcessor将多个过滤器应用于产品集合时导致PHP错误的问题。 现在可以使用多个筛选条件正确筛选产品集合。

_AC-15018 - [GitHub问题](https://github.com/magento/magento2/issues/40014) - [GitHub代码贡献](https://github.com/magento/magento2/commit/7aecc9f1)_

#### 大型目录可能存在的索引器性能问题 — 批量插入和锁定整个CL表以标识最新版本

为了保障大型企业目录上的数据库性能，系统数据库索引器管道已得到强化，可以解析有界批次中的计划数据修改，从而消除高压数据库锁定。

_AC-16238 - [GitHub问题](https://github.com/magento/magento2/issues/40331) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40546)_

#### [问题]性能改进

为了消除不必要的内存分配并降低运行时处理开销，已重构几个核心字符串操作例程以利用优化的PHP本机行为。

_AC-16565 - [GitHub问题](https://github.com/magento/magento2/issues/40383) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40375)_

#### [问题]修复了对非GNU Linux系统上的GLOB_BRACE的支持

为确保在轻量级虚拟化环境中实现无缝部署功能，修复了一个关键路径发现错误，以完全恢复对使用非GNU库（如Alpine Linux Docker映像）的系统的执行支持。

_AC-16568 - [GitHub问题](https://github.com/magento/magento2/issues/40552) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40538)_

#### 营销参数已添加回用于创建内置FPC标识符的查询

为了提高缓存命中率并消除服务器性能退化，在本机内置全页缓存(FPC)系统中修复了一个结构缺陷，该缺陷导致营销和跟踪查询参数意外地重新引入缓存标识符签名中。

_AC-16583 - [GitHub问题](https://github.com/magento/magento2/issues/40350) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40349)_

#### 在消息队列通信中添加对具有提升属性的纯对象的支持

为了支持现代PHP开发实践并简化异步架构工作流，已增强框架反射引擎，以利用公共、提升和只读构造函数属性原生处理数据传输对象(DTO)。

_AC-16672 - [GitHub问题](https://github.com/magento/magento2/issues/36660) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40457)_

#### [问题]修复： Real列类型内部检查跳过无符号/可空处理器，使用默认值

为了确保准确的系统设置跟踪，解决了数据库抽象缺陷，其中声明性模式验证命令永久报告没有显式精度或缩放属性的DOUBLE UNSIGNED列的挂起修改更改。

_AC-16758 - [GitHub问题](https://github.com/magento/magento2/issues/40646) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40582)_

#### [功能]支持管理配置中单个选择选项的“已禁用”状态

为了增强后端表单灵活性并为开发人员提供粒度布局控制，引入了框架级别的支持，以将单个选项标记在表单元素内标记为不可选。

_AC-16761 - [GitHub问题](https://github.com/magento/magento2/issues/40564) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40565)_

#### ⚡性能：在StoreManager中缺少内存以及存储模块中的插件开销

为了大幅降低CPU的执行负担并最大程度地减少不必要的应用程序内存流失，已实施了一个关键配置值缓存例程来截获冗余存储检查进程。

_AC-16838 - [GitHub问题](https://github.com/magento/magento2/issues/40706) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40732)_

#### [问题]修复：在JwkFactory中删除无效的openssl_free_key()代码路径

为了清理结构性技术债务并使加密工具与现代执行配置文件保持一致，已从JSON Web密钥实用程序后端清除旧版资源释放挂接。

_AC-16958 - [GitHub问题](https://github.com/magento/magento2/issues/40761) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40688)_

#### [问题] PHPDoc更正拼写

为了保持高代码质量标准并提高集成开发环境(IDE)代码提示准确性，已对核心框架模块中的内联代码文档层应用了结构清理。

_AC-16960 - [GitHub问题](https://github.com/magento/magento2/issues/40763) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40745)_

#### [问题] perf(di:compile)：在Type、Config/Reader和ClassReader中缓存ReflectionClass实例化

为了显着加快编译时间并最大化连续集成(CI)部署吞吐量，已优化内部依赖项注入编译器后端(`setup:di:compile`)，以消除冗余的PHP反射周期。

_AC-17077 - [GitHub问题](https://github.com/magento/magento2/issues/40796) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40615)_

#### [问题]更新Filter.php以允许`{{block template="Magento_Module::path/to/template.phtml"}}`并将\Magento\Framework\View\Element\Template设置为默认类

为了简化内容创建并使CMS指令与模板布局标准保持一致，核心标记标记标记处理系统已得到增强，可支持没有显式类定义的块声明。

_AC-17078 - [GitHub问题](https://github.com/magento/magento2/issues/38477) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38469)_

#### [问题] perf(di:compile)：在编译期间将侦听配置范围读取记忆体

为了显着加快站点部署和自动后端编译，已优化依赖项注入编译器(`setup:di:compile`)以消除冗余XML解析操作。

_AC-17313 - [GitHub问题](https://github.com/magento/magento2/issues/40852) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40614)_

#### 将underscore.js升级到1.13.8以防止出现安全漏洞

捆绑的Underscore.js库(lib/web/underscore.js)已从1.13.7升级到1.13.8。无需更改配置。

_AC-17349 - [GitHub问题](https://github.com/magento/magento2/issues/40857) - [GitHub代码贡献](https://github.com/magento/magento2/commit/12d0be1e)_

#### 当部署目标为符号链接时，magento-composer-installer会自动取消填充设置/（和其他映射的dir）

修复了在将部署目标配置为符号链接时，magento-composer-installer无法以静默方式填充setup/和其他Composer映射目录的问题。 这可能会导致文件丢失和Commerce部署不完整。

_AC-17360 - [GitHub问题](https://github.com/magento/magento2/issues/40864)_

#### 使用Symfony Cache适配器时，缓存预加载键不再需要ID前缀

现在可以配置Symfony缓存适配器的预加载键(preload_keys)，而不使用缓存id_prefix。 以前，按照记录的配置并在每个键上包含前缀（例如061_SYSTEM_DEFAULT）会导致不预加载键。 现在，您可以完全按照应用程序的请求指定键（例如，SYSTEM_DEFAULT），Adobe Commerce会自动应用id_prefix。

_AC-17407 - [GitHub问题](https://github.com/magento/magento2/issues/40877) - [GitHub代码贡献](https://github.com/magento/magento2/commit/3a6b9667)_

#### [问题]当类别属性具有“frontend_input”时，修复PHP 8.5弃用……

修复了当类别属性frontend_input设置为null时，在“管理员”面板中打开类别在PHP 8.5上导致错误的问题。 类别页面现在已打开，可以成功编辑，而不会出现弃用错误。

_AC-17499 - [GitHub问题](https://github.com/magento/magento2/issues/40908) - [GitHub代码贡献](https://github.com/magento/magento2/commit/ecbeba3a)_

#### [问题]替换已弃用的PHPUnit断言和测试存根配置

通过替换7个已弃用的PHPUnit用途，更新了Magento 2的核心单元测试套件，以便将来进行PHPUnit升级。 这些更改用于处理测试存根上的`isType()`声明和`with*()`配置，这些模式会在当前PHPUnit版本中触发弃用通知，并计划在PHPUnit 13或更高版本中移除。

_AC-17750 - [GitHub问题](https://github.com/magento/magento2/issues/41040) - [GitHub代码贡献](https://github.com/magento/magento2/pull/41033)_

#### GraphQL order_date和注释时间戳在非en_US区域设置下返回错误的日历日期（IntlDateFormatter错误解析） — AC-14431修复不完整

修复了GraphQL订单日期可能显示法语和德语区域设置的错误日历日期的问题。
现在，订单日期和相关的评论时间戳将返回正确的日期和时间。
改进了日期格式，以便应用程序能够可靠地解析GraphQL日期值。
en_US区域设置的现有行为保持不变。

_AC-18084 - [GitHub代码贡献](https://github.com/magento/magento2/commit/d10ab92b)_

#### [问题]移除禁止使用的@author标记

为确保与核心技术准则严格保持一致，已完成增量代码维护清理，以清理多个系统模块中的内联资源文档块。

_AC-8366 - [GitHub问题](https://github.com/magento/magento2/issues/37248) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36993)_

#### [问题]从`Magento_Catalog`中删除禁止的`@author`标记（第2部分）

为了确保与Magento的统一代码投放准则完全一致，已执行增量清理过程，以系统地消除核心店面资源模型中不符合规范的文件注释。

_AC-8370 - [GitHub问题](https://github.com/magento/magento2/issues/37247) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36988)_

#### 分层价格存储界面删除错误不会删除所有分层价格

解决了TierPriceStorage中存在的一个问题：通过更新价格ID匹配逻辑以考虑分配的网站ID，删除跨多个网站的产品层价格未能删除所有价格。

_AC-9738 - [GitHub问题](https://github.com/magento/magento2/issues/37949) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40557)_

#### [B2B]采购订单未使用ActiveMQ自动转换为销售订单

修复了将ActiveMQ与STOMP协议一起使用时，由cron启动的用户不会处理消息的问题。 因此，自动批准的采购订单未转换为销售订单。 现在，STOMP队列的消息处理更加可靠，并且与DB和AMQP队列实施一致。

_ACP2E-4349 - [GitHub代码贡献](https://github.com/magento/magento2/commit/08b91f1a) - [GitHub代码贡献](https://github.com/magento/inventory/commit/239464da)_

#### 使用配置的AWS S3存储空间导出失败

配置AWS S3远程存储后，产品导出现在可正常工作。 以前，由于存储驱动程序中的路径解析无效，无法将导出的文件写入S3。

_ACP2E-4786 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8d95ae6e)_

#### 索引器与“use_application_lock”和“file”提供程序陷入自锁循环

修复了当索引器use_application_lock设置与文件锁定提供程序一起启用时，在重新索引过程中索引器无限期挂起的问题。 现在，重新索引操作按预期完成。

_ACP2E-5027 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ec436b10)_

#### 在云UI下设置MAGENTO_DC变量导致性能降低

修复后，每当请求的键不存在并定义了某些环境变量时，都不会重新加载部署配置。

_ACP2E-5094 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2b9e8316)_

#### [CLOUD]格式错误的URL路径在URL重写路由器中返回HTTP 500而不是404

修复了格式错误的店面URL返回HTTP 500错误页面而不是标准404 Not Found的问题。 以前，某些格式错误的请求路径会在URL重写解析期间导致未捕获的错误。

_ACP2E-5154 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4d0357d7)_

#### [CLOUD] PHP 8.5兼容性 — ComponentRegistrar：：getPath() null数组偏移崩溃安装程序:static-content:在2.4.9上部署（紧凑策略）

修复了在编译使用//@magento_import指令的模块LESS文件时，`setup:static-content:deploy`在PHP 8.5上失败并出现“Using null as a array offset”错误的问题。 现在，静态内容部署已在PHP 8.5上成功完成。

_ACP2E-5183 - [GitHub代码贡献](https://github.com/magento/magento2/commit/597c7211)_

#### [CMS]在保存带有锚点href且后跟另一个属性的HTML块时，出现误报“所提供的无效CMS内容”

启用cms/wysiwyg/force_valid后，包含标准锚点链接（例如`&lt;a href="https://example.com/page" target="_blank" rel="noopener">`）的CMS内容不再触发虚假的“提供的HTML内容无效”验证警告或保存失败。

_ACP2E-5203 - [GitHub代码贡献](https://github.com/magento/magento2/commit/24667df1)_

### 框架，GraphQL

#### 如果稍后配置使用了数字键，将替换di.xml数组项

为了保护体系结构数据完整性和提高模块可扩展性，已解决了依赖项注入(DI) XML解析引擎中的一个核心错误，在该引擎中，在模块编译期间，使用数字键“0”的数组配置被自动覆盖或删除。

_AC-8102 - [GitHub问题](https://github.com/magento/magento2/issues/36861) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40880)_

### GraphQL

#### 如果属性代码是模型代码，addProductsToCart会对custom_attributesV2引发错误

修复了以下问题：当产品具有代码模型的自定义属性时，addProductsToCart返回内部服务器错误。 现在，可通过custom_attributesV2正确检索自定义属性。

_AC-16987 - [GitHub代码贡献](https://github.com/magento/magento2/commit/809ba93c)_

#### 当stock_status为IN_STOCK时，GQL数量null

产品GraphQL查询中的数量字段错误地为自定义MSI库存中的库存产品返回了null。 在获取实际库存数量之前，解析程序正在对cataloginventory/options/not_available_message配置值上的响应进行选通，并且此配置的XML默认值（2 — “没有足够的物料可供销售”）导致在任何新存储上返回null，而没有明确的管理覆盖。
现在在解决可销售数量后评估该检查。 仅当产品没有可用库存(saleableQty &lt;= 0)并且存储明确配置了“没有足够的商品可供销售”时，才会返回null。 无论此配置设置如何，库存产品始终返回其实际可销售数量。 配置读取也被更正为使用存储范围，以便遵循存储级覆盖。

_ACP2E-4840 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b63925d9)_

#### [CLOUD] BundleProduct items.options.price在目录价格范围=网站时忽略网站范围的价格

修复了GraphQL中网站范围的捆绑包选项价格：解决了将目录价格范围设置为网站时，通过GraphQL查询捆绑包产品选项时返回全局“所有商店视图”价格而不是网站范围的价格的问题。 Magento\BundleGraphQl\Model\Resolver\Links\Collection解析程序现在可以正确检查价格范围，并根据请求的商店范围加入特定于网站的选择价格。

_ACP2E-5057 - [GitHub代码贡献](https://github.com/magento/magento2/commit/597c7211)_

#### 因并发customerCart GraphQL请求竞争条件而为客户创建的活动购物车重复

现在，系统可确保每个客户只创建一个活动购物车，而不管请求并发情况如何。 以前，如果对同一验证过的客户同时执行两个customerCart GraphQL查询或对其执行POST /V1/carts/我的REST请求，而后者没有处于活动状态的购物车，则可能会导致数据库中出现重复的活动购物车记录。

_ACP2E-5077 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8d70f246)_

#### [Cloud]处理了QuoteGraphQl中记录到exception.log的GraphQlNoSuchEntityException，导致日志增长不受限制

修复了预期的GraphQlNoSuchEntityException错误（例如为已过期或无效的购物车ID返回的错误）写入var/log/exception.log的问题。 这些已处理的错误仍会作为正常的GraphQL错误响应返回到客户端，但它们不再填充异常日志。

_ACP2E-5122 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2b9e8316)_

### GraphQL、库存/MSI

#### GraphQL：作为网站ID传递到ProductStock：：isProductAvailable中的商店ID会导致“找不到网站”错误

以前，由于在需要网站ID的情况下使用了商店ID，因此某些店面在将商品添加到购物车时检查产品库存可用性时，可能会遇到未发现网站错误。 此问题已得到修复，因此库存可用性检查会使用正确的网站上下文，以防止出现错误。

_ACP2E-5242 - [GitHub代码贡献](https://github.com/magento/magento2/commit/597c7211)_

### GraphQL，订购

#### [功能请求]在更改装运承运人时清除商店提货数据中的多余项

当从店内取货切换到到家交货方法时，取货位置和关联的商店地址从购物车中删除。 必须提供有效的送货地址，然后才能下订单。

_ACP2E-4973 - [GitHub代码贡献](https://github.com/magento/inventory/commit/57047d29)_

### GraphQL，产品

#### 愿望清单值数据中缺少键\&quot;model\&quot;

修复了通过GraphQL查询愿望清单详细信息时返回内部服务器错误的问题。
现在，愿望清单查询成功返回，没有“愿望清单值数据中缺少键模型”错误。

_AC-8062 - [GitHub问题](https://github.com/magento/magento2/issues/36909) - [GitHub代码贡献](https://github.com/magento/magento2/commit/515d3dd3)_

### 导入和导出

#### [问题]修复导入iframe可见性

为确保Magento管理面板中的用户界面干净整洁，已解决模板布局缺陷，即在执行数据验证期间，商店经理可以看到内部后台执行iframe

_AC-13250 - [GitHub问题](https://github.com/magento/magento2/issues/39267) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39265)_

#### [问题]修复：产品导入中的硬编码xxh128哈希算法

为了清理内部子系统并利用现代系统优化基线，产品导入组件已简化为使用单个永久哈希算法。

_AC-16967 - [GitHub问题](https://github.com/magento/magento2/issues/40770) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40687)_

#### 当验证策略设置为“出错时停止”时，出现验证错误后，导入按钮仍然可用

修复了当验证策略设置为“出错时停止”时，在数据验证失败后，导入按钮仍显示在验证结果中的问题。 以前，即使所有记录都未能通过验证，按钮仍会出现，并且可以单击该按钮，因此尝试的导入会立即终止。

_ACP2E-5124 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2b9e8316)_

### 安装和管理

#### [云]更正过时的现有ISO细分代码

更新了13个国家的区域代码以符合ISO 3166-2标准。 以前，某些区域代码与标准不匹配，这可能会导致第三方集成和国际合规性问题。 比利时、哥伦比亚、西班牙、法国、意大利和拉脱维亚的新增地区。 为奥地利、哥伦比亚、哥斯达黎加、德国、爱沙尼亚、西班牙、芬兰、法国、印度、冰岛和拉脱维亚更新了区域代码。

_ACP2E-4495 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9b6a8bd9)_

### 库存/MSI

#### [CLOUD]礼品卡和相关不可销售的WF-1688

当使用非默认库存/来源并保存相关（相关或追加或交叉销售）产品时，产品不会消失。

_ACP2E-4741 - [GitHub代码贡献](https://github.com/magento/inventory/commit/30fbdb0f)_

#### 捆绑产品库存状态不一致

以前，当商店管理员从管理员面板手动更新捆绑产品的库存状态时，更改未反映在配置了多个库存源的商店的店面上。 尽管管理员进行了更改，客户仍会继续看到过时的库存状态。

此问题已修复。 现在，在“管理员”面板中所做的捆绑产品库存状态更改可正确传播到所有已配置的库存源和库存位置，从而确保客户可始终在店面中看到准确的库存可用性。

_ACP2E-4866 - [GitHub代码贡献](https://github.com/magento/inventory/commit/db712a46)_

#### GetStockIdForCurrentWebsite.php引发的NoSuchEntityException“未找到请求的存储”

修复了使用无效的？store=查询参数访问店面页面导致每个此类请求在CRITICAL级别记录NoSuchEntityException的问题。 以前，MSI Stock数据插件将原始存储代码直接传递到StoreManager：：getStore()，而不处理存储不存在的情况，从而导致异常日志混乱。

_ACP2E-5003 - [GitHub代码贡献](https://github.com/magento/inventory/commit/1bf25e46)_

### 订购

#### 当范围为前端或webapi_rest范围时，取消未执行的订单观察器

修复了从店面或通过webapi_rest范围取消订单时未正确执行取消观察者的问题。 现在，取消订单后，礼品卡金额将恢复到客户的商店贷方。

_AC-16353 - [GitHub问题](https://github.com/magento/magento2/issues/40414) - [GitHub代码贡献](https://github.com/magento/magento2/commit/64eb754d)_

#### 在Admin中编辑现有订单时（例如，“每位客户的使用量= 1”），不会应用使用量有限的购物车价格规则

修复了在管理员中编辑现有订单时，购物车价格规则折扣和使用限制被删除的问题。 现在，编辑订单时，即使达到使用限制，原始折扣也会保留。

_AC-16671 - [GitHub问题](https://github.com/magento/magento2/issues/40624) - [GitHub代码贡献](https://github.com/magento/magento2/commit/c10554e1)_

#### 捆绑包产品的管理面板中出现最小数量验证错误

为了改进后端订购体验并在生成手动报价单时删除功能块，已解决在管理订单创建期间子项目参数评估不正确的验证错误。

_AC-17193 - [GitHub问题](https://github.com/magento/magento2/issues/40812) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40863)_

#### 在前端订单视图中捆绑产品子项数量不一致

店面订单详细信息页面现在将显示每个捆绑包产品选项的总订购数量。 以前，每个子选项的quantity列显示父捆绑的订购数量，而不是每个选项的总订购数量。

_ACP2E-4820 - [GitHub代码贡献](https://github.com/magento/magento2/commit/b63925d9)_

#### [ASUS] OrderMutex：：execute()缺少DeadlockException重试导致永久性ShipOrder/InvoiceOrder失败 — 

现在，在出现死锁的情况下，可以成功解决ShipOrder和InvoiceOrder操作。
以前，ShipOrder和InvoiceOrder操作由于死锁而永久失败

_ACP2E-4913 - [GitHub代码贡献](https://github.com/magento/magento2/commit/51f6d191)_

#### 在发票生成期间对父可配置项目的FPT/WEEE行级计算不正确

现在，可配置产品的发票和贷项通知单总计正确包含了固定产品税额。 以前，FPT行层金额不会传播到父可配置订单项目，从而导致发票和贷项通知单合计低于FPT金额的订单总计。

_ACP2E-4977 - [GitHub代码贡献](https://github.com/magento/magento2/commit/51f6d191)_

#### 从管理员创建订单时，在页面刷新时修改的产品数量

解决了刷新页面可能会导致多次添加同一SKU的问题。

_ACP2E-5046 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ec436b10)_

#### 并发异步电子邮件cron工作人员为同一订单发送重复的订单确认电子邮件

解决了并发电子邮件工作人员可能为同一订单发送重复订单确认电子邮件的问题。

_ACP2E-5059 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8d70f246)_

#### [CLOUD] sales_clean_quotes cron作业内存不足

修复了在清除大量过期报价时sales_clean_quotes cron作业内存不足的问题。 以前，作业会保留内存中每个已处理的引号，并在删除所有过期的引号之前以内存耗尽错误终止。

_ACP2E-5137 - [GitHub代码贡献](https://github.com/magento/magento2/commit/4d0357d7)_

### 订购，促销

#### [云]添加多个优惠券以进行重新排序时出现问题

解决了在无效优惠券尝试失败后，不再将有效优惠券应用于订单的问题。 现在，如果输入了无效的优惠券，则之前应用的所有有效优惠券都将保持正确应用。

_ACP2E-4810_

#### 当规则与捆绑包父项匹配时，固定金额类别购物车价格规则对非匹配动态捆绑包子项进行折扣

修复了当具有类别条件的固定金额购物车价格规则仅与捆绑包父项匹配时，该规则错误地将折扣应用于动态价格捆绑包的所有子项的问题。 以前，不属于目标类别的捆绑子项将获得按比例分配的折扣份额，而不是零。

_ACP2E-5075 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2b9e8316)_

### 支付

#### config:show命令不适用于较新版本中的部分路径

`config:show`命令现在接受部分配置路径（如付款），并显示该路径下的配置值。 以前，运行`php bin/magento config:show`付款返回错误： `The "payment" path doesn't exist. Verify and try again.`，而不是显示正确的值。

_AC-13908 - [GitHub问题](https://github.com/magento/magento2/issues/39610) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40432)_

### 性能

#### 安装程序:upgrade正在将索引器模式从`schedule`更改为`save`，从而显着减慢其速度

解决了一个长期存在的问题，即运行bin/magento设置:upgrade会无意中将索引器模式从“按计划保存”更改为“按计划保存”，并且不必要地删除并重新创建数据库触发器，从而大大减少停机时间并防止在大型目录上部署期间出现性能瓶颈。

_AC-2423 - [GitHub问题](https://github.com/magento/magento2/issues/33386) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40643)_

#### Valkey LAYOUT缓存键为大型产品目录占用了大量空间

以前，每个产品在每次存储视图时都生成自己的布局缓存项，导致大型目录的Redis/Valkey内存消耗过多。 现在，布局缓存条目在具有相同类型、属性集和存储视图的产品之间共享，无论目录大小如何，都会限制缓存增长。

_ACP2E-4908 - [GitHub代码贡献](https://github.com/magento/magento2/commit/9b6a8bd9)_

#### 产品查询出现死锁错误

修复了在包含按类别筛选的CatalogWidget产品列表的页面上发生的InnoDB死锁问题，此问题在计划模式价格索引器同时运行时发生。

_ACP2E-5052 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ec436b10)_

#### [Quans] Adobe Commerce URL解析查询性能下降

修复了GraphQL路由查询始终呈现完整CMS页面内容的问题，包括页面生成器小组件执行和产品收藏集加载，即使仅请求了URL路由元数据(relative_url、redirect_code、type)也是如此。 以前，这会导致不必要的构件/产品渲染，并导致每个请求中包含Page Builder构件的CMS页面的数据库查询显着增加。

_ACP2E-5143 - [GitHub代码贡献](https://github.com/magento/magento2/commit/597c7211)_

#### 当“客户帐户共享”设置为“全局”时，“管理客户编辑”性能会降低

修复了“管理员客户编辑”页面上的性能问题：当共享客户帐户设置为“全局”时，加载时间和HTTP响应大小呈二次增长。

_ACP2E-5164 - [GitHub代码贡献](https://github.com/magento/magento2/commit/24667df1)_

### 产品

#### “点击价格”弹出窗口中的“添加到购物车”按钮不起作用。

修复了产品列表页面上“单击价格”弹出窗口中的“添加到购物车”按钮未将产品添加到购物车的问题。
现在，可以从弹出窗口将产品成功添加到购物车。

_AC-11896 - [GitHub问题](https://github.com/magento/magento2/issues/30356) - [GitHub代码贡献](https://github.com/magento/magento2/commit/29a7cdbe)_

#### BundleGraphQL解析器创建单独的延迟产品实例，从而取消查询批量处理(N+1)

为了大幅提高API响应吞吐量并最大程度地减少服务器开销，GraphQL解析层已得到优化，可强制对捆绑产品进行真正的查询批处理，从而消除会消耗性能的N+1数据库漏洞。

_AC-16647 - [GitHub问题](https://github.com/magento/magento2/issues/40595) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40867)_

#### EAV Select和Multiselect属性验证错误地拒绝值为“0”的选项标签

为了提高数据完整性并消除客户和目录表单中的意外提交错误，已解决一个验证缺陷：EAV核心框架错误地拒绝了包含精确字符串值“0”的选项标签

_AC-16986 - [GitHub问题](https://github.com/magento/magento2/issues/40634) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40827)_

#### 当用户的角色限制在特定范围时，无法保存可自定义的选项标签和可自定义的选项标题

修复了由访问受限于特定存储范围的管理员用户编辑时恢复可自定义选项标签和标题的问题。
现在，已正确保存所选范围的更新标签和标题。

_AC-2684 - [GitHub问题](https://github.com/magento/magento2/issues/35210)_

#### 礼品卡价格在愿望清单中显示不正确

修复了配置的礼品卡最低价格在愿望清单中显示为$0.00的问题。
正确的最低礼品卡价格现在显示在“我的愿望清单”页面和“愿望清单”侧边栏小部件上。

_AC-8037_

#### 产品警报消费者忽略商店范围的系统/stmp/disable

产品警报使用者现在将商店范围的系统/stmp/disable设置考虑在内。

_ACP2E-4870 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ec436b10)_

#### 前端比较页面显示错误的简短描述标签翻译

以前，在比较产品页面上，可比较属性标签（如简短描述）显示的翻译来自不同的商店视图，而不是当前商店的视图。 现在，会显示正确的商店特定翻译。

_ACP2E-4929 - [GitHub代码贡献](https://github.com/magento/magento2/commit/08b91f1a)_

#### Page Builder产品轮播忽略类别位置排序顺序，改为按entity_id DESC顺序显示产品

修复了以下问题：在设置为按类别位置排序的页面生成器轮播中显示的产品在店面中的显示顺序不正确。 现在，产品将按照在Admin → Catalog → Categories → Products选项卡中配置的顺序显示。

_ACP2E-4980 - [GitHub代码贡献](https://github.com/magento/magento2/commit/51f6d191)_

### 提升规则

#### 当一个应用的购物车价格规则具有折扣数量步骤值时，折扣计算错误

修复了在应用多个购物车价格规则并且一个规则具有折扣数量步骤（购买X）值时折扣计算不正确的问题。
现在可以正确计算所有合格数量的折扣。

_AC-12307 - [GitHub代码贡献](https://github.com/magento/magento2/commit/c10554e1)_

### 提升、定位

#### 相关产品将被自动删除

修复了当产品的属性发生更改并且它停止匹配Target规则时未删除相关产品的问题。 以前，mview索引器无法删除过时的规则 — 产品关联，并在重新索引期间发出PHP警告（未定义数组键）。

_ACP2E-4836_

### 返回

#### RMA — 添加退货评论API — 会向发件人（销售代表）而不是客户触发电子邮件

修复了通过Returns API发送的退货评论电子邮件发送给销售代表，但未发送给客户的问题。
现在，当通过启用了客户通知的API添加返回评论时，客户会收到电子邮件通知。

_AC-1138 - [GitHub问题](https://github.com/magento/magento2/issues/33985)_

### 销售

#### 从rest api V1/orders或V1/orders/create端点下订单时，`[Order][REST]` sales_order_items product_options列缺少数据

修复了通过REST API创建的订单项目不包含完整product_options数据的问题。 现在，通过REST API创建的订单的自定义选项标签和相关选项详细信息均可正确保存。

_AC-15187 - [GitHub代码贡献](https://github.com/magento/magento2/commit/8b67e8ed)_

#### 由于绑定的updated_at时间戳而启用了异步网格索引时，销售订单网格永久停滞在过时状态

修复了在启用异步网格索引时，销售订单网格可能会因旧订单状态而卡住的问题。 现在，订单网格状态会正确更新以匹配当前的订单状态，包括在同一秒内发生多次订单更新的情况。

_AC-17118 - [GitHub代码贡献](https://github.com/magento/magento2/commit/478f8e7c)_

### 安全性

#### [问题]更新js.phtml DOM文本（重新解释为HTML）

为加强平台的安全基线并将恶意输入执行的风险降至最低，对处理动态DOM更新的主要内联脚本模板进行了重构，以消除跨站点脚本(XSS)注入矢量。

_AC-12118 - [GitHub问题](https://github.com/magento/magento2/issues/38821) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38804)_

### 配送

#### USPS REST API问题，最大包重量的比率不正确

修复了订单拆分为多个包时（例如，大于“最大包重量”）的运费估计不正确的问题。 现在，运营商会为每个包请求费率并合计金额，这与旧版Web工具流程保持一致。

_ACP2E-4813 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6c67a9b5)_

### 暂存和预览

#### 计划更新预览模式中的控制台错误

修复了当两个更新共享相同的开始时间时，因JavaScript控制台错误而导致暂存更新的预览页面无法正确加载的问题。 以前，签名的预览URL使用的递增版本ID与预览JavaScript派生的时间戳不匹配，从而导致签名不匹配，并阻止页面在预览模式下正确加载。

_ACP2E-4828_

#### 安装:upgrade在Magento_CatalogStaging数据修补程序上花费太长时间，因为存储审阅和类别数太多

修复了CE-to-EE数据迁移修补程序未将计划的类别设计更新和产品特价正确迁移到暂存更新中的问题。 由于不正确的暂存上下文方法，具有计划设计日期的类别生成了空的暂存更新。 当PHP 8.1+上上次迁移运行中有NULL日期时间值时，将静默跳过产品。 此外，通过仅加载受影响的类别和产品而不是迭代完整目录来提高迁移性能。

_ACP2E-5009_

#### 内容暂存功能板目录价格规则网格显示重复数据

目录价格规则网格现在可以正确显示分配给暂存更新的每个目录价格规则的唯一详细信息。 以前，如果将两个或多个目录价格规则分配给同一个暂存更新时，内容暂存功能板中该更新页面上的“目录价格规则”网格显示的行数正确，但每行错误地显示的是相同的（最后一个）规则数据，而不是每个规则自己的详细信息。

_ACP2E-5097_

### 税金

#### 没有为父产品设置base_wee_tax_applied_amount

现在，会为数据库表（如sales_order_item、sales_invoice_item、sales_creditmemo_item）中的可配置产品填充base_weee_tax_applied_amount值，而不只是为其子项填充

_ACP2E-4922 - [GitHub代码贡献](https://github.com/magento/magento2/commit/08b91f1a)_

### 测试框架

#### [问题]更新GraphQL测试Client.php以进行不区分大小写的子字符串比较

修复了标头使用其他字母大小写时，GraphQL API测试无法识别Set-Cookie标头的问题。 测试现在可以正确处理Set-Cookie、set-Cookie和SET-COOKIE标头。

_AC-15337 - [GitHub问题](https://github.com/magento/magento2/issues/39713) - [GitHub代码贡献](https://github.com/magento/magento2/commit/c10554e1)_

#### WebAPI GraphQL功能测试速度非常慢

为了优化构建投放设置和加快持续集成(CI)环境，通过将缓存清除行为从外部系统命令调用转换为本机进程内内存处理，解决了测试基础架构瓶颈问题。

_AC-15395 - [GitHub问题](https://github.com/magento/magento2/issues/39725) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40804)_

### UI框架

#### Minicart不能在同一页面中使用两次

为了向前端开发人员提供更大的布局灵活性，已解决了一个长期存在的核心UI限制，从而允许在单个页面布局上独立存在和更新多个微型卡块（例如，页眉中一个和页脚中另一个块）。

_AC-12579 - [GitHub问题](https://github.com/magento/magento2/issues/38958) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40871)_

### from-github

#### [问题]修复(pagecache)：将PATCH识别为Varnish VCL中的有效HTTP方法

Magento的默认清漆VCL现在将PATCH识别为有效的HTTP方法，因此REST API部分更新请求（例如PATCH /rest/V1/products/:sku）将传递到后端而不是管道传输。 修复了将全页缓存设置为Varnish时PATCH调用失败或行为不正确的问题。

_AC-16954 - [GitHub问题](https://github.com/magento/magento2/issues/40757) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40657)_

#### [问题]替换VCL中的所有gad_*参数

为了消除动态广告营销活动导致的性能下降，已更新应用程序的缓存层，以主动忽略所有Google Ads gad_*查询字符串。 这样可防止外部营销活动链接使页面缓存失效并减慢目标页面的速度

_AC-16980 - [GitHub问题](https://github.com/magento/magento2/issues/40781) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40780)_

#### [问题]修复：将bootstrap中的最低PHP版本检查更新为8.3

为了防止混淆运行时错误并改进开发人员安装故障排除，系统引导框架内的本机PHP环境验证器已按照应用程序的实际核心要求引入。

_AC-17312 - [GitHub问题](https://github.com/magento/magento2/issues/40851) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40686)_

#### 安装`igbinary`并使用默认文件缓存时，`health_check.php`返回500 （清漆503）

修复了在使用默认文件缓存后端安装igbinary时，health_check.php返回HTTP 500的问题。 运行状况检查现在接受没有显式后端密钥的有效缓存配置，从而阻止Varnish将后端标记为不正常并返回HTTP 503。

_AC-17400 - [GitHub问题](https://github.com/magento/magento2/issues/40876) - [GitHub代码贡献](https://github.com/magento/magento2/commit/8b67e8ed)_

#### [问题]修复：更新gzip类型并删除nginx配置中的IE6解决方法

为了提高页面加载速度并优化网络资产交付，已对后备服务器配置进行了现代化处理，以更好地支持现代店面组件并消除旧的技术开销

_AC-17498 - [GitHub问题](https://github.com/magento/magento2/issues/40774) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40681)_

#### [问题]尝试修复不稳定的graphql OrderStatusChangeDateTest。

为了提高持续集成(CI)可靠性并减少误报构建失败，已在WebAPI功能测试套件中解决了争用情况。 GraphQL订单状态验证测试(OrderStatusChangeDateTest)以前由于PHP内存和MySQL时间戳之间的细微定时差异而遇到间歇性故障

_AC-17959 - [GitHub问题](https://github.com/magento/magento2/issues/41126) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40618)_
