---
title: 发行说明
description: 了解Adobe Commerce可用的修补程序以及它们解决的问题。
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: 26bde6684b3f38ed16ede6ec9c63cc90fa849fd9
workflow-type: tm+mt
source-wordcount: '19990'
ht-degree: 0%

---

# 发行说明

此 [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) 提供由Adobe和Magento Open Source团体开发的各个修补程序。 它允许您应用、还原和查看有关已安装Adobe Commerce或Magento Open Source版本可用的所有单个修补程序的一般信息。 无论谁开发了修补程序，您都可以将修补程序应用到Adobe Commerce和Magento Open Source项目。 例如，您可以将社区开发的修补程序应用于Adobe Commerce项目。

>[!INFO]
>
>请参阅 [应用修补程序](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) 以获取有关将修补程序应用于Adobe Commerce或Magento Open Source项目的说明。 请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 查看已发布修补程序的完整列表。

>[!INFO]
>
>有关信息 [!DNL quality patches] 由社区创建以进行Magento Open Source，请参见 [发行说明](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了在库存数量更改时，即使产品仍有库存，类别页面缓存也会失效的问题。
* **ACSD-54656** (适用于Adobe Commerce >=2.4.5 &lt;2.4.6) — 修复了在签出期间不可见Recaptcha失败，从而阻止下达订单的问题。
* **ACSD-55100** (对于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了GraphQL在搜索结果中返回的产品不超过10,000的问题。
* **ACSD-56621** (对于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了更新的名字和姓氏未反映在公司管理员用户的问候语标头部分的问题。
* **ACSD-56842** (对于Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修复了运行后缺少延迟代理和延迟代理工厂的问题 `setup:di:compile`.
* **ACSD-57003** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了订单状态更改为的问题 *[!UICONTROL Complete]* 而不是更改为 *[!UICONTROL Processing]* 订单部分退款和部分发运时。
* 更新的修补程序：ACSD-50260-v2、ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了计划更新禁用了两个子产品中的其中一个子产品时，可配置产品缺货的问题。
* **ACSD-56616** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了捆绑产品在其简单产品缺货时在店面显示为现货的问题。
* **ACSD-56515** (对于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了具有网站级别权限的管理员无法添加或编辑动态块的问题。
* **ACSD-56447** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了通过并行REST Web API请求将同一产品添加到购物车会在购物车中导致两个单独项目的问题。
* **ACSD-56415** (对于Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修复了由于 `DELETE` 查询时数据库中有大量的要索引的部分价格数据。
* **ACSD-54965** (对于Adobe Commerce >=2.4.5 &lt;2.4.6) — 修复了将产品仅分配给自定义库存时，可视化促销网格不显示正确库存的问题。
* **ACSD-52824** (对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了在公司设置中禁用此类付款方法时，为公司客户显示PayPal Express、Google Pay和Apple Pay按钮的问题。
* 更新的修补程序： ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了在使用对类别产品进行分类时，用户会被重定向到管理员功能板的问题。 **从缺货到缺货** 选项及 `Invalid security or form key. Please refresh the page` 错误显示在屏幕顶部。
* **ACSD-56280** (对于Adobe Commerce >=2.4.4 &lt;2.4.7) — 修复了从礼品注册处订购商品会导致异常的问题。
* **ACSD-56246** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了在产品的计划更新生效时，从自定义多选属性中删除数据的问题。
* **ACSD-56193** (对于Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.4) — 修复了在使用页面生成器的类别描述中使用计划块时，Varnish/Fastly缓存未更新的问题。
* **ACSD-56158** (对于Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修复了“购物车”查询返回每个税则的总税值的问题。
* **ACSD-56023** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了在启用缓存后，CMS页面上的小组件内容未更新的问题。
* **ACSD-55427** (对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了管理员用户无法从管理员的产品页面中取消分配共享目录中的产品的问题。
* **ACSD-55352** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了在使用客户奖励积分创建部分贷项通知单之后，订单状态更改为“已关闭”并且贷项通知单选项从“管理员订单”页中消失的问题。
* **ACSD-55231** (适用于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了无法使用快速订购功能将产品添加到购物车的问题。
* **ACSD-54283** (对于Adobe Commerce >=2.4.3 &lt;2.4.4) — 修复了以下问题：未分配给共享目录(默认目录（常规组）)的产品/类别仍包含在XML Sitemap中。
* 更新的修补程序：ACSD-52041、ACSD-54040、ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了在更改类别URL后，规范类别URL未更新的问题。
* **ACSD-53636** (对于Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.5) — 修复了具有具有特价子产品的可配置产品的产品列表页面上未显示常规价格的问题。
* **ACSD-54885** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了当管理员用户使用 *客户登录* 功能。
* **ACSD-55610** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修复了部分取消的订单的折扣额不正确的问题。
* **ACSD-55334** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 在GraphQL响应中通过翻译词典修复标签的翻译。
* **ACSD-54739** (适用于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了产品库存状态条件未应用于相关产品规则的问题。
* **ACSD-53925** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了以下问题：当遇到产品轮播时，管理员无法保存CMS块 `catalog_product_price` dimensions-mode设置为 *网站*.
* **ACSD-52714** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了将日期格式设置为时，日期过滤器在管理网格中不起作用的问题 *Y-m-d*.
* **ACSD-55055** (对于Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 提高了在购物车的购物车价格规则中加载产品属性的性能。
* **ACSD-53790** (对于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了通过REST API为单个产品创建多个RMA的问题。
* **ACSD-56090** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5) — 修复了GraphQL请求响应所有存储区数据而非专门请求的存储区数据的问题。
* **ACSD-54983** (对于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了当用户状态设置为时，无法通过GraphQL请求获取公司用户UID的问题 *[!UICONTROL Inactive]*.
* **ACSD-53309** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了以下问题中尚未完全纳税： *[!UICONTROL Regular Price]* 标记在选择了可自定义选项时。
* **ACSD-55305** (对于Adobe Commerce >=2.4.4 &lt;2.4.7) — 修复了以下问题 *[!UICONTROL Edit Company User]* 上的弹出窗口 **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** 屏幕上有加载器时会冻结页面。
* 更新的修补程序： ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了以下问题： *[!UICONTROL Recently Viewed]* 产品数据未在商店视图中正确更新。
* **ACSD-54626** (对于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了无法创建新采购订单规则的问题(`createPurchaseOrderApprovalRule`) `NUMBER_OF_SKUS` 属性通过 [!DNL GraphQL].
* **ACSD-53845** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复 [!DNL MySQL] 连接超时问题出现于 `consumer max_messages` = 0。
* **ACSD-54890** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了以下问题： `aggregate_sales_report_bestsellers_data` 原因 [!DNL MySQL] 错误源于 `/tmp` 磁盘空间不足。
* **ACSD-55112** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了以下问题： *[!UICONTROL Submit review]* 多次单击按钮，不需要 [!DNL Google reCAPTCHA v3] 验证。
* **ACSD-54264** (对于Adobe Commerce >=2.4.4-p5 &lt;2.4.5) || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) — 修复了错误消息的问题 *“您无法更新请求的属性。 行ID： store_id&quot;* 当客户尝试使用另一商店视图中的可转让报价结帐时显示。
* **ACSD-54418** (对于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修复了将固定数量的折扣错误地应用于动态定价捆绑包的每个子产品的问题。
* **ACSD-55238** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了保存空产品的问题 *[!UICONTROL Meta Description]*.
* **ACSD-54966** (对于Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修复了在上一个订单失败时，无法重用每个客户限量使用的优惠券代码的问题。
* **ACSD-54060** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了受限制管理员无法保存产品（如果它是分配给其他范围的另一个产品的子产品）的问题。
* **ACSD-48910** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了在为订单开票和发运订单后，即使订单仍然具有非零数量，分配给多个来源的捆绑产品也会缺货的问题。
* **ACSD-55381** (对于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了查询时的内部服务器错误 `configurable_product_option_uid` 和 `configurable_product_option_value_uid` 字段来自 [!DNL B2B] *[!UICONTROL Requisition list]* via [!DNL GraphQL].
* **ACSD-55628** (对于Adobe Commerce >=2.4.4-p2 &lt; 2.4.5) || >=2.4.5-p1 &lt; 2.4.6) — 修复了在公司注册表中上传文件的操作，以及替换店面中客户属性的文件的操作。
* 更新的修补程序：ACSD-51240、ACSD-51890、ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (适用于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了在将产品添加到购物车后，当产品从共享目录中删除时购物车中发生的问题。
* **ACSD-53722** (对于Adobe Commerce >=2.4.4 &lt;2.4.7) — 修复了以下问题：当其他范围的计划更新生效时，捆绑产品选项价格更改为$0。
* **ACSD-53643** (对于Adobe Commerce >=2.4.3 &lt;2.4.7) — 修复了在订购禁用或缺货的产品时，订单总额不正确的问题。 通过隐藏 *[!UICONTROL Place Order]* 此类采购订单的按钮。
* **ACSD-54067** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了产品视频无法在移动设备上播放的问题。
* **ACSD-55414** (对于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 在MariaDB尝试将EAV entity_id从字符串转换为整数时，提高性能。
* **ACSD-51819** (对于Adobe Commerce >=2.4.4 &lt;2.4.4-p4) — 修复了可使用同一报价ID下达多个订单的问题。
* **ACSD-53118** (对于Adobe Commerce >=2.4.0 &lt;2.4.7) — 修复了以下问题 *[!UICONTROL Cart Price Rule]* 当产品具有空属性时，使用优惠券代码应用。
* **ACSD-54324** (对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了GraphQL requisition_lists请求不考虑分页设置并返回所有结果的问题。
* 更新的修补程序： MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** (对于Adobe Commerce >=2.4.0 &lt;2.4.6) — 修复了无法处理为具有多分配来源的产品提交的B2B报价的问题。
* **ACSD-54040** (对于Adobe Commerce >=2.4.4-p5 &lt;2.4.5) || >=2.4.5-p4 &lt;2.4.6) — 修复了 *[!UICONTROL Created]* 启用B2B模块后，字段的订单详细信息为空。
* **ACSD-54319** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了以下产品价格为零的问题： *[!UICONTROL Product in Cart]* 报告。
* **ACSD-53378** (对于Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 为拥有大地址簿的客户缩短结帐页面加载时间。
* **ACSD-52657** (对于Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修复了在使用子域的二级存储库中未更新minicart的问题。
* **ACSD-53414** (对于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了受限制的管理员用户在其权限范围之外查看CMS页面的问题。
* **ACSD-54472** (对于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了以下问题：被拒绝公司的客户仍然可以执行身份验证，被阻止和被拒绝公司的客户仍然可以下订单。 该修补程序添加了对GraphQL端点的其他验证。
* **ACSD-52801** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 添加了在GraphQL中搜索产品时进行部分匹配的选项。
* **ACSD-55004** (对于Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修复了在上传大于中配置的值的导入文件时，验证器崩溃的问题 `php.ini`.
* **ACSD-54989** (对于Adobe Commerce >=2.4.4-p5 &lt;2.4.5) || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) — 修复了以下情况下公司管理员无法下订单的问题 *[!UICONTROL Enable Purchase Orders]* 设置为 *[!UICONTROL Yes]* 和 *[!UICONTROL Purchase Order]* 设置为 *[!UICONTROL No]*.
* **ACSD-54007** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复错误 *未定义数组键“_scope”* 导入客户数据时。
* **ACSD-55031** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复 *“混合”类型不能为空* 编译期间出错。
* **ACSD-54961** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了受限管理员用户无法批量更新的问题 *产品审查* 状态。
* **ACSD-55256** (对于Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修复了图像滑块中仅成功显示第一个图像的问题。
* 更新的修补程序：ACSD-52041、ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (对于Adobe Commerce >=2.4.0 &lt;2.4.7) — 修复了在奖励点过期后错误地计算奖励点余额历史记录的问题。
* **ACSD-53583** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 改进的部分重新索引性能， *类别产品* 和 *产品类别* 索引器。
* **ACSD-54026** (对于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了的错误消息。 `updateCompanyRole` 非授权用户的GraphQL请求。
* **ACSD-54106** (对于Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5) — 修复了按名称对土耳其语重音字符进行类别产品排序不正确的问题。
* **ACSD-52219** (对于Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修复了在书签视图之间频繁切换时，管理员网格保存的过滤器无法按预期工作的问题。
* **ACSD-54342** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复不正确的错误消息 *数据结构错误：值混合* 导入没有有效数据的CSV文件时。
* **ACSD-54660** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 添加了新输入属性 *sort* 在GraphQL中排序客户订单的依据 `sort_field` 和 `sort_direction`.
* **ACSD-54776** (对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了未选中此项的问题 *[!UICONTROL Use Default Value]* 对于第二个网站、商店和商店视图，和非默认产品字段值不会保存。
* **ACSD-53998** (对于Adobe Commerce和Magento Open Source >=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7) — 修复了 **[!UICONTROL Dynamic Block]** 基于 **[!UICONTROL Customer Segment]** 从客户帐户注销后无法正常工作。
* **ACSD-53204** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复 *无法保存产品。* 并发请求使用向产品库添加图像时出错 `rest/V1/products/<sku>/media` 端点。
* **ACSD-47657** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 为AWS凭据添加了缓存机制。 凭据提供程序现在使用Magento缓存来缓存从AWS检索到的凭据以进行EC2配置。
* 更新了修补程序：ACSD-51984、ACSD-51574。

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4) — 修复了在执行部分索引时，分配给共享目录的产品未显示在店面中的问题。
* **ACSD-54018** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复的性能问题 [!UICONTROL Product List] 在构件条件中使用非全局属性的构件。
* **ACSD-54111** (对于Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修复了以下问题：当水印图像的宽高比与产品图像不匹配时，产品缩略图图像不会显示在店面上。
* **ACSD-47669** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复 *完整性约束违规： 1452无法添加或更新子行：外键约束失败* 导入产品CSV时出错。
* **ACSD-53347** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修复了价格索引器执行时间过长的问题。
* **ACSD-52287** (适用于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了在启用异步网格索引时，归档订单网格中的订单状态不正确的问题。
* **ACSD-52929** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修复了在异步模式下配置库存索引器时冗余请求对默认源项目重新索引的问题。
* **ACSD-53824** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了以下问题： `UpdateMultiselectAttributesBackendTypes` 迁移数据修补程序超过数据库事务大小限制 `setup:upgrade`.

## v1.1.37 {#v1-1-37}

* **ACSD-52613** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了即使没有对进行更新，缓存和索引也会刷新的问题。 `Inventory_source` REST API列出的项目。
* **ACSD-51884** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了在运行resize命令后，产品图像缓存路径不正确的问题。
* **ACSD-53628** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修复了CSV销售订单报表显示错误的特殊字符的问题。
* **ACSD-53148** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了以下问题：在GraphQL中，将同一可配置产品添加到购物车的两个并行请求在购物车上产生了具有相同产品SKU的两个单独项目。
* **ACSD-52606** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了错误消息的问题 *您的订单未准备好取货* 在用户单击时显示 **[!UICONTROL Notify Order is Ready for Pickup]**.
* **ACSD-51574** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了将图像替换为具有相同名称的其他图像后，图像未在前端更新的问题。
* **ACSD-53728** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了产品EAV索引器需要更长时间才能完成的问题。
* **ACSD-53979** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了在欢迎消息包含单引号时主页出现的JS问题。
* **ACSD-52085** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了具有特殊价格的可配置产品在产品轮播中不可见的问题。
* **ACSD-53795** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了中无效数据类型的问题 `indexer_update_all_views` cron作业。
* **ACSD-52143** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了产品导入后删除自定义选项的问题。
* **ACSD-53750** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复 *管道断开或连接关闭* 多线程运行期间出错 `catalog_product_price` 重新索引。
* **ACSD-49843** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.0) || >=2.4.1 &lt;2.4.7) — 修复了以下问题：使用在线付款方法对订购的项目自动开票后，产品下载链接不可用 **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** 设置已启用。
* **ACSD-47054** (对于Adobe Commerce >=2.4.2 &lt;2.4.6) — 修复了预览重新索引为所有存储区运行重新索引，从而导致速度缓慢的问题。
* 添加了ACSD-46541、ACSD-47079的新版本。
* 已将ACSD-49970-v3替换为ACSD-54095。

## v1.1.36 {#v1-1-36}

* **ACSD-53239** (对于Adobe Commerce和Magento Open Source >=2.4.3 &lt; 2.4.6) — 修复了清单索引器在“按计划更新”模式下清理所有缓存的问题。
* **ACSD-50887** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了产品属性的问题 *[!UICONTROL Use in Search Results Layered Navigation]* 可以设置为 *是* 不使用 *[!UICONTROL Use in search]* 选项设置为 *是*.
* **ACSD-51846** (对于Adobe Commerce和Magento Open Source>=2.4.3-p2 &lt;2.4.6) — 修复 *内部错误* 由于未验证所有级别的REST API有效负载而发生的问题。
* **ACSD-52906** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了为属于同一客户区段的已登录客户错误设置XMagento差异Cookie而导致某些页面缓存不正确的问题。
* **ACSD-52736** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了以下问题： *购物车价格规则* 可配置产品数量的要求无法按预期工作。
* **ACSD-47875** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了以下问题：对于具有库存管理的特定商店视图范围，管理员用户无法从管理员将产品添加到客户购物车。
* **ACSD-53176** (对于Adobe Commerce >=2.3.7 &lt;2.4.5) — 修复了以下问题： *相关产品规则* 替换为 *是其中之一* 条件与产品不匹配。
* **ACSD-51666** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复错误 *会话已过期，请重新登录。* 这种情况会在客户尝试登录后发生。
* 添加了MDVA-39305-v2的新版本。
* 更新了ACSD-19640的要求。

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (对于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修复了以下问题：使用之前选定的店内装货地址自动填充结账配送步骤中的默认配送地址。
* **ACSD-52041** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了错误消息的问题： *[错误] [!DNL Page Builder] 渲染了5秒钟，没有释放锁定。* 保存编辑的内容时在Chrome浏览器中显示 [!DNL Page Builder].
* **ACSD-52095** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了以下问题： `manage_stock` 导出产品后，CSV文件中的值未正确设置为0。
* **ACSD-51358** (对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了以下问题：删除没有结束日期的计划更新会导致删除同一实体的其他计划更新。
* **ACSD-48070** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了编辑计划更新会触发异常的问题。
* **ACSD-51890** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了以下问题： [!UICONTROL Submit review] 多次单击按钮，不需要 [!DNL Google reCAPTCHA] v3验证。
* **ACSD-51984** (对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了未选中此项的问题 *[!UICONTROL Use Default Value]* 和 *[!UICONTROL non-default product field]* 不会保存第二个网站、商店和商店视图的值。
* **ACSD-52398** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复错误 *请求的数量不可用* 在尝试更新店面购物车中捆绑产品的数量时会发生这种情况。
* **ACSD-52786** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了目录规则条件的问题 *SKU是* 适用于从给定SKU开始的所有产品。
* **ACSD-52921** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了在购物车中有缺货的可配置产品时从GraphQL请求购物车详细信息时发生内部错误的问题。
* **ACSD-51683** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了使用GraphQL时无法将可自定义选项添加到购物车的问题。
* **ACSD-52133** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了在升级后无法保存客户帐户的问题。
* **ACSD-52202** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在订单履行中，非默认库存更改为0数量时，默认库存的可销售数量错误地更改为0的问题。
* **ACSD-51265** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复的问题 `catalog_product_price` 当系统中捆绑的产品过多时，重新索引性能。
* **ACSD-52831** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了以下情况下客户无法下达可转让报价单的问题 [!DNL Google reCAPTCHA v3 Invisible] 已启用。
* **ACSD-51845** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修复了无法通过异步批量REST API更新具有层价格和其他属性集的后续产品的问题。
* **ACSD-52815** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修复了非默认来源的quantity字段输入最多支持6位数的问题，默认库存不支持8位。
* **ACSD-51149** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了启用了目录权限的计划导入导出使索引器失效，然后通过cron缓存刷新的问题。
* **ACSD-50815** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了简单产品的小数数量不能用于新的捆绑产品选项的问题。
* ACSD-47803的更新版本。
* 更新了ACSD-51892的标题。
* 更新了ACSD-51379。
* 更新了ACSD-49970-v2。

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了在Admin中创建新订单时，管理员用户在选择商店视图后未正确重定向的问题。
* **ACSD-50813** (对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了以下问题：管理员无法在SKU中添加包含斜杠的捆绑产品 [!UICONTROL Add Products by SKU] 管理订单的功能。
* **ACSD-51630** (对于Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修复了大量系统消息减慢管理员页面下载速度的问题。
* **ACSD-51853** (对于Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.7) — 修复了在使用 [!UICONTROL Page Builder].
* **ACSD-52160** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了以下问题：根据购物车价格规则的产品验证结果未根据规则条件“如果在购物车中找到/未找到项目，且所有/任何这些条件均为true”正确评估问题。
* **ACSD-51636** (对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了以下问题：公司管理员尽管拥有所有必要的角色和权限，但无法从客户帐户部分添加新用户。
* **ACSD-51739** (对于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了以下情况下返回错误的问题： `structure_id` 是在CompanyTeam GraphQL请求中提出的。
* **ACSD-51857** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了性能缓慢的问题。 `aggregate_sales_report_bestsellers_data` 大型sales_order和cron报告 `sales_order_item` 数据库表是由于主数据查询的写入方式造成的。
* **ACSD-48448** (对于Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修复了在订单取消期间发生竞争条件问题，从而导致 `inventory_reservation` 表格。
* **ACSD-52689** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.6) — 修复了使用REST API无法将图像上传到Amazon S3存储的问题。
* **B2B-2674** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 将缓存功能添加到1customAttributeMetadata1 GraphQL查询。
* 添加了新版本的ACSD-44938。
* 添加了ACSD-46988的要求。

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (对于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.5) — 修复了数据库回滚命令适用于数据库转储包含触发器和一个 *分隔符* sql命令。
* **ACSD-50512** (对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复 *错误：可下载的链接与产品无关。 请验证链接并重试。* 更新可下载产品暂存更新的开始日期时出错。
* **ACSD-50949** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了以下问题：在与SKU过滤器一起使用时，高级搜索中的价格过滤器无法返回正确结果。
* **ACSD-51645** (对于Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修复了保存新的购物车价格规则时引发的错误（如果扩展） `Magento_OfflineShipping` 已禁用。
* **ACSD-50895** (对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了以下问题： [!DNL Google Analytics] 3 GTM标记未触发，如果 [!DNL Google Analytics] 4 GTM未配置。
* **ACSD-51102** (对于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了以下问题：当计划更新启用了适用于大量产品的目录规则时，该规则无法正确编制索引。
* **ACSD-50368** (对于Adobe Commerce和Magento Open Source>= 2.4.3 &lt;2.4.5) — 修复了以下问题： `group_id` 通过异步REST API或异步批量REST API创建客户时，忽略该参数。
* **ACSD-51497** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.0) || >= 2.4.1 &lt;2.4.7) — 修复了客户无法按下拉列表类型的自定义属性对目录页面进行排序的问题。
* **ACSD-51408** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt; 2.4.7) — 修复了订单项目状态错误设置为的问题 *[!UICONTROL Backordered]*.
* **ACSD-51735** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5) — 修复了订单项目状态错误设置为的问题 *[!UICONTROL Ordered]* 当产品库存为 *0*.
* **ACSD-51792** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了以下情况下页面没有展示事件的问题： [!DNL Google Tag Manager] 4已启用。
* **ACSD-51471** (对于Adobe Commerce >=2.4.3 &lt;2.4.7) — 修复了以下问题：对于使用简单产品的捆绑产品，管理员用户无法为其保存计划更新，而该产品本身具有计划更新。
* **ACSD-51700** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在管理员的可下载产品编辑页面上切换商店视图时发生的错误。
* **ACSD-51120** (适用于Adobe Commerce >=2.3.7 &lt;2.4.3) — 修复了包含通过暂存更新更新更新的CMS块的GraphQLGET请求缓存未获得清除的问题。
* **ACSD-51240** (对于Adobe Commerce >=2.4.4 &lt;2.4.6) — 修复了通过公司注册表进行注册时上传文件缺失的问题。
* **ACSD-51907** (对于Adobe Commerce >=2.4.2 &lt;2.4.3) — 修复了受限管理员用户无法创建具有离线退款的贷项通知单的问题。
* **ACSD-52148** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 修复了以下问题： [!DNL Google V3 reCAPTCHA] 管理员登录偶尔会失败。
* **ACSD-51431** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修复了索引器状态为的问题 *工作* 即使更改日志中没有新条目。
* **ACSD-51892** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了配置文件加载多次的性能问题。
* 已弃用ACSD-51114。

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了以下问题： [!UICONTROL Page Builder's] 多个错误会导致管理员无法保存没有内容权限的产品。
* **ACSD-51305** (对于Adobe Commerce和Magento Open Source >=2.4.6 &lt;2.4.7) — 修复了GraphQL响应中不可用可配置缺货子产品的问题。
* **ACSD-50621** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了以下问题： [!UICONTROL Tier Prices] 对于共享目录中的不同网站，尝试在多网站环境中编辑它们时不可见。
* **ACSD-51041** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.0) || >=2.4.1 &lt;2.4.6) — 提高价格索引器的性能。
* **ACSD-51379** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修复了以下方式更改页面文本内容的问题： [!UICONTROL Page Builder] 未保存。
* **ACSD-49480** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修复了仅将一个购物车价格规则应用于购物车的问题。
* **ACSD-51230** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了在订单中处理简单产品的部分退款时删除礼品卡帐户的问题。
* **ACSD-51238** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 修复了在更新可配置产品和编辑价格时删除库存来源的问题。
* **ACSD-50794** (适用于Adobe Commerce >=2.4.1 &lt;2.4.7) — 修复了通过GraphQL删除礼品消息或礼品包装时，数据库中未更新礼品消息或礼品包装详细信息的问题。
* **ACSD-51528** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了以下问题： *x_forwarded_for* 列在 *sales_order* 表格。
* **ACSD-50849** (对于Adobe Commerce >=2.4.4 &lt;2.4.6) — 修复了在清除缓存后向类别添加新产品导致现有产品的位置和选择不匹配的问题。
* **ACSD-51294** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了GTM/GA价格、数量、税、运费和收入作为字符串发送到的问题。 [!DNL Google Analytics] 和GTM。
* **ACSD-51204** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在创建贷项通知单后，完全销售的产品未返回库存的问题。
* **ACSD-51291** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3) — 修复了以下问题：如果管理员限制只能访问一个网站，则可以将图像/视频添加到已分配给多个网站的产品。
* 添加了新版本的ACSD-50336。
* 已更换ACSD-49970修补程序。

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (对于Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) — 修复了Recaptcha v2在提交失败的付款后未重新加载的问题。
* **ACSD-50817** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 优化Cron作业 `sales_clean_quotes` 跑得更快。
* **ACSD-49392** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.0) || >= 2.4.1 &lt;2.4.7) — 修复了在对捆绑产品进行部分退款后，订单状态更改为已关闭的问题。
* **ACSD-51036** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5) — 修复了以下问题：在并发REST API调用期间，出现的争用情况会导致 [!UICONTROL Items Ordered] 表格。
* **ACSD-50858** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 提高加载横幅内容的性能。
* 添加了新版本的MDVA-39305-v2、ACSD-45169。
* 更新了ACSD-50260-v2修补程序。

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (对于Adobe Commerce和Magento Open Source>=2.4.4-p1 &lt;2.4.4-p3) — 修复了在产品重新上架或价格更改时，不会发送产品警报电子邮件的问题。
* **ACSD-50367** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修复了在创建没有值的多选客户地址属性时，客户地址导出无法正常工作的问题。
* **ACSD-49877** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修复了视频自动播放在移动设备中不起作用的问题 [!DNL Safari] 当视频直接链接到远程视频文件而不是流服务时。
* **ACSD-50165** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复错误 *无法删除该文件。 警告！unlink：没有这样的文件或目录* 从管理员刷新JS/CSS缓存时。
* **ACSD-49737** (对于Adobe Commerce和Magento Open Source>=2.4.1-p1 &lt;2.4.7) — 修复了在卡付款失败后将优惠券错误地标记为使用的问题。
* **ACSD-50814** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了管理员用户无法创建贷项通知单的问题。
* **ACSD-50116** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了管理员用户无法为子类别级别3或更低级别创建URL重写的问题。
* **ACSD-49513** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5) — 修复了由于0字节文件而导致远程存储同步失败的问题。
* **ACSD-46683** (对于Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修复了运输价格显示的问题 *尚未计算*.
* **ACSD-49129** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了以下问题： *[!UICONTROL content]* 属性（base64图像代码）未返回到 `rest/V1/products/sku/media` 产品媒体API响应。
* **ACSD-50276** (对于Adobe Commerce >=2.4.0 &lt;2.4.7) — 修复了在创建多选客户属性后，客户注册表单在店面中无法正常工作的问题。
* **ACSD-50527** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了在保存具有空动态块的页面时发生的错误。
* **ACSD-49973** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5) — 改进了通过GraphQL获取捆绑产品的性能。
* **ACSD-51114** (对于Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修复了在启用异步索引时，随机产品从大型目录中消失的问题。 改进大型目录的异步重新索引性能。
* **B2B-2598** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 将缓存功能添加到 [!UICONTROL availableStores]， [!UICONTROL countries]， [!UICONTROL country]， [!UICONTROL currency]、和 [!UICONTROL storeConfig] GraphQL查询。
* 为MDVA-42806、ACSD-48627、ACSD-46815添加了新版本。
* 更新了ACSD-49773、ACSD-47179、ACSD-48300的修补程序元数据。

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了在订单无法接收时通过API发送接收就绪电子邮件的问题。
* **ACSD-49822** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了中的更新问题 [!UICONTROL Requisition List] 页面未反映在 [!UICONTROL Print Requisition List].
* **ACSD-48771** (对于Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修复了从更早版本升级列块内容类型时出现的问题 [!DNL Page Builder] 版本。
* **ACSD-49464** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了当orderId不同时，发票、装运和贷项通知单不会从存档移回的问题。
* **ACSD-49773** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了使用AWS S3作为远程存储时产品导出失败的问题。
* **ACSD-49748** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了无法发送邀请的问题。
* **ACSD-49502** (对于Adobe Commerce >=2.4.3 &lt;2.4.7) — 修复了在将暂存更新应用于可下载产品后，可下载链接未正确更新的问题。
* **ACSD-49527** (对于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了GraphQL公司角色无法正确显示分页的问题。
* **ACSD-49706** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了在未选择任何值时为可视样本属性保存默认值的问题。
* **ACSD-49835** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了多选属性的存储级别上未正确保存使用默认复选框值的问题。
* **ACSD-49898** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修复了捆绑产品的特殊价格超过1000时，产品网格会引发异常的问题。
* **ACSD-50234** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.5) — 修复了以下情况下确认电子邮件中客户名称有误的问题： [!DNL PayPal].
* **ACSD-49960** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了按日期过滤不适用于客户订单网格的问题。
* **ACSD-49849** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了将客户电子邮件替换为 [!DNL PayPal] 在下订单时发送电子邮件 [!DNL PayPal Express] 通过GraphQL。
* **ACSD-49839** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了以下问题：当产品在SKU中带有单引号或双引号时，共享目录定价和结构会在“管理员”中引发错误。
* **ACSD-49970** (对于Adobe Commerce和Magento Open Source >=2.4.5 &lt;2.4.7) — 修复了以下情况下对GraphQL错误的不正确处理： [!DNL New Relic] 报表处于打开状态。
* **ACSD-50260** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了GraphQL产品搜索结果限制为仅包含10,000个结果的问题。
* **ACSD-48813** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了搜索未根据属性的搜索权重显示相关结果的问题。

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.3) — 修复了基于“是/否”属性创建的目录价格规则不考虑所选范围的问题。
* **ACSD-47704** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修复了捆绑产品仅显示库存产品价格的问题。
* **ACSD-49370** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了以下问题： *日期时间* 产品属性具有 *FilterMatchTypeInput* 键入GraphQL架构。
* **ACSD-48807** (对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.7) — 修复了通过GraphQL存储审阅未过滤客户产品审阅的问题。
* **ACSD-49433** (对于Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.7) — 修复了在具有未结金额的礼品卡的购物车中，将默认金额显示为小计的问题。
* **ACSD-48866** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修复了在请求类别的RSS馈送时出现错误的问题。
* **ACSD-48784** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修复了在客户组之间错误地缓存客户区段价格的问题。
* **ACSD-48857** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了用户在使用页面生成器编辑后无法保存更改的问题。
* **ACSD-49065** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了报价单项目仅分配给自定义库存时在Admin中不可见的问题。
* **ACSD-49179** (对于Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修复了以下问题：如果不同商店使用不同的货币，订单报表会显示不正确的金额。
* **ACSD-49286** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了当页面上存在多个产品小组件时，将产品两次添加到购物车的问题。
* **ACSD-49574** (对于Adobe Commerce >=2.4.4 &lt;2.4.7) — 添加了通过GraphQL支持购物车中礼品卡产品更新的功能。
* 更新了修补程序：ACSD-48694。

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (对于Adobe Commerce >=2.4.1 &lt;2.4.7) — 修复了在使用可转让报价下订单时使用默认送货地址而不是新送货地址的问题。
* **ACSD-48059** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了商家无法保存&#39;&#39;的问题[!UICONTROL Match product by rule]”类别中的。
* **ACSD-48216** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) — 修复了以下问题： [!UICONTROL AUTO_INCREMENT] 的 [!UICONTROL inventory_source_item] 表在 [!UICONTROL UPDATE] 操作。
* **ACSD-47908** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) — 修复了在结帐期间选择运输步骤中的源和数量时出现的错误“值应小于或等于0”。
* **ACSD-49497** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.6) — 修复了以下问题：订单在发运后仍处于处理状态，并且应用了部分退款。
* **ACSD-48694** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.1 &lt;2.4.7) — 修复了错误“请求的状态更改无效”导致客户无法下订单的问题。
* **ACSD-49013** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在使用批量API创建客户时，电子邮件确认无法转换为网站区域设置的问题。
* **ACSD-48164** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了受限管理员无法保存网站级别值的问题。
* **ACSD-48404** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 修复了按下浏览器的“返回”按钮时，“记住类别分页=是”导致错误的问题。
* **ACSD-48634** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修复了当&quot;[!UICONTROL Google Analytics Content Experiments]“”已启用。
* **ACSD-49042** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 修复了无法从店面订购无限延交订单产品的问题。
* 更新了修补程序：ACSD-48366、ACSD-48661。

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (适用于Adobe Commerce和Magento Open Source2.4.4) || >=2.4.5 &lt;2.4.6) — 修复了由于应用程序级别的缓存而并非总是发送价格下降通知的问题。
* **ACSD-48661** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了公司的信用额度大于999的问题，即由于验证错误，使用逗号分隔符无法保存公司。
* **ACSD-48773** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了从错误商店获取奖励点电子邮件模板的问题。
* **ACSD-48587** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了在产品小组件匹配规则中HTML特殊字符导致无法显示匹配产品的问题。
* **ACSD-48212** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了产品导入将产品分配给错误源的问题。
* **ACSD-47988** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了产品导出会裁剪页面生成器产品描述中的HTML标签的问题。
* **ACSD-48366** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了产品图像未显示在补货电子邮件模板上的问题。
* **ACSD-48417** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了在为产品创建计划更改并保存另一个产品后显示SQL错误的问题。

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了将捆绑产品分配给任何网站时，产品价格重新索引无法正常工作的问题。
* **ACSD-48262** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了将“允许每页所有产品”设置设为“是”时，产品在前端不可见的问题。
* **ACSD-48293** (对于Adobe Commerce和Magento Open Source >=2.4.3 &lt;2.4.4) — 修复了以下问题：当售出的子产品返回库存时，复合产品缺货。
* **ACSD-47520** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在创建贷项通知单时客户失去奖励点的问题。
* **ACSD-48044** (对于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.4) — 修复了向包含多批发运的单个订单应用多张礼品卡导致无法下订单的问题。
* **ACSD-48300** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在删除可配置产品时无法创建返回的问题。
* **ACSD-47910** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修复了各个实体网格中缺少订单、发票、装运和贷项通知单的问题。
* **ACSD-47292** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修复了将“显示缺货产品”设置为“是”时，GraphQL响应中无法使用缺货捆绑产品的问题。
* **ACSD-48234** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了启用“显示缺货”选项时，目录搜索结果显示错误的类别项目计数的问题。
* **ACSD-48313** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5) — 修复了当属性值包含逗号时，无法解析“configurable_variations”列的问题。 “additional_attributes”使用相同的解析算法。
* **ACSD-48627** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了在发送GraphQL请求以获取购物车详细信息时，缺货的可配置产品会导致错误的问题。
* 更新了修补程序：MDVA-39384。

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (对于Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修复了以下产品未生成SEO友好URL的问题： *url_key* 在store-view级别覆盖的属性。
* **ACSD-46865** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修复了在启用异步索引时未填充Shipment和Credit Memo网格的问题。
* **ACSD-47004** (对于Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.6) — 修复了在没有VAT ID的帐单地址中不应用VAT的问题。
* **ACSD-47803** (对于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修复了缺货可配置产品样本显示为可用的问题。
* **ACSD-47137** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 当pub/media文件夹非常大时，提高图像库的加载速度。
* **ACSD-46770** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了发送管理员订单电子邮件的问题，即使在 *电子邮件订单确认* 未选中。
* **ACSD-47955** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了GraphQL未正确显示购物车折扣的问题。
* **ACSD-46617** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了以下问题： *继续操作直到进入结账流程* 即使小计大于配置的，按钮也会灰显 *最小订单金额*.
* **ACSD-47079** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 修复了在子产品库存状态通过REST APIPOST/rest/V1/inventory/source-items更改时，复合产品（捆绑、分组和可配置）库存状态未更新的问题。
* **ACSD-47336** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复 *发生错误。* 在商务管理中取消通知时出错。
* **ACSD-47559** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了“预览电子邮件模板”区域不完全可见的问题。
* **ACSD-47920** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了通过Rest API作为来宾用户下达订单的问题，即使在 *允许访客签出* 已关闭。
* 已更换修补程序：MDVA-39305、MDVA-42855。

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了具有特定范围受限访问权限的管理员无法删除产品审阅的问题。
* **ACSD-47107** (对于Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.5) — 修复了目录价格规则折扣应用于自定义产品选项的问题。
* **ACSD-47232** (对于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修复了无法在管理员中应用具有总权重条件的优惠券的问题。
* **ACSD-46519** (对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.6) — 修复了GraphQL categoryList请求为锚记类别返回错误的product_count的问题。
* **ACSD-47027** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了更新缓慢的CompanyRole GraphQL请求。
* **ACSD-47666** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了以下问题：在“管理员”>“系统”>“权限”>“用户角色”>“角色”>“角色用户”网格中，过滤器功能不起作用。
* **ACSD-47497** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在“管理员”下的“配置”中看不到“服务”选项卡的问题。
* 更新了修补程序：ACSD-47743。
* 已更换修补程序：MDVA-42807。

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3) — 修复 _正在尝试访问布尔值类型的数组偏移_ 访问PHP 7.4中已知产品的某些不存在类别路径时出错。
* **ACSD-47332** (对于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修复了cron失败并出现错误的问题，该错误仅在00:00 UTC到00:59 UTC之间运行时报告。
* **ACSD-47280** (对于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修复了在特定范围上禁用共享目录功能无法正常工作的问题。
* **ACSD-47106** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了无法在公司创建页面上的新自定义属性中保存值的问题。
* 更新了修补程序：ACSD-45143。

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了在分配大量产品源时，用户收到错误的问题。
* **ACSD-46856** (对于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 通过系统>配置>导入>高级定价来更新层价格，从而提高性能。
* **ACSD-46541** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 修复了在删除订单项目时，管理员用户无法创建贷项通知单的问题。
* **ACSD-46581** (对于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 修复了在购物车中选择国家/地区后预计税务总额未更新的问题。
* **ACSD-46618** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了产品列表构件为已登录的客户显示不正确的缓存价格的问题。
* **ACSD-46674** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在客户电子邮件中将图像类型的自定义选项显示为HTML的问题。
* **ACSD-46988** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了GraphQL“货币”API请求为自定义货币返回NULL值的问题。
* **ACSD-47076** (对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5) — 修复了Vimeo视频无法在店面播放的问题。
* **ACSD-45071** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4) — 修复了在导入期间将默认源添加到产品的问题。
* **AC-3023** (对于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 将DHL方案更新到最新版本10.0。
* 更新了修补程序：MDVA-42584。
* 已更换修补程序：MDVA-36572、ACSD-45241。

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5*) — 修复了用户在使用商店积分退款时获得错误订单状态的问题。
* **ACSD-46703** (*对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6*) — 修复了在产品编辑页面上无法拖放自定义选项的问题。
* **ACSD-44851** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6*) — 修复了包含子类别的类别无法打开或展开的问题。
* **ACSD-46815** (*对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6*) — 修复了类别树请求限制为20个类别的问题。
* **ACSD-45675** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6*) — 修复了产品导出使用 *默认存储视图* 范围。
* **ACSD-46869** (*对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6*) — 修复了购物车中的可配置产品未通过 *PUTREST API* 请求而不更改产品数量。
* **MDVA-42768-V2** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了可配置产品将正常价格显示为 *0* 时间 *显示缺货* 是 *是*.
* 更新了修补程序：MDVA-44562、ACSD-46213、MDVA-41305、MDVA-38346、MDVA-13203。
* 已弃用的修补程序：MDVA-42768。

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了类别树请求限制为20个类别的问题。
* **ACSD-45781** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.2*) — 修复了移动设备上未显示商店前端搜索字段的问题。
* **ACSD-46192** (*对于Adobe Commerce和Magento Open Source>=2.3.6 &lt;2.4.5*) — 修复了使用时出现的问题 `async/bulk/V1/configurable-products/bySku/options` 端点。
* **ACSD-46404** (*对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5*) — 修复了管理员用户在升级到2.4.4后无法登录的问题。
* 更新了修补程序：MDVA-41305、MDVA-38626、MDVA-38728、MDVA-41061-V4、MDVA-42269、MDVA-39305。

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了以下问题：特定存储的GraphQL产品突变返回所有可配置变体，包括那些未分配给所请求存储的变体。
* **ACSD-46146** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.6*) — 修复了管理员下订单后发送两封订单确认电子邮件的问题。
* **ACSD-45255** (*对于Adobe Commerce >=2.4.3 &lt;2.4.6*) — 修复了受限制管理员用户在低库存报表页面上的异常。
* **ACSD-45488** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6*) — 修复了具有多个来源的可配置产品无法自动返回到In Stock的问题。
* **ACSD-45754** (*对于Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.6*) — 修复了将优惠券应用到购物车后未添加奖励点数的问题。
* **ACSD-45849** (*对于Adobe Commerce >=2.4.3 &lt;2.4.4*) — 修复了应用暂存更新后视频元数据丢失的问题。
* **ACSD-45257** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.4*) — 修复了GraphQL未正确显示购物车折扣的问题。
* **ACSD-44938** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4*) — 修复了以下问题： `VAT_ID` 无法应用于GraphQL访客用户的请求。
* 更新了修补程序：MDVA-43417。

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*对于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.4*) — 修复了在创建贷项通知单后虚拟产品的库存数量计算错误的问题。
* **ACSD-43887** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了在启用公司的采购订单时，在结帐付款页面上显示不正确详细信息的问题。
* **ACSD-45143** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5*) — 修复了 `setShippingAddressesOnCart` 突变不允许将数字区域代码设置为 *区域*.
* **ACSD-44591** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.6*) — 修复了在未进行验证码确认的情况下下达订单时发生的错误。
* **ACSD-45520** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.6*) — 修复了当用户从购物车编辑可配置产品时，未在产品详细信息页面上预先选择样本选项的问题。
* **ACSD-45169** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.6*) — 修复了以下问题： [!DNL Visual Merchandiser] 在应用暂存更新后，不会显示可配置产品的正确库存和价格。
* **ACSD-45424** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.6*) — 修复了在部分退款（贷项通知单）之后创建错误预订补偿的问题。
* **MDVA-42807** (*对于Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.6*) — 修复了自定义货币符号未显示在商店正面的问题。
* 更新的修补程序：MDVA-42689、AC-3022。

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了订单报表中针对受限管理员用户错误计算订单总数的问题。
* **MDVA-44940** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了从管理员保存类别时发生的SQL错误。
* **MDVA-44562** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.2-p2*) — 修复了以下问题：尽管非默认存储视图发起了GraphQL请求，但报价项目的非默认存储ID会由默认存储ID覆盖。
* **MDVA-43167** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了当管理员用户选择所有订单时，管理员订单网格批量操作不适用于多页的问题。
* **MDVA-44044** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.2-p2*) — 修复了将产品分配给新网站后无法在类别页面上显示产品的问题。
* **MDVA-42509** (*对于Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.4*) — 修复了无法快速上传CSV导致出现错误的问题 *无法发送Cookie* 错误。
* 更新的修补程序： MDVA-41061和MDVA-42584。
* 新的前缀 [!DNL Quality Patches Tool] 修补程序将从 *MDVA* 到 *ACSD* 因为内部流程变更。

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了当购物车中已有最小数量商品时，无法将其他商品添加到购物车的问题。
* **MDVA-44887** (*对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5*) — 修复了 *未捕获的SyntaxError：意外的令牌&#39;const&#39;* “管理”面板中的错误。
* **MDVA-43718** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复 *使用者无权访问%resources。* 从自定义集成访问共享目录时出错。
* **MDVA-44660** (*对于Adobe Commerce和Magento Open Source>=2.4.2-p1 &lt;2.4.5*) — 修复了重音符号字符的问题 ``` ` ``` 无法用于客户的名字和姓氏。
* **MDVA-40896** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了 *错误： TypeError：参数3传递给Magento* 异步产品批量API时出错。
* **MDVA-38559** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3*) — 修复了 */V1/customers/search API* 具有多个订阅的客户出错。
* **MDVA-44533** (*对于Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.4*) — 修复了将折扣错误地应用于捆绑子产品的问题。
* 更新的修补程序： MDVA-41061和MDVA-42269。

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了产品的问题 *无法单独显示* 仍显示在目录高级搜索结果中。
* **MDVA-44100** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了将所有FPT分配给购物车中的最后一个产品并重置为其他产品的问题。
* **MDVA-43605** (*对于Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.5*) — 修复了使用Rest API时，订单数据返回行总计负值的问题。
* **MDVA-43102** (*对于Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.5*) — 修复了通过REST API进行退款时，可销售数量未正确更新的问题。
* **MDVA-43178** (*对于Adobe Commerce和Magento Open Source >=2.4.3-p2 &lt;2.4.5*) — 修复了无法在GraphQL中检索自定义存储的客户令牌的问题。
* **MDVA-43859** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修复了错误的问题 *没有具有customerId =的此类实体* 当已删除的客户尝试登录时记录。
* **MDVA-44147** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了GraphQL请求不返回申请列表的问题。
* **MDVA-44505** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.3*) — 修复了GraphQL应用奖励点数未更新总计，以及在下单过程中多次应用商店点数的问题。
* 更新的修补程序：MDVA-29148、MDVA-36464-V5、MDVA-42584、MDVA-39993-V2。

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.3*) — 修复了仅当“客户区段”设置为时，“相关产品规则”才能正常工作的问题 *全部*.
* **MDVA-39605** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.5*) — 修复了Redis缓存TTL（过期日期）具有错误值的问题。
* **MDVA-43862** (*对于Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.5*) — 修复了由于GraphQL而导致客户无法更新购物车项目的问题 *UpdateCartItems突变* 错误。
* **MDVA-43824** (*对于Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) — 修复了取消带有折扣的订单时出现错误的问题。
* **MDVA-43451** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了错误的问题 *未找到所请求的存储。 请验证存储并重试。* 在为特定网站配置共享目录时显示。
* **MDVA-43491** (*对于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.5*) — 修复了在导入多商店网站的产品时，基本图像标签未更新的问题。
* **MDVA-43601** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复完全重新索引后触发器缺失的问题。
* **MDVA-42046** (*对于Adobe Commerce和Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) — 修复了在更新产品时，为带有日期输入字段的产品属性分配了错误值的问题。
* **MDVA-43935** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修复了向上销售产品显示两次的问题。
* **MDVA-44188** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了以下系统颁发的电子邮件存在的问题： `.-` 中的地址不会发送。
* **MDVA-42283** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了法语区域设置的管理订单网格中的日期时间格式无效的问题。
* 更新了修补程序：MDVA-41061-V2、MDVA-36309、MDVA-30862、MDVA-39713。
* 为添加了修补程序元数据 [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.3.6*) — 修复了用户能够编辑活动计划更新的开始时间的问题。
* **MDVA-42410** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了优惠券报表仅显示默认基础货币的问题。
* **MDVA-41136** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了的过期日期的问题 `mage-cache-sessid` 不扩展，从而导致客户数据清理。
* **MDVA-39993** (*对于Adobe Commerce和Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) — 修复了通过API完成的库存更改未在前端产品页面上反映的问题。
* **MDVA-42855** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了签出期间新客户地址未保存到通讯簿中的问题。
* **MDVA-42645** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了在禁用商店信用功能的情况下，管理员无法退还奖励点数的问题。
* **MDVA-43414** (*对于Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) — 修复了在运行 `inventory.reservations.updateSalabilityStatus` 数值SKU上的队列消费者。
* **MDVA-41628** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5*) — 修复了在添加新模块时现有受限管理员用户访问新资源的问题。
* **MDVA-43348** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了礼品卡GraphQL请求在以下情况下显示错误的问题： `gift_card_options` contain *uid*.
* **MDVA-39546** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了在编辑期间，将暂存更新开始日期设置为早于当前日期的问题。
* **MDVA-42950** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了视频无法在产品页面上播放的问题。
* **MDVA-42689** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了Adobe Commerce引发的问题 *完整性约束违规* 在导入过程中更新产品类别时出错。
* **MDVA-41229** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了可配置产品导入后，前端上可用的图像未显示的问题。
* **MDVA-43731** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了以下问题： *搜索同义词* 在中添加值后不再有效 *要匹配的最少搜索词*.
* **MDVA-43232** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.5*) — 修复了中的产品排序问题。 [!DNL Visual Merchandiser] 按“特殊价格至底部/顶部”选项会在保存类别时出错。
* **MDVA-43726** (*对于Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.3*) — 修复了在部分重新索引后无法应用基于存储级别属性匹配的目录价格规则的问题。
* 更新了修补程序：MDVA-36464、MDVA-37478、MDVA-38608。
* 为添加了修补程序元数据 [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了无法通过REST API为特定网站更新产品价格属性的问题。
* **MDVA-41350** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了当具有受限访问权限的管理员用户按SKU顺序添加产品超出其角色范围时，引发异常的问题。
* **MDVA-42269** (*对于Adobe Commerce和Magento Open Source>=2.4.3-p1 &lt;2.4.5*) — 修复了管理员用户因以下原因无法登录到管理员的问题 *TypeError： strtotime()要求参数1为字符串，但给定null* 错误。
* **MDVA-40830** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了在下订单期间多次应用商店点数的问题。
* **MDVA-42237** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了可配置产品特殊价格在子产品价格发生更改后未更新的问题。
* **MDVA-42520** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了以下情况下两次应用税率的问题 *支持跨境贸易* 已使用。
* 更新了修补程序：MDVA-27239、MDVA-39305、MDVA-41236、MDVA-36832。
* 已弃用的修补程序：MDVA-37725。

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*对于Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.4.5*) — 修复了批量属性更新仅在更改后才会为默认存储创建URL重写的问题 *产品可见性*.
* **MDVA-43091** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了在后端从管理员订购捆绑产品时出现错误的问题 *不能对此产品使用小数数量*.
* **MDVA-40816** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了相关产品规则显示规则条件中未定义类别中产品的问题。
* **MDVA-41305** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了GraphQL突变在将其添加到愿望清单后不返回可配置产品选项的问题。
* **MDVA-39181** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修复了相关产品规则显示规则条件中未定义类别中产品的问题。
* **MDVA-42584** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了通过Import或API更改数量和库存状态后无法更新后端可配置库存状态的问题。
* **MDVA-40175** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3*) — 修复了以下问题： *单击以更改配送方式* 在重新排序过程中，不会显示用于在管理员中选择配送方法的单选按钮。
* **MDVA-42768** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.5*) — 修复了在以下情况下，可配置产品将正常价格显示为0的问题： *显示缺货* 是Yes。
* **MDVA-43201** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了在特定区域设置中使用DOB属性时客户登录中发生错误的问题。
* 更新的修补程序： MDVA-35092和MDVA-33970。

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了当Adobe Commerce时区与本地环境时区不同时日期过滤器无法正常工作的问题。
* **MDVA-42657** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修复了管理员用户无法在客户区段条件中选择类别的问题。
* **MDVA-42806** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了 *新的公司注册* 每次通过REST API更新现有公司时都会发送电子邮件。
* **MDVA-37984** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修复了 [!DNL Visual Merchandiser] *按规则匹配产品* 功能无法正确筛选具有暂存更新的产品。
* **MDVA-40488** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了具有缺货子产品的可配置产品无法在其正确价格范围内显示的问题。
* **MDVA-42507** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了在为购物车规则应用暂存更新后清理全页缓存的问题。
* **MDVA-39163** (*对于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.5*) — 修复了在注册新用户且购物车中的产品来自访客会话时配送方式不可用的问题。
* **MDVA-38626** (*对于Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.5*) — 修复了管理员用户无法使用在后端下达订单的问题。 [!DNL PayPal Payflow Pro] 付款。
* **MDVA-38666** (*对于Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.3.6*) — 修复了管理员用户无法更改客户购物车中可配置产品选项的问题。
* **MDVA-38526** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修复了管理员用户无法访问 [!DNL Site-Wide Analysis tool].
* 更新了修补程序：MDVA-40101。

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了用户在设置之后收到500错误的问题。 *图像消息* cookie（如果已存在），但不存在新消息。
* **MDVA-41139** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了当简单产品的某个来源的数量为0时，可配置产品在产品导入后脱销的问题。
* **MDVA-42326** (*对于Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修复了以下问题：即使启用了永久购物车，客户在会话超时后结账时也会出错。
* **MDVA-42341** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了 `categoryList` 如果请求具有商店标头，GraphQL查询不会筛选结果。
* **MDVA-38393** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了在重新命名可配置产品的简单产品时，目录规则停止工作的问题。
* **MDVA-39153** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了在管理员中重新排序期间折扣金额计算不正确的问题。
* 更新了修补程序：MDVA-28993、MDVA-41061、MDVA-35984。

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.3*) — 修复了管理员用户在删除网站后无法访问客户网格的问题。
* **MDVA-40311** (*对于Adobe Commerce和Magento Open Source >=2.4.2-p2 &lt;2.4.4*) — 修复了管理员用户收到错误消息的问题 *无效的安全性或表单密钥。 请刷新页面* 在登录到管理员后（如果已配置自定义管理员路径并启用密钥）。
* **MDVA-41631** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修复了用户在尝试在没有可选设置的情况下检索订单信息时出现错误的问题 *电话* GraphQL中的值。
* **MDVA-27239** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.3.6*) — 修复了交叉销售产品未显示的问题。
* 更新了修补程序：MDVA-37068、MDVA-35254、MDVA-41164、MDVA-37916、MDVA-37478、MDVA-34551、MDVA-31791。

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*对于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.4*) — 修复了在重新索引期间前端缺少产品的问题。
* **MDVA-40120** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修复了按DESC/ASC排序的GraphQL不适用于具有相同相关性或价格的产品的问题。
* **MDVA-41399** (*对于Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.2*) — 修复了管理员用户无法访问 *管理购物车* 页面（如果客户将产品添加到愿望清单）。
* **MDVA-40609** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了禁用产品数据缺失的问题。 `cataloginventory_stock_status` 索引表，显示不正确的禁用产品数量。
* **MDVA-39031** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修复了通过GraphQL将产品添加到购物车是可行的，即使它未分配到目标网站的问题。
* **MDVA-41597** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了用户在使用GraphQL将多个可配置产品添加到购物车时收到错误的问题。
* **MDVA-27456** (*对于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.3.7*) — 修复了用户在尝试加载时收到错误的问题 [!DNL Swagger].
* **MDVA-32776** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.2*) — 修复了下达但未发运订单时库存状态未更新的问题。
* **MDVA-30862** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.0*) — 修复了打印的PDF发票上的订单日期不正确的问题。
* 改进了的索引页 [!DNL Quality Patch Tool]. 添加了方便的搜索和筛选 [!DNL quality patches] 更新该工具的最新版本。
* 更新的修补程序： MDVA-33382和MDVA-39482。

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了如果之前删除了结束日期，则无法为产品创建新的计划更新或编辑现有的计划更新的问题。
* **MDVA-41046** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了具有自定义选项的简单产品可用于分配给可配置/分组的产品的问题。
* **MDVA-40545** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了即使同一页面有多个节点，仅检索页面的第一个节点的问题。
* **MDVA-41164** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3-p1*) — 修复了管理员用户无法使用文件或图像类型自定义客户属性保存或编辑公司的问题。
* **MDVA-39229** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了在更新目录规则暂存更新开始时间后导致出现以下错误的问题： *Cron作业staging_synchronize_entities_period出错：无法删除活动更新。*
* **MDVA-40619** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了对CMS页面层级所做的更改在尝试在CMS页面上执行内联编辑时导致500错误的问题。
* **MDVA-41061** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了从管理员保存产品时，库存状态重置为可销售的问题。
* **MDVA-31763** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了在手动重新索引之前还原（或不应用）目录价格规则的问题。
* **MDVA-37748** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了GraphQL查询返回未分配给共享目录的产品的问题。

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了无法通过REST API同时创建同一订单的部分发票的问题。
* **MDVA-40101** (*对于Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.4.0*) — 修复了在使用成功下订单后无法从迷你购物车中删除项目的问题 [!DNL PayPal Express] 结帐。
* **MDVA-40401** (*对于Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修复了即使下订单失败，优惠券使用值也会更改的问题。
* **MDVA-40537** (*对于Adobe Commerce和Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) — 修复了在创建存储视图时，如果存在具有相同URL键的多个CMS页面，用户会收到错误的问题。
* **MDVA-37725** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.4.3-p1*) — 修复了从非默认网站发送的异步订单电子邮件包含默认网站的徽标URL的问题。
* **MDVA-39482** (*对于Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修复了在启用延交订单的情况下，如果以“0”数量导入产品，则产品缺货的问题。
* **MDVA-40435** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.4*) — 修复了通过GraphQL应用时，带动态价格的捆绑产品的折扣不正确的问题。
* **MC-42528** (*对于Adobe Commerce和Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) — 修复了 `categoryList` GraphQL查询返回已分配和未分配的类别。
* **MDVA-29400** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 修复了以下重复订单的问题： [!DNL PayPal Express Checkout].
* **MDVA-26005** (*对于Adobe Commerce和Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) — 修复了无法在类别树中为购物车价格规则条件选择类别的问题。
* **MDVA-25631** (*对于Adobe Commerce和Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) — 提高了编辑和保存包含大量客户的客户区段的性能。

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了GraphQL搜索查询无法在管理员的常用搜索词中显示的问题。
* **MDVA-40601** (*对于Adobe Commerce和Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) — 修复了用户在尝试获取有关通过GraphQL计划更新更改的类别的信息时出现错误的问题。
* **MDVA-37234** (*对于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) — 修复了以下问题：对于同一SKU，将项目多次添加到购物车（并行请求）会为同一购物车ID创建一个重复的行项目。
* **MDVA-33606** (*对于Adobe Commerce和Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) — 修复了用户收到 *唯一约束违规* 保存分配给层次结构的CMS页面时出错。
* **MDVA-31590** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;=2.4.1-p1*) — 修复了用户无法使用MySQL异步队列批量更新属性的问题。
* **MDVA-36309** (*对于Adobe Commerce和Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) — 修复了在管理网格中按属性搜索产品速度缓慢的问题。

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了从商店贷方支付订单时，使用FPT的发票显示错误的总计的问题。
* **MDVA-37364** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;=2.4.3*) — 修复了日期类型的自定义客户属性破坏客户的网格UI的问题。
* **MDVA-39195** (*对于Adobe Commerce和Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) — 修复了以下问题： *添加到购物车* 启用“重定向到购物车”后，类别页面上的按钮处于非活动状态。
* **MDVA-37115** (*对于Adobe Commerce和Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) — 修复了不需要的问题 *剩余0个* 注意事项显示在可配置的产品页面上。
* **MDVA-39521** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4*) — 修复了用户无法通过GraphQL为电话号码为空的购物车设置送货地址的问题。
* **MDVA-39384** (*对于Adobe Commerce和Magento Open Source>=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) — 修复了公司用户的自定义客户属性未保存的问题。
* **MDVA-39043** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.4.3*) — 修复了具有有限访问权限的管理员用户在尝试添加 *产品* CMS页面的构件。
* **MDVA-39966** (*对于Adobe Commerce和Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) — 修复了部署错误区域设置的问题。
* **MDVA-38852** (*对于Adobe Commerce和Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) — 修复了以下问题：当有多个并行订单时，设计目录库存会为会显着降低性能的更新锁定表。
* **MDVA-39986** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.3*) — 修复了用户无法使用Safari浏览器在MacOS上的Admin中下达订单的问题。
* **MDVA-38447** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了两个问题：其中， *无法单独显示* 可配置的子产品在GraphQL响应中返回，并使用类别过滤器优化GraphQL产品查询的MySQL查询。
* **MDVA-40134** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了在启用共享目录后，GraphQL未返回相关产品的问题。
* **MDVA-39935** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修复了GraphQL返回在网站级别禁用的可配置子产品的问题。

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4*) — 修复了 *调用成员函数getId()* 错误显示在管理员的订单详细信息页面上。
* **MDVA-34948** (*对于Adobe Commerce和Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 修复了长时间运行的查询的问题，例如 `GET_LOCK`.
* **MDVA-39305** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;=2.4.2-p1*) — 修复了注册客户无法使用已启用的Google ReCaptcha进行登录的问题。
* **MDVA-37897** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了客户尝试使用“最近查看的”小组件中的选项添加产品时，重定向不正确的问题。

## v1.1.0 {#v1-1-0}

* 引入了修补程序类别，以改进用户体验并使客户更轻松地搜索所需的修补程序。
* 此 `patches.json` 文件已重命名为 `support-patches.json`.
* **MDVA-38799** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了在创建暂存更新后未保存可下载产品的问题。
* **MDVA-37592** (*对于Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) — 修复了按价格排序对分配给共享目录的零价格产品无法正常工作的问题。
* **MDVA-38827** (*对于Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) — 修复了客户收到包含错误消息的订单装运电子邮件的问题。

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*对于Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) — 修复了保存CMS页面时的错误： *已存在具有相同ID PAGE_ID的项目*.
* **MDVA-34680** (*对于Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) — 修复了客户网格中客户帐户创建时间过滤不正确的问题。
* **MDVA-37068** (*对于Adobe Commerce >=2.3.1 &lt;2.4.4*) — 修复了购物车仅包含虚拟产品时显示的税率不正确的问题。
* **MDVA-38608** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了重新索引未成功完成时临时表未删除的问题。
* **MDVA-38308** (*对于Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) — 修复了与添加相关的问题 [!DNL Vimeo] 产品视频。

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*对于Adobe Commerce >=2.3.6 &lt;2.4.3*) — 修复了在使用时，客户未进入支付确认页面的问题 [!DNL Paypal Payment Advanced] 方法。
* **MDVA-37082** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了在保存分组产品的自定义库存时导致产品在前端无库存的问题。
* **MDVA-36572** (*对于Adobe Commerce >=2.3.5 &lt;2.4.3*) — 修复了贷项通知单更新不再导致数据库中重复产品预订更新的问题。
* **MDVA-38132** (*对于Adobe Commerce >=2.3.3 &lt;2.4.3*) — 修复了由于以下原因无法访问管理员面板的问题： *重定向次数过多* 错误。
* **MDVA-38270** (*对于Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修复了GraphQL中订单总计中缺少礼品卡信息的问题。

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*对于Adobe Commerce >=2.4.2 &lt;=2.4.4*) — 修复了在网站ID与商店ID不符时通过GraphQL将可配置产品添加到购物车的问题。
* **MDVA-36832** (*对于Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) — 修复了当视图宽度为768px时在页面上复制图像的问题。
* **MDVA-37874** (*对于Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) — 修复了以下问题： *整个购物车的固定折扣金额* 错误地应用于包含多个选项的捆绑产品。
* **MDVA-37913** (*对于Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) — 修复了通过API更新可下载产品时，可下载链接消失的问题。
* **MDVA-34330** (*对于Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) — 修复了“订单”网格中的订单未根据管理时区进行过滤的问题。

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*对于Adobe Commerce >=2.3.0 &lt;=2.3.7*) — 修复了在为使用下达的订单创建部分发票时，Adobe Commerce引发错误的问题 *分期付款* 通过REST API的支付方式。
* **MDVA-37362** (*对于Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) — 修复了GraphQL响应中可配置产品选项值和变量属性值为空的问题。
* **MDVA-37288** (*适用于Adobe Commerce 2.4.2的*) — 修复了在GraphQL请求后返回错误层价的问题。
* **MDVA-37225** (*对于Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) — 修复了在快速创建订单期间，当导入的SKU中存在整数值时上传流程卡住的问题。
* **MDVA-37224** (*对于Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) — 修复了客户无法向支付可协商报价的问题 [!DNL PayFlow Pro] 购物车中有其他产品。
* **MDVA-36286** (*对于Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) — 修复了当同一SKU在子类别中具有不同位置时，页面生成器产品小组件预览中断的问题。
* **MDVA-30186** (*对于Adobe Commerce >=2.3.4 &lt;=2.3.5-p2， >=2.4.0 &lt;=2.4.0-p1， >=2.4.2 &lt;=2.4.2-p1*) — 修复了GraphQL响应中，属性选项按选项值而不是属性项目计数进行排序的问题。

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*对于Adobe Commerce >=2.3.0 &lt;=2.4.2*) — 修复了通过API更改旧自定义选项后保留旧自定义选项的问题。
* **MDVA-35773** (*对于Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) — 修复了具有100%折扣的订单的发票上“总计”未显示为零的问题。
* **MDVA-36833** (*适用于Adobe Commerce 2.4.2的*) — 修复了将某些产品从共享目录排除之后，搜索结果显示每页产品随机数量的问题。
* **MDVA-37182** (*对于Adobe Commerce >=2.4.1 &lt;=2.4.2*) — 修复了在两个页面中获取错误搜索结果的问题 [!DNL Elasticsearch] 版本6和版本7。
* **MDVA-36253** (*对于Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) — 修复了在删除项目后，迷你购物车中显示错误小计的问题。
* **MDVA-36853** (*适用于Adobe Commerce 2.4.2的*) — 修复了在加载大型媒体集时不会显示图像的问题。

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*对于Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) — 修复了类别页面上缺少捆绑产品的问题。
* **MDVA-36615** (*适用于Adobe Commerce 2.4.2的*) — 修复了管理员产品网格中的产品计数不正确的问题。
* **MDVA-36464** (*对于Adobe Commerce >=2.4.0 &lt;=2.4.2*) — 修复了电子邮件通知配置在存储视图级别无法正常工作的问题。
* **MDVA-36138** (*适用于Adobe Commerce ^2.3.2的*) — 修复了以下问题：不调整送货价格，如果购物车中的所有商品都不符合免运费购物车规则，则会向客户显示完整的送货价格。
* **MDVA-36424** (*对于Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) — 修复了在后端基本URL与店面基本URL不同时，当内容被重复编辑时，附加到页面生成器元素的媒体图像消失的问题。
* **MDVA-35984** (*适用于Adobe Commerce ^2.4.0的*) — 修复了在为同一产品创建多个并发装运后产品数量和可销售数量不正确的问题。

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*对于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 这修复了GraphQL查询未使用类别缓存标记缓存的问题。
* **MDVA-33168** (*对于Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修复了通过API更新产品属性时，所有其他属性均更改为空值的问题。
* **MDVA-19640** (*适用于Adobe Commerce >=2.3.0*) — 修复了以下问题： [!DNL Advanced Reporting] 未显示任何数据。
* **MDVA-11189** (*对于Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修复了在导入CSV文件以更新产品库存后，来自的行 `cataloginventory_stock` 表格将被删除。
* **MDVA-26639** (*对于Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) — 修复了以下问题：如果创建新的订单确认电子邮件模板，则订单邮件中缺少订单项目。
* **MDVA-15546** (*适用于Adobe Commerce >=2.3.0*) — 修复了创建订单后 *列entity_id where子句不明确* 错误显示在异常日志中。
* **MDVA-21095** (*对于Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修复了查询时出现的问题 `INSERT INTO search_tmp` 批量属性值更新后不会结束。
* **MDVA-23845** (*对于Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) — 修复了在启用JavaScript缩小后无法预览电子邮件模板的问题。
* **MDVA-22026** (*对于Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修复了从CSV文件导入产品（包括来自外部URL的图像）失败的问题。
* **MDVA-22383** (*对于Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修复了保存产品耗时较长，并且页面会中断的问题。
* **MC-41359** (*对于Adobe Commerce >=2.3.6-p1 &lt;2.3.7， >=2.4.2 &lt;2.4.3*) — 修复了SameSite Cookie参数设置不正确的问题。

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*适用于Adobe Commerce 2.4.1的*) — 修复了页面生成器引发以下错误的问题： *启动页面生成器时出错。 请咨询您的技术支持联系人。*
* **MDVA-35356** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了取消部分开票的订单后，商店退款不正确的问题。
* **MDVA-33289** (*对于Adobe Commerce >=2.4.0 &lt;2.4.3*) — 修复了在签出期间，帐单地址UI中显示原始JavaScript代码的问题，如果 [!DNL Google Tag Manager] 已启用。
* **MDVA-35982** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了仅限特定网站的管理员用户无法为同一网站上的订单创建装运的问题。
* **MDVA-35155** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修复了在选项标题更改时无法购买捆绑产品的问题。
* **MDVA-35910** (*对于Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修复了在禁用“作为客户登录”功能后无法创建新客户帐户的问题。
* **MDVA-34474** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了使用API将产品添加到申请列表时出现的问题。
* **MDVA-34591** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了计算购物车规则折扣不正确的问题 *最大数量折扣应用于* 和 *折扣数量步骤（购买X）*.
* **MDVA-33704** (*对于Adobe Commerce >=2.4.0 &lt;2.4.3*) — 修复了 *店内提货* 虽然已将配送选项配置为可用，但不会显示。
* **MDVA-34928** (*对于Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) — 修复了从付款中删除商店积分后无限期显示页面加载程序的问题。
* **MDVA-35254** (*对于Adobe Commerce >=2.3.1 &lt;2.4.3*) — 修复了签出期间验证码的问题。
* **MDVA-35569** (*对于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了 *固定产品税* 当指定状态时，GraphQL响应中未填充字段。
* **MDVA-35847** (*对于Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修复了在使用自定义客户属性时公司用户表单中断的B2B问题。
* **MDVA-31307** (*对于Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修复了存在以下问题的情况 *内存不足* 由于缓存块的动态CSP白名单出现问题，导致某些类别上出现错误。

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了错误 *进行中* 消息状态正确 *完成* 面向消费者的消息 `quoteItemCleaner` 删除多个产品后。
* **MDVA-34102** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了“产品网格”和“管理”区域的“编辑产品”页面上禁用产品的默认库存数量为零。
* **MDVA-35286** (*对于Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修复了以下问题：如果客户在购物车中捆绑了产品，并且从多个地址签出切换到联机签出，则会出现错误。
* **MDVA-35312** (*对于Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) — 修复了空GraphQL请求时的响应代码500。
* **MDVA-34189** (*对于Adobe Commerce >=2.3.4 &lt;2.4.3*) — 修复了503第一个字节超时 [!DNL Visual Merchandiser] 查询（在加载管理员类别页面时）。
* **MDVA-34695** (*对于Adobe Commerce >=2.3.0 &lt;2.4.1*) — 修复负数 `children_count` 删除类别之后。

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*对于Adobe Commerce >=2.3.1 &lt;2.4.3*) — 修复了 *使用默认值* 在应用计划的更改后，复选框会被清除。 一旦计划的更改不再有效，问题即出现。
* **MDVA-35064** (*对于Adobe Commerce >=2.3.3 &lt;2.4.3*) — 修复了无法为通过API创建的可配置产品生成URL重写的问题。
* **MDVA-34943** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了快速订单缓存之前输入的SKU的问题。
* **MDVA-35197** (*对于Adobe Commerce >=2.3.5 &lt;2.4.0*) — 修复了在使用GraphQL添加到购物车时，如果之前添加的产品缺货，则会出错的问题。
* **MDVA-34850** (*对于Adobe Commerce >=2.3.1 &lt;2.4.0*) — 修复了可配置产品的缺货选项未显示而非显示为删除的问题。
* **MDVA-34867** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了为计划更新设置的条件字段的值未保存的问题。
* **MDVA-35092** (*对于Adobe Commerce >=2.3.5 &lt;2.4.3*) — 修复了用户无法添加的问题 [!DNL Vimeo] 已弃用的视频 [!DNL Vimeo] API。

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*对于Adobe Commerce >=2.3.6 &lt;2.4.3*) — 修复了当匹配的产品对每个网站的价格不同时，页面生成器产品内容类型预览中断的问题。
* **MDVA-32634** (*适用于Adobe Commerce ^2.3.1的*) — 修复了 `url_path` 在层次结构中移动类别后，分配给所有商店的类别保持不变。
* **MDVA-33344** (*适用于Adobe Commerce ^2.3.0的*) — 修复了硬编码的问题 `rma_item` 使用实体默认属性集ID，而不是数据库中的值。
* **MDVA-34192** (*对于Adobe Commerce >=2.3.4 &lt;2.4.3*) — 修复了无法使用dd/mm/yyyy格式修改/指定客户出生日期的问题。
* **MDVA-34847** (*适用于Adobe Commerce ^2.3.0的*) — 修复了具有自定义权限的管理员用户的管理员集合中，对于SQL条件，将ID类型转换为整数的过程。
* **MDVA-34886** (*适用于Adobe Commerce ^2.3.2的*) — 修复了以下情况下搜索不返回结果的问题 *粗细* 产品属性配置为可搜索。

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复的问题 [!DNL PayPal Payflow Pro] 付款失败，并出现重定向参数列表格式错误。
* **MDVA-34023** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了错误的问题 *没有此类具有addressId的实体* 会在访客的浏览器中随机显示。
* **MDVA-32759** (*对于Adobe Commerce >=2.3.1 &lt;2.4.3，带B2B扩展*) — 修复了共享目录删除现有层定价的问题。
* **MDVA-33482** (*适用于Adobe Commerce ^2.3.5的*) — 修复了以下问题：根据部分发票生成贷项通知单会导致对订单总额计税，而不是对该部分发票计税。
* **MDVA-33393** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复错误 *提供的国家/地区ID不存在*.
* **MDVA-33632** (*对于Adobe Commerce >=2.3.0 &lt;2.3.7*) — 修复了异常消息的位置 *此产品缺货* 现在，当尝试重新订购缺货的产品时，会向管理员用户显示。
* **MDVA-34469** (*对于Adobe Commerce >=2.4.1 &lt;2.4.2*) — 修复了在使用多个商店视图时，客户购物车上的GraphQL突变失败的问题。
* **MDVA-33976** (*对于Adobe Commerce >=2.3.0 &lt;2.3.7*) — 修复了从捆绑产品中删除第二个选项后，在店面中显示捆绑产品缺货的问题。
* **MDVA-33894** (*对于Adobe Commerce >=2.4.0 &lt;2.4.1，带B2B扩展*) — 修复了快速订购功能的多个问题，包括添加和删除多个产品以及SKU区分大小写。
* **MDVA-27664** (*对于Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修复了客户注册表单中显示错误的问题： *错误 — 出生日期不应晚于今天。*
* **MDVA-33970** (*对于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了在将价格属性的范围设置为网站时，贷项通知单中存在错误货币符号的问题。
* **MDVA-33992** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了B2B特殊定价在结账过程中显示错误的问题。
* **MDVA-34100** (*对于Adobe Commerce >=2.3.4 &lt;2.4.2，带有B2B扩展*) — 修复了无法从公司结构页面创建公司帐户的问题。

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*对于Adobe Commerce >=2.3.3 &lt;2.3.5， >=2.4.0 &lt;2.4.2*) — 修复了从CSV文件导入产品后重复图像的问题。
* **MDVA-33382** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了从类别中删除产品后索引器失效的问题。
* **MDVA-28511** (*对于Adobe Commerce >=2.3.5 &lt;2.3.6*) — 修复了无法完成的问题 [!DNL PayPal] 如果“名称”字段包含某些字符（如重音大写字母），请结帐。
* **MDVA-31519** (*对于Adobe Commerce >=2.3.5 &lt;2.3.6*) — 修复了在使用全站点销售规则时访客结账中等待超时的问题。
* **MDVA-33281** (*对于Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修复了中出现致命错误的问题。 `inventory:reservation:list-inconsistencies` 由于SKU参数类型错误。
* **MDVA-24201** (*对于Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修复了在手动重新编制索引之前，价格无法反映计划的购物车价格规则的问题。
* **MDVA-32694** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) — 修复了管理员用户无法将产品添加到可转让报价单（如果它与非默认商店相关）的问题。
* **MDVA-33516** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修复了在申请列表中编辑捆绑产品会导致错误的问题。
* **MDVA-33975** (*对于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了GraphQL请求中与价格计算相关的多个问题。

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复的问题 [!DNL PayPal] 结算报告不可用于 **报表** > **销售** > **[!DNL PayPal]** 按预期结算。
* **MCP-87** (*对于Adobe Commerce >=2.3.1 &lt;2.4.2*) — 改进了大型用户档案的类别产品和库存索引器的索引时间。
* **MDVA-33106** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在cron之后擦除重新计划的产品更改的问题 `run` 命令被执行。
* **MDVA-19391** (*对于Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修复了以下问题： `analytics_collect_data` 由于 `catalog_category_entity_text` 表格。
* **MDVA-20376** (*对于Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修复的问题 *没有具有customerId = 1的此类实体* 中的错误 `exception.log` ，用于在下单后登录客户。
* **MDVA-23764** (*对于Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修复中的错误 `JsFooterPlugin.php` 这会影响动态块的显示。
* **MDVA-13203** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了 *完整性约束违规search_tmp_表* 完全重新索引后出现错误。
* **MDVA-23426** (*对于Adobe Commerce >=2.3.3 &lt;2.3.5*) — 修复了Adobe Commerce发送的通知电子邮件包含一个空白正文并将内容添加为附件的问题。
* **MDVA-22150** (*对于Adobe Commerce >=2.3.1 &lt;2.3.4*) — 修复了以下问题：如果在Admin中禁用了可配置产品，那么在购物车中使用可配置产品并应用了优惠券的客户将无法登录。
* **MDVA-32545** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在从管理员创建订单时未自动发送发票的问题。
* **MDVA-32714** (*对于Adobe Commerce >=2.3.4 &lt;2.4.1*) — 修复了客户组价格在GraphQL产品查询中不起作用的问题。

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*对于Adobe Commerce >=2.3.2 &lt;2.4.2*) — 添加 *小计(包括 Tax)* 定价规则条件的选项。
* **MDVA-31236** (*对于Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修复了具有自定义资源访问权限的管理员无法设置2FA或登录的问题。
* **MDVA-30845** (*对于Adobe Commerce >=2.3.5 &lt;2.3.7*) — 修复了 *抱歉，目前此订单没有报价* 无法连接到UPS XML/USPS/DHL时显示错误，并且没有其他送货方法可用。
* **MDVA-32133** (*对于Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修复了在某些情况下无法从页面生成器加载媒体集的问题。
* **MDVA-12304** (*适用于Adobe Commerce >=2.3.0*) — 将最大Cookie数量从50增加到200。
* **MDVA-32632** (*对于Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修复了订单出现在支付系统中，但未出现在Adobe Commerce中的问题。
* **MDVA-32449** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2，带有B2B扩展*) — 修复了订单历史记录加载非常缓慢或根本不加载的问题。
* **MDVA-32739** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了启用异步电子邮件通知发送旧销售电子邮件的问题。

## v1.0.11 {#v1-0-11}

* **MC-38509** (*适用于Adobe Commerce 2.3.6和2.4.1的*) — 修复了 *创建帐户* 在更正中的无效数据后，按钮保持禁用状态 *新建客户帐户* 表单。
* **MDVA-31006** (*适用于Adobe Commerce 2.3.0和2.3.1的*) — 修复了使用下达订单后出现重复订单的问题。 [!DNL Paypal Express] 付款。
* **MDVA-25602** (*适用于Adobe Commerce 2.3.0的*) — 修复的问题 [!DNL PayPal Payflow Pro] 支付方法和将Cookie视为 `SameSite=Lax` 默认情况下，在Chrome 80浏览器和API响应中，重定向到客户登录页面。

## v1.0.10 {#v1-0-10}

修补程序版本的小修复

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*对于Adobe Commerce >=2.3.2 &lt;2.4.2*) — 修复了在以下情况下，带优惠券的购物车价格规则不通过GraphQL应用的问题 *整个购物车的固定金额折扣* 操作被使用。
* **MDVA-30889** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在使用虚拟和简单产品作为选项开具捆绑包发票后发生错误的问题。
* **MDVA-31791** (*对于Adobe Commerce >=2.3.4 &lt;2.3.5*) — 在使用目标规则或链接的产品时，提高产品页面的性能。
* **MDVA-31168** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了产品导出CSV文件未显示，并且存在内存分配错误的问题。
* **MDVA-32313** (*对于Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修复了使用错误的配置选项将可配置产品添加到愿望清单的问题。
* **MDVA-31759** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了产品未更新的问题 *下拉列表* 和 *文本区域* CSV导入期间的属性值。
* **MDVA-32012** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了韩国和阿根廷的邮政编码无法验证的问题。
* **MDVA-31640** (*对于Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) — 修复了无法通过REST API更新特殊价格的问题。
* **MDVA-28651** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0带有B2B扩展*) — 修复了通过REST API加载可转让报价时出现性能问题的情况。

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*对于Adobe Commerce >=2.3.0 &lt;2.4.1，带B2B扩展*) — 修复了贷项通知单网格中显示错误货币符号的问题。
* **MDVA-31295** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了完成部分订购并征税项目后未计算奖励点数的问题。
* **MDVA-30112** (*对于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了订单数超过 *簇大小* 值，Adobe Commerce会考虑以下订单 *待处理* 状态为不一致。
* **MDVA-31150** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了GET发票Rest API调用未返回商店信用和礼品卡余额的问题，当时，发票通过Rest API调用过帐，并且订单部分由商店信用和礼品卡帐户支付。
* **MDVA-30963** (*对于Adobe Commerce >=2.3.2 &lt;2.4.2*) — 修复了将产品筛选结果设置为仅包含为指定的值的问题 *所有商店视图* 在管理员中定义范围，包括在商店视图级别覆盖值的产品。
* **MDVA-29954** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2带有B2B扩展*) — 修复了 *新建公司注册请求* 和 *您已被链接到某个公司* 电子邮件是从错误的地址发送的。
* **MDVA-28357** (*对于Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) — 将标准分析器替换为带有关键字的SKU字段的自定义分析器 [!DNL ElasticSearch] 索引，使通配符搜索查询可与包含连字符(“ — ”)的SKU配合使用。

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了自定义订单状态更改为的问题 *正在处理* 在使用WebApi创建部分装运后。
* **MDVA-30428** (*对于Adobe Commerce >=2.3.4 &lt;2.3.5*) — 修复了将产品分配给自定义库存源时，客户无法将产品添加到愿望清单的问题。
* **MDVA-30594** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在配置FPT时签出期间无法保存带多个地址的订单的问题。
* **MDVA-29148** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了通过API调用（的产品自定义属性）创建产品时的问题。 `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` （如多选）如果有效负载中未提供值，则该类型不使用其默认值。
* **MDVA-30837** (*对于Adobe Commerce >=2.3.1 &lt;2.3.5*) — 添加了配置设置 *含税目标金额：是/否* 在“免运费”方法配置中。 时间 *含税目标金额* 设置为 *是*，最小订单金额计算为小计+税。 时间 *含税目标金额* 设置为 *否*，最小订单金额计算为小计
* **MDVA-25028** (*对于Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) — 修复了使用下达订单时的问题 [!DNL PayPal Payflow Pro] 触发欺诈过滤器时，未设置为可疑欺诈状态。
* **MDVA-31224** (*对于Adobe Commerce >=2.3.3 &lt;2.3.5*) — 改进性能 `catalog_product_price` 对捆绑产品执行重新索引操作。
* **MDVA-31321** (*对于Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修复以下情况时的空白页面（错误）： *显示全部* 已选中。 [!DNL Elasticsearch] 返回产品ID的大列表。 在此方案中，order by子句将转换为不正确的SQL格式。
* **MDVA-30815** (*对于Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修复了以下问题：当您更改搜索结果页面上应显示的搜索结果数量时，Adobe Commerce会显示一个空白页面。 [!DNL Elasticsearch] 现在，当您更改每个页面查看的搜索结果数时，可以正确显示类别页面中的结果。
* **MDVA-30782** (*对于Adobe Commerce >=2.3.5 &lt;2.4.2*) — 修复了在不考虑购物车规则的情况下显示动态块的问题。
* **MDVA-31021** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了中存在的性能问题。 `module-catalog-import-export/Model/Import/Product/Option.php`. 如果中有超过~10万个记录 `catalog_product_option` 表，对带有单个产品的新CSV进行验证需要的时间少于10秒。
* **MDVA-31007** (*对于Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修复了自定义地址属性未正确显示在我的帐户区域和后端的订单详细信息页面中的问题。
* **MDVA-29389** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了高级报表的问题，其中 `analytics_collect_data` cronjob说： *必须在host参数（如localhost：3306）中配置端口*.
* **MDVA-31343** (*对于Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修复了已删除主体类的问题 `page-layout-category-full-width` 在计划类别时。
* **MDVA-30945** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在更新购物车时收到致命错误消息的问题 `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*对于Adobe Commerce >=2.3.4 &lt;2.4.0*) — 实施 *最小值应匹配* 功能和部分搜索 [!DNL Elasticsearch] 引擎。 解决了搜索查询中连字符的问题。
* **MDVA-30102** (*对于Adobe Commerce >=2.3.2 &lt;=2.4.0*) — 修复了布局缓存没有TTL时Redis缓存快速增长的问题。
* **MDVA-30599** (*对于Adobe Commerce >=2.3.4 &lt;=2.4.0*) — 修复了使用API创建的访客报价错误地标记为已登录客户的报价的问题。
* **MDVA-29446** (*对于Adobe Commerce >=2.3.3 &lt;=2.4.0*) — 修复了结账期间不适用的配送方式价格显示为零的问题。
* **MDVA-30357** (*对于Adobe Commerce >=2.3.2 &lt;=2.4.0*) — 修复了在通过cron生成Sitemap时创建错误图像URL的问题。
* **MDVA-30565** (*对于Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) — 修复了以下问题： *没有cartid = 0的此类实体* 如果启用了永久购物车，则在storefront结帐时为访客客户显示错误。
* **MDVA-29787** (*对于Adobe Commerce >=2.3.0 &lt;=2.4.0*) — 修复了以下情况时，相关产品的目标规则不起作用的问题 *是其中之一* 条件用于定义要显示的产品。
* **MDVA-30977** (*对于Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) — 修复了重新索引后类别中随机缺少产品的问题。
* **MDVA-28202** (*对于Adobe Commerce >=2.3.4 &lt;=2.4.2*) — 修复了在使用MSI时，分层导航无法正确过滤可配置产品的问题。
* **MDVA-28300** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修复了GQL请求未反映目录价格规则中的价格更改的问题。
* **MDVA-31006** (*对于Adobe Commerce >=2.3.2 &lt;=2.4.2*) — 修复了使用下达订单后出现重复订单的问题。 [!DNL Paypal Express] 付款。

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*对于Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修复了分层导航的问题，其中 *否* 在以下情况下，布尔类型产品属性的值未包含在分层导航中： [!DNL Elasticsearch] 用作搜索引擎。
* **MDVA-28191** (*对于Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修复了在通过管理员创建订单期间无法加载付款方法的问题。
* **MDVA-29959** (*对于Adobe Commerce >=2.3.0 &lt;=2.3.3-p1，带B2B扩展*) — 修复了受限管理员用户使用的问题。 *公司* 不允许使用权限删除公司帐户。
* **MDVA-30265** (*对于Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修复了在创建发票后装运跟踪链接停止工作的问题。
* **MDVA-28409** (*对于Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修复了 `sales_clean_quotes` cron作业失败于 *内存不足* 当数据库中的过期引号数量很大时出错。
* **MDVA-30593** (*对于Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修复了未清理根据报价生命周期设置过期的报价的问题。
* **MDVA-30107** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修复了在将不同的基本URL用于商店视图时，商店切换器无法按预期工作的问题。
* **MDVA-28763** (*对于Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修复了使用REST API多次更新产品信息后产品图像复制的问题。
* **MDVA-30284** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了目录搜索索引器由于以下原因而失败的问题 *[!DNL Elasticsearch]错误：已超过索引中字段总数的限制。*
* **MDVA-29042** (*对于Adobe Commerce >=2.3.3 &lt;=2.3.4-p2，带B2B扩展*) — 修复了目录权限更改为的问题。 *允许* 将新产品添加到共享目录后自动更新。
* **MDVA-30428** (*对于Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修复了将产品分配给自定义库存源时，客户无法将产品添加到愿望清单的问题。
* **MDVA-28661** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2，带B2B扩展*) — 修复了在更改公司管理员后，“公司用户”公司帐户部分中引发错误的问题。

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*适用于Adobe Commerce 2.3.1的 — 2.3.4-p2*) — 修复了以下问题：如果数据库名称太长，则cron作业会失败，从而导致前端未更新类别。
* **MDVA-30106** (*适用于Adobe Commerce ^2.3.0的*) — 修复了结账过程中付款未加载的问题 *无法读取null的“length”属性* JS控制台中出错。
* **MDVA-28656** (*对于Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) — 修复了以下问题：如果下订单时不需要付款信息（例如，100%折扣），并且为订单创建了发票，则订单状态将更改为 *已关闭* 而不是“完成”。
* **MDVA-30209** (*适用于Adobe Commerce 2.3.0的 — 2.3.3-p1*) — 修复了客户更新其帐户信息时，客户组更改为默认的问题。
* **MDVA-30123** (*对于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了无法正确为GraphQL查询翻译属性选项标签的问题。
* **MDVA-29996** (*对于Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修复了在启用类别权限后，类别页面不会由完整页面缓存的问题。
* **MDVA-30164** (*对于Adobe Commerce >=2.3.1 &lt;2.4.2*) — 修复了存在自定义客户属性时无法从客户网格导出客户记录的问题。
* **MDVA-30444** (*对于Adobe Commerce >=2.3.0 &lt;2.4.1*) — 修复了使用GraphQL下订单时不会发送确认电子邮件的问题。
* **MDVA-30490** (*适用于Adobe Commerce 2.3.4的 — 2.3.5-p2*) — 修复了以下问题：如果其中一个产品的简短描述为空，“产品比较”会引发“500”错误页面。
* **MDVA-30232** (*对于Adobe Commerce >=2.3.1 &lt;2.4.1*) — 修复了原始订单包含礼品卡时无法重新订购的问题。
* **MDVA-29965** (*对于Adobe Commerce >=2.3.3 &lt;2.4.0*) — 修复了将产品添加到购物车时，客户收到“表单密钥无效”错误的问题。
* **MDVA-30008** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了无法通过Admin API为公共目录中的产品下订单的B2B问题。
* **MDVA-22469** (*适用于Adobe Commerce的2.3.2-p2 - 2.3.3-p1*) — 修复了以下问题：升级到Adobe Commerce 2.3.3后，页面生成器在“管理”面板中无法正常工作，以及某些JS和CSS文件无法加载。
* **MC-35984** (*对于Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修复了商家为退货授权(RMA)创建配送标签后无法与“退货”页面上的任何页面元素交互的问题。

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*适用于Adobe Commerce 2.3.0的 — 2.3.4*) — 修复的问题 [!DNL PayPal Payflow Pro] 支付方法和将Cookie视为 `SameSite=Lax` 默认情况下，在Chrome 80浏览器和API响应中，重定向到客户登录页面。
* **MDVA-26694** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) — 修复了产品和目录缓存每天过期的问题，但过期时间安排不同。
* **MDVA-27825** (*对于Adobe Commerce >=2.3.0 &lt;2.4.1*) — 修复了因内存泄漏导致导出大量数据失败的问题。
* **MDVA-29085** (*对于Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) — 修复了B2B问题，即如果API创建了公司，则不会发送任何所需的新公司电子邮件。
* **MDVA-29344** (*对于Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) — 修复了将文本从标题元素复制到文本元素后页面生成器卡住的问题。
* **MDVA-29835** (*适用于Adobe Commerce的>2.3.1 &lt;2.4.2*) — 修复了礼品卡订单包含两个代码而不是一个代码的问题。
* **MDVA-30052** (*对于Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) — 修复了专用内容（本地存储）未正确填充而导致性能问题的情况。
* **MDVA-30131** (*对于Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修复了分层导航的问题，其中 *否* 在以下情况下，布尔类型产品属性的值未包含在分层导航中： [!DNL Elasticsearch] 用作搜索引擎。
* **MDVA-35514** (*对于Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修复了在“创建软件包”模式窗口中创建送货标签并将订购的产品添加到软件包时出现的问题。
