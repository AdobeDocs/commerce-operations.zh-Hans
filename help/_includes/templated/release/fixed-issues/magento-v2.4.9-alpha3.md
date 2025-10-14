---
source-git-commit: 151272eed6c4bb2e1c2e5138a5c8a3a7e7bd8fe6
workflow-type: tm+mt
source-wordcount: '6079'
ht-degree: 0%

---
# Magento Open Source发行说明(v2.4.9-alpha3)

## 修复了v2.4.9-alpha3中的问题

我们已在Magento Open Source 2.4.9-alpha3核心代码中修复了129个问题。 此版本中包含的已修复问题的子集如下所述。

### API

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

#### REST API端点export-stock-salable-qty返回不正确的项目total_count

修复了库存导出库存可销售数量API中total_count错误地限制为页面大小的分页问题。 以前，如果将/rest/all/V1/inventory/export-stock-salable-qty/website/base端点与分页参数（如page_size=5）一起使用，则响应中的total_count字段将返回5，而不是符合搜索条件的实际产品总数。 进行此修复后，total_count字段现在可正确反映可用的产品总数，而不考虑page_size参数，从而确保在所有Magento REST API端点之间具有一致的分页行为。

_ACP2E-4086 - [GitHub代码贡献](https://github.com/magento/inventory/commit/5632fb5e)_

#### 攻击者可以使用REST API的POST请求并发送RCE有效负载

REST API V1/guest-carts/&lt;cartId>/items/和V1/carts/mine/items/现在验证“product_options.extension_attributes.custom_options”。*.option_id”作为购物车项目SKU中的有效option_id。 以前，在数据库中处理和保存此类选项时不会进行任何验证。

_ACP2E-4138 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a1c57b2e)_

### 帐户

#### [问题]删除了后端网格上不必要的间距

现在，当存在选定项时，系统会删除后端网格中不必要的间距

