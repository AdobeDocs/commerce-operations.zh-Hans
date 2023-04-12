---
title: 发行说明
description: 了解Adobe Commerce可用的修补程序及其解决的问题。
source-git-commit: ef501b34947f24f8028bd5876bd4a167551e03ec
workflow-type: tm+mt
source-wordcount: '11914'
ht-degree: 0%

---

# 发行说明

的 [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) 提供由Adobe和Magento Open Source社区开发的各个修补程序。 它允许您应用、还原和查看有关可用于已安装版本的Adobe Commerce或Magento Open Source的所有修补程序的常规信息。 无论谁开发了修补程序，您都可以将修补程序应用于Adobe Commerce和Magento Open Source项目。 例如，您可以将社区开发的修补程序应用到Adobe Commerce项目。

>[!INFO]
>
>请参阅 [应用修补程序](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) 有关将修补程序应用到Adobe Commerce或Magento Open Source项目的说明。 请参阅 [可用的修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) ，以查看已发布修补程序的完整列表。

>[!INFO]
>
>有关 [!DNL quality patches] 由社区创建以用于Magento Open Source，请参阅 [发行说明](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (对于Adobe Commerce和Magento Open Source>=2.4.4-p1 &lt;2.4.4-p3) — 修复了当产品重新库存或价格发生更改时，未发送产品警报电子邮件的问题。
* **ACSD-50367** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了在创建多选客户地址属性（不含值）时，无法导出客户地址的问题。
* **ACSD-49877** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了视频自动播放在移动设备上不起作用的问题 [!DNL Safari] 视频直接链接到远程视频文件而不是流服务时。
* **ACSD-50165** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了错误 *无法删除文件。 警告！取消链接：没有此类文件或目录* 从管理员刷新JS/CSS缓存时。
* **ACSD-49737** (对于Adobe Commerce和Magento Open Source>=2.4.1-p1 &lt;2.4.7) — 修复了在信用卡付款失败后，优惠券被错误标记为使用的问题。
* **ACSD-50814** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了管理员用户无法创建贷项通知单的问题。
* **ACSD-50116** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了管理员用户无法为子类别级别3或更低级别创建URL重写的问题。
* **ACSD-49513** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5) — 修复了由于0字节文件导致远程存储同步失败的问题。
* **ACSD-46683** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了发运价格显示的问题 *尚未计算*.
* **ACSD-49129** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了 *[!UICONTROL content]* 属性（base64图像代码）未在 `rest/V1/products/sku/media` 产品媒体API响应。
* **ACSD-50276** (对于Adobe Commerce >=2.4.0 &lt;2.4.7) — 修复了在创建多选客户属性时，客户注册表单在店面上不起作用的问题。
* **ACSD-50527** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了使用空动态块保存页面时出现的错误。
* **ACSD-49973** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 改进了通过GraphQL获取捆绑产品的性能。
* **BB2B-2598** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 将缓存功能添加到 [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency]和 [!UICONTROL storeConfig] GraphQL查询。
* 添加了MDVA-42806、ACSD-48627和ACSD-46815的新版本。
* 更新了ACSD-49773、ACSD-47179、ACSD-48300的修补程序元数据。

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了当订单未准备好接收时，API发送准备接收电子邮件的问题。
* **ACSD-49822** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了 [!UICONTROL Requisition List] 页面未反映在 [!UICONTROL Print Requisition List].
* **ACSD-48771** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了从旧版本升级列块内容类型时出现的问题 [!DNL Page Builder] 版本。
* **ACSD-49464** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了当orderId不同时，发票、发运和贷项通知单未从存档中移回的问题。
* **ACSD-49773** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了将AWS S3用作远程存储时产品导出失败的问题。
* **ACSD-49748** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了无法发送邀请的问题。
* **ACSD-49502** (对于Adobe Commerce >=2.4.3 &lt;2.4.7) — 修复了在对可下载产品应用暂存更新后，可下载链接未正确更新的问题。
* **ACSD-49527** (对于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了GraphQL公司角色无法正确显示分页的问题。
* **ACSD-49706** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了未选择任何值时，为可视色板属性保存默认值的问题。
* **ACSD-49835** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了“使用默认”复选框值未在多选属性的存储级别正确保存的问题。
* **ACSD-49898** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了当捆绑产品的特殊价格超过1000时，产品网格会引发异常的问题。
* **ACSD-50234** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.5) — 修复了在下订单时，确认电子邮件中出现错误的客户名称的问题 [!DNL PayPal].
* **ACSD-49960** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了按日期筛选不适用于客户订单网格的问题。
* **ACSD-49849** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了客户电子邮件被替换为 [!DNL PayPal] 通过 [!DNL PayPal Express] 通过GraphQL。
* **ACSD-49839** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了当产品在SKU中具有单引号或双引号时，共享目录定价和结构在“管理员”中引发错误的问题。
* **ACSD-49970** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了在 [!DNL New Relic] 报表已打开。
* **ACSD-50260** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了GraphQL产品搜索结果限制为仅10,000个结果的问题。
* **ACSD-48813** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了搜索未根据属性的搜索权重显示相关结果的问题。

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.3) — 修复了基于“是”/“否”属性创建的目录价格规则不考虑选定范围的问题。
* **ACSD-47704** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了捆绑产品仅显示现货产品价格的问题。
* **ACSD-49370** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了 *日期时间* 产品属性具有 *FilterMatchTypeInput* 在GraphQL架构中键入。
* **ACSD-48807** (对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.7) — 修复了客户产品评论未按通过GraphQL的storeview过滤的问题。
* **ACSD-49433** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在购物车中显示默认金额为未结金额礼品卡小计的问题。
* **ACSD-48866** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了在请求类别的RSS馈送时出错的问题。
* **ACSD-48784** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了客户群之间客户区段价格缓存不正确的问题。
* **ACSD-48857** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了用户在使用页面生成器进行编辑后无法保存更改的问题。
* **ACSD-49065** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了仅分配给自定义库存时，“管理员”中看不到报价项的问题。
* **ACSD-49179** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了订单报表在不同商店中以不同货币显示错误金额的问题。
* **ACSD-49286** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了当页面上存在多个产品小组件时，将产品添加到购物车两次的问题。
* **ACSD-49574** (对于Adobe Commerce >=2.4.4 &lt;2.4.7) — 添加了通过GraphQL支持购物车中礼品卡产品更新的功能。
* 更新了修补程序：ACSD-48694。

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (对于Adobe Commerce >=2.4.1 &lt;2.4.7) — 修复了在使用可转让报价下单时使用默认送货地址而不是新地址的问题。
* **ACSD-48059** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了商户无法保存“[!UICONTROL Match product by rule]”。
* **ACSD-48216** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) — 修复了 [!UICONTROL AUTO_INCREMENT] 的 [!UICONTROL inventory_source_item] 表格在 [!UICONTROL UPDATE] 操作。
* **ACSD-47908** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) — 修复了在结帐期间在发运步骤中选择来源和数量时出现的错误“值小于或等于0”。
* **ACSD-49497** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了订单在发运后仍处于处理状态且应用部分退款的问题。
* **ACSD-48694** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.3.8) || >=2.4.1 &lt;2.4.7) — 修复了错误“请求的状态更改无效”阻止客户下订单的问题。
* **ACSD-49013** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在使用批量API创建客户时，电子邮件确认未翻译为网站区域设置的问题。
* **ACSD-48164** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了受限管理员无法保存网站级别值的问题。
* **ACSD-48404** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 修复了按浏览器的返回按钮时，“记住类别分页=是”导致错误的问题。
* **ACSD-48634** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了测试更新页面上的JS错误，当“[!UICONTROL Google Analytics Content Experiments]已启用。
* **ACSD-49042** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 修复了无限延交订单的产品无法从Storefront订购的问题。
* 更新的修补程序：ACSD-48366和ACSD-48661。

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (对于Adobe Commerce和Magento Open Source2.4.4) || >=2.4.5 &lt;2.4.6) — 修复了由于应用程序级别缓存，并非总是发送降价通知的问题。
* **ACSD-48661** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了以下问题：如果公司的信用限制大于999，则逗号分隔符会因验证错误而阻止保存公司。
* **ACSD-48773** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了奖励点电子邮件模板从错误商店中获取的问题。
* **ACSD-48587** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了产品小组件匹配规则中HTML特殊字符阻止它们显示匹配产品的问题。
* **ACSD-48212** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了产品导入将产品分配到错误源的问题。
* **ACSD-47988** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了产品导出会从页面生成器产品说明中HTML标记的问题。
* **ACSD-48366** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了产品图像未显示在“返回至库存”电子邮件模板中的问题。
* **ACSD-48417** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了在为产品创建计划更改并保存其他产品后出现SQL错误的问题。

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了未将捆绑产品分配到任何网站时，产品价格重新索引不起作用的问题。
* **ACSD-48262** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了将“允许每页所有产品”设置设为“是”时，产品在前端不可见的问题。
* **ACSD-48293** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4) — 修复了在售出的子产品退回到现货时，复合产品无现货的问题。
* **ACSD-47520** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了创建贷项通知单时客户丢失奖励积分的问题。
* **ACSD-48044** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 修复了将多个礼品卡应用于具有多次发运的单个订单时阻止下订单的问题。
* **ACSD-48300** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在删除可配置产品时无法创建返回的问题。
* **ACSD-47910** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了相应实体网格中缺少订单、发票、发运和贷项通知单的问题。
* **ACSD-47292** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了将“显示缺货产品”设置为“是”时，GraphQL响应中无法提供捆绑产品缺货的问题。
* **ACSD-48234** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了启用“显示缺货”选项后，目录搜索结果显示错误类别项目计数的问题。
* **ACSD-48313** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5) — 修复了当属性值包含逗号时，无法解析“configurable_variations”列的问题。 “additional_attributes”使用相同的解析算法。
* **ACSD-48627** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了在发送GraphQL请求获取购物车详细信息时，无现货可配置产品导致错误的问题。
* 更新了修补程序：MDVA-39384。

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了以下产品不生成SEO友好URL的问题： *url_key* 在存储视图级别上被覆盖的属性。
* **ACSD-46865** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了启用异步索引时未填充“发运”和“贷项通知单”网格的问题。
* **ACSD-47004** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了增值税未应用于没有增值税ID的帐单地址的问题。
* **ACSD-47803** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了可配置的无现货产品色板显示为可用的问题。
* **ACSD-47137** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 当pub/media文件夹非常大时，可提高图像库的加载速度。
* **ACSD-46770** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了即使在 *电子邮件订单确认* 未选中。
* **ACSD-47955** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了GraphQL无法正确显示购物车折扣的问题。
* **ACSD-46617** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了 *继续结帐* 即使小计大于配置的值，按钮也会灰显 *最低订单金额*.
* **ACSD-47079** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 修复了当子产品库存状态通过REST APIPOST/rest/V1/inventory/source-items发生更改时，复合产品（捆绑包、分组和可配置）库存状态未更新的问题。
* **ACSD-47336** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复 *出了点问题。* 在商务管理员中取消通知时出错。
* **ACSD-47559** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了“预览电子邮件模板”区域不完全可见的问题。
* **ACSD-47920** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了即使在 *允许来宾结帐* 关闭。
* 已替换修补程序：MDVA-39305和MDVA-42855。

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了对特定范围具有受限访问权限的管理员无法删除产品评论的问题。
* **ACSD-47107** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5) — 修复了目录价格规则折扣应用于自定义产品选项的问题。
* **ACSD-47232** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了无法在管理员中应用具有总权重条件的优惠券的问题。
* **ACSD-46519** (对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.6) — 修复了GraphQL categoryList请求为锚点类别返回错误product_count的问题。
* **ACSD-47027** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了updateCompanyRole GraphQL请求缓慢的问题。
* **ACSD-47666** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了“管理员”>“系统”>“权限”>“用户角色”>“角色”>“用户角色”网格中无法使用过滤器功能的问题。
* **ACSD-47497** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了“管理员”下的“配置”中不显示“服务”选项卡的问题。
* 更新了修补程序：ACSD-47743。
* 已替换修补程序：MDVA-42807。

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3) — 修复了 _尝试访问类型为bool的值上的数组偏移_ 在PHP 7.4上访问已知产品的某些非现有类别路径时出错。
* **ACSD-47332** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了cron失败，并出现仅在运行UTC时才报告的错误的问题。
* **ACSD-47280** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了无法正确禁用特定范围上的共享目录功能的问题。
* **ACSD-47106** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了无法在公司创建页面上的新自定义属性中保存值的问题。
* 更新了修补程序：ACSD-45143。

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了用户在分配大量产品源时遇到错误的问题。
* **ACSD-46856** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 通过系统>配置>导入>高级定价改进性能更新层价格。
* **ACSD-46541** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 修复了在删除订单项目时，管理员用户无法创建贷项通知单的问题。
* **ACSD-46581** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在选择购物车中的国家/地区后，预计税收总额未更新的问题。
* **ACSD-46618** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了产品列表小组件显示登录客户缓存的价格不正确的问题。
* **ACSD-46674** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在客户电子邮件中，图像类型的自定义选项显示为HTML的问题。
* **ACSD-46988** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了GraphQL“货币”API请求为自定义货币返回NULL值的问题。
* **ACSD-47076** (对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5) — 修复了Vimeo视频无法在店面播放的问题。
* **ACSD-45071** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4) — 修复了导入期间向产品添加默认源的问题。
* **AC-3023** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 将DHL方案更新到最新版本10.0。
* 更新的修补程序：MDVA-42584。
* 已替换修补程序：MDVA-36572和ACSD-45241。

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*(对于Adobe Commerce和Magento Open Source)>=2.4.0 &lt;2.4.5*) — 修复了用户在使用商店信用退款时获得错误订单状态的问题。
* **ACSD-46703** (*(对于Adobe Commerce和Magento Open Source)>=2.4.4 &lt;2.4.6*) — 修复了无法在产品编辑页面上拖放自定义选项的问题。
* **ACSD-44851** (*(对于Adobe Commerce和Magento Open Source)>=2.4.0 &lt;2.4.6*) — 修复了具有子类别的类别无法打开或展开的问题。
* **ACSD-46815** (*(对于Adobe Commerce和Magento Open Source)>=2.4.5 &lt;2.4.6*) — 修复了类别树请求限制为20个类别的问题。
* **ACSD-45675** (*(对于Adobe Commerce和Magento Open Source)>=2.4.0 &lt;2.4.6*) — 修复了产品导出使用 *默认商店视图* 范围。
* **ACSD-46869** (*(对于Adobe Commerce和Magento Open Source)>=2.4.4 &lt;2.4.6*) — 修复了购物车中可配置产品未通过 *PUTREST API* 请求，而不更改产品数量。
* **MDVA-42768-V2** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.3*) — 修复了可配置产品将常规价格显示为 *0* when *显示缺货* is *是*.
* 更新的修补程序：MDVA-44562、ACSD-46213、MDVA-41305、MDVA-38346、MDVA-13203。
* 已弃用的修补程序：MDVA-42768。

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.3*) — 修复了类别树请求限制为20个类别的问题。
* **ACSD-45781** (*(对于Adobe Commerce和Magento Open Source)>=2.4.1 &lt;2.4.2*) — 修复了移动设备上未显示商店前搜索字段的问题。
* **ACSD-46192** (*(对于Adobe Commerce和Magento Open Source)>=2.3.6 &lt;2.4.5*) — 修复了使用 `async/bulk/V1/configurable-products/bySku/options` 端点。
* **ACSD-46404** (*(对于Adobe Commerce和Magento Open Source)>=2.4.4 &lt;2.4.5*) — 修复了管理员用户在升级到2.4.4后无法登录的问题。
* 更新的修补程序：MDVA-41305、MDVA-38626、MDVA-38728、MDVA-41061-V4、MDVA-42269、MDVA-39305。

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.4*) — 修复了特定商店的GraphQL产品变异会返回所有可配置变体（包括未分配给所请求商店的变体）的问题。
* **ACSD-46146** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.6*) — 修复了向管理员下订单后发送两封订单确认电子邮件的问题。
* **ACSD-45255** (*for Adobe Commerce >=2.4.3 &lt;2.4.6*) — 修复了受限管理员用户在“低库存报表”页面上的异常。
* **ACSD-45488** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.6*) — 修复了具有多个来源的可配置产品未自动返回至库存的问题。
* **ACSD-45754** (*(对于Adobe Commerce和Magento Open Source)>=2.3.1 &lt;2.4.6*) — 修复在将优惠券应用到购物车后未添加奖励积分的问题。
* **ACSD-45849** (*for Adobe Commerce >=2.4.3 &lt;2.4.4*) — 修复了应用暂存更新后视频元数据丢失的问题。
* **ACSD-45257** (*(对于Adobe Commerce和Magento Open Source)>=2.3.4 &lt;2.4.4*) — 修复了GraphQL无法正确显示购物车折扣的问题。
* **ACSD-44938** (*(对于Adobe Commerce和Magento Open Source)>=2.4.0 &lt;2.4.4*) — 修复了 `VAT_ID` 无法在GraphQL请求中应用来宾用户。
* 更新的修补程序：MDVA-43417。

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*(对于Adobe Commerce和Magento Open Source)>=2.3.5 &lt;2.4.4*) — 修复在创建贷项通知单后，虚拟产品的库存数量计算错误的问题。
* **ACSD-43887** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.5*) — 修复了启用公司的采购订单后，结账付款页面上显示错误详细信息的问题。
* **ACSD-45143** (*(对于Adobe Commerce和Magento Open Source)>=2.4.0 &lt;2.4.5*) — 修复了 `setShippingAddressesOnCart` 突变不允许将数字区域代码设置为 *地区*.
* **ACSD-44591** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;2.4.6*) — 修复在下单时未确认验证码时发生的错误。
* **ACSD-45520** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.6*) — 修复了用户从购物车编辑可配置产品时，产品详细信息页面上未预选样本选项的问题。
* **ACSD-45169** (*(对于Adobe Commerce和Magento Open Source)>=2.4.1 &lt;2.4.6*) — 修复了 [!DNL Visual Merchandiser] 在应用暂存更新后，无法显示可配置产品的正确库存和价格。
* **ACSD-45424** (*(对于Adobe Commerce和Magento Open Source)>=2.3.4 &lt;2.4.6*) — 修复在部分退款（贷项通知单）后创建错误保留报酬的问题。
* **MDVA-42807** (*(对于Adobe Commerce和Magento Open Source)>=2.3.1 &lt;2.4.6*) — 修复了自定义货币符号未显示在商店前面的问题。
* 更新的修补程序：MDVA-42689和AC-3022。

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;2.4.4*) — 修复了受限管理员用户的订单总数计算错误的问题。
* **MDVA-44940** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;2.4.4*) — 修复从管理员保存类别时发生的SQL错误。
* **MDVA-44562** (*(对于Adobe Commerce和Magento Open Source)>=2.4.0 &lt;2.4.2-p2*) — 修复了尽管GraphQL请求源自非默认商店视图，但引用项目的非默认商店ID仍会被默认商店ID覆盖的问题。
* **MDVA-43167** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.4*) — 修复了当管理员用户选择所有订单时，管理员订单网格批量操作不适用于多页面的问题。
* **MDVA-44044** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.2-p2*) — 修复了将产品分配到新网站后，产品未显示在类别页面上的问题。
* **MDVA-42509** (*(对于Adobe Commerce和Magento Open Source)>=2.3.3 &lt;2.4.4*) — 修复了无法上传CSV以快速排序，从而导致 *无法发送Cookie* 错误。
* 更新的修补程序：MDVA-41061和MDVA-42584。
* 新 [!DNL Quality Patches Tool] 修补程序将从 *MDVA* to *ACSD* 因内部流程更改而导致。

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;2.4.4*) — 修复当购物车中已有最小数量的商品时，无法将其他商品添加到购物车的问题。
* **MDVA-44887** (*(对于Adobe Commerce和Magento Open Source)>=2.4.4 &lt;2.4.5*) — 修复了 *未捕获的语法错误：意外的令牌“const”* “管理”面板中出错。
* **MDVA-43718** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.5*) — 修复 *用户无权访问%resources。* 从自定义集成访问共享目录时显示的错误。
* **MDVA-44660** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2-p1 &lt;2.4.5*) — 修复重音字符出现的问题 ``` ` ``` 无法用于客户的名字和姓氏。
* **MDVA-40896** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;2.4.4*) — 修复了 *错误：类型错误：传递到Magento的参数3* 异步产品批量API中出错。
* **MDVA-38559** (*(对于Adobe Commerce和Magento Open Source)>=2.4.0 &lt;2.4.3*) — 修复了 */V1/customers/search API* 对于具有多个订阅的客户，出现错误。
* **MDVA-44533** (*(对于Adobe Commerce和Magento Open Source)>=2.3.1 &lt;2.4.4*) — 修复了将折扣错误地应用于捆绑子产品的问题。
* 更新的修补程序：MDVA-41061和MDVA-42269。

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.5*) — 修复了产品 *不单独显示* 仍显示在“目录高级搜索结果”中。
* **MDVA-44100** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;2.4.5*) — 修复了将所有FPT分配给购物车中最后一个产品并重置其他产品的问题。
* **MDVA-43605** (*(对于Adobe Commerce和Magento Open Source)>=2.3.1 &lt;2.4.5*) — 修复了使用Rest API时，订单数据对行总数返回负值的问题。
* **MDVA-43102** (*(对于Adobe Commerce和Magento Open Source)>=2.3.1 &lt;2.4.5*) — 修复了通过REST API执行退款时，可售数量未正确更新的问题。
* **MDVA-43178** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3-p2 &lt;2.4.5*) — 修复了无法在GraphQL中检索自定义商店的客户令牌的问题。
* **MDVA-43859** (*(对于Adobe Commerce和Magento Open Source)>=2.4.1 &lt;2.4.5*) — 修复错误 *没有具有customerId =的此类实体* 已删除的客户尝试登录时记录。
* **MDVA-44147** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.5*) — 修复了GraphQL请求未返回申请列表的问题。
* **MDVA-44505** (*(对于Adobe Commerce和Magento Open Source)>=2.4.1 &lt;2.4.3*) — 修复了GraphQL应用奖励积分不更新总计以及在下单期间多次应用商店点数的问题。
* 更新的修补程序：MDVA-29148、MDVA-36464-V5、MDVA-42584、MDVA-39993-V2。

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*(对于Adobe Commerce和Magento Open Source)>=2.4.1 &lt;2.4.3*) — 修复了仅当客户区段设置为时，相关产品规则才起作用的问题 *全部*.
* **MDVA-39605** (*(对于Adobe Commerce和Magento Open Source)>=2.3.4 &lt;2.4.5*) — 修复了Redis缓存TTL（过期日期）值错误的问题。
* **MDVA-43862** (*(对于Adobe Commerce和Magento Open Source)>=2.3.3 &lt;2.4.5*) — 修复了客户因GraphQL而无法更新购物车项目的问题 *UpdateCartItems突变* 错误。
* **MDVA-43824** (*(对于Adobe Commerce和Magento Open Source)>=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) — 修复了在取消具有折扣的订单时出现错误的问题。
* **MDVA-43451** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;2.4.5*) — 修复错误 *未找到请求的商店。 请验证该存储，然后重试。* 为特定网站配置共享目录时显示。
* **MDVA-43491** (*(对于Adobe Commerce和Magento Open Source)>=2.3.5 &lt;2.4.5*) — 修复了在为多商店网站导入产品时，基本图像标签未更新的问题。
* **MDVA-43601** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.5*) — 修复了完全重新索引后缺少触发器的问题。
* **MDVA-42046** (*(对于Adobe Commerce和Magento Open Source)>=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) — 修复了在更新产品时，为具有日期输入字段的产品属性分配错误值的问题。
* **MDVA-43935** (*(对于Adobe Commerce和Magento Open Source)>=2.4.1 &lt;2.4.5*) — 修复了追加销售产品显示两次的问题。
* **MDVA-44188** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;2.4.5*) — 修复了系统发送的 `.-` 地址中的。
* **MDVA-42283** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.5*) — 修复了法语区域设置的管理顺序网格中的日期时间格式无效的问题。
* 更新的修补程序：MDVA-41061-V2、MDVA-36309、MDVA-30862、MDVA-39713。
* 为 [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.3.6*) — 修复了用户无法编辑活动计划更新的开始时间的问题。
* **MDVA-42410** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.5*) — 修复了优惠券报表仅显示默认基本货币的问题。
* **MDVA-41136** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.5*) — 修复了 `mage-cache-sessid` 未扩展，从而导致客户数据清理。
* **MDVA-39993** (*(对于Adobe Commerce和Magento Open Source)>=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) — 修复了通过API完成的库存更改未反映在前端产品页面上的问题。
* **MDVA-42855** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;2.4.5*) — 修复了结帐期间新客户地址未保存到通讯簿的问题。
* **MDVA-42645** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;2.4.5*) — 修复了禁用商店信用功能时管理员无法退款奖励点的问题。
* **MDVA-43414** (*(对于Adobe Commerce和Magento Open Source)>=2.3.6 &lt;=2.3.7-p2*) — 修复运行 `inventory.reservations.updateSalabilityStatus` 数值SKU上的队列消费者。
* **MDVA-41628** (*(对于Adobe Commerce和Magento Open Source)>=2.4.0 &lt;2.4.5*) — 修复了现有受限管理员用户在添加新模块时获得新资源访问权限的问题。
* **MDVA-43348** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.5*) — 修复了在以下情况下，礼品卡GraphQL请求显示错误的问题 `gift_card_options` contain *uid*.
* **MDVA-39546** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.5*) — 修复了在编辑期间，暂存更新的开始日期可以设置为早于当前日期的问题。
* **MDVA-42950** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.5*) — 修复了产品页面上不播放视频的问题。
* **MDVA-42689** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.4*) — 修复了Adobe Commerce在 *完整性约束违规* 导入期间更新产品类别时出错。
* **MDVA-41229** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.5*) — 修复了在可配置产品导入后，后端可用的图像无法在前端显示的问题。
* **MDVA-43731** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;2.4.4*) — 修复了 *搜索同义词* 在中添加值后，将不再起作用 *要匹配的最小术语数*.
* **MDVA-43232** (*(对于Adobe Commerce和Magento Open Source)>=2.3.4 &lt;2.4.5*) — 修复了 [!DNL Visual Merchandiser] 按特殊价格从底部/顶部保存类别时导致错误。
* **MDVA-43726** (*(对于Adobe Commerce和Magento Open Source)>=2.3.3 &lt;2.4.3*) — 修复了基于存储级别属性匹配的目录价格规则在部分重新索引后无法应用的问题。
* 更新的修补程序：MDVA-36464、MDVA-37478、MDVA-38608。
* 为 [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;2.4.5*) — 修复了无法通过REST API为特定网站更新产品价格属性的问题。
* **MDVA-41350** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.5*) — 修复了当具有受限访问权限的管理员用户按SKU在其角色范围之外按订单添加产品时，会引发异常的问题。
* **MDVA-42269** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3-p1 &lt;2.4.5*) — 修复了管理员用户由于 *类型错误：strtotime()要求参数1为字符串，给定null* 错误。
* **MDVA-40830** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.5*) — 修复了在下单期间多次应用商店点数的问题。
* **MDVA-42237** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.5*) — 修复了在可配置产品特价的子产品价格发生更改后，其特价未更新的问题。
* **MDVA-42520** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;2.4.4*) — 修复在以下情况下税率应用两次的问题 *启用跨境贸易* 中，将使用。
* 更新的修补程序：MDVA-27239、MDVA-39305、MDVA-41236、MDVA-36832。
* 已弃用的修补程序：MDVA-37725。

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*(对于Adobe Commerce和Magento Open Source)>=2.3.2 &lt;2.4.5*) — 修复了批量属性更新仅在更改 *产品可见性*.
* **MDVA-43091** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;2.4.4*) — 修复了从后端的管理员订购捆绑产品时出现错误的问题 *不能对此产品使用小数量*.
* **MDVA-40816** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.5*) — 修复了相关产品规则显示规则条件中未定义类别的产品的问题。
* **MDVA-41305** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.5*) — 修复了GraphQL突变将产品添加到愿望列表后不返回可配置产品选项的问题。
* **MDVA-39181** (*(对于Adobe Commerce和Magento Open Source)>=2.4.1 &lt;2.4.5*) — 修复了相关产品规则显示规则条件中未定义类别的产品的问题。
* **MDVA-42584** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.3*) — 修复了通过导入或API更改数量和库存状态后，后端的可配置库存状态未更新的问题。
* **MDVA-40175** (*(对于Adobe Commerce和Magento Open Source)>=2.4.0 &lt;2.4.3*) — 修复了 *单击以更改发运方法* 在重新排序期间，不会在“管理员”中显示用于选择送货方法的单选按钮。
* **MDVA-42768** (*(对于Adobe Commerce和Magento Open Source)>=2.3.4 &lt;2.4.5*) — 修复了“可配置产品”在 *显示缺货* 是。
* **MDVA-43201** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.4*) — 修复了在使用具有特定区域设置的DOB属性时客户登录中出现错误的问题。
* 更新的修补程序：MDVA-35092和MDVA-33970。

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.5*) — 修复了当Adobe Commerce时区与本地环境时区不同时，日期过滤器无法正常工作的问题。
* **MDVA-42657** (*(对于Adobe Commerce和Magento Open Source)>=2.4.1 &lt;2.4.5*) — 修复了管理员用户在客户区段条件中无法选择类别的问题。
* **MDVA-42806** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.4*) — 修复了 *新公司注册* 每次通过REST API更新现有公司时，都会发送电子邮件。
* **MDVA-37984** (*(对于Adobe Commerce和Magento Open Source)>=2.4.1 &lt;2.4.5*) — 修复了 [!DNL Visual Merchandiser] *按规则匹配产品* 功能无法通过暂存更新正确筛选产品。
* **MDVA-40488** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.4*) — 修复了具有无现货子产品的可配置产品无法在其正确价格范围内显示的问题。
* **MDVA-42507** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;2.4.5*) — 修复了在对购物车规则应用暂存更新后，清理完整页面缓存的问题。
* **MDVA-39163** (*(对于Adobe Commerce和Magento Open Source)>=2.3.5 &lt;2.4.5*) — 修复了注册新用户且购物车中的产品来自来宾会话时，无法使用送货方法的问题。
* **MDVA-38626** (*(对于Adobe Commerce和Magento Open Source)>=2.3.3 &lt;2.4.5*) — 修复了管理员用户无法使用 [!DNL PayPal Payflow Pro] 付款。
* **MDVA-38666** (*(对于Adobe Commerce和Magento Open Source)>=2.3.2 &lt;2.3.6*) — 修复了管理员用户无法更改客户购物车中可配置产品选项的问题。
* **MDVA-38526** (*(对于Adobe Commerce和Magento Open Source)>=2.4.1 &lt;2.4.4*) — 修复了管理员用户无法访问 [!DNL Site-Wide Analysis tool].
* 更新的修补程序：MDVA-40101。

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.4*) — 修复了用户在将 *图像消息* cookie（如果它已存在，但没有新消息）。
* **MDVA-41139** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;2.4.4*) — 修复了当简单产品的qty=0（其其中一个来源）时，可配置产品在产品导入后变为无现货的问题。
* **MDVA-42326** (*(对于Adobe Commerce和Magento Open Source)>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修复了即使启用了永久性购物车，客户在会话超时后结帐时仍会出现错误的问题。
* **MDVA-42341** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.4*) — 修复了 `categoryList` 如果请求具有Store标头，则GraphQL查询不会筛选结果。
* **MDVA-38393** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.4*) — 修复了如果可配置产品的简单产品被重新命名，则目录规则停止工作的问题。
* **MDVA-39153** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.4*) — 修复了在管理员中重新排序期间折扣额计算不正确的问题。
* 更新的修补程序：MDVA-28993、MDVA-41061、MDVA-35984。

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.3*) — 修复了管理员用户在删除网站后无法访问客户网格的问题。
* **MDVA-40311** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2-p2 &lt;2.4.4*) — 修复了管理员用户收到错误消息的问题 *安全性或表单密钥无效。 请刷新页面* 登录到管理员后（如果配置了自定义管理员路径并启用了密钥）。
* **MDVA-41631** (*(对于Adobe Commerce和Magento Open Source)>=2.4.1 &lt;2.4.4*) — 修复了用户在尝试检索订单信息时遇到错误且没有可选内容的问题 *电话* 价值通过GraphQL。
* **MDVA-27239** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.3.6*) — 修复了不显示交叉销售产品的问题。
* 更新的修补程序：MDVA-37068、MDVA-35254、MDVA-41164、MDVA-37916、MDVA-37478、MDVA-34551、MDVA-31791。

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*(对于Adobe Commerce和Magento Open Source)>=2.3.5 &lt;2.4.4*) — 修复了在重新索引期间前端缺少产品的问题。
* **MDVA-40120** (*(对于Adobe Commerce和Magento Open Source)>=2.4.1 &lt;2.4.4*) — 修复了GraphQL按DESC/ASC排序时，无法处理具有相同相关性或价格的产品的问题。
* **MDVA-41399** (*(对于Adobe Commerce和Magento Open Source)>=2.3.3 &lt;2.4.2*) — 修复了管理员用户无法访问 *管理购物车* 页面。
* **MDVA-40609** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.3*) — 修复了 `cataloginventory_stock_status` 索引表，显示不正确的禁用产品数量。
* **MDVA-39031** (*(对于Adobe Commerce和Magento Open Source)>=2.4.1 &lt;2.4.4*) — 修复了即使未将产品分配到目标网站，仍可以通过GraphQL将产品添加到购物车的问题。
* **MDVA-41597** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.4*) — 修复了用户在使用GraphQL向购物车添加多个可配置产品时遇到错误的问题。
* **MDVA-27456** (*(对于Adobe Commerce和Magento Open Source)>=2.3.5 &lt;2.3.7*) — 修复了用户在尝试加载时遇到错误的问题 [!DNL Swagger].
* **MDVA-32776** (*(对于Adobe Commerce和Magento Open Source)>=2.4.0 &lt;2.4.2*) — 修复下单但未发运时库存状态未更新的问题。
* **MDVA-30862** (*(对于Adobe Commerce和Magento Open Source)>=2.3.4 &lt;2.4.0*) — 修复了打印的PDF发票上订单日期不正确的问题。
* 改进了 [!DNL Quality Patch Tool]. 为 [!DNL quality patches] 工具的最新版本。
* 更新的修补程序：MDVA-33382和MDVA-39482。

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.4*) — 修复了在以前删除了结束日期的情况下，无法为产品创建新计划更新或编辑现有计划更新的问题。
* **MDVA-41046** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.4*) — 修复了具有自定义选项的简单产品可分配给可配置/分组产品的问题。
* **MDVA-40545** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.4*) — 修复了即使同一页面有多个节点，也只检索页面的第一个节点的问题。
* **MDVA-41164** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.3-p1*) — 修复了管理员用户无法保存或编辑具有文件或图像类型自定义客户属性的公司的问题。
* **MDVA-39229** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.4*) — 修复了在更新目录规则暂存更新开始时间后显示以下错误的问题： *Cron Job staging_synchronize_entities_period出现错误：无法删除活动更新。*
* **MDVA-40619** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.4*) — 修复了在CMS页面上尝试进行内联编辑时，对CMS页面层次结构所做的更改导致500错误的问题。
* **MDVA-41061** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.3*) — 修复了当从管理员保存产品时，库存状态重置为可出售的问题。
* **MDVA-31763** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.4*) — 修复了在手动重新编入索引之前，目录价格规则会恢复（或未应用）的问题。
* **MDVA-37748** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.3*) — 修复了GraphQL查询返回未分配到共享目录的产品的问题。

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.4*) — 修复了无法通过REST API同时创建同一订单的部分发票的问题。
* **MDVA-40101** (*(对于Adobe Commerce和Magento Open Source)>=2.3.2 &lt;2.4.0*) — 修复在使用 [!DNL PayPal Express] 结帐。
* **MDVA-40401** (*(对于Adobe Commerce和Magento Open Source)>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修复即使下单失败，优惠券使用值也发生更改的问题。
* **MDVA-40537** (*(对于Adobe Commerce和Magento Open Source)>=2.3.4 &lt;=2.4.0-p1*) — 修复了当存在具有相同URL键的多个CMS页面时，用户在创建存储视图时遇到错误的问题。
* **MDVA-37725** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;=2.4.3-p1*) — 修复了从非默认网站发送的异步订单电子邮件包含来自默认网站的徽标URL的问题。
* **MDVA-39482** (*(对于Adobe Commerce和Magento Open Source)>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修复了启用延交订单后，导入数量为“0”的产品时出现缺货的问题。
* **MDVA-40435** (*(对于Adobe Commerce和Magento Open Source)>=2.3.4 &lt;2.4.4*) — 修复了通过GraphQL应用时，具有动态价格的捆绑产品的折扣不正确的问题。
* **MC-42528** (*(对于Adobe Commerce和Magento Open Source)>=2.4.3 &lt;=2.4.3-p1*) — 修复了 `categoryList` GraphQL查询返回已分配和未分配的类别。
* **MDVA-29400** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 修复了与 [!DNL PayPal Express Checkout].
* **MDVA-26005** (*(对于Adobe Commerce和Magento Open Source)>=2.3.4 &lt;=2.3.5-p2*) — 修复了在类别树中无法为购物车价格规则条件选择类别的问题。
* **MDVA-25631** (*(对于Adobe Commerce和Magento Open Source)>=2.3.3 &lt;=2.3.5-p2*) — 提高编辑和保存包含大量客户的客户区段的性能。

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.4*) — 修复了GraphQL搜索查询未在管理员的热门搜索词中显示的问题。
* **MDVA-40601** (*(对于Adobe Commerce和Magento Open Source)>=2.3.1 &lt;=2.4.2-p2*) — 修复了用户在尝试通过GraphQL计划更新获取有关已更改类别的信息时遇到错误的问题。
* **MDVA-37234** (*(对于Adobe Commerce和Magento Open Source)>=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) — 修复了对同一SKU多次向购物车添加项目（并行请求）时，为同一购物车ID创建重复的行项目的问题。
* **MDVA-33606** (*(对于Adobe Commerce和Magento Open Source)>=2.4.1 &lt;=2.4.2-p2*) — 修复了用户在 *唯一约束冲突* 保存分配给层次结构的CMS页面时出错。
* **MDVA-31590** (*(对于Adobe Commerce和Magento Open Source)>=2.4.0 &lt;=2.4.1-p1*) — 修复了用户无法使用MySQL异步队列批量更新属性的问题。
* **MDVA-36309** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;=2.4.2-p2*) — 修复了管理网格中按属性划分的产品搜索缓慢的问题。

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.4*) — 修复了使用FPT的发票在从商店信用支付订单时显示错误的总计的问题。
* **MDVA-37364** (*(对于Adobe Commerce和Magento Open Source)>=2.4.0 &lt;=2.4.3*) — 修复了日期类型的自定义客户属性损坏客户网格UI的问题。
* **MDVA-39195** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;=2.4.2-p2*) — 修复了 *添加到购物车* “重定向到购物车”启用后，“类别”页面上的按钮处于不活动状态。
* **MDVA-37115** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;=2.4.2-p2*) — 修复了 *仅剩0个* “可配置产品”页面上会显示“注意事项”。
* **MDVA-39521** (*(对于Adobe Commerce和Magento Open Source)>=2.4.0 &lt;2.4.4*) — 修复了用户无法通过GraphQL在购物车上为空电话号码设置送货地址的问题。
* **MDVA-39384** (*(对于Adobe Commerce和Magento Open Source)>=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) — 修复了无法保存公司用户的自定义客户属性的问题。
* **MDVA-39043** (*(对于Adobe Commerce和Magento Open Source)>=2.3.4 &lt;=2.4.3*) — 修复了具有有限访问权限的管理员用户在尝试添加 *产品* 小组件到CMS页面。
* **MDVA-39966** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) — 修复了部署错误区域设置时出现的问题。
* **MDVA-38852** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;=2.3.5-p2*) — 修复了设计目录清单锁定表以获取在多个并行订单情况下会显着降低性能的更新的问题。
* **MDVA-39986** (*(对于Adobe Commerce和Magento Open Source)>=2.4.1 &lt;2.4.3*) — 修复了用户无法使用Safari浏览器在MacOS的管理员中下订单的问题。
* **MDVA-38447** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.4*) — 修复了两个问题：其中 *不单独显示* 可配置的子产品在GraphQL响应中返回，并使用类别筛选器优化GraphQL产品查询的MySQL查询。
* **MDVA-40134** (*(对于Adobe Commerce和Magento Open Source)>=2.4.2 &lt;2.4.3*) — 修复了启用共享目录后GraphQL不返回相关产品的问题。
* **MDVA-39935** (*(对于Adobe Commerce和Magento Open Source)>=2.4.1 &lt;2.4.4*) — 修复了GraphQL在网站级别返回禁用的可配置子产品的问题。

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*(对于Adobe Commerce和Magento Open Source)>=2.4.0 &lt;2.4.4*) — 修复了 *调用成员函数getId()* 错误显示在“管理员”的“订单详细信息”页面上。
* **MDVA-34948** (*(对于Adobe Commerce和Magento Open Source)>=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 修复了长时间运行查询的问题，如 `GET_LOCK`.
* **MDVA-39305** (*(对于Adobe Commerce和Magento Open Source)>=2.4.0 &lt;=2.4.2-p1*) — 修复了注册客户无法使用启用的Google ReCaptcha登录的问题。
* **MDVA-37897** (*(对于Adobe Commerce和Magento Open Source)>=2.3.0 &lt;2.4.4*) — 修复了当客户尝试使用“最近查看”小组件中的选项添加产品时，错误重定向的问题。

## v1.1.0 {#v1-1-0}

* 为了改善用户体验，并使客户更轻松地搜索所需的修补程序，我们引入了修补程序类别。
* 的 `patches.json` 文件已重命名为 `support-patches.json`.
* **MDVA-38799** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.3*) — 修复了在创建暂存更新后无法保存可下载产品的问题。
* **MDVA-37592** (*for Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) — 修复了按价格排序的产品对于分配给共享目录的零价格产品无法正常工作的问题。
* **MDVA-38827** (*(对于Adobe Commerce)>=2.3.3-p1 &lt;2.4.4*) — 修复了客户收到包含错误消息的订单发运电子邮件的问题。

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*对于Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) — 修复了保存CMS页面时的错误： *具有相同ID的项目PAGE_ID已存在*.
* **MDVA-34680** (*(对于Adobe Commerce)>=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) — 修复了客户帐户创建时间在客户网格中无法正确过滤的问题。
* **MDVA-37068** (*(对于Adobe Commerce)>=2.3.1 &lt;2.4.4*) — 修复了当购物车只包含虚拟产品时，税率显示不正确的问题。
* **MDVA-38608** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.3*) — 修复了未成功完成重新索引时未删除临时表的问题。
* **MDVA-38308** (*for Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) — 修复了与添加 [!DNL Vimeo] 视频到产品。

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*for Adobe Commerce >=2.3.6 &lt;2.4.3*) — 修复了在使用 [!DNL Paypal Payment Advanced] 方法。
* **MDVA-37082** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.3*) — 修复了保存已分组产品的自定义库存时导致产品在前端显示无库存的问题。
* **MDVA-36572** (*for Adobe Commerce >=2.3.5 &lt;2.4.3*) — 修复了贷项通知单更新不再导致数据库中重复的产品预订更新的问题。
* **MDVA-38132** (*for Adobe Commerce >=2.3.3 &lt;2.4.3*) — 修复了由于 *重定向过多* 错误。
* **MDVA-38270** (*for Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修复了GraphQL中订单总数中缺少礼品卡信息的问题。

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*(对于Adobe Commerce)>=2.4.2 &lt;=2.4.4*) — 修复了当网站ID与商店ID不一致时，通过GraphQL将可配置产品添加到购物车的问题。
* **MDVA-36832** (*for Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) — 修复了当视图宽度为768像素时，图像在页面上重复的问题。
* **MDVA-37874** (*(对于Adobe Commerce)>=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) — 修复了 *整个购物车的固定折扣金额* 被错误地应用于包含多个选项的捆绑产品。
* **MDVA-37913** (*对于Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) — 修复了如果可下载产品通过API进行更新，则可下载链接消失的问题。
* **MDVA-34330** (*for Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) — 修复了“订单”网格中的订单未按照管理时区进行过滤的问题。

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*(对于Adobe Commerce)>=2.3.0 &lt;=2.3.7*) — 修复了Adobe Commerce在为随 *按帐户付款* 付款方法。
* **MDVA-37362** (*for Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) — 修复了GraphQL响应中可配置产品选项值和变量属性值为空的问题。
* **MDVA-37288** (*(对于Adobe Commerce 2.4.2)*) — 修复在GraphQL请求后返回错误层价的问题。
* **MDVA-37225** (*for Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) — 修复了导入的SKU中存在整数值时，快速订单创建过程中上传过程卡住的问题。
* **MDVA-37224** (*for Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) — 修复了客户无法通过 [!DNL PayFlow Pro] 购物车中的其他产品。
* **MDVA-36286** (*for Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) — 修复了当同一SKU在子类别中的位置不同时，页面生成器产品小组件预览会中断的问题。
* **MDVA-30186** (*for Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) — 修复了在GraphQL响应中，属性选项按选项值而不是属性项目计数进行排序的问题。

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*(对于Adobe Commerce)>=2.3.0 &lt;=2.4.2*) — 修复了通过API更改旧自定义选项后仍保留的问题。
* **MDVA-35773** (*for Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) — 修复了折扣为100%的订单的发票上未显示总计为零的问题。
* **MDVA-36833** (*(对于Adobe Commerce 2.4.2)*) — 修复了在从共享目录中排除某些产品后，搜索结果每页显示随机数的产品的问题。
* **MDVA-37182** (*(对于Adobe Commerce)>=2.4.1 &lt;=2.4.2*) — 修复了在这两个变量中获取错误搜索结果的问题 [!DNL Elasticsearch] 版本6和版本7。
* **MDVA-36253** (*对于Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) — 修复了删除项目后，迷你购物车中显示错误小计的问题。
* **MDVA-36853** (*(对于Adobe Commerce 2.4.2)*) — 修复了加载大型媒体集时不显示图像的问题。

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*对于Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) — 修复了类别页面上缺少捆绑产品的问题。
* **MDVA-36615** (*(对于Adobe Commerce 2.4.2)*) — 修复了管理产品网格中产品计数不正确的问题。
* **MDVA-36464** (*(对于Adobe Commerce)>=2.4.0 &lt;=2.4.2*) — 修复了电子邮件通知配置在商店视图级别不起作用的问题。
* **MDVA-36138** (*对于Adobe Commerce ^2.3.2*) — 修复了未调整发运价格，且如果购物车中的所有物品不符合免费送货车规则，则会向客户显示完整发运价格的问题。
* **MDVA-36424** (*对于Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) — 修复了当后端基本URL与店面基本URL不同时，重复编辑内容时，附加到页面生成器元素的媒体图像消失的问题。
* **MDVA-35984** (*对于Adobe Commerce ^2.4.0*) — 修复在为同一产品创建多个并发发运后，产品数量和可售数量不正确的问题。

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*for Adobe Commerce >=2.3.4 &lt;2.4.2*) — 这修复了GraphQL查询未使用类别缓存标记进行缓存的问题。
* **MDVA-33168** (*(对于Adobe Commerce)>=2.3.3 &lt;2.4.2*) — 修复了通过API更新产品属性时，所有其他属性都更改为空值的问题。
* **MDVA-19640** (*(对于Adobe Commerce)>=2.3.0*) — 修复了 [!DNL Advanced Reporting] 不显示任何数据。
* **MDVA-11189** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.5*) — 修复了在导入CSV文件以更新产品库存后， `cataloginventory_stock` 表格。
* **MDVA-26639** (*(对于Adobe Commerce)>=2.3.3-p1 &lt;2.3.6*) — 修复了在创建新的订单确认电子邮件模板时，订单邮件中缺少订单项的问题。
* **MDVA-15546** (*(对于Adobe Commerce)>=2.3.0*) — 修复了在创建订单后， *列entity_id其中子句不明确* 异常日志中显示错误。
* **MDVA-21095** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.5*) — 修复了查询 `INSERT INTO search_tmp` 在批量属性值更新后不会结束。
* **MDVA-23845** (*(对于Adobe Commerce)>=2.3.2-p2 &lt;2.3.5*) — 修复了启用JavaScript缩小后无法预览电子邮件模板的问题。
* **MDVA-22026** (*for Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修复了从CSV文件导入产品（包括来自外部URL的图像）失败的问题。
* **MDVA-22383** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.4*) — 修复了保存产品需要较长时间且分页时出现的问题。
* **MC-41359** (*for Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) — 修复了SameSite Cookie参数设置不正确的问题。

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*(对于Adobe Commerce 2.4.1)*) — 修复了页面生成器引发以下错误的问题： *启动页面生成器时出错。 请咨询您的技术支持联系人。*
* **MDVA-35356** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.3*) — 修复了取消部分开票订单后，商店信用退回不正确的问题。
* **MDVA-33289** (*(对于Adobe Commerce)>=2.4.0 &lt;2.4.3*) — 修复了在结帐期间，原始JavaScript代码显示在帐单地址UI中(如果 [!DNL Google Tag Manager] 启用。
* **MDVA-35982** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.3*) — 修复了管理员用户受限于特定网站时无法为同一网站上的订单创建装运的问题。
* **MDVA-35155** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.6*) — 修复了选项标题发生更改时无法购买捆绑产品的问题。
* **MDVA-35910** (*for Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修复了在禁用“作为客户登录”功能后无法创建新客户帐户的问题。
* **MDVA-34474** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.3*) — 修复了使用API将产品添加到申请列表时出现的问题。
* **MDVA-34591** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.3*) — 修复了购物车规则折扣计算不正确的问题 *最大数量折扣应用于* 和 *折扣数量步骤（购买X）*.
* **MDVA-33704** (*(对于Adobe Commerce)>=2.4.0 &lt;2.4.3*) — 修复了 *在商店取货* 未显示送货选项，但已将其配置为可用。
* **MDVA-34928** (*for Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) — 修复在从付款中删除商店信用后，无限期显示页面加载器的问题。
* **MDVA-35254** (*for Adobe Commerce >=2.3.1 &lt;2.4.3*) — 修复了验证码在结账期间出现的问题。
* **MDVA-35569** (*for Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了 *固定产品税* 指定状态时，未在GraphQL响应中填充字段。
* **MDVA-35847** (*for Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修复了B2B问题：如果使用自定义客户属性，则“公司用户”表单会损坏。
* **MDVA-31307** (*(对于Adobe Commerce)>=2.4.0 &lt;2.4.2*) — 修复了 *内存不足* 由于缓存块的动态CSP白名单问题，导致某些类别出错。

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.3*) — 修复了错误 *正在进行* 消息状态为正确 *complete* 消费者消息 `quoteItemCleaner` 删除多个产品后，Analytics会立即删除这些产品。
* **MDVA-34102** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.3*) — 修复“产品网格”和“编辑产品”页面上“管理员”区域中的禁用产品的“默认库存”数量为零的问题。
* **MDVA-35286** (*(对于Adobe Commerce)>=2.4.0 &lt;2.4.2*) — 修复了客户在购物车中捆绑了产品并从“多地址结账”切换到“Onepage结账”时出现错误的问题。
* **MDVA-35312** (*(对于Adobe Commerce)>=2.4.1-p1 &lt;2.4.2*) — 修复了空GraphQL请求时的响应代码500。
* **MDVA-34189** (*for Adobe Commerce >=2.3.4 &lt;2.4.3*) — 修复了 [!DNL Visual Merchandiser] 查询。
* **MDVA-34695** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.1*) — 修复负数 `children_count` 删除类别后。

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*for Adobe Commerce >=2.3.1 &lt;2.4.3*) — 修复了 *使用默认值* 复选框会在应用计划更改后清除。 计划更改不再生效后，即会显示问题。
* **MDVA-35064** (*for Adobe Commerce >=2.3.3 &lt;2.4.3*) — 修复了无法为通过API创建的可配置产品生成URL重写的问题。
* **MDVA-34943** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了快速订购缓存先前输入的SKU的问题。
* **MDVA-35197** (*(对于Adobe Commerce)>=2.3.5 &lt;2.4.0*) — 修复了使用GraphQL添加到购物车时，如果之前添加的产品无现货，则出现错误的问题。
* **MDVA-34850** (*(对于Adobe Commerce)>=2.3.1 &lt;2.4.0*) — 修复了不显示可配置产品的无现货选项，而是显示为点进的问题。
* **MDVA-34867** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.3*) — 修复了计划更新的条件字段集的值无法保存的问题。
* **MDVA-35092** (*for Adobe Commerce >=2.3.5 &lt;2.4.3*) — 修复了用户无法添加 [!DNL Vimeo] 视频由于已弃用 [!DNL Vimeo] API。

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*for Adobe Commerce >=2.3.6 &lt;2.4.3*) — 修复了当匹配的产品每个网站的价格不同时，页面生成器产品内容类型预览会中断的问题。
* **MDVA-32634** (*对于Adobe Commerce ^2.3.1*) — 修复了 `url_path` 在层次结构中移动类别后，分配给所有商店的类别保持不变。
* **MDVA-33344** (*对于Adobe Commerce ^2.3.0*) — 修复了硬编码的问题 `rma_item` 使用实体默认属性集ID，而不是数据库中的值。
* **MDVA-34192** (*for Adobe Commerce >=2.3.4 &lt;2.4.3*) — 修复了无法使用dd/mm/yyyy格式修改/指定客户出生日期的问题。
* **MDVA-34847** (*对于Adobe Commerce ^2.3.0*) — 在具有自定义权限的管理员用户的管理员收藏集中，修复了SQL条件的存储ID类型转换为整数的问题。
* **MDVA-34886** (*对于Adobe Commerce ^2.3.2*) — 修复在 *权重* 产品属性配置为可搜索。

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.3*) — 修复了 [!DNL PayPal Payflow Pro] 付款失败，并出现重定向参数列表格式错误。
* **MDVA-34023** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.3*) — 修复错误 *没有具有addressId的此类实体* 在访客的浏览器中随机显示。
* **MDVA-32759** (*对于Adobe Commerce >=2.3.1 &lt;2.4.3，带有B2B扩展*) — 修复了共享目录删除现有层定价的问题。
* **MDVA-33482** (*对于Adobe Commerce ^2.3.5*) — 修复了根据部分发票生成贷项通知单时，导致对总订单征税而不是对该部分发票征税的问题。
* **MDVA-33393** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了错误 *提供的countryId不存在*.
* **MDVA-33632** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.7*) — 提供异常消息所在位置的修复 *此产品无现货* 现在，在尝试重新订购无现货产品时，会向管理员用户显示。
* **MDVA-34469** (*for Adobe Commerce >=2.4.1 &lt;2.4.2*) — 修复了使用多个商店视图时客户购物车上的GraphQL突变失败的问题。
* **MDVA-33976** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.7*) — 修复了在从捆绑产品中删除第二个选项后，在店面上显示捆绑产品无现货的问题。
* **MDVA-33894** (*对于Adobe Commerce >=2.4.0 &lt;2.4.1，带有B2B扩展*) — 修复了快速订购功能的多个问题，包括添加和删除多个产品以及SKU区分大小写。
* **MDVA-27664** (*for Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修复了客户注册表单中导致显示错误的问题： *错误 — 出生日期不应大于今天。*
* **MDVA-33970** (*for Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了将价格属性的范围设置为网站时，贷项通知单中存在错误货币符号的问题。
* **MDVA-33992** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了B2B特殊定价在结帐过程中显示不正确的问题。
* **MDVA-34100** (*(对于Adobe Commerce)>=2.3.4 &lt;2.4.2，带有B2B扩展*) — 修复了无法从公司结构页面创建公司帐户的问题。

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*for Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) — 修复了从CSV文件导入产品后复制的图像的问题。
* **MDVA-33382** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了从类别中删除产品后索引器失效的问题。
* **MDVA-28511** (*for Adobe Commerce >=2.3.5 &lt;2.3.6*) — 修复了无法完成的问题 [!DNL PayPal] 如果“名称”字段包含某些字符（如重音大写字母），则结帐。
* **MDVA-31519** (*for Adobe Commerce >=2.3.5 &lt;2.3.6*) — 修复了使用站点范围的销售规则时来宾结账中等待超时的问题。
* **MDVA-33281** (*for Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修复了 `inventory:reservation:list-inconsistencies` 因为SKU参数类型错误。
* **MDVA-24201** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.5*) — 修复在手动重新编制索引之前，价格未反映计划购物车价格规则的问题。
* **MDVA-32694** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) — 修复了管理员用户在产品与非默认商店相关时，无法将产品添加到可转让报价的问题。
* **MDVA-33516** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.6*) — 修复了在申请列表中编辑捆绑产品会导致错误的问题。
* **MDVA-33975** (*for Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了与GraphQL请求中的价格计算相关的多个问题。

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了 [!DNL PayPal] 无法在 **报表** > **销售** > **[!DNL PayPal]** 按预期结算。
* **MCP-87** (*for Adobe Commerce >=2.3.1 &lt;2.4.2*) — 大型配置文件的类别产品和库存索引器的索引时间缩短。
* **MDVA-33106** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复在崩溃后删除重新计划的产品更改的问题 `run` 命令。
* **MDVA-19391** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.5*) — 修复了 `analytics_collect_data` 由于 `catalog_category_entity_text` 表。
* **MDVA-20376** (*for Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修复了 *没有customerId = 1的此类实体* 错误 `exception.log` 订单投放后登录的客户。
* **MDVA-23764** (*(对于Adobe Commerce)>=2.3.2 &lt;2.3.5*) — 修复了 `JsFooterPlugin.php` 会影响动态块的显示。
* **MDVA-13203** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了 *完整性约束违规search_tmp_表* 完全重新索引后出现错误。
* **MDVA-23426** (*(对于Adobe Commerce)>=2.3.3 &lt;2.3.5*) — 修复了由Adobe Commerce发送的通知电子邮件包含空白正文且内容作为附件添加的问题。
* **MDVA-22150** (*for Adobe Commerce >=2.3.1 &lt;2.3.4*) — 修复了当管理员中禁用了可配置产品时，购物车中具有可配置产品且应用了优惠券的客户无法登录的问题。
* **MDVA-32545** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了在从管理员创建订单时发票不自动发出的问题。
* **MDVA-32714** (*(对于Adobe Commerce)>=2.3.4 &lt;2.4.1*) — 修复了客户组价格在GraphQL产品查询中不起作用的问题。

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*(对于Adobe Commerce)>=2.3.2 &lt;2.4.2*) — 添加 *小计(包括 税)* 选项来为规则条件定价。
* **MDVA-31236** (*(对于Adobe Commerce)>=2.4.0 &lt;2.4.2*) — 修复了具有自定义资源访问权限的管理员无法设置2FA或登录的问题。
* **MDVA-30845** (*(对于Adobe Commerce)>=2.3.5 &lt;2.3.7*) — 修复了 *抱歉，此订单目前没有报价* 无法连接到UPS XML/USPS/DHL时显示错误，并且没有其他送货方法可用。
* **MDVA-32133** (*(对于Adobe Commerce)>=2.4.0 &lt;2.4.1*) — 修复了在某些情况下无法从页面生成器中加载媒体集的问题。
* **MDVA-12304** (*(对于Adobe Commerce)>=2.3.0*) — 将Cookie的最大数量从50增加到200。
* **MDVA-32632** (*(对于Adobe Commerce)>=2.3.2 &lt;2.3.5*) — 修复了订单显示在付款系统中，但不在Adobe Commerce中的问题。
* **MDVA-32449** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2，带有B2B扩展*) — 修复订单历史记录加载非常缓慢或完全未加载的问题。
* **MDVA-32739** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了启用异步电子邮件通知会发送旧销售电子邮件的问题。

## v1.0.11 {#v1-0-11}

* **MC-38509** (*适用于Adobe Commerce 2.3.6、2.4.1*) — 修复了 *创建帐户* 按钮在更正 *新建客户帐户* 表单。
* **MDVA-31006** (*适用于Adobe Commerce 2.3.0、2.3.1*) — 修复了在使用 [!DNL Paypal Express] 付款。
* **MDVA-25602** (*(对于Adobe Commerce 2.3.0)*) — 修复了 [!DNL PayPal Payflow Pro] 支付方法和Cookie `SameSite=Lax` 默认情况下，在Chrome 80浏览器和API响应重定向到客户登录页面中。

## v1.0.10 {#v1-0-10}

修补程序版本的小修复

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*(对于Adobe Commerce)>=2.3.2 &lt;2.4.2*) — 修复了当 *整个购物车的固定金额折扣* 操作。
* **MDVA-30889** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了以虚拟和简单产品作为选项开票捆绑包后出现错误的问题。
* **MDVA-31791** (*for Adobe Commerce >=2.3.4 &lt;2.3.5*) — 在使用Target规则或关联的产品时，会提高产品页面的性能。
* **MDVA-31168** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了产品导出CSV文件未显示，且内存分配错误的问题。
* **MDVA-32313** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.4*) — 修复了可配置产品添加到愿望列表时使用错误配置选项的问题。
* **MDVA-31759** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了产品未更新为 *下拉列表* 和 *textarea* 属性值。
* **MDVA-32012** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了无法验证韩国和阿根廷邮政编码的问题。
* **MDVA-31640** (*for Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) — 修复了无法通过REST API更新特价的问题。
* **MDVA-28651** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.6 || >2.4.0，带有B2B扩展*) — 修复了通过REST API加载可转让报价时出现性能问题的问题。

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*对于Adobe Commerce >=2.3.0 &lt;2.4.1，带有B2B扩展*) — 修复了在贷项通知单网格中显示错误货币符号的问题。
* **MDVA-31295** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复在完成部分订单并对项目征税时，不计算奖励点数的问题。
* **MDVA-30112** (*for Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复订单数超过 *束团大小* 值，Adobe Commerce会将 *待定* 状态为不一致。
* **MDVA-31150** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了GET发票余额API调用未返回商店信用卡和礼品卡余额的问题，该问题是：通过Rest API调用过帐发票，并且订单部分由商店信用卡和礼品卡帐户支付。
* **MDVA-30963** (*(对于Adobe Commerce)>=2.3.2 &lt;2.4.2*) — 修复了产品筛选结果集仅包含为 *所有商店查看次数* 在“管理员”中的范围中，包括在商店视图级别上值被覆盖的产品。
* **MDVA-29954** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2，带有B2B扩展*) — 修复了 *新公司注册请求* 和 *你已经跟一家公司有联系了* 从错误地址发送电子邮件。
* **MDVA-28357** (*(对于Adobe Commerce)>=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) — 将标准分析器替换为 [!DNL ElasticSearch] 用于执行通配符搜索查询的索引，可与包含连字符(“ — ”)的SKU配合使用。

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了自定义订单状态更改为 *处理* 使用WebApi创建部分发运后。
* **MDVA-30428** (*for Adobe Commerce >=2.3.4 &lt;2.3.5*) — 修复了如果将产品分配给自定义库存源，客户无法将产品添加到愿望列表的问题。
* **MDVA-30594** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了配置FPT后，在结帐期间无法保存具有多个地址的订单的问题。
* **MDVA-29148** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了通过API调用创建产品时，产品自定义属性( `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` （如多选）如果有效负载中未提供任何值，则类型不会使用其默认值。
* **MDVA-30837** (*(对于Adobe Commerce)>=2.3.1 &lt;2.3.5*) — 添加了配置设置 *包括税额：是/否* 在Free Shipping方法配置中。 When *包括税额* 设置为 *是*，最小订单金额计算为小计+税。 When *包括税额* 设置为 *否*，最小订单金额计算为小计
* **MDVA-25028** (*for Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) — 修复了使用 [!DNL PayPal Payflow Pro] 触发欺诈筛选器时，未将其设置为“怀疑欺诈”状态。
* **MDVA-31224** (*(对于Adobe Commerce)>=2.3.3 &lt;2.3.5*) — 提高 `catalog_product_price` 对捆绑产品进行重新索引操作。
* **MDVA-31321** (*(对于Adobe Commerce)>=2.3.2 &lt;2.3.5*) — 修复空白页面（错误），当 *显示全部* 中。 [!DNL Elasticsearch] 返回大量产品id列表。 在此方案中， order by子句将转换为错误的SQL格式。
* **MDVA-30815** (*for Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修复了当您更改搜索结果页面上应显示多少个搜索结果时，Adobe Commerce显示空白页面的问题。 [!DNL Elasticsearch] 现在，当您更改每页查看的搜索结果数时，可以正确显示类别页面的结果。
* **MDVA-30782** (*for Adobe Commerce >=2.3.5 &lt;2.4.2*) — 修复了在不考虑购物车规则的情况下显示动态块的问题。
* **MDVA-31021** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了中存在性能问题的问题 `module-catalog-import-export/Model/Import/Product/Option.php`. 如果中的记录超过约10万条 `catalog_product_option` 表中，包含单个产品的新CSV需要不到10秒才能验证。
* **MDVA-31007** (*(对于Adobe Commerce)>=2.4.0 &lt;2.4.1*) — 修复了自定义地址属性未正确显示在我的帐户区域和后端的订单详细信息页面中的问题。
* **MDVA-29389** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了高级报表中， `analytics_collect_data` cronjob表示： *必须在主机参数内配置端口（如localhost:3306）*.
* **MDVA-31343** (*for Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修复了删除的body类的问题 `page-layout-category-full-width` 计划类别时。
* **MDVA-30945** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了更新购物车时出现错误消息的问题 `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*(对于Adobe Commerce)>=2.3.4 &lt;2.4.0*) — 实施 *最小值应匹配* 功能和部分搜索 [!DNL Elasticsearch] 引擎。 解决了搜索查询中连字符的问题。
* **MDVA-30102** (*(对于Adobe Commerce)>=2.3.2 &lt;=2.4.0*) — 修复了由于布局缓存没有TTL，因此Redis缓存快速增长的问题。
* **MDVA-30599** (*(对于Adobe Commerce)>=2.3.4 &lt;=2.4.0*) — 修复了使用API创建的来宾引号被错误地标记为已登录客户的引号的问题。
* **MDVA-29446** (*(对于Adobe Commerce)>=2.3.3 &lt;=2.4.0*) — 修复了在结帐期间，不适用送货方法的价格显示为零的问题。
* **MDVA-30357** (*(对于Adobe Commerce)>=2.3.2 &lt;=2.4.0*) — 修复了通过cron生成站点地图时创建错误图像URL的问题。
* **MDVA-30565** (*for Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) — 修复了 *没有具有cartid = 0的此类实体* 如果启用了永久性购物车，则店面结账时来宾客户会显示错误。
* **MDVA-29787** (*(对于Adobe Commerce)>=2.3.0 &lt;=2.4.0*) — 修复了相关产品的目标规则在 *是* 条件来定义要显示的产品。
* **MDVA-30977** (*对于Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) — 修复了重新索引后类别中缺少随机产品的问题。
* **MDVA-28202** (*(对于Adobe Commerce)>=2.3.4 &lt;=2.4.2*) — 修复了使用MSI时，分层导航无法正确筛选可配置产品的问题。
* **MDVA-28300** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.6*) — 修复了GQL请求未反映目录价格规则中的价格更改的问题。
* **MDVA-31006** (*(对于Adobe Commerce)>=2.3.2 &lt;=2.4.2*) — 修复了在使用 [!DNL Paypal Express] 付款。

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*for Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修复了分层导航的问题，其中 *否* 如果 [!DNL Elasticsearch] 用作搜索引擎。
* **MDVA-28191** (*(对于Adobe Commerce)>=2.3.3 &lt;2.4.2*) — 修复了在通过管理员创建订单期间未加载付款方法的问题。
* **MDVA-29959** (*(对于Adobe Commerce)>=2.3.0 &lt;=2.3.3-p1，带有B2B扩展*) — 修复了管理员用户在 *公司* 不允许删除公司帐户。
* **MDVA-30265** (*(对于Adobe Commerce)>=2.3.3 &lt;2.4.2*) — 修复了发票创建后发运跟踪链接停止工作的问题。
* **MDVA-28409** (*for Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修复了 `sales_clean_quotes` cron作业失败， *内存不足* 数据库中过期引号的数量过大时出错。
* **MDVA-30593** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.4*) — 修复了未清除根据“报价生命周期”设置过期的报价的问题。
* **MDVA-30107** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.6*) — 修复了当使用不同的基本URL进行存储视图时，存储切换器无法按预期工作的问题。
* **MDVA-28763** (*for Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修复了在使用REST API多次更新产品信息后，产品图像重复出现的问题。
* **MDVA-30284** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了目录搜索索引器由于以下原因而失败的问题 *[!DNL Elasticsearch]错误：已超出索引中总字段的限制。*
* **MDVA-29042** (*(对于Adobe Commerce)>=2.3.3 &lt;=2.3.4-p2，带有B2B扩展*) — 修复了目录权限更改为 *允许* 将新产品添加到共享目录后自动执行此操作。
* **MDVA-30428** (*(对于Adobe Commerce)>=2.3.3 &lt;2.4.2*) — 修复了如果将产品分配给自定义库存源，客户无法将产品添加到愿望列表的问题。
* **MDVA-28661** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2，带有B2B扩展*) — 修复了更改公司管理员后，“公司用户”公司帐户区域中引发错误的问题。

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*适用于Adobe Commerce 2.3.1 - 2.3.4-p2*) — 修复了当数据库名称过长时，cron作业失败，从而导致前端未更新类别的问题。
* **MDVA-30106** (*对于Adobe Commerce ^2.3.0*) — 修复了在结账付款期间未加载的问题 *无法读取值为null的属性“length”* JS控制台中出错。
* **MDVA-28656** (*for Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) — 修复了在下订单时不需要付款信息（例如，折扣为100%）并且为订单创建了发票时，订单状态将更改为 *已关闭* 而不是“完成”。
* **MDVA-30209** (*适用于Adobe Commerce 2.3.0 - 2.3.3-p1*) — 修复了客户组在客户更新其帐户信息时被更改为默认值的问题。
* **MDVA-30123** (*for Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了属性选项标签未针对GraphQL查询正确转换的问题。
* **MDVA-29996** (*(对于Adobe Commerce)>=2.3.3 &lt;2.4.2*) — 修复了启用类别权限后，类别页面未被全页缓存缓存的问题。
* **MDVA-30164** (*for Adobe Commerce >=2.3.1 &lt;2.4.2*) — 修复了存在自定义客户属性时无法从“客户”网格导出客户记录的问题。
* **MDVA-30444** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.1*) — 修复了使用GraphQL下达的订单未发送确认电子邮件的问题。
* **MDVA-30490** (*适用于Adobe Commerce 2.3.4 - 2.3.5-p2*) — 修复了当其中一个产品的简短描述为空时，产品比较会引发500错误页面的问题。
* **MDVA-30232** (*(对于Adobe Commerce)>=2.3.1 &lt;2.4.1*) — 修复了原始订单包含礼品卡时无法重新排序的问题。
* **MDVA-29965** (*(对于Adobe Commerce)>=2.3.3 &lt;2.4.0*) — 修复了客户将产品添加到购物车时出现“表单密钥无效”错误的问题。
* **MDVA-30008** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.2*) — 修复了B2B问题，该问题导致无法通过管理员API为位于公共目录中的产品下订单。
* **MDVA-22469** (*用于Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) — 修复了升级到Adobe Commerce 2.3.3后，页面生成器在“管理员”面板中无法工作，且某些JS和CSS文件未加载的问题。
* **MC-35984** (*(对于Adobe Commerce)>=2.4.0 &lt;2.4.1*) — 修复了在为退货授权(RMA)创建送货标签后，商家无法与退货页面上的任何页面元素进行交互的问题。

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*适用于Adobe Commerce 2.3.0 - 2.3.4*) — 修复了 [!DNL PayPal Payflow Pro] 支付方法和Cookie `SameSite=Lax` 默认情况下，在Chrome 80浏览器和API响应重定向到客户登录页面中。
* **MDVA-26694** (*(对于Adobe Commerce)>=2.3.0 &lt;2.3.6 || 2.4.0*) — 修复了产品和目录缓存每天过期（尽管计划的过期时间不同）的问题。
* **MDVA-27825** (*(对于Adobe Commerce)>=2.3.0 &lt;2.4.1*) — 修复了由于内存泄漏导致导出大量数据失败的问题。
* **MDVA-29085** (*对于Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) — 修复了B2B问题：如果某个公司是由API创建的，则不会发送任何必需的新公司电子邮件。
* **MDVA-29344** (*对于Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) — 修复了将文本从标题元素复制到文本元素后，页面生成器卡住的问题。
* **MDVA-29835** (*适用于Adobe Commerce >2.3.1 &lt;2.4.2*) — 修复了礼品卡订单包含两个代码而非一个代码的问题。
* **MDVA-30052** (*(对于Adobe Commerce)>=2.3.2-p2 &lt;2.3.5*) — 修复了私有内容（本地存储）填充不正确导致性能问题的问题。
* **MDVA-30131** (*for Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修复了分层导航的问题，其中 *否* 如果 [!DNL Elasticsearch] 用作搜索引擎。
* **MDVA-35514** (*(对于Adobe Commerce)>=2.4.0 &lt;2.4.1*) — 修复了在“创建包”模式窗口中创建送货标签并将已订购的产品添加到包时出现的问题。
