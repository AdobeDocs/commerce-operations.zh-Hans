---
title: 发行说明
description: 了解Adobe Commerce可用的修补程序及其解决的问题。
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: 7649f4ffb0a04053d9a674aae7c29eb09ed02006
workflow-type: tm+mt
source-wordcount: '13737'
ht-degree: 0%

---

# 发行说明

此 [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) 提供由Adobe和Magento Open Source群体开发的各个修补程序。 它允许您应用、还原和查看所有适用于已安装的Adobe Commerce版本或Magento Open Source的个别修补程序的一般信息。 无论谁开发了修补程序，您都可以将修补程序应用到Adobe Commerce和Magento Open Source项目。 例如，您可以将社区开发的修补程序应用到Adobe Commerce项目。

>[!INFO]
>
>参见 [应用修补程序](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) 有关将修补程序应用于Adobe Commerce或Magento Open Source项目的说明。 参见 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 查看已发布修补程序的完整列表。

>[!INFO]
>
>有关信息 [!DNL quality patches] 由Community为Magento Open Source创建，请参见 [发行说明](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (对于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修复了以下问题：结账配送步骤中的默认配送地址会自动填充为之前选择的店内提货地址。
* **ACSD-52041** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了错误消息的问题： *[错误] [!DNL Page Builder] 渲染了5秒钟，没有释放锁定。* 保存编辑内容时在Chrome浏览器中显示 [!DNL Page Builder].
* **ACSD-52095** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了以下问题： `manage_stock` 产品导出后，CSV文件中的值未正确设置为0。
* **ACSD-51358** (对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了在删除没有结束日期的计划更新时，会导致为同一实体删除其他计划更新的问题。
* **ACSD-48070** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了编辑计划更新会触发异常的问题。
* **ACSD-51890** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了以下问题： [!UICONTROL Submit review] 按钮点击多次，不需要 [!DNL Google reCAPTCHA] v3验证。
* **ACSD-51984** (对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复未选中的问题 *[!UICONTROL Use Default Value]* 和 *[!UICONTROL non-default product field]* 不会保存第二个网站、商店和商店视图的值。
* **ACSD-52398** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复错误 *请求的数量不可用* 在尝试更新店面购物车中捆绑产品的数量时会发生这种情况。
* **ACSD-52786** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了目录规则条件的问题 *SKU是* 适用于从给定SKU开始的所有产品。
* **ACSD-52921** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了当购物车中存在缺货的可配置产品时，从GraphQL请求购物车详细信息时出现内部错误的问题。
* **ACSD-51683** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了使用GraphQL时无法将可自定义选项添加到购物车的问题。
* **ACSD-52133** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了在升级后无法保存客户帐户的问题。
* **ACSD-52202** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在订单履行中，当非默认库存数量更改为0数量时，默认库存的可销售数量错误地更改为0的问题。
* **ACSD-51265** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复的问题 `catalog_product_price` 当系统中捆绑的产品过多时，重新索引性能。
* **ACSD-52831** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了以下情况下客户无法下可转让报价单的问题 [!DNL Google reCAPTCHA v3 Invisible] 已启用。
* **ACSD-51845** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了无法通过异步批量REST API更新具有层价格和其他属性集的后续产品的问题。
* **ACSD-52815** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 修复了非默认来源的quantity字段输入最多仅支持6位数的问题，不同于默认库存的8位。
* **ACSD-51149** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了启用了目录权限的计划导入导出使索引器无效，然后通过cron缓存刷新的问题。
* **ACSD-50815** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了简单产品的小数数量不能用于新的捆绑产品选项的问题。
* ACSD-47803的更新版本。
* 更新了ACSD-51892的标题。
* 更新了ACSD-51379。
* 更新了ACSD-49970-v2。

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了在“管理员”中创建新订单时，管理员用户在选择商店视图后未正确重定向的问题。
* **ACSD-50813** (对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了以下问题：管理员无法在SKU中添加包含斜杠的捆绑产品 [!UICONTROL Add Products by SKU] 管理订单的功能。
* **ACSD-51630** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了大量系统消息导致下载管理页变慢的问题。
* **ACSD-51853** (对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.7) — 修复了在使用时，未应用复制的文本样式的问题 [!UICONTROL Page Builder].
* **ACSD-52160** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了以下问题：根据购物车价格规则，产品验证结果未根据规则条件“如果在购物车中找到/未找到项目，且所有/任何这些条件均为true”来正确评估。
* **ACSD-51636** (对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了以下问题：公司管理员尽管拥有所有必要的角色和权限，但无法从客户帐户部分添加新用户。
* **ACSD-51739** (对于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了以下情况下返回错误的问题： `structure_id` 在CompanyTeam GraphQL请求中查找。
* **ACSD-51857** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了性能缓慢的问题 `aggregate_sales_report_bestsellers_data` 大型销售订单和的cron报告 `sales_order_item` 数据库表是由于写入主数据查询的方式造成的。
* **ACSD-48448** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了在订单取消期间发生竞争条件问题，从而导致 `inventory_reservation` 表格。
* **ACSD-52689** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.6) — 修复了无法使用REST API将图像上传到Amazon S3存储的问题。
* **B2B-2674** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 将缓存功能添加到1customAttributeMetadata1 GraphQL查询。
* 添加了ACSD-44938的新版本。
* 添加了ACSD-46988的要求。

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5) — 修复了数据库回滚命令是否适用于数据库转储包含触发器和一个 *分隔符* SQL命令。
* **ACSD-50512** (对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复 *错误：可下载的链接与产品无关。 请验证链接并重试。* 更新可下载产品暂存更新的开始日期时出错。
* **ACSD-50949** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了高级搜索中的价格过滤器在与SKU过滤器一起使用时未返回正确结果的问题。
* **ACSD-51645** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了在保存新的Cart Price Rule（如果扩展）时引发的错误 `Magento_OfflineShipping` 已禁用。
* **ACSD-50895** (对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了以下问题： [!DNL Google Analytics] 3如果 [!DNL Google Analytics] 4 GTM未配置。
* **ACSD-51102** (对于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了以下问题：当计划更新启用了目录规则时，应用于大量产品的目录规则无法正确编制索引。
* **ACSD-50368** (对于Adobe Commerce和Magento Open Source>= 2.4.3 &lt;2.4.5) — 修复了以下问题： `group_id` 在通过Async REST API或Async Bulk REST API创建客户时，被忽略。
* **ACSD-51497** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) — 修复了客户无法按下拉列表类型的自定义属性对目录页面进行排序的问题。
* **ACSD-51408** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt; 2.4.7) — 修复了将订单项目状态错误设置为的问题 *[!UICONTROL Backordered]*.
* **ACSD-51735** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 修复了将订单项目状态错误设置为的问题 *[!UICONTROL Ordered]* 当产品库存为 *0*.
* **ACSD-51792** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了以下情况下页面没有展示事件的问题： [!DNL Google Tag Manager] 4已启用。
* **ACSD-51471** (对于Adobe Commerce >=2.4.3 &lt;2.4.7) — 修复了以下问题：对于使用本身具有计划更新的简单产品的捆绑产品，管理员用户无法保存其计划更新。
* **ACSD-51700** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在管理员的可下载产品编辑页面上切换商店视图时发生的错误。
* **ACSD-51120** (对于Adobe Commerce >=2.3.7 &lt;2.4.3) — 修复了包含通过暂存更新更新的CMS块的CMS页面未清除GraphQLGET请求缓存的问题。
* **ACSD-51240** (对于Adobe Commerce >=2.4.4 &lt;2.4.6) — 修复了通过公司注册表进行注册时上传文件缺失的问题。
* **ACSD-51907** (对于Adobe Commerce >=2.4.2 &lt;2.4.3) — 修复了受限管理员用户无法创建具有离线退款的贷项通知单的问题。
* **ACSD-52148** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 修复了以下问题： [!DNL Google V3 reCAPTCHA] 管理员登录偶尔会失败。
* **ACSD-51431** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复索引器状态为的问题 *工作* 即使changelog中没有新条目。
* **ACSD-51892** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了在部署期间配置文件加载多次的性能问题。
* 已弃用ACSD-51114。

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了以下问题： [!UICONTROL Page Builder's] 多个错误导致管理员无法保存没有内容权限的产品。
* **ACSD-51305** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了缺货可配置子产品在GraphQL响应中不可用的问题。
* **ACSD-50621** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了以下问题： [!UICONTROL Tier Prices] 对于共享目录中的不同网站，尝试在多网站环境中编辑它们时不可见。
* **ACSD-51041** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.6) — 改进了价格索引器的性能。
* **ACSD-51379** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了以下对页面文本内容进行更改的问题： [!UICONTROL Page Builder] 未保存。
* **ACSD-49480** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了仅将一个购物车价格规则应用于购物车的问题。
* **ACSD-51230** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了在订单中处理简单产品的部分退款时删除礼品卡帐户的问题。
* **ACSD-51238** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了在更新可配置产品和编辑价格时删除库存来源的问题。
* **ACSD-50794** (对于Adobe Commerce >=2.4.1 &lt;2.4.7) — 修复了通过GraphQL删除礼品消息或礼品包装时，数据库中未更新礼品消息或礼品包装详细信息的问题。
* **ACSD-51528** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了以下问题： *x_forwarded_for* 列在 *sales_order* 表格。
* **ACSD-50849** (对于Adobe Commerce >=2.4.4 &lt;2.4.6) — 修复了在清除缓存后将新产品添加到类别导致现有产品的位置和选择不匹配的问题。
* **ACSD-51294** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了GTM/GA价格、数量、税、运费和收入作为字符串发送到的问题 [!DNL Google Analytics] 和GTM。
* **ACSD-51204** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在创建贷项通知单后，完全销售的产品未返回库存的问题。
* **ACSD-51291** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3) — 修复了限制管理员只能访问一个网站的问题，即管理员可以将图像/视频添加到分配给多个网站的产品。
* 添加了ACSD-50336的新版本。
* 已更换ACSD-49970修补程序。

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) — 修复了Recaptcha v2在提交失败的付款后未重新加载的问题。
* **ACSD-50817** (对于Adobe Commerce和Magento Open Source >=2.3.7 &lt;2.4.7) — 优化Cron作业 `sales_clean_quotes` 跑得更快。
* **ACSD-49392** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) — 修复了在对捆绑产品进行部分退款后，订单状态更改为已关闭的问题。
* **ACSD-51036** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 修复了以下问题：并发REST API调用期间的争用条件会覆盖 [!UICONTROL Items Ordered] 表格。
* **ACSD-50858** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.7) — 提高加载横幅内容的性能。
* 添加了MDVA-39305-v2、ACSD-45169的新版本。
* 更新了修补程序ACSD-50260-v2。

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (对于Adobe Commerce和Magento Open Source>=2.4.4-p1 &lt;2.4.4-p3) — 修复了当产品重新上架或价格更改时，不会发送产品警报电子邮件的问题。
* **ACSD-50367** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了在创建没有值的多选客户地址属性时，客户地址导出无法正常工作的问题。
* **ACSD-49877** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了视频自动播放在移动设备中不起作用的问题 [!DNL Safari] 当视频直接链接到远程视频文件，而不是流服务时。
* **ACSD-50165** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复错误 *无法删除该文件。 Warning！unlink：没有这样的文件或目录* 从管理员刷新JS/CSS缓存时。
* **ACSD-49737** (对于Adobe Commerce和Magento Open Source>=2.4.1-p1 &lt;2.4.7) — 修复了在卡付款失败后优惠券被错误地标记为使用的问题。
* **ACSD-50814** (对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了管理员用户无法创建贷项通知单的问题。
* **ACSD-50116** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了管理员用户无法为子类别级别3或更低级别创建URL重写的问题。
* **ACSD-49513** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5) — 修复了由于0字节文件而导致远程存储同步失败的问题。
* **ACSD-46683** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了运输价格显示的问题 *尚未计算*.
* **ACSD-49129** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了以下问题： *[!UICONTROL content]* 属性（base64图像代码）未返回到 `rest/V1/products/sku/media` 产品媒体API响应。
* **ACSD-50276** (对于Adobe Commerce >=2.4.0 &lt;2.4.7) — 修复了创建多选客户属性后，客户注册表单在店面中无法正常工作的问题。
* **ACSD-50527** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了在保存具有空动态块的页面时发生的错误。
* **ACSD-49973** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.5) — 通过GraphQL提高捆绑产品的获取性能。
* **ACSD-51114** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在启用异步索引时，随机产品从大型目录中消失的问题。 改进大型目录的异步重新索引性能。
* **B2B-2598** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 将缓存功能添加到 [!UICONTROL availableStores]， [!UICONTROL countries]， [!UICONTROL country]， [!UICONTROL currency]、和 [!UICONTROL storeConfig] GraphQL查询。
* 添加了MDVA-42806、ACSD-48627、ACSD-46815的新版本。
* 更新了ACSD-49773、ACSD-47179、ACSD-48300的修补程序元数据。

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了订单未准备好取货时，API会发送准备取货电子邮件的问题。
* **ACSD-49822** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了中的更新问题 [!UICONTROL Requisition List] 页面未反映在 [!UICONTROL Print Requisition List].
* **ACSD-48771** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了从更早版本升级列块内容类型的问题 [!DNL Page Builder] 版本。
* **ACSD-49464** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了当orderId不同时，发票、发运和贷项通知单不会从存档移回的问题。
* **ACSD-49773** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了将AWS S3用作远程存储时，产品导出失败的问题。
* **ACSD-49748** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了无法发送邀请的问题。
* **ACSD-49502** (对于Adobe Commerce >=2.4.3 &lt;2.4.7) — 修复了在将暂存更新应用于可下载产品后，可下载链接未正确更新的问题。
* **ACSD-49527** (对于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了GraphQL公司角色无法正确显示分页的问题。
* **ACSD-49706** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了在未选择任何值时为可视样本属性保存默认值的问题。
* **ACSD-49835** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了多选属性的存储级别上未正确保存使用默认复选框值的问题。
* **ACSD-49898** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了捆绑产品的特殊价格超过1000时，产品网格引发异常的问题。
* **ACSD-50234** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.5) — 修复了在使用下订单时，确认电子邮件中客户名称有误的问题 [!DNL PayPal].
* **ACSD-49960** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了按日期过滤不适用于客户订单网格的问题。
* **ACSD-49849** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了将客户电子邮件替换为 [!DNL PayPal] 使用以下方式下订单时发送电子邮件 [!DNL PayPal Express] 通过GraphQL。
* **ACSD-49839** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了以下问题：当产品在SKU中具有单引号或双引号时，共享目录定价和结构会在“管理员”中引发错误。
* **ACSD-49970** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了以下情况下对GraphQL错误的不正确处理： [!DNL New Relic] 报表处于打开状态。
* **ACSD-50260** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了GraphQL产品搜索结果限制为仅包含10,000个结果的问题。
* **ACSD-48813** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了搜索未根据属性的搜索权重显示相关结果的问题。

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.3) — 修复了基于“是/否”属性创建的目录价格规则不考虑所选范围的问题。
* **ACSD-47704** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了捆绑产品仅显示现成产品价格的问题。
* **ACSD-49370** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了以下问题： *日期时间* 产品属性具有 *FilterMatchTypeInput* 键入GraphQL架构。
* **ACSD-48807** (对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.7) — 修复了客户产品评论未通过GraphQL的storeview进行过滤的问题。
* **ACSD-49433** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了以下问题：对于未结金额的礼品卡，购物车中的默认金额显示为小计。
* **ACSD-48866** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了在请求类别的RSS馈送时出现错误的问题。
* **ACSD-48784** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了在客户组之间错误地缓存客户区段价格的问题。
* **ACSD-48857** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了用户在使用页面生成器编辑后无法保存更改的问题。
* **ACSD-49065** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了报价单项目在仅分配给自定义库存的情况下无法在管理员中显示的问题。
* **ACSD-49179** (对于Adobe Commerce和Magento Open Source >=2.4.2 &lt;2.4.7) — 修复了以下问题：对于不同的商店，如果使用的货币不同，订单报表会显示不正确的金额。
* **ACSD-49286** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了当页面上存在多个产品小组件时，将产品两次添加到购物车的问题。
* **ACSD-49574** (对于Adobe Commerce >=2.4.4 &lt;2.4.7) — 添加了通过GraphQL支持购物车中礼品卡产品更新的功能。
* 更新了修补程序：ACSD-48694。

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (对于Adobe Commerce >=2.4.1 &lt;2.4.7) — 修复了使用可转让报价下订单时，使用默认送货地址而不是新送货地址的问题。
* **ACSD-48059** (对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了商家无法保存“”的问题[!UICONTROL Match product by rule]”类别中的。
* **ACSD-48216** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) — 修复了以下问题： [!UICONTROL AUTO_INCREMENT] 的 [!UICONTROL inventory_source_item] 表在 [!UICONTROL UPDATE] 操作。
* **ACSD-47908** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) — 修复了结帐期间在配送步骤中选择源和数量时，出现“值应小于或等于0”错误。
* **ACSD-49497** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了以下问题：订单在发运后仍处于处理状态，并且应用了部分退款。
* **ACSD-48694** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7) — 修复了错误“请求的状态更改无效”阻止客户下订单的问题。
* **ACSD-49013** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在使用批量API创建客户时，电子邮件确认未转换为网站区域设置的问题。
* **ACSD-48164** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了受限管理员无法保存网站级别值的问题。
* **ACSD-48404** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 修复了按下浏览器的“返回”按钮时，“记住类别分页=是”导致错误的问题。
* **ACSD-48634** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了以下情况下暂存更新页面上的JS错误：[!UICONTROL Google Analytics Content Experiments]已启用。
* **ACSD-49042** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 修复了无法从店面订购无限延期交货的产品的问题。
* 更新了修补程序：ACSD-48366、ACSD-48661。

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (适用于Adobe Commerce和Magento Open Source2.4.4) || >=2.4.5 &lt;2.4.6) — 修复了由于应用程序级别的缓存，无法始终发送价格下降通知的问题。
* **ACSD-48661** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了公司的信用额度大于999的问题，即由于验证错误，逗号分隔符阻止保存公司。
* **ACSD-48773** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了从错误的商店获取奖励积分电子邮件模板的问题。
* **ACSD-48587** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了产品小组件匹配规则中HTML特殊字符导致无法显示匹配产品的问题。
* **ACSD-48212** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了产品导入将产品分配给错误源的问题。
* **ACSD-47988** (对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了产品导出会从页面生成器产品描述中裁切HTML标签的问题。
* **ACSD-48366** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了产品图像未显示在补货电子邮件模板上的问题。
* **ACSD-48417** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了在为产品创建计划更改并保存另一个产品后显示SQL错误的问题。

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了将捆绑产品分配给任何网站时产品价格重新索引不起作用的问题。
* **ACSD-48262** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了将“允许每页所有产品”设置设为“是”时，产品在前端不可见的问题。
* **ACSD-48293** (对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4) — 修复了以下问题：当售出的子产品重新上架时，复合产品缺货。
* **ACSD-47520** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在创建贷项通知单时客户丢失奖励点的问题。
* **ACSD-48044** (对于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.4) — 修复了向包含多批发运的单个订单应用多张礼品卡时阻止下订单的问题。
* **ACSD-48300** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了删除可配置产品时无法创建返回值的问题。
* **ACSD-47910** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 修复了相应实体网格中缺少订单、发票、装运和贷项通知单的问题。
* **ACSD-47292** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了将“显示缺货产品”设置为“是”时，GraphQL响应中无法使用缺货捆绑产品的问题。
* **ACSD-48234** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了启用“显示缺货”选项时，目录搜索结果显示错误的类别项目计数的问题。
* **ACSD-48313** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5) — 修复了当属性值包含逗号时，无法解析“configurable_variations”列的问题。 “additional_attributes”使用相同的解析算法。
* **ACSD-48627** (对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了缺货的可配置产品在发送GraphQL请求以获取购物车详细信息时导致错误的问题。
* 更新了修补程序：MDVA-39384。

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了以下产品未生成SEO友好URL的问题： *url_key* 在store-view级别覆盖的属性。
* **ACSD-46865** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了在启用异步索引时未填充“装运”和“贷项通知单”网格的问题。
* **ACSD-47004** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了在没有VAT ID的账单地址中不应用VAT的问题。
* **ACSD-47803** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了显示现成可配置产品样本的问题。
* **ACSD-47137** (对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 当pub/media文件夹非常大时，提高图像库的加载速度。
* **ACSD-46770** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了以下情况下发送管理员订单电子邮件的问题： *电子邮件订单确认* 未选中。
* **ACSD-47955** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了GraphQL无法正确显示购物车折扣的问题。
* **ACSD-46617** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了以下问题： *继续结帐* 即使小计大于配置的，按钮也会灰显 *最小订单金额*.
* **ACSD-47079** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 修复了当子产品库存状态通过REST APIPOST/rest/V1/inventory/source-items更改时，复合产品（捆绑、分组和可配置）库存状态未更新的问题。
* **ACSD-47336** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复 *出现错误。* 在Commerce Admin中取消通知时出错。
* **ACSD-47559** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了“预览电子邮件模板”区域不完全可见的问题。
* **ACSD-47920** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了以下问题：即使在 *允许访客签出* 已关闭。
* 已更换修补程序：MDVA-39305、MDVA-42855。

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了具有特定范围受限访问权限的管理员无法删除产品审阅的问题。
* **ACSD-47107** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5) — 修复了目录价格规则折扣应用于自定义产品选项的问题。
* **ACSD-47232** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了无法在管理员中应用具有总权重条件的优惠券的问题。
* **ACSD-46519** (对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.6) — 修复了GraphQL categoryList请求为锚点类别返回错误的product_count的问题。
* **ACSD-47027** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了更新缓慢的CompanyRole GraphQL请求。
* **ACSD-47666** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了以下问题：在“管理员”>“系统”>“权限”>“用户角色”>“角色”>“角色用户”网格中，筛选功能无法正常工作。
* **ACSD-47497** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在“管理员”下的“配置”中看不到“服务”选项卡的问题。
* 更新了修补程序：ACSD-47743。
* 已更换修补程序：MDVA-42807。

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3) — 修复 _正在尝试访问bool类型值上的数组偏移_ 访问PHP 7.4中已知产品的某些非现有类别路径时出错。
* **ACSD-47332** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了cron失败并出现错误的问题，该错误仅在00:00 UTC到00:59 UTC之间运行时报告。
* **ACSD-47280** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在特定范围上禁用共享目录功能无法正常工作的问题。
* **ACSD-47106** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了无法在公司创建页面上的新自定义属性中保存值的问题。
* 更新了修补程序：ACSD-45143。

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了用户在分配大量产品源时出错的问题。
* **ACSD-46856** (对于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 通过系统>配置>导入>高级定价提高更新层价格的性能。
* **ACSD-46541** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 修复了删除订单项后管理员用户无法创建贷项通知单的问题。
* **ACSD-46581** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在购物车中选择国家/地区后，估计税额合计未更新的问题。
* **ACSD-46618** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了产品列表小组件为已登录的客户显示不正确的缓存价格的问题。
* **ACSD-46674** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在客户电子邮件中将图像类型的自定义选项显示为HTML的问题。
* **ACSD-46988** (对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了GraphQL“货币”API请求为自定义货币返回NULL值的问题。
* **ACSD-47076** (对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5) — 修复了Vimeo视频无法在店面播放的问题。
* **ACSD-45071** (对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4) — 修复了在导入期间将默认源添加到产品的问题。
* **AC-3023** (对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 将DHL方案更新到最新版本10.0。
* 更新了修补程序：MDVA-42584。
* 已更换修补程序：MDVA-36572、ACSD-45241。

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5*) — 修复了用户在使用商店点数退款时获得错误订单状态的问题。
* **ACSD-46703** (*对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6*) — 修复了无法在产品编辑页面上拖放自定义选项的问题。
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
* **ACSD-46192** (*对于Adobe Commerce和Magento Open Source>=2.3.6 &lt;2.4.5*) — 修复了使用的问题 `async/bulk/V1/configurable-products/bySku/options` 端点。
* **ACSD-46404** (*对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5*) — 修复了管理员用户在升级到2.4.4后无法登录的问题。
* 更新了修补程序：MDVA-41305、MDVA-38626、MDVA-38728、MDVA-41061-V4、MDVA-42269、MDVA-39305。

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了以下问题：特定存储的GraphQL产品突变返回所有可配置变体，包括未分配给所请求存储的变体。
* **ACSD-46146** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.6*) — 修复了管理员下订单后发送两封订单确认电子邮件的问题。
* **ACSD-45255** (*对于Adobe Commerce >=2.4.3 &lt;2.4.6*) — 修复了受限制管理员用户的“低库存报表”页面上的异常。
* **ACSD-45488** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6*) — 修复了具有多个来源的可配置产品未自动返回到库存中的问题。
* **ACSD-45754** (*对于Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.6*) — 修复了将优惠券应用到购物车后未添加奖励积分的问题。
* **ACSD-45849** (*对于Adobe Commerce >=2.4.3 &lt;2.4.4*) — 修复了应用暂存更新后视频元数据丢失的问题。
* **ACSD-45257** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.4*) — 修复了GraphQL未正确显示购物车折扣的问题。
* **ACSD-44938** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4*) — 修复了以下问题： `VAT_ID` 无法应用于GraphQL请求中的来宾用户。
* 更新了修补程序：MDVA-43417。

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*对于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.4*) — 修复了在创建贷项通知单后虚拟产品的库存数量计算错误的问题。
* **ACSD-43887** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了在启用公司的采购订单时，结帐付款页面上显示不正确详细信息的问题。
* **ACSD-45143** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5*) — 修复了以下问题 `setShippingAddressesOnCart` 突变不允许将数字区域代码设置为 *区域*.
* **ACSD-44591** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.6*) — 修复了在未进行验证码确认的情况下下订单时发生的错误。
* **ACSD-45520** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.6*) — 修复了当用户从购物车编辑可配置产品时，未在产品详细信息页面上预先选择样本选项的问题。
* **ACSD-45169** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.6*) — 修复了以下问题： [!DNL Visual Merchandiser] 在应用暂存更新后，不会显示可配置产品的正确库存和价格。
* **ACSD-45424** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.6*) — 修复了在部分退款（贷项通知单）之后创建错误预订补偿的问题。
* **MDVA-42807** (*对于Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.6*) — 修复了自定义货币符号未显示在商店正面的问题。
* 更新了修补程序：MDVA-42689、AC-3022。

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了订单报表中针对受限管理员用户错误计算订单总数的问题。
* **MDVA-44940** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复从管理员保存类别时发生的SQL错误。
* **MDVA-44562** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.2-p2*) — 修复了以下问题：尽管非默认商店视图发起了GraphQL请求，但报价单项目的非默认商店ID会被默认商店ID覆盖。
* **MDVA-43167** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了当管理员用户选择所有订单时，管理员订单网格批量操作不适用于多页的问题。
* **MDVA-44044** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.2-p2*) — 修复了将产品分配给新网站后未在类别页面上显示产品的问题。
* **MDVA-42509** (*对于Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.4*) — 修复了无法快速上传CSV以获取 *无法发送Cookie* 错误。
* 更新了修补程序：MDVA-41061和MDVA-42584。
* 新文件的前缀 [!DNL Quality Patches Tool] 修补程序将从 *MDVA* 到 *ACSD* 由于内部流程更改。

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了当购物车中已有最小数量的项目时，无法将其他项目添加到购物车的问题。
* **MDVA-44887** (*对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5*) — 修复了 *未捕获的SyntaxError：意外的令牌“const”* “管理”面板中出错。
* **MDVA-43718** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复 *使用者无权访问%resources。* 从自定义集成访问共享目录时出错。
* **MDVA-44660** (*对于Adobe Commerce和Magento Open Source>=2.4.2-p1 &lt;2.4.5*) — 修复了重音符号字符的问题 ``` ` ``` 无法用于客户的名字和姓氏。
* **MDVA-40896** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了 *错误： TypeError：传递给Magento的参数3* 异步产品批量API时出错。
* **MDVA-38559** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3*) — 修复了 */V1/customers/search API* 具有多个订阅的客户出错。
* **MDVA-44533** (*对于Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.4*) — 修复了错误将折扣应用于捆绑子产品的问题。
* 更新了修补程序：MDVA-41061和MDVA-42269。

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了产品的问题 *无法单独显示* 仍显示在目录高级搜索结果中。
* **MDVA-44100** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了将所有FPT分配给购物车中的最后一个产品并重置为其他产品的问题。
* **MDVA-43605** (*对于Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.5*) — 修复了使用Rest API时，订单数据返回行总计的负值的问题。
* **MDVA-43102** (*对于Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.5*) — 修复了通过REST API进行退款时，可销售数量未正确更新的问题。
* **MDVA-43178** (*对于Adobe Commerce和Magento Open Source>=2.4.3-p2 &lt;2.4.5*) — 修复了无法在GraphQL中检索自定义存储区的客户令牌的问题。
* **MDVA-43859** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修复了错误的问题 *没有具有customerId =* 在已删除的客户尝试登录时记录。
* **MDVA-44147** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了GraphQL请求不返回申请列表的问题。
* **MDVA-44505** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.3*) — 修复了GraphQL应用奖励点数不会更新全部内容以及在下订单期间多次应用商店积分的问题。
* 更新了修补程序：MDVA-29148、MDVA-36464-V5、MDVA-42584、MDVA-39993-V2。

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.3*) — 修复了仅当“客户区段”设置为时，“相关产品规则”才有效的问题 *全部*.
* **MDVA-39605** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.5*) — 修复了Redis缓存TTL（过期日期）的值错误的问题。
* **MDVA-43862** (*对于Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.5*) — 修复了由于GraphQL而导致客户无法更新购物车项目的问题 *UpdateCartItems变异* 错误。
* **MDVA-43824** (*对于Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) — 修复了取消带有折扣的订单时出现错误的问题。
* **MDVA-43451** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了错误的问题 *未找到所请求的存储。 请验证存储并重试。* 在为特定网站配置共享目录时显示。
* **MDVA-43491** (*对于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.5*) — 修复了在导入多商店网站的产品时，基本图像标签未更新的问题。
* **MDVA-43601** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了完全重新索引后触发器缺失的问题。
* **MDVA-42046** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) — 修复了在更新产品时，为带有日期输入字段的产品属性分配了错误值的问题。
* **MDVA-43935** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修复了向上销售产品显示两次的问题。
* **MDVA-44188** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了系统颁发的电子邮件的问题 `.-` 中的地址不会发送。
* **MDVA-42283** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了法语区域设置的管理顺序网格中的日期时间格式无效的问题。
* 更新了修补程序：MDVA-41061-V2、MDVA-36309、MDVA-30862、MDVA-39713。
* 为添加了修补程序元数据 [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.3.6*) — 修复了用户能够编辑活动计划更新的开始时间的问题。
* **MDVA-42410** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了优惠券报表仅显示默认基本货币的问题。
* **MDVA-41136** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了的过期日期的问题 `mage-cache-sessid` 不扩展，从而导致客户数据清理。
* **MDVA-39993** (*对于Adobe Commerce和Magento Open Source>=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) — 修复了通过API完成的库存更改未在前端产品页面上反映的问题。
* **MDVA-42855** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了签出期间新客户地址未保存到通讯簿中的问题。
* **MDVA-42645** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了在禁用商店信用功能的情况下，管理员无法退还奖励点数的问题。
* **MDVA-43414** (*对于Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2*) — 修复了在运行 `inventory.reservations.updateSalabilityStatus` 数值SKU上的队列使用者。
* **MDVA-41628** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5*) — 修复了在添加新模块时，现有受限管理员用户访问新资源的问题。
* **MDVA-43348** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了礼品卡GraphQL请求在以下情况下显示错误的问题： `gift_card_options` contain *uid*.
* **MDVA-39546** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了在编辑期间，将暂存更新的开始日期设置为早于当前日期的问题。
* **MDVA-42950** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了视频无法在产品页面上播放的问题。
* **MDVA-42689** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了Adobe Commerce引发的问题 *完整性约束违规* 在导入过程中更新产品类别时出错。
* **MDVA-41229** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了可配置产品导入后，前端上可用的图像未显示的问题。
* **MDVA-43731** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了以下问题： *搜索同义词* 在中添加值后不再有效 *要匹配的最少搜索词*.
* **MDVA-43232** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.5*) — 修复了对中的产品进行分类的问题 [!DNL Visual Merchandiser] 按“特殊价格至底部/顶部”会在保存类别时出错。
* **MDVA-43726** (*对于Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.3*) — 修复了基于存储级别属性匹配的目录价格规则在部分重新索引后无法应用的问题。
* 更新了修补程序：MDVA-36464、MDVA-37478、MDVA-38608。
* 为添加了修补程序元数据 [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了无法通过REST API为特定网站更新产品价格属性的问题。
* **MDVA-41350** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了当具有受限访问权限的管理员用户按SKU顺序添加产品超出其角色范围时，引发异常的问题。
* **MDVA-42269** (*对于Adobe Commerce和Magento Open Source>=2.4.3-p1 &lt;2.4.5*) — 修复了管理员用户由于 *TypeError： strtotime()要求参数1为字符串，但给定null* 错误。
* **MDVA-40830** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了在下订单期间多次应用商店积分的问题。
* **MDVA-42237** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了可配置产品特殊价格在子产品价格发生更改后未更新的问题。
* **MDVA-42520** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了以下情况下两次应用税率的问题 *启用跨境贸易* 已使用。
* 更新了修补程序：MDVA-27239、MDVA-39305、MDVA-41236、MDVA-36832。
* 已弃用的修补程序：MDVA-37725。

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*对于Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.4.5*) — 修复了批量属性更新仅在更改后才会为默认存储创建URL重写的问题 *产品可见性*.
* **MDVA-43091** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了在后端从管理员订购捆绑产品时出现错误的问题 *不能对此产品使用小数数量*.
* **MDVA-40816** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了相关产品规则显示规则条件中未定义类别中产品的问题。
* **MDVA-41305** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了GraphQL突变在添加到愿望清单后不返回可配置产品选项的问题。
* **MDVA-39181** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修复了相关产品规则显示规则条件中未定义类别中产品的问题。
* **MDVA-42584** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了通过Import或API更改数量和库存状态后端Stock可配置状态未更新的问题。
* **MDVA-40175** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3*) — 修复了以下问题： *单击以更改配送方式* 在重新排序过程中，不会显示用于选择配送方法的单选按钮。
* **MDVA-42768** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.5*) — 修复了在以下情况下，可配置产品将正常价格显示为0的问题 *显示缺货* 是。
* **MDVA-43201** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了在特定区域设置中使用DOB属性时，客户登录中发生错误的问题。
* 更新了修补程序：MDVA-35092和MDVA-33970。

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了当Adobe Commerce时区与本地环境时区不同时，日期过滤器无法正常工作的问题。
* **MDVA-42657** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修复了管理员用户无法在客户区段条件中选择类别的问题。
* **MDVA-42806** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了以下问题 *新公司注册* 每次通过REST API更新现有公司时都会发送电子邮件。
* **MDVA-37984** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修复了以下问题 [!DNL Visual Merchandiser] *按规则匹配产品* 功能无法正确筛选具有暂存更新的产品。
* **MDVA-40488** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了具有缺货子产品的可配置产品无法在其正确价格范围内显示的问题。
* **MDVA-42507** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了在为购物车规则应用暂存更新后清理全页缓存的问题。
* **MDVA-39163** (*对于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.5*) — 修复了在注册新用户且购物车中的产品来自访客会话时配送方式不可用的问题。
* **MDVA-38626** (*对于Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.5*) — 修复了管理员用户无法使用在后端下达订单的问题 [!DNL PayPal Payflow Pro] 付款。
* **MDVA-38666** (*对于Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.3.6*) — 修复了管理员用户无法更改客户购物车中可配置产品选项的问题。
* **MDVA-38526** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修复了管理员用户无法访问 [!DNL Site-Wide Analysis tool].
* 更新了修补程序：MDVA-40101。

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了用户在设置后出现500错误的问题 *图像消息* Cookie（如果已存在），但不存在新消息。
* **MDVA-41139** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了以下问题：当简单产品的某个来源的数量为0时，可配置产品在产品导入后脱销。
* **MDVA-42326** (*对于Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修复了以下问题：即使启用了永久购物车，客户在会话超时后仍会在结账时遇到错误。
* **MDVA-42341** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了以下问题 `categoryList` 如果请求具有商店标头，GraphQL查询不会筛选结果。
* **MDVA-38393** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了当可配置产品的简单产品被重新命名时，目录规则停止工作的问题。
* **MDVA-39153** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了在管理员中重新排序期间折扣金额计算不正确的问题。
* 更新了修补程序：MDVA-28993、MDVA-41061、MDVA-35984。

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.3*) — 修复了管理员用户在删除网站后无法访问客户网格的问题。
* **MDVA-40311** (*对于Adobe Commerce和Magento Open Source>=2.4.2-p2 &lt;2.4.4*) — 修复了管理员用户收到错误消息的问题 *安全性或表单密钥无效。 请刷新页面* 在登录到管理员后（如果已配置自定义管理员路径并启用密钥）。
* **MDVA-41631** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修复了在没有可选设置的情况下尝试检索订单信息时，用户遇到错误的问题 *电话* GraphQL中的值。
* **MDVA-27239** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.3.6*) — 修复了交叉销售产品不显示的问题。
* 更新了修补程序：MDVA-37068、MDVA-35254、MDVA-41164、MDVA-37916、MDVA-37478、MDVA-34551、MDVA-31791。

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*对于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.4*) — 修复了在重新索引期间前端缺少产品的问题。
* **MDVA-40120** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修复了按DESC/ASC排序的GraphQL不适用于具有相同相关性或价格的产品的问题。
* **MDVA-41399** (*对于Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.2*) — 修复了管理员用户无法访问 *管理购物车* 页面（如果客户将产品添加到愿望清单）。
* **MDVA-40609** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了禁用产品数据缺失的问题。 `cataloginventory_stock_status` 索引表，显示不正确的禁用产品数量。
* **MDVA-39031** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修复了即使未将产品分配给目标网站，也可以通过GraphQL将产品添加到购物车的问题。
* **MDVA-41597** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了用户在使用GraphQL将多个可配置产品添加到购物车时收到错误的问题。
* **MDVA-27456** (*对于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.3.7*) — 修复了用户在尝试加载时出现错误的问题 [!DNL Swagger].
* **MDVA-32776** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.2*) — 修复了下达但未发运订单时库存状态未更新的问题。
* **MDVA-30862** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.0*) — 修复了打印的PDF发票上的订单日期不正确的问题。
* 已改进以下项的索引页： [!DNL Quality Patch Tool]. 添加了方便的搜索和筛选功能 [!DNL quality patches] 更新工具的版本。
* 更新了修补程序：MDVA-33382和MDVA-39482。

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了以下问题：如果之前删除了结束日期，则无法为产品创建新的计划更新或编辑现有的计划更新。
* **MDVA-41046** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了具有自定义选项的简单产品可用于分配给可配置/分组的产品的问题。
* **MDVA-40545** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了即使同一页面有多个节点，仅检索页面的第一个节点的问题。
* **MDVA-41164** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3-p1*) — 修复了管理员用户无法保存或编辑具有文件或图像类型自定义客户属性的公司的问题。
* **MDVA-39229** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了在更新目录规则暂存更新开始时间后导致出现以下错误的问题： *Cron作业staging_synchronize_entities_period出错：无法删除活动更新。*
* **MDVA-40619** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了对CMS页面层次结构所做的更改在尝试在CMS页面上执行内联编辑时导致500错误的问题。
* **MDVA-41061** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了从管理员保存产品时，库存状态重置为可销售的问题。
* **MDVA-31763** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了在手动重新索引之前恢复（或不应用）目录价格规则的问题。
* **MDVA-37748** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了GraphQL查询返回未分配给共享目录的产品的问题。

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了无法通过REST API同时创建同一订单的部分发票的问题。
* **MDVA-40101** (*对于Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.4.0*) — 修复了在使用成功下订单后无法从迷你购物车中删除项目的问题 [!DNL PayPal Express] 结帐。
* **MDVA-40401** (*对于Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修复了即使下订单失败，优惠券使用值也会更改的问题。
* **MDVA-40537** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.4.0-p1*) — 修复了以下问题：如果存在具有相同URL键的多个CMS页面，则用户在创建商店视图时会收到错误。
* **MDVA-37725** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.4.3-p1*) — 修复了从非默认网站发送的异步订单电子邮件包含默认网站的徽标URL的问题。
* **MDVA-39482** (*对于Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修复了在启用延交订单的情况下，如果以“0”数量导入产品，则产品缺货的问题。
* **MDVA-40435** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.4*) — 修复了通过GraphQL应用时，带动态价格的捆绑产品折扣不正确的问题。
* **MC-42528** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;=2.4.3-p1*) — 修复了以下问题 `categoryList` GraphQL查询返回已分配和未分配的类别。
* **MDVA-29400** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 修复了以下订单重复的问题： [!DNL PayPal Express Checkout].
* **MDVA-26005** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.3.5-p2*) — 修复了无法在类别树中为购物车价格规则条件选择类别的问题。
* **MDVA-25631** (*对于Adobe Commerce和Magento Open Source>=2.3.3 &lt;=2.3.5-p2*) — 提高编辑和保存包含大量客户的客户区段的性能。

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了GraphQL搜索查询未显示在管理员中的常用搜索词中的问题。
* **MDVA-40601** (*对于Adobe Commerce和Magento Open Source>=2.3.1 &lt;=2.4.2-p2*) — 修复了用户在尝试获取有关通过GraphQL计划更新更改的类别的信息时出现错误的问题。
* **MDVA-37234** (*对于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) — 修复了以下问题：对于同一SKU，将项目多次添加到购物车（并行请求）会为同一购物车ID创建一个重复的行项目。
* **MDVA-33606** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;=2.4.2-p2*) — 修复了用户收到 *唯一约束违规* 保存分配给层次结构的CMS页面时出错。
* **MDVA-31590** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;=2.4.1-p1*) — 修复了用户无法使用MySQL异步队列批量更新属性的问题。
* **MDVA-36309** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;=2.4.2-p2*) — 修复了管理网格中按属性搜索产品速度缓慢的问题。

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了从商店贷方支付订单时，带FPT的发票显示错误的总计的问题。
* **MDVA-37364** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;=2.4.3*) — 修复了日期类型的自定义客户属性破坏客户的网格UI的问题。
* **MDVA-39195** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;=2.4.2-p2*) — 修复了以下问题： *添加到购物车* “重定向到购物车”启用时，类别页面上的按钮处于不活动状态。
* **MDVA-37115** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;=2.4.2-p2*) — 修复了不需要的问题 *剩余0个* 通知显示在可配置产品页面上。
* **MDVA-39521** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4*) — 修复了用户无法通过GraphQL在具有空电话号码的购物车上设置送货地址的问题。
* **MDVA-39384** (*对于Adobe Commerce和Magento Open Source>=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) — 修复了公司用户的自定义客户属性未保存的问题。
* **MDVA-39043** (*对于Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.4.3*) — 修复了具有有限访问权限的管理员用户在尝试添加 *产品* CMS页面的构件。
* **MDVA-39966** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) — 修复了部署不正确的区域设置时出现的问题。
* **MDVA-38852** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.3.5-p2*) — 修复了以下问题：在设计目录库存时，如果存在多个并行订单，则会为大幅降低性能的更新锁定表。
* **MDVA-39986** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.3*) — 修复了用户无法使用Safari浏览器在MacOS上的管理员中下达订单的问题。
* **MDVA-38447** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了以下两个问题： *无法单独显示* 可配置的子产品在GraphQL响应中返回，并使用类别过滤器优化GraphQL产品查询的MySQL查询。
* **MDVA-40134** (*对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了在启用共享目录后，GraphQL未返回相关产品的问题。
* **MDVA-39935** (*对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修复了GraphQL返回在网站级别禁用的可配置子产品的问题。

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4*) — 修复了以下问题 *调用成员函数getId()* 错误显示在管理员的订单详细信息页面上。
* **MDVA-34948** (*对于Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 修复了长时间运行的查询的问题，例如 `GET_LOCK`.
* **MDVA-39305** (*对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;=2.4.2-p1*) — 修复了注册客户无法使用已启用的Google ReCaptcha登录的问题。
* **MDVA-37897** (*对于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了当客户尝试使用最近查看的构件中的选项添加产品时，重定向不正确的问题。

## v1.1.0 {#v1-1-0}

* 引入了修补程序类别，以改善用户体验，并使客户更轻松地搜索所需的修补程序。
* 此 `patches.json` 文件已重命名为 `support-patches.json`.
* **MDVA-38799** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了在创建暂存更新后未保存可下载产品的问题。
* **MDVA-37592** (*对于Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) — 修复了按价格排序对分配给共享目录的0价格产品无法正确工作的问题。
* **MDVA-38827** (*对于Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) — 修复了客户收到包含错误消息的订单装运电子邮件的问题。

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*对于Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) — 修复了保存CMS页面时的错误： *已存在具有相同ID PAGE_ID的项目*.
* **MDVA-34680** (*对于Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) — 修复了客户网格中无法正确过滤客户帐户创建时间的问题。
* **MDVA-37068** (*对于Adobe Commerce >=2.3.1 &lt;2.4.4*) — 修复了当购物车仅包含虚拟产品时显示错误税率的问题。
* **MDVA-38608** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了重新索引未成功完成时临时表未删除的问题。
* **MDVA-38308** (*对于Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) — 修复了与添加相关的问题 [!DNL Vimeo] 产品视频。

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*对于Adobe Commerce >=2.3.6 &lt;2.4.3*) — 修复了在使用时，客户未进入支付确认页面的问题 [!DNL Paypal Payment Advanced] 方法。
* **MDVA-37082** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了在保存分组产品的自定义库存时导致产品在前端无库存的问题。
* **MDVA-36572** (*对于Adobe Commerce >=2.3.5 &lt;2.4.3*) — 修复了贷项通知单更新不再导致数据库中重复产品预订更新的问题。
* **MDVA-38132** (*对于Adobe Commerce >=2.3.3 &lt;2.4.3*) — 修复了由于以下原因无法访问管理面板的问题： *重定向次数过多* 错误。
* **MDVA-38270** (*对于Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修复了GraphQL中订单总计中缺少礼品卡信息的问题。

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*对于Adobe Commerce >=2.4.2 &lt;=2.4.4*) — 修复了当网站ID与商店ID不符时，通过GraphQL将可配置产品添加到购物车时出现的问题。
* **MDVA-36832** (*对于Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) — 修复了当视图宽度为768px时在页面上复制图像的问题。
* **MDVA-37874** (*对于Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) — 修复了以下问题： *整个购物车的固定折扣金额* 错误地应用于包含多个选项的捆绑产品。
* **MDVA-37913** (*对于Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) — 修复了通过API更新可下载产品时可下载链接消失的问题。
* **MDVA-34330** (*对于Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) — 修复了“订单”网格中的订单未按照管理时区进行过滤的问题。

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*对于Adobe Commerce >=2.3.0 &lt;=2.3.7*) — 修复了在为使用下达的订单创建部分发票时，Adobe Commerce引发错误的问题 *分期付款* 通过REST API付款方式。
* **MDVA-37362** (*对于Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) — 修复了GraphQL响应中可配置产品选项值和变量属性值为空的问题。
* **MDVA-37288** (*适用于Adobe Commerce 2.4.2的*) — 修复了在GraphQL请求后返回错误层价的问题。
* **MDVA-37225** (*对于Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) — 修复了当导入的SKU中存在整数值时，快速订单创建期间上传流程卡住的问题。
* **MDVA-37224** (*对于Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) — 修复了客户无法向支付可协商报价的问题 [!DNL PayFlow Pro] 购物车中有其他产品。
* **MDVA-36286** (*对于Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) — 修复了当同一SKU在子类别中具有不同位置时，页面生成器产品小组件预览中断的问题。
* **MDVA-30186** (*对于Adobe Commerce >=2.3.4 &lt;=2.3.5-p2， >=2.4.0 &lt;=2.4.0-p1， >=2.4.2 &lt;=2.4.2-p1*) — 修复了在GraphQL响应中，属性选项按选项值而不是属性项目计数排序的问题。

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*对于Adobe Commerce >=2.3.0 &lt;=2.4.2*) — 修复了通过API更改旧自定义选项后仍保持不变的问题。
* **MDVA-35773** (*对于Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) — 修复了具有100%折扣的订单的发票上，总计未显示为零的问题。
* **MDVA-36833** (*适用于Adobe Commerce 2.4.2的*) — 修复了在从共享目录排除某些产品后，搜索结果显示每页产品随机数的问题。
* **MDVA-37182** (*对于Adobe Commerce >=2.4.1 &lt;=2.4.2*) — 修复了获取两个中的错误搜索结果的问题 [!DNL Elasticsearch] 版本6和版本7。
* **MDVA-36253** (*对于Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) — 修复了删除项目后迷你购物车中显示错误小计的问题。
* **MDVA-36853** (*适用于Adobe Commerce 2.4.2的*) — 修复了在加载大型媒体集时不会显示图像的问题。

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*对于Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) — 修复了类别页面上缺少捆绑产品的问题。
* **MDVA-36615** (*适用于Adobe Commerce 2.4.2的*) — 修复了管理产品网格中产品计数不正确的问题。
* **MDVA-36464** (*对于Adobe Commerce >=2.4.0 &lt;=2.4.2*) — 修复了电子邮件通知配置在存储视图级别无法工作的问题。
* **MDVA-36138** (*适用于Adobe Commerce ^2.3.2的*) — 修复了以下问题：不调整送货价格，并且如果购物车中的所有项目都不符合免运费购物车规则，则会向客户显示完整的送货价格。
* **MDVA-36424** (*对于Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) — 修复了在后端基本URL与店面基本URL不同时，当重复编辑内容时，附加到页面生成器元素的媒体图像消失的问题。
* **MDVA-35984** (*适用于Adobe Commerce ^2.4.0的*) — 修复了为同一产品创建多个并发发运后，产品数量和可销售数量不正确的问题。

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*对于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 这修复了GraphQL查询未使用类别缓存标记缓存的问题。
* **MDVA-33168** (*对于Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修复了通过API更新产品属性时，所有其他属性会更改为空值的问题。
* **MDVA-19640** (*对于Adobe Commerce >=2.3.0*) — 修复了以下问题： [!DNL Advanced Reporting] 未显示任何数据。
* **MDVA-11189** (*对于Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修复了在导入CSV文件以更新产品库存后，来自的行 `cataloginventory_stock` 表已被删除。
* **MDVA-26639** (*对于Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) — 修复了以下问题：如果创建新的订单确认电子邮件模板，则订单邮件中缺少订单项目。
* **MDVA-15546** (*对于Adobe Commerce >=2.3.0*) — 修复了创建订单后 *列entity_id where子句不明确* 错误显示在异常日志中。
* **MDVA-21095** (*对于Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修复了查询时出现的问题 `INSERT INTO search_tmp` 批量属性值更新后不会结束。
* **MDVA-23845** (*对于Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) — 修复了在启用JavaScript缩小后无法预览电子邮件模板的问题。
* **MDVA-22026** (*对于Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修复了从CSV文件（包括来自外部URL的图像）导入产品时失败的问题。
* **MDVA-22383** (*对于Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修复了保存产品耗时较长，并且页面会中断的问题。
* **MC-41359** (*对于Adobe Commerce >=2.3.6-p1 &lt;2.3.7， >=2.4.2 &lt;2.4.3*) — 修复了SameSite Cookie参数设置不正确的问题。

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*适用于Adobe Commerce 2.4.1的*) — 修复了页面生成器引发以下错误的问题： *启动页面生成器时出错。 请咨询您的技术支持联系人。*
* **MDVA-35356** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了取消部分开票的订单后，商店退款不正确的问题。
* **MDVA-33289** (*对于Adobe Commerce >=2.4.0 &lt;2.4.3*) — 修复了在签出期间，计费地址UI中显示原始JavaScript代码的问题，如果 [!DNL Google Tag Manager] 已启用。
* **MDVA-35982** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了仅限特定网站的管理员用户无法为同一网站上的订单创建装运的问题。
* **MDVA-35155** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修复了在选项标题更改时无法购买捆绑产品的问题。
* **MDVA-35910** (*对于Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修复了在禁用“以客户身份登录”功能后无法创建新客户帐户的问题。
* **MDVA-34474** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了使用API将产品添加到申请列表时出现的问题。
* **MDVA-34591** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了计算购物车规则折扣不正确的问题 *最大数量折扣应用于* 和 *折扣数量步骤（购买X）*.
* **MDVA-33704** (*对于Adobe Commerce >=2.4.0 &lt;2.4.3*) — 修复了以下问题 *店内提货* 尽管已将配送选项配置为可用，但该选项不显示。
* **MDVA-34928** (*对于Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) — 修复了从付款中删除商店积分后无限期显示页面加载程序的问题。
* **MDVA-35254** (*对于Adobe Commerce >=2.3.1 &lt;2.4.3*) — 修复了签出期间验证码的问题。
* **MDVA-35569** (*对于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了以下问题 *固定产品税* 当指定状态时，GraphQL响应中未填充字段。
* **MDVA-35847** (*对于Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修复了在使用自定义客户属性时“公司用户”表单中断的B2B问题。
* **MDVA-31307** (*对于Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修复了以下问题： *内存不足* 由于缓存块的动态CSP白名单出现问题，导致某些类别上出现错误。

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了错误 *进行中* 消息状态正确 *complete* 给消费者的消息 `quoteItemCleaner` 删除多个产品后。
* **MDVA-34102** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了“产品网格”和“管理”区域的“编辑产品”页面上禁用产品的默认库存数量为零。
* **MDVA-35286** (*对于Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修复了以下问题：如果客户在购物车中捆绑了产品，并且从多个地址签出切换到网络签出，则会出现错误。
* **MDVA-35312** (*对于Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) — 修复了空GraphQL请求时的响应代码500。
* **MDVA-34189** (*对于Adobe Commerce >=2.3.4 &lt;2.4.3*) — 修复了上的503第一个字节超时 [!DNL Visual Merchandiser] 查询（加载管理类别页面时）。
* **MDVA-34695** (*对于Adobe Commerce >=2.3.0 &lt;2.4.1*) — 修复负数 `children_count` 删除类别之后。

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*对于Adobe Commerce >=2.3.1 &lt;2.4.3*) — 修复了以下问题 *使用默认值* 在应用计划的更改后，复选框会被清除。 一旦计划的更改不再有效，就会出现此问题。
* **MDVA-35064** (*对于Adobe Commerce >=2.3.3 &lt;2.4.3*) — 修复了无法为通过API创建的可配置产品生成URL重写的问题。
* **MDVA-34943** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了快速订单缓存之前输入的SKU的问题。
* **MDVA-35197** (*对于Adobe Commerce >=2.3.5 &lt;2.4.0*) — 修复了当之前添加的产品缺货时，使用GraphQL添加到购物车时出现错误的问题。
* **MDVA-34850** (*对于Adobe Commerce >=2.3.1 &lt;2.4.0*) — 修复了未显示可配置产品的缺货期权而不是显示为删除的问题。
* **MDVA-34867** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了为计划更新设置的条件字段的值未保存的问题。
* **MDVA-35092** (*对于Adobe Commerce >=2.3.5 &lt;2.4.3*) — 修复了用户无法添加的问题 [!DNL Vimeo] 已弃用的视频 [!DNL Vimeo] API。

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*对于Adobe Commerce >=2.3.6 &lt;2.4.3*) — 修复了当匹配的产品针对每个网站具有不同的价格时，Page Builder产品内容类型预览中断的问题。
* **MDVA-32634** (*适用于Adobe Commerce ^2.3.1的*) — 修复了以下问题 `url_path` 在层次结构中移动类别后，分配给所有商店的类别保持不变。
* **MDVA-33344** (*适用于Adobe Commerce ^2.3.0的*) — 修复了硬编码的问题 `rma_item` 使用实体默认属性集ID，而不是来自数据库的值。
* **MDVA-34192** (*对于Adobe Commerce >=2.3.4 &lt;2.4.3*) — 修复了无法使用dd/mm/yyyy格式修改/指定客户出生日期的问题。
* **MDVA-34847** (*适用于Adobe Commerce ^2.3.0的*) — 修复了具有自定义权限的管理员用户的管理员集合中，对于SQL条件，将ID类型转换为整数的存储过程。
* **MDVA-34886** (*适用于Adobe Commerce ^2.3.2的*) — 修复了以下情况下搜索不返回结果的问题 *权重* 产品属性配置为可搜索。

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了的问题 [!DNL PayPal Payflow Pro] 付款失败，并出现重定向参数列表格式错误。
* **MDVA-34023** (*对于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了错误的问题 *没有addressId的此类实体* 会在访客的浏览器中随机显示。
* **MDVA-32759** (*对于Adobe Commerce >=2.3.1 &lt;2.4.3，带有B2B扩展*) — 修复了共享目录删除现有层定价的问题。
* **MDVA-33482** (*适用于Adobe Commerce ^2.3.5的*) — 修复了以下问题：根据部分发票生成贷项通知单导致对订单总额征税，而不是对该部分发票征税。
* **MDVA-33393** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复错误 *提供的国家/地区ID不存在*.
* **MDVA-33632** (*对于Adobe Commerce >=2.3.0 &lt;2.3.7*) — 修复了异常消息的位置 *此产品缺货* 在尝试重新订购缺货的产品时，现在向管理员用户显示。
* **MDVA-34469** (*对于Adobe Commerce >=2.4.1 &lt;2.4.2*) — 修复了在使用多个商店视图时，客户购物车上的GraphQL突变失败的问题。
* **MDVA-33976** (*对于Adobe Commerce >=2.3.0 &lt;2.3.7*) — 修复了从捆绑产品中删除第二个选项后，在店面中显示捆绑产品缺货的问题。
* **MDVA-33894** (*对于Adobe Commerce >=2.4.0 &lt;2.4.1，带B2B扩展*) — 修复了快速订购功能的多个问题，包括添加和删除多个产品以及SKU区分大小写。
* **MDVA-27664** (*对于Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修复了客户注册表单中导致显示错误的问题： *错误 — 出生日期不应晚于今天。*
* **MDVA-33970** (*对于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了将价格属性的范围设置为网站时，贷项通知单中存在错误货币符号的问题。
* **MDVA-33992** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了B2B特殊定价在结账时显示不正确的问题。
* **MDVA-34100** (*对于Adobe Commerce >=2.3.4 &lt;2.4.2，带有B2B扩展*) — 修复了无法从公司结构页面创建公司帐户的问题。

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*对于Adobe Commerce >=2.3.3 &lt;2.3.5， >=2.4.0 &lt;2.4.2*) — 修复了从CSV文件导入产品后重复图像的问题。
* **MDVA-33382** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了从类别中删除产品后索引器失效的问题。
* **MDVA-28511** (*对于Adobe Commerce >=2.3.5 &lt;2.3.6*) — 修复了无法完成的问题 [!DNL PayPal] 检查名称字段是否包含某些字符（如重音大写字母）。
* **MDVA-31519** (*对于Adobe Commerce >=2.3.5 &lt;2.3.6*) — 修复了在使用全站点销售规则时来宾结帐中的等待超时问题。
* **MDVA-33281** (*对于Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修复了中出现致命错误的问题。 `inventory:reservation:list-inconsistencies` 由于SKU参数类型错误。
* **MDVA-24201** (*对于Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修复了在手动重新索引之前，价格无法反映计划的购物车价格规则的问题。
* **MDVA-32694** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) — 修复了管理员用户无法将产品添加到可转让报价（如果它与非默认商店相关）的问题。
* **MDVA-33516** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修复了在申请列表中编辑捆绑产品会导致错误的问题。
* **MDVA-33975** (*对于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了GraphQL请求中与价格计算相关的多个问题。

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了的问题 [!DNL PayPal] 结算报告不可用于 **报告** > **销售** > **[!DNL PayPal]** 按预期结算。
* **MCP-87** (*对于Adobe Commerce >=2.3.1 &lt;2.4.2*) — 改进了大型用户档案的类别产品和库存索引器的索引时间。
* **MDVA-33106** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了重新计划的产品更改在cron之后被擦除的问题 `run` 命令被执行。
* **MDVA-19391** (*对于Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修复了以下问题： `analytics_collect_data` 由于NULL描述记录位于 `catalog_category_entity_text` 表格。
* **MDVA-20376** (*对于Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修复了的问题 *没有具有customerId = 1的此类实体* 中的错误 `exception.log` ，用于在下单后登录的客户。
* **MDVA-23764** (*对于Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修复中的错误 `JsFooterPlugin.php` 这会影响动态块的显示。
* **MDVA-13203** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了以下问题 *完整性约束search_tmp_table* 完全重新索引后出现错误。
* **MDVA-23426** (*对于Adobe Commerce >=2.3.3 &lt;2.3.5*) — 修复了Adobe Commerce发送的通知电子邮件包含空白正文且内容被添加为附件的问题。
* **MDVA-22150** (*对于Adobe Commerce >=2.3.1 &lt;2.3.4*) — 修复了以下问题：如果在Admin中禁用了可配置产品，那么在购物车中使用可配置产品并应用优惠券的客户将无法登录。
* **MDVA-32545** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了从管理员创建订单时未自动发送发票的问题。
* **MDVA-32714** (*对于Adobe Commerce >=2.3.4 &lt;2.4.1*) — 修复了客户组价格在GraphQL产品查询中不起作用的问题。

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*对于Adobe Commerce >=2.3.2 &lt;2.4.2*) — 添加 *小计(包括 Tax)* 定价规则条件的选项。
* **MDVA-31236** (*对于Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修复了具有自定义资源访问权限的管理员无法设置2FA或登录的问题。
* **MDVA-30845** (*对于Adobe Commerce >=2.3.5 &lt;2.3.7*) — 修复了以下问题 *抱歉，目前此订单没有报价* 无法连接到UPS XML/USPS/DHL时显示错误，并且没有其他送货方法可用。
* **MDVA-32133** (*对于Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修复了在某些情况下无法从页面生成器加载媒体集的问题。
* **MDVA-12304** (*对于Adobe Commerce >=2.3.0*) — 将最大Cookie数量从50增加到200。
* **MDVA-32632** (*对于Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修复了订单显示在支付系统中，但未显示在Adobe Commerce中的问题。
* **MDVA-32449** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2，带B2B扩展*) — 修复了订单历史记录加载非常缓慢或完全不加载的问题。
* **MDVA-32739** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了启用异步电子邮件通知发送旧销售电子邮件的问题。

## v1.0.11 {#v1-0-11}

* **MC-38509** (*适用于Adobe Commerce 2.3.6和2.4.1的*) — 修复了以下问题 *创建帐户* 在更正中的无效数据后，按钮保持禁用状态 *新建客户帐户* 表单。
* **MDVA-31006** (*适用于Adobe Commerce 2.3.0和2.3.1的*) — 修复了使用下达订单后出现重复订单的问题 [!DNL Paypal Express] 付款。
* **MDVA-25602** (*适用于Adobe Commerce 2.3.0的*) — 修复的问题 [!DNL PayPal Payflow Pro] 支付方法和将Cookie处理为 `SameSite=Lax` 默认情况下，在Chrome 80浏览器和API响应中重定向到客户登录页面。

## v1.0.10 {#v1-0-10}

修补程序版本的较小修复

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*对于Adobe Commerce >=2.3.2 &lt;2.4.2*) — 修复了以下问题：具有优惠券的购物车价格规则在以下情况下不通过GraphQL应用 *整个购物车的固定金额折扣* 操作已被使用。
* **MDVA-30889** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在使用虚拟和简单产品作为选项开具捆绑包发票后发生错误的问题。
* **MDVA-31791** (*对于Adobe Commerce >=2.3.4 &lt;2.3.5*) — 在使用目标规则或链接的产品时，提高产品页面的性能。
* **MDVA-31168** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了产品导出CSV文件未显示，并且存在内存分配错误的问题。
* **MDVA-32313** (*对于Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修复了使用错误的配置选项将可配置产品添加到愿望清单中的问题。
* **MDVA-31759** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了产品未使用进行更新的问题 *下拉列表* 和 *文本区域* CSV导入期间的属性值。
* **MDVA-32012** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了韩国和阿根廷的邮政编码无法验证的问题。
* **MDVA-31640** (*对于Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) — 修复了无法通过REST API更新特殊价格的问题。
* **MDVA-28651** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0（带B2B扩展）*) — 修复了通过REST API加载可转让报价时出现性能问题的问题。

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*对于Adobe Commerce >=2.3.0 &lt;2.4.1，带B2B扩展*) — 修复了贷项通知单网格中显示错误货币符号的问题。
* **MDVA-31295** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了完成部分订购并对项目征税后不计算奖励积分的问题。
* **MDVA-30112** (*对于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了订单数超过 *束团大小* 值，Adobe Commerce会考虑以下订单： *待处理* 状态是不一致的。
* **MDVA-31150** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了以下问题：当通过Rest API调用过帐发票，并且订单由商店信用卡和礼品卡帐户部分支付时，GET发票Rest API调用未返回商店信用卡和礼品卡余额。
* **MDVA-30963** (*对于Adobe Commerce >=2.3.2 &lt;2.4.2*) — 修复了将产品筛选结果设置为仅包含为指定的值的问题 *所有商店视图* 范围中，包括在商店视图级别上覆盖值的产品。
* **MDVA-29954** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2（含B2B扩展）*) — 修复了以下问题 *新建公司注册请求* 和 *您已被链接到公司* 电子邮件是从错误的地址发送的。
* **MDVA-28357** (*对于Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) — 将标准分析器替换为带有关键字的SKU字段的自定义分析器 [!DNL ElasticSearch] 索引使通配符搜索查询适用于包含连字符(“ — ”)的SKU。

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了自定义订单状态更改为的问题 *正在处理* 在使用WebApi创建部分装运后。
* **MDVA-30428** (*对于Adobe Commerce >=2.3.4 &lt;2.3.5*) — 修复了将产品分配给自定义库存源时，客户无法将产品添加到愿望清单的问题。
* **MDVA-30594** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在配置FPT时签出期间无法保存带多个地址的订单的问题。
* **MDVA-29148** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了通过API调用（的产品自定义属性）创建产品时的问题 `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` （如Multiselect）如果在有效负载中未提供值，则类型不会使用其默认值。
* **MDVA-30837** (*对于Adobe Commerce >=2.3.1 &lt;2.3.5*) — 添加了配置设置 *含税至金额：是/否* “免运费”方法配置中的。 时间 *包括税额目标* 设置为 *是*，最小订单金额计算为小计+税。 时间 *包括税额目标* 设置为 *否*，最小订单金额计算为小计
* **MDVA-25028** (*对于Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) — 修复了使用以下方式下订单时出现的问题 [!DNL PayPal Payflow Pro] 触发欺诈过滤器时，未设置为“可疑欺诈”状态。
* **MDVA-31224** (*对于Adobe Commerce >=2.3.3 &lt;2.3.5*) — 改进性能 `catalog_product_price` 对捆绑产品执行重新索引操作。
* **MDVA-31321** (*对于Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修复以下情况时的空白页面（错误）： *全部显示* 已选中。 [!DNL Elasticsearch] 返回产品ID的大列表。 在此方案中，order by子句将转换为不正确的SQL格式。
* **MDVA-30815** (*对于Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修复了以下问题：当您更改搜索结果页面上应显示的搜索结果数量时，Adobe Commerce会显示一个空白页。 [!DNL Elasticsearch] 现在，当您更改每个页面查看的搜索结果数时，可以正确显示类别页面中的结果。
* **MDVA-30782** (*对于Adobe Commerce >=2.3.5 &lt;2.4.2*) — 修复了在不考虑购物车规则的情况下显示动态块的问题。
* **MDVA-31021** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了中存在的性能问题 `module-catalog-import-export/Model/Import/Product/Option.php`. 如果中记录超过10万条 `catalog_product_option` 表，验证具有单个产品的新CSV需要的时间少于10秒。
* **MDVA-31007** (*对于Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修复了自定义地址属性未正确显示在我的帐户区域和后端的订单详细信息页面中的问题。
* **MDVA-29389** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了高级报告的问题，其中 `analytics_collect_data` cronjob说： *必须在host参数（如localhost：3306）中配置端口*.
* **MDVA-31343** (*对于Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修复了已删除主体类的问题 `page-layout-category-full-width` 在计划类别时。
* **MDVA-30945** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在更新购物车时收到严重错误消息的问题 `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*对于Adobe Commerce >=2.3.4 &lt;2.4.0*) — 实施 *最小值应匹配* 功能和部分搜索 [!DNL Elasticsearch] 引擎。 解决了搜索查询中连字符的问题。
* **MDVA-30102** (*对于Adobe Commerce >=2.3.2 &lt;=2.4.0*) — 修复了布局缓存没有TTL时Redis缓存快速增长的问题。
* **MDVA-30599** (*对于Adobe Commerce >=2.3.4 &lt;=2.4.0*) — 修复了使用API创建的访客报价错误地标记为已登录客户的报价的问题。
* **MDVA-29446** (*对于Adobe Commerce >=2.3.3 &lt;=2.4.0*) — 修复了签出期间，不适用的配送方式价格显示为零的问题。
* **MDVA-30357** (*对于Adobe Commerce >=2.3.2 &lt;=2.4.0*) — 修复了由cron生成站点地图时创建错误图像URL的问题。
* **MDVA-30565** (*对于Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) — 修复了以下问题： *没有cartid = 0的此类实体* 如果启用了永久购物车，则在storefront结帐时为访客客户显示错误。
* **MDVA-29787** (*对于Adobe Commerce >=2.3.0 &lt;=2.4.0*) — 修复了以下情况下相关产品的目标规则不起作用的问题 *为其中之一* 条件用于定义要显示的产品。
* **MDVA-30977** (*对于Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) — 修复了重新索引后类别中随机产品缺失的问题。
* **MDVA-28202** (*对于Adobe Commerce >=2.3.4 &lt;=2.4.2*) — 修复了在使用MSI时，分层导航无法正确筛选可配置产品的问题。
* **MDVA-28300** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修复了GQL请求未反映目录价格规则中的价格更改的问题。
* **MDVA-31006** (*对于Adobe Commerce >=2.3.2 &lt;=2.4.2*) — 修复了使用下达订单后出现重复订单的问题 [!DNL Paypal Express] 付款。

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*对于Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修复了分层导航的问题，其中 *否* 在以下情况下，布尔类型产品属性的值未包含在分层导航中： [!DNL Elasticsearch] 用作搜索引擎。
* **MDVA-28191** (*对于Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修复了在通过管理员创建订单期间无法加载付款方法的问题。
* **MDVA-29959** (*对于Adobe Commerce >=2.3.0 &lt;=2.3.3-p1，带B2B扩展*) — 修复了受限管理员用户使用的问题 *公司* 不允许使用权限删除公司帐户。
* **MDVA-30265** (*对于Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修复了在创建发票后装运跟踪链接停止工作的问题。
* **MDVA-28409** (*对于Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修复了以下问题 `sales_clean_quotes` cron作业失败 *内存不足* 当数据库中的过期引号数量很大时出错。
* **MDVA-30593** (*对于Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修复了未清理根据报价生命周期设置过期的报价的问题。
* **MDVA-30107** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修复了当存储视图使用不同的基本URL时，存储切换器无法按预期工作的问题。
* **MDVA-28763** (*对于Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修复了使用REST API多次更新产品信息后产品图像复制的问题。
* **MDVA-30284** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了目录搜索索引器由于以下原因而失败的问题 *[!DNL Elasticsearch]错误：已超过索引中字段总数的限制。*
* **MDVA-29042** (*对于Adobe Commerce >=2.3.3 &lt;=2.3.4-p2，带B2B扩展*) — 修复了目录权限更改为的问题 *允许* 在将新产品添加到共享目录后自动更新。
* **MDVA-30428** (*对于Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修复了将产品分配给自定义库存源时，客户无法将产品添加到愿望清单的问题。
* **MDVA-28661** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2，带有B2B扩展*) — 修复了在更改公司管理员后，“公司用户”公司帐户部分中引发错误的问题。

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*对于Adobe Commerce 2.3.1 - 2.3.4-p2*) — 修复了数据库名称太长时cron作业失败，从而导致类别无法在前端更新的问题。
* **MDVA-30106** (*适用于Adobe Commerce ^2.3.0的*) — 修复了结账过程中付款无法加载的问题 *无法读取null的属性&#39;length&#39;* JS控制台中出错。
* **MDVA-28656** (*对于Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) — 修复了以下问题：如果下订单时不需要付款信息（例如，100%折扣），并且为订单创建了发票，则订单状态将更改为 *已关闭* 而不是“完成”。
* **MDVA-30209** (*对于Adobe Commerce 2.3.0 - 2.3.3-p1*) — 修复了客户更新其帐户信息时客户组更改为默认的问题。
* **MDVA-30123** (*对于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了无法为GraphQL查询正确翻译属性选项标签的问题。
* **MDVA-29996** (*对于Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修复了在启用类别权限后，类别页面未被完整页面缓存的问题。
* **MDVA-30164** (*对于Adobe Commerce >=2.3.1 &lt;2.4.2*) — 修复了存在自定义客户属性时无法从客户网格导出客户记录的问题。
* **MDVA-30444** (*对于Adobe Commerce >=2.3.0 &lt;2.4.1*) — 修复了使用GraphQL下订单时不会发送确认电子邮件的问题。
* **MDVA-30490** (*对于Adobe Commerce 2.3.4 - 2.3.5-p2*) — 修复了以下问题：如果其中一个产品的简短描述为空，则产品比较会引发500错误页面。
* **MDVA-30232** (*对于Adobe Commerce >=2.3.1 &lt;2.4.1*) — 修复了原始订单包含礼品卡时无法重新订购的问题。
* **MDVA-29965** (*对于Adobe Commerce >=2.3.3 &lt;2.4.0*) — 修复了将产品添加到购物车时，客户收到“表单密钥无效”错误的问题。
* **MDVA-30008** (*对于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了无法通过管理员API为公共目录中的产品下订单的B2B问题。
* **MDVA-22469** (*适用于Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) — 修复了升级到Adobe Commerce 2.3.3后，Page Builder在“管理”面板中无法正常工作以及某些JS和CSS文件未加载的问题。
* **MC-35984** (*对于Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修复了商家为退货授权(RMA)创建配送标签后无法与退货页面上的任何页面元素交互的问题。

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*适用于Adobe Commerce 2.3.0的 — 2.3.4*) — 修复了的问题 [!DNL PayPal Payflow Pro] 支付方法和将Cookie处理为 `SameSite=Lax` 默认情况下，在Chrome 80浏览器和API响应中重定向到客户登录页面。
* **MDVA-26694** (*对于Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) — 修复了产品和目录缓存每天过期的问题，但过期时间安排各不相同。
* **MDVA-27825** (*对于Adobe Commerce >=2.3.0 &lt;2.4.1*) — 修复了因内存泄漏导致导出大量数据失败的问题。
* **MDVA-29085** (*对于Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) — 修复了通过API创建公司时不会发送任何所需新公司电子邮件的B2B问题。
* **MDVA-29344** (*对于Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) — 修复了将文本从标题元素复制到文本元素后页面生成器卡住的问题。
* **MDVA-29835** (*适用于Adobe Commerce的>2.3.1 &lt;2.4.2*) — 修复了礼品卡订单包含两个代码而不是一个代码的问题。
* **MDVA-30052** (*对于Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) — 修复了专用内容（本地存储）未正确填充，从而导致性能问题的问题。
* **MDVA-30131** (*对于Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修复了分层导航的问题，其中 *否* 在以下情况下，布尔类型产品属性的值未包含在分层导航中： [!DNL Elasticsearch] 用作搜索引擎。
* **MDVA-35514** (*对于Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修复了在“创建软件包”模式窗口中创建送货标签并将订购的产品添加到软件包时出现的问题。