_AC-11579 - [GitHub问题](https://github.com/magento/magento2/issues/38502) - [GitHub代码贡献](https://github.com/magento/magento2/pull/32622)_

#### 无法通过`updateProductsInWishlist` GraphQL突变清除愿望清单项备注

修复了希望列表注释未通过GraphQL突变进行更新的问题。
现在，注释会正确更新，并反映在API响应和店面中。

_AC-14682 - [GitHub问题](https://github.com/magento/magento2/issues/39911) - [GitHub代码贡献](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 当设置为“否”时，忽略显示前缀/后缀设置

修复了即使在配置中禁用客户名称前缀/后缀后，订单中仍继续显示客户名称前缀的问题。
现在，根据配置设置，从订单详细信息中去除前缀/后缀值。

_AC-15074 - [GitHub问题](https://github.com/magento/magento2/issues/40036) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Storefront客户帐户注册：电子邮件地址格式已转换为不同的域格式

此错误解决了域中具有特殊字符(例如tec55241@adòbe.com)的客户电子邮件自动转换为旁路代码格式(tec55241@xn--adbe-mqa.com)的问题。
在Magento 2.4.9-alpha3中，此修复程序可确保此类电子邮件ID保持不变并有效，从而防止出现投放错误。

_AC-15177 - [GitHub代码贡献](https://github.com/magento/magento2/commit/68a45d0a)_

#### 注册表单上缺少验证消息(mage-error)

修复了客户帐户创建页面上的必填字段在留空时未显示验证消息的问题。
现在，对于所有空或不正确的字段，会显示相应的错误消息。

_AC-15185 - [GitHub问题](https://github.com/magento/magento2/issues/40076) - [GitHub代码贡献](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 登录magento 2.4.8后出现的问题 — p1

修复了Magento 2.4.8-p1上登录后主页仍显示“Create an Account”（创建帐户）链接的问题。
现在，与其他页面一样，该链接在登录后正确隐藏。

_AC-15292 - [GitHub问题](https://github.com/magento/magento2/issues/40120)_

### 管理员UI

#### [问题]替换已弃用的转义符

此PR将删除已弃用的getEscaper()，并通过构造函数注入来添加它

_AC-15132 - [GitHub问题](https://github.com/magento/magento2/issues/40062) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38135)_

#### 欢迎消息与移动视图中的产品类别重叠。

修复了欢迎名称与移动设备视图中的产品类别重叠、阻止点击的UI问题。
现在，类别完全可见且可点击，没有重叠问题。

_AC-15166 - [GitHub代码贡献](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Google reCAPTCHA管理面板的exception.log中的“无法解析reCAPTCHA参数”条目

已解决Google V3 reCAPTCHA管理员登录的`var/log/exception.log`文件中的reCaptcha错误，并且未记录任何错误消息。 以前，当管理员用户配置其&#x200B;**配置** > **安全性** > **Google reCAPTCHA管理员面板**&#x200B;设置时，每隔几秒会引发一次以下错误： `main.ERROR: Can not resolve reCAPTCHA parameter. {&quot;exception&quot;:&quot;[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)&quot;} []`。  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [GitHub问题](https://github.com/magento/magento2/issues/34975) - [GitHub代码贡献](https://github.com/magento/magento2/commit/4f7e5983) - [GitHub代码贡献](https://github.com/magento/security-package/commit/804dbc2a)_

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

### 管理员UI、税务

#### 税率管理员UI错误

该票证修复了以下税率管理员UI问题：切换国家/地区(例如，从美国→英国)仍显示之前选择的美国州，从而误导用户。
在2.4.9-alpha3中，如果所选国家没有国家，则状态字段现在重置为*。

_AC-8440 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a3b1abc2)_

### B2B

#### Rest API products-render-info返回错误的已登录客户的最终价格

该票证已修复Rest API产品 — render-info会返回错误的已登录客户的最终价格

_AC-5979 - [GitHub问题](https://github.com/magento/magento2/issues/35757) - [GitHub代码贡献](https://github.com/magento/magento2/commit/)_

#### 当我们尝试从目录页添加申请列表时，“添加到申请列表”按钮将消失

当我们尝试从类别页（现已修复）添加之前的“添加到申请列表”按钮时，该按钮将消失，我们可以在“类别”页上看到申请按钮

_AC-8575_

### B2B、购物车和结账

#### 通过管理员功能“以客户身份登录”登录B2B公司用户时，Storefront上不会显示此类具有cartId = X错误的实体

现在，使用“以客户身份登录”功能从管理员后端成功登录后，不再显示“具有cartId = X的此类实体”错误。

_ACP2E-3994 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2a1e1e55)_

### 购物车和结帐

#### [问题]将EventPrefix和EventObject添加到签出协议模型

系统现在包含签出协议模型的EventPrefix和EventObject，允许使用事件前缀触发事件。 此增强功能为开发人员处理签出协议事件提供了更大的灵活性。 以前，签出协议模型不支持EventPrefix和EventObject，从而限制了自定义事件处理的能力。

_AC-13252 - [GitHub问题](https://github.com/magento/magento2/issues/32510) - [GitHub代码贡献](https://github.com/magento/magento2/pull/32451)_

#### [Graphql]无法为不可为空的字段“SelectedCustomizableOption.label”返回null

现在，当所选的选项不再存在时，系统不会引发包含消息的内部服务器错误

_AC-14256 - [GitHub问题](https://github.com/magento/magento2/issues/39729) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39888)_

#### [2.4.8]无法在城市名称中包含数字0-9、与号、句号或圆括号的城市下订单

修复了包含特殊字符（如）的城市名称签出失败的问题。、和，或括号。
现在，成功下达了具有此类城市名称的订单，且没有出现验证错误。

_AC-14495 - [GitHub问题](https://github.com/magento/magento2/issues/39854) - [GitHub代码贡献](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Salesrule Subselect with Quantity条件无法应用

修复了包含产品子选择条件的购物车价格规则在结账时未应用的问题。
现在，根据配置的规则成功应用折扣。

_AC-14884 - [GitHub问题](https://github.com/magento/magento2/issues/39965) - [GitHub代码贡献](https://github.com/magento/magento2/commit/fe72c407)_

#### Graphql — 启用延交时，合并购物车无法正常工作

修复了在通过GraphQL合并购物车时访客购物车项目未与客户购物车合并的问题。
现在，客户购物车可正确反映访客和客户购物车的合并数量。

_AC-15148 - [GitHub问题](https://github.com/magento/magento2/issues/40064) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [集成] [签出] Depend指令已在失败的付款电子邮件模板中更新

更新了失败的付款电子邮件模板以正确处理depend指令。
修复程序可确保在适用的情况下正确显示送货地址和送货方式。
以前，失败的付款电子邮件中缺少这些字段。

_AC-15363 - [GitHub代码贡献](https://github.com/magento/magento2/commit/36d4d6fb)_

#### 当购物车不再符合要求时，[云]免运费折扣未正确移除

小计(不包括 Tax)将合并以前规则中的折扣。

_ACP2E-3973 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 在多次配送中发现同一客户的重复订单

使用多个发运地址下达订单的并发请求不会再导致同一客户的订单重复

_ACP2E-4117 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a1c57b2e)_

### 购物车和结帐、订购、产品

#### 即使订单发票失败，也会发送礼品卡电子邮件

在实施此修复之前，在创建发票后会发送礼品卡电子邮件。 但是，应用此修复后，现在会在成功保存和提交发票后发送礼品卡电子邮件。

_ACP2E-3905_

### 购物车和结帐、安全性

#### 实施sri修补程序后首次尝试时，在签出页面上获取[CLOUD]的JS文件404

在启用了精简和捆绑时，修复mixin之前的版本将不会加载到购物车和结账中。 修复后，所有mixin都应按预期加载。

_ACP2E-4128 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e457c5e2)_

### 目录

#### 价格范围和config.php的问题

在Magento 2.4.2中，通过config.php更改价格范围时，无法正确更新catalog_eav_attribute中price属性的is_global值。
因此，产品价格仍是全球性的，无法按网站进行保存，即使将价格范围设置为网站也是如此。
要解决此问题，需要手动更新数据库中的is_global列，这对于生产环境并不理想。
此行为与Magento的默认设计一致，即价格范围为全局或网站，但不是按商店视图定价。

_AC-13857 - [GitHub问题](https://github.com/magento/magento2/issues/33559)_

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

#### 动态图像生成生成大量图像

修复后，将仅为分配了产品的网站生成图像。

_ACP2E-3927 - [GitHub代码贡献](https://github.com/magento/magento2/commit/fab20b00)_

#### 由于布局中缓存的布局结构不正确，前端出现500错误

修复了由于布局中缓存的布局结构不正确而导致页面返回500错误代码的问题

_ACP2E-4040 - [GitHub代码贡献](https://github.com/magento/magento2/commit/47721be6)_

#### 计划更新中的目录价格规则折扣金额字段的验证错误

以前，在解决此问题之前，对于目录价格规则的计划更新，如果折扣金额为by_fixed ，则由于validation-number-range规则的原因，无法正确验证该金额。 应用此修复后，验证可对固定价格目录价格规则正常工作。

_ACP2E-4054 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 禁用后，产品显示为缺货

修复后，产品小部件中不存在禁用的产品。

_ACP2E-4136 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [云]重复条目错误(temp_category_descendants_%)

修复了在为具有高嵌套类别数的环境创建计划更新期间重复条目的问题

_ACP2E-4159 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a1c57b2e)_

### 目录，GraphQL

#### GraphQl折扣计算无效

现在，当目录价格配置为包含税时，GraphQL可正确显示折扣百分比和基本价格。 以前，出现舍入错误，例如显示19.99%而不是20%。

_ACP2E-3993 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e457c5e2)_

### 目录、产品

#### 通过GraphQL在PDP中未显示通过相关产品规则关联的产品

以前，在应用此修复之前，相对产品规则为与规则匹配的产品返回空/空。 应用此修复后，将针对匹配的产品成功返回产品的相对规则。

_ACP2E-3949_

### 内容

#### graphql (magento 2.4.6-p4 ) — 尝试获取非活动状态cms页面时出错

修复了针对已禁用的CMS页面的GraphQL查询返回内部服务器错误的问题。
现在，查询会获取正确的响应，并且不会出现错误。

_AC-12302 - [GitHub问题](https://github.com/magento/magento2/issues/38877) - [GitHub代码贡献](https://github.com/magento/magento2/commit/1b1baf1d)_

#### [GraphQl]路由查询无限循环

此工单修复了请求路径和目标路径相同的GraphQL路由查询导致无限循环并最终超时的问题。
在2.4.9-alpha3中，查询现在返回正确的错误响应，而不是循环。

_AC-14269 - [GitHub问题](https://github.com/magento/magento2/issues/39707) - [GitHub代码贡献](https://github.com/magento/magento2/commit/68a45d0a)_

#### 将常量IMAGE_FILE_NAME_PATTERN更改为公共可见，以获得更大的灵活性

GenerateRenditions.php中的常量IMAGE_FILE_NAME_PATTERN已公开，以便让开发人员在处理图像呈现时具有更大的灵活性。此修复包含在Magento 2.4.9-alpha3中，具有完整的单元测试和集成测试覆盖率。

_AC-15338 - [GitHub问题](https://github.com/magento/magento2/issues/39733) - [GitHub代码贡献](https://github.com/magento/magento2/commit/68a45d0a)_

#### 内容暂存预览不适用于搜索结果

在暂存预览中搜索现在会根据选定的范围返回产品。 以前，搜索会在默认范围中返回结果，而不考虑所选存储。

_ACP2E-4095_

#### 页面生成器 — 产品条件逻辑问题（OR逻辑行为不正确显示较少产品）

现在，在“匹配任意”条件中使用具有全局范围的属性时，页面生成器产品小组件会返回正确结果

_ACP2E-4096 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e457c5e2)_

### 客户/客户

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

#### [问题]使方法签名与接口一致

getAttributes的方法签名现在与其接口一致，从而防止在覆盖方法时发生任何错误。 以前，在尝试覆盖getAttributes方法时，方法签名不一致会导致错误。

_AC-11578 - [GitHub问题](https://github.com/magento/magento2/issues/38501) - [GitHub代码贡献](https://github.com/magento/magento2/pull/31955)_

#### [问题]修复用户界面组件的验证电子邮件规则

系统现在可以正确验证在UI组件中输入的多个电子邮件地址，确保正确裁剪和验证每个电子邮件。 以前，系统使用不正确的方法修剪电子邮件地址，这可能导致验证错误。

_AC-11719 - [GitHub问题](https://github.com/magento/magento2/issues/38528) - [GitHub代码贡献](https://github.com/magento/magento2/pull/33470)_

#### [问题]删除冗余方法

代码质量：删除了AsynchronousOperations和Sales组件中仅调用父方法而没有添加功能的冗余方法，从而提高了代码可维护性。

_AC-11915 - [GitHub问题](https://github.com/magento/magento2/issues/29748) - [GitHub代码贡献](https://github.com/magento/magento2/pull/29147)_

#### 对于在字段项下包含注释的etc/adminhtml/system.xml文件，xsd验证失败。

此PR修复了phpstorm中注释节点的XML架构定义

_AC-12945 - [GitHub问题](https://github.com/magento/magento2/issues/39148) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39867)_

#### Magento 2.4.8使用不遵循语义版本控制的开发包

Magento 2.4.8需要开发版本的pdeat/pdepend和phpmd/phpmd (3.x-dev)才能兼容PHP 8.4。
这些开发版本与第三方工具冲突，这些工具需要符合SemVer的包，从而阻止某些升级。
临时解决方法是为composer.json中的开发版本别名（例如，“3.x-dev as 3.99.0”），以便在满足语义版本控制的同时允许兼容性。
这可确保PHP 8.4的支持并避免冲突，直到稳定发行版可用。

_AC-14519 - [GitHub问题](https://github.com/magento/magento2/issues/39796)_

#### Rest API：在null时调用成员函数getVideoProvider()

修复了在子产品只有YouTube视频而没有其他图像的情况下，调用可配置产品子级API返回500内部服务器错误的问题。
该错误是由ExternalVideoEntryConverter中的空引用导致的。
现在，API可正确返回包含媒体集条目的子产品，包括外部视频数据，而不会引发错误。
这可确保通过REST API正确检索子产品的所有媒体类型。

_AC-15046 - [GitHub问题](https://github.com/magento/magento2/issues/40021)_

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

#### 更新模块自述文件和修复文档链接

_AC-15340 - [GitHub代码贡献](https://github.com/magento/magento2/commit/ec9459d0)_

#### [问题]仅当插件未禁用时记录未声明的插件

此PR可修复并记录实际未声明且未使用的插件（已启用且缺少实例）。

_AC-15386 - [GitHub问题](https://github.com/magento/magento2/issues/40086) - [GitHub代码贡献](https://github.com/magento/magento2/pull/40081)_

#### Magento 2.4.8-p2，magento/framework版本103.0.8-p2：EmailMessage类调用不存在的方法

_AC-15446 - [GitHub问题](https://github.com/magento/magento2/issues/40170) - [GitHub代码贡献](https://github.com/magento/magento2/commit/059fd469) - [GitHub代码贡献](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x]数据/架构修补程序getAliases()在`setup:upgrade`期间导致错误

getAliases()在安装:upgrade期间导致错误，此PR修复了相同的

_AC-15559 - [GitHub问题](https://github.com/magento/magento2/issues/31396) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38239)_

#### 应为类型“Magento\Customer\Api\Data\GroupInterface”。 找到&#39;Magento\Customer\Model\Group&#39;。

修复了使用GroupFactory通过GroupRepositoryInterface保存客户组时导致类型错误的问题。
以前，存储库需要GroupInterface，但传递了组模型实例，从而导致致命错误。
现在，通过确保正确的界面实施，可以通过存储库成功保存客户组。
这解决了以编程方式创建或更新客户组时IDE警告和运行时错误。

_AC-6909 - [GitHub问题](https://github.com/magento/magento2/issues/36269)_

#### [问题]删除禁止的`@author`标记

此PR从代码库中移除`@author`标记

_AC-8349 - [GitHub问题](https://github.com/magento/magento2/issues/37266) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37016)_

#### [问题]删除禁止的`@author`标记

此PR从代码库中移除`@author`标记

_AC-8350 - [GitHub问题](https://github.com/magento/magento2/issues/37265) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37015)_

#### [问题]删除禁止的`@author`标记

此PR从代码库中移除`@author`标记

_AC-8359 - [GitHub问题](https://github.com/magento/magento2/issues/37262) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37012)_

#### [问题]删除禁止的`@author`标记

此PR从代码库中移除`@author`标记

_AC-8362 - [GitHub问题](https://github.com/magento/magento2/issues/37259) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37009)_

#### [问题]从`@author`和`Magento_Backup`中删除禁止的`Magento_Bundle`标记

此PR从代码库中移除`@author`标记

_AC-8367 - [GitHub问题](https://github.com/magento/magento2/issues/37244) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36979)_

#### [问题]修复catalogsearch中的变量名称

系统现在可以在搜索引擎模块中正确命名变量，从而提高代码清晰度和可维护性。 以前，在搜索引擎模块中使用不相关的变量名称$defaultCountry，从而导致混淆。

_AC-9215 - [GitHub问题](https://github.com/magento/magento2/issues/37810) - [GitHub代码贡献](https://github.com/magento/magento2/pull/33533)_

#### [QUANS]服务器问题可能是由无效的S3访问密钥导致的

错误的AWS S3凭据不再导致页面无限期地加载到店面。

_ACP2E-3890 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [Cloud] Minify js不起作用

启用JS缩小功能后，以下JS文件现在可以完全且正确地缩小： mage/backend/tabs.min.j、jquery/jquery.validate.min.js和Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js。 因此，页面生成器CSS类字段验证可按预期工作。

_ACP2E-3925 - [GitHub代码贡献](https://github.com/magento/magento2/commit/47721be6)_

#### Cron作业未清除数据库表 — 导致因Galera崩溃而发生中断

Changelog表清理现在批量运行，以避免大量删除操作。

_ACP2E-3995 - [GitHub代码贡献](https://github.com/magento/magento2/commit/52f46328)_

#### 未缩小的JS有时会加载，忽略“启用js缩小”

在修复之前，即使启用了缩小，也会请求一些JS文件，但其中不包含导致404状态代码的“min”前缀。 修复后，在启用缩小功能时，不会请求非缩小的JS资源。

_ACP2E-4058 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6dd3fa99)_

#### 自定义属性组中的日期属性无法在管理员中显示日期选取器

修复了将日期属性的日历弹出窗口分配给自定义属性组时显示在屏幕外的问题。

_ACP2E-4060 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6dd3fa99)_

### GraphQL

#### 客户订单GraphQL ：检索关联产品的产品类别“不可单独显示”

在修复之前，如果订单包含隐藏的产品，则其类别将在客户订单GraphQl响应中显示空数组。
现在，修复之后，即使产品已隐藏，产品类别也会包含在客户订单GraphQl请求的响应中。

_ACP2E-3945 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2a1e1e55)_

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

在修复之前，错误节点位置不提供与2.4.7和2.4.9版本的无缝兼容性。 现在，修复后，错误节点可正确放置以适应这两个版本。

_ACP2E-4115 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e457c5e2)_

#### 即使子级在Graphql调用中已安装，捆绑父级仍显示缺货

修复后，使用GraphQL请求产品列表会返回捆绑产品的正确库存状态。

_ACP2E-4168 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a1c57b2e) - [GitHub代码贡献](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL、库存/MSI

#### GraphQL mergeCart突变差异

修复后，合并购物车GraphQL请求会根据库存配置正确检查产品数量。

_ACP2E-4184 - [GitHub代码贡献](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL，安全性

#### 通过GraphQL重置客户密码不符合限制

解决了通过GraphQL突变发出的客户密码重置请求不符合在商店>配置>客户>客户配置>密码选项下配置的密码重置限制的问题。 这些设置现已正确实施。

_ACP2E-3992 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6dd3fa99)_

### 导入/导出

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

### 库存/MSI

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

### 订购

#### Magento 2.4.8 GraphQL — 订单项目order_date格式错误

修复了GraphQL响应中的order_date字段以yyyy-mm-dd格式返回的问题。
现在，order_date以dd-mm-yyyy格式正确显示。

_AC-14431 - [GitHub问题](https://github.com/magento/magento2/issues/39805) - [GitHub代码贡献](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 从管理员订单视图提交时未发送装运电子邮件，尽管在商店配置中启用了此功能

系统现在会发送装运确认电子邮件，因为它在下达订单的商店配置中启用。

_AC-14563 - [GitHub问题](https://github.com/magento/magento2/issues/39861) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39897)_

#### 由于字段名称不明确，无法按日期过滤

在Magento 2.4.7-p6中，按日期过滤订单网格已报告由于与Braintree模块的连接而引发错误。
该问题涉及在应用日期过滤器时联接braintree_transaction_details和sales_order表的查询。
Adobe Commerce Engineering已审查此案例，但无法在环境中重现错误。
预期行为是，按日期过滤应返回与过滤器匹配的订单并且没有错误。

_AC-15037 - [GitHub问题](https://github.com/magento/magento2/issues/40024)_

#### Magento2：无法创建促销活动规则

此PR修复，我们
\Magento\Catalog\Model\ResourceModel\Eav\Attribute模型，而不是\Magento\SalesRule\Model\Rule\Condition\Product：：loadAttributeOptions方法中的\Magento\Catalog\Model\ResourceModel\Eav\Attribute

_AC-15358 - [GitHub问题](https://github.com/magento/magento2/issues/12176) - [GitHub代码贡献](https://github.com/magento/magento2/pull/30479)_

#### 取消发票重定向至404

取消使用“非捕获”类型开具的发票不会导致第404页。

_ACP2E-4001 - [GitHub代码贡献](https://github.com/magento/magento2/commit/2a1e1e55)_

#### 销售存档Cron作业导致数据库锁定问题

在修复之前，按存档cron顺序找到的未绑定DELETE查询导致Galera出现问题。 现在，更新后，删除查询的执行受到限制。

_ACP2E-4010_

#### 使用REST API的配置选项导致更新订单出现问题

通过rest api端点更新订单时，保留销售订单物料上的现有产品选项。

_ACP2E-4061 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6dd3fa99)_

### 其他开发人员工具

#### [问题]正在清除未使用的代码。

系统现在删除有关未使用导入的未使用代码。

_AC-10980 - [GitHub问题](https://github.com/magento/magento2/issues/38424) - [GitHub代码贡献](https://github.com/magento/magento2/pull/33499)_

#### [问题]辅助功能：菜单中的WAI-ARIA角色嵌套错误

系统现在可以生成Lighthouse辅助功能，并且菜单错误中的WAI-ARIA角色嵌套没有错误，报告应为绿色

_AC-15082 - [GitHub问题](https://github.com/magento/magento2/issues/40045) - [GitHub代码贡献](https://github.com/magento/magento2/pull/38617)_

#### 在Magento管理员中预览电子邮件时出现控制台错误

在预览电子邮件模板时，系统不会引发任何控制台错误

_AC-9245 - [GitHub问题](https://github.com/magento/magento2/issues/37820) - [GitHub代码贡献](https://github.com/magento/magento2/pull/37933)_

### 支付

#### 来自PayPal的未知IPN滥用应用程序IPN处理器

IPN处理程序现在会忽略不支持的或未知的IPN类型。 它不会返回500错误，而是会记录问题并继续处理，不会出现中断。

_ACP2E-4049 - [GitHub代码贡献](https://github.com/magento/magento2/commit/6dd3fa99)_

#### PayflowPro保存的卡令牌付款时失败

PayPal PayFlow Pro交易ID (PNREF)现在可在12个月的固定期限内的参考交易中使用。 过期后，保存的卡将不再显示，必须再次添加。 以前，有效性由原始交易中使用的支付卡的到期日确定。

_ACP2E-4064 - [GitHub代码贡献](https://github.com/magento/magento2/commit/52f46328)_

### 性能

#### [问题]更新使用静态站点不可变的缓存控制

此PR通过以下方式提高了性能：在&amp;发生更改之前，不验证每个页面加载上的静态内容。

_AC-15171 - [GitHub问题](https://github.com/magento/magento2/issues/39486) - [GitHub代码贡献](https://github.com/magento/magento2/pull/39484)_

#### [云]无法将产品添加到类别

改进了通过Visual Merchandiser将产品添加到类别时的性能。

_ACP2E-3946 - [GitHub代码贡献](https://github.com/magento/inventory/commit/29653b1d)_

#### [云] cache_invalidate超过10K日志

以前，在每次访问PLP或购物车时都会清除缓存，从而造成不必要的性能开销。 Target规则缓存不再在这些页面上失效，从而提高了浏览效率。

_ACP2E-4059_

### 定价

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

#### 对于测试用例AC-6158的可配置产品，仍会显示“低至”标签

具有相应的变体和类别分配的实现和验证的可配置产品(P1-P7)。 已确保C类产品正确显示店面价格和“最低”标签行为。

_AC-10847 - [GitHub代码贡献](https://github.com/magento/magento2/commit/a3b1abc2)_

#### 通过存储库请求产品时额外的日志记录失败

改进了未找到SKU或ID时ProductRepository：：get和getById的错误消息。
以前，异常不提供有关哪个SKU或ID导致错误的上下文。
现在，异常消息包括缺少的SKU或ID，有助于调试和改进开发人员体验。
此更改不会影响API的任何功能行为。

_AC-15199 - [GitHub问题](https://github.com/magento/magento2/issues/40090) - [GitHub代码贡献](https://github.com/magento/magento2/commit/1b1baf1d)_

#### 按受限角色编辑可配置产品时未分配简单产品

在此修复之前，如果受限管理员用户保存的可配置产品包含管理员用户无权访问的简单产品，则会在保存时从可配置产品中删除。 修复后，可配置产品将按从完全权限管理员保存的形式保留。

_ACP2E-4081_

#### [云] Sitemap生成性能显着降低

针对带图像的产品生成Sitemap的过程不再出现指数级放缓。 以前，为启用了图像包含的存储生成站点地图会导致处理时间较长。

_ACP2E-4153 - [GitHub代码贡献](https://github.com/magento/magento2/commit/e457c5e2)_

### 促销活动

#### 通过GraphQl客户请求获取客户订单的订单物料折扣appliced_to时出错

之前，当通过GraphQl客户请求获取客户订单的appliced_to折扣时出现内部服务器错误，该错误现已修复，并且会获取包含应用折扣的正确客户订单数据

_AC-14888 - [GitHub问题](https://github.com/magento/magento2/issues/39963) - [GitHub代码贡献](https://github.com/magento/magento2/commit/fe72c407)_

#### 通过GraphQl客户请求获取客户订单的订单项目优惠券代码时出错

修复了通过GraphQL获取包含优惠券详细信息的订单时返回内部服务器错误的问题。
现在，查询执行成功，并在响应中返回正确的优惠券信息。

_AC-14889 - [GitHub问题](https://github.com/magento/magento2/issues/39962) - [GitHub代码贡献](https://github.com/magento/magento2/commit/fe72c407)_

### SEO

#### ProductRepository getById中未定义数组键

在调用具有无效ID（如123abc）的ProductRepository：：getById()时出现了此问题，导致出现“未定义数组键值”错误。
在Magento 2.4.9-alpha3中进行修复后，此类请求现在可正确返回404页面，而不是引发异常。
QA使用有效且格式错误的ID进行了确认，没有发现其他问题。

_AC-15345 - [GitHub问题](https://github.com/magento/magento2/issues/40146) - [GitHub代码贡献](https://github.com/magento/magento2/commit/68a45d0a)_

#### [云]站点地图生成从不会结束

在此修复之前，如果目录包含超过100万个产品，则无法成功完成Sitemap生成。 修复后，Sitemap的生成将以较低的内存分配完成，每个商店有多达100万个产品。

_ACP2E-3902 - [GitHub代码贡献](https://github.com/magento/magento2/commit/52f46328)_

#### [Cloud]存储切换器无法从EN工作到FR以查找常见问题页

修复了在商店视图之间切换时，将用户重定向到主页而不是对应的已翻译CMS页面的问题。 现在，商店切换器会检查目标商店中的URL重写，以确保正确重定向(例如，英语的常见问题页面→法语的常见问题页面)。

_ACP2E-4112_

### 暂存和预览

#### 使用其他管理域时，签出时暂存更新预览中断

当商店基本URL与管理员URL不同时，客户可以登录并在商店预览模式下查看其购物车。

_ACP2E-3906_

#### 内容暂存功能板显示的时间不正确

现在，“内容暂存仪表板”中的“开始时间”和“结束时间”日期过滤器显示正确的日期和时间。 以前，在日期选取器中选择日期和时间后，显示不正确的日期和时间

_ACP2E-3969_

#### 在预览计划更新产品和类别时，范围显示不同的“商店视图”

在此修复以前的版本中，类别和产品的预览链接未针对正确的存储生成。 进行此修复后，预览链接将自动选择创建预览的存储区。

_ACP2E-4053_

### UI框架

#### [问题]从`@author`中删除禁止的`Magento_Backend`标记

此PR从代码库中移除`@author`标记

_AC-8814 - [GitHub问题](https://github.com/magento/magento2/issues/37522) - [GitHub代码贡献](https://github.com/magento/magento2/pull/36976)_
