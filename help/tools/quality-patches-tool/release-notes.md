---
title: 发行说明
description: 了解Adobe Commerce可用的修补程序以及它们解决的问题。
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '20485'
ht-degree: 0%

---

# 发行说明

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches)提供了由Adobe和Magento Open Source团体开发的各个修补程序。 它允许您应用、还原和查看有关已安装Adobe Commerce版本可用的所有单个修补程序的一般信息。 无论谁开发了修补程序，您都可以将修补程序应用到Adobe Commerce和Magento Open Source项目。 例如，您可以将社区开发的修补程序应用于Adobe Commerce项目。

>[!INFO]
>
>有关将修补程序应用于Adobe Commerce项目的说明，请参阅[应用修补程序](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches)。 请参阅“软件更新指南”中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)，以查看已发布修补程序的完整列表。

>[!INFO]
>
>有关社区为Magento Open Source而创建的[!DNL quality patches]的信息，请参阅[发行说明](https://github.com/magento/quality-patches/blob/master/community-release-notes.md)。

## v1.1.48 {#v1-1-48}

* **ACSD-55566**(对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在合并具有相同捆绑项目的源和目标购物车时，[!DNL GraphQL]响应中的`mergeCart`突变失败并出现“*内部服务器错误*”的问题。
* **ACSD-56546**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了当&#x200B;**显示缺货产品配置**&#x200B;为&#x200B;*已禁用*&#x200B;时，可配置和捆绑产品在店面中显示为&#x200B;**缺货**&#x200B;的问题。
* **ACSD-56635**(对于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了在将&#x200B;**帐户共享**&#x200B;设置为&#x200B;*全局*&#x200B;的情况下使用导入时，导入的客户使用同一电子邮件地址复制的问题。
* **ACSD-56741**(对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了错误消息“*尝试访问在`setup:upgrade`期间显示的null*&#x200B;类型的值上的数组偏移”，当数据库包含与索引机制和[!DNL MView]无关的自定义[!DNL MySQL]触发器时。
* **ACSD-57315**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了每次在Admin中的&#x200B;**[!UICONTROL View transaction]**&#x200B;屏幕上单击[!UICONTROL Fetch]按钮时在[!DNL PayPal Payflow Pro]中创建新事务时的问题。
* **ACSD-57337**(对于Adobe Commerce >=2.4.4 &lt;2.4.6) — 修复了具有特定网站访问限制的管理员用户能够查看&#x200B;**[!UICONTROL Companies]**&#x200B;网格中所有网站的公司的问题。
* **ACSD-57394**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了[!DNL GraphQL]中按多个排序字段对产品排序不正确的问题。
* **ACSD-57565**(对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了在更新时间段之前&#x200B;**[!UICONTROL Order]**&#x200B;功能板显示错误订单信息的问题。 现在，仪表板在首次加载时显示正确的订单统计信息。
* **ACSD-57854**(对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了产品[!DNL GraphQL]请求在类别聚合中返回禁用类别的问题。
* **ACSD-58008**(对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了在未指定结束日期的情况下，更新计划更新会删除暂存项目的先前版本的问题。
* 更新的修补程序：MDVA-39305-V2、ACSD-48627、ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了在使用多个地址进行签出时，*[!UICONTROL Used]*&#x200B;和&#x200B;*[!UICONTROL Times Used]*&#x200B;属性显示生成的赠券的不正确值的问题。
* **ACSD-56760**(适用于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了以下问题：如果Webstore具有自己的根类别，则仅限特定网站的管理员用户无法对类别内的产品进行排序或添加新产品。
* **ACSD-56858**(适用于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了受限制公司管理员的B2B公司角色权限显示不正确的问题。
* **ACSD-57074**(对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了以`price_`开头的`attrbute_code`的&#x200B;*是/否*&#x200B;自定义属性无法正确处理索引的问题，并且具有此类属性的产品在前端不可用。
* 更新的修补程序：ACSD-53378、ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767**(适用于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了在库存数量更改时，即使产品仍有库存，类别页面缓存也会失效的问题。
* **ACSD-54656**(适用于Adobe Commerce >=2.4.5 &lt;2.4.6) — 修复了在签出期间不可见的Recaptcha失败，从而阻止下达订单的问题。
* **ACSD-55100**(对于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了GraphQL在搜索结果中返回的产品不超过10,000的问题。
* **ACSD-56621**(对于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了更新的名字和姓氏未反映在公司管理员用户的问候语标头部分中的问题。
* **ACSD-56842**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了在运行`setup:di:compile`后缺少延迟代理和延迟代理工厂的问题。
* **ACSD-57003**(对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了订单部分退款或部分发运时，订单状态更改为&#x200B;*[!UICONTROL Complete]*&#x200B;而不是更改为&#x200B;*[!UICONTROL Processing]*&#x200B;的问题。
* 更新的修补程序：ACSD-50260-v2、ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886**(适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了计划更新禁用了两个子产品之一时，可配置产品缺货的问题。
* **ACSD-56616**(适用于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了捆绑产品在其简单产品缺货时在店面显示为有货的问题。
* **ACSD-56515**(对于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了具有网站级别权限的管理员无法添加或编辑动态块的问题。
* **ACSD-56447**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了通过并行REST Web API请求将同一产品添加到购物车中导致购物车中有两个单独项目的问题。
* **ACSD-56415**(对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了在数据库包含大量要索引的部分价格数据时，由于`DELETE`查询而导致部分价格索引的性能变慢的问题。
* **ACSD-54965**(适用于Adobe Commerce >=2.4.5 &lt;2.4.6) — 修复了将产品仅分配给自定义库存时，可视化促销网格不显示正确库存的问题。
* **ACSD-52824**(适用于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了在公司设置中禁用此类付款方法时，向公司客户显示PayPal Express、Google Pay和Apple Pay按钮的问题。
* 更新的修补程序： ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790**(对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了在使用&#x200B;**从库存中移动到底部**&#x200B;选项对产品进行分类时，用户被重定向到管理员功能板并且`Invalid security or form key. Please refresh the page`错误显示在屏幕顶部的问题。
* **ACSD-56280**(对于Adobe Commerce >=2.4.4 &lt;2.4.7) — 修复了从礼品注册表中订购商品会导致异常的问题。
* **ACSD-56246**(适用于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了在产品的计划更新生效时从自定义多选属性中删除数据的问题。
* **ACSD-56193**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4) — 修复了在使用页面生成器的类别描述中使用计划块时Varnish/Fastly缓存未更新的问题。
* **ACSD-56158**(对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了“购物车”查询返回每个税则的总税值的问题。
* **ACSD-56023**(适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了在启用缓存后，CMS页面上的小组件内容未更新的问题。
* **ACSD-55427**(对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了管理员用户无法从管理员的产品页面中取消分配共享目录中的产品的问题。
* **ACSD-55352**(适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了在使用客户奖励积分创建部分贷项通知单之后，订单状态更改为“已关闭”并且贷项通知单选项从“管理员”订单页中消失的问题。
* **ACSD-55231**(对于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了无法使用快速订购功能将产品添加到购物车的问题。
* **ACSD-54283**(对于Adobe Commerce >=2.4.3 &lt;2.4.4) — 修复了以下问题：未分配给默认共享目录（常规组）的产品/类别仍包含在XML Sitemap中。
* 更新的修补程序：ACSD-52041、ACSD-54040、ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了在更改类别URL后规范类别URL未更新的问题。
* **ACSD-53636**(适用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5) — 修复了具有具有特价子产品的可配置产品的产品列表页面上未显示常规价格的问题。
* **ACSD-54885**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了当管理员用户使用&#x200B;*以客户身份登录*&#x200B;功能时多个地址签出的问题。
* **ACSD-55610**(适用于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了部分取消的订单折扣金额不正确的问题。
* **ACSD-55334**(适用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 通过GraphQL响应中的翻译词典修复标签的翻译。
* **ACSD-54739**(对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了产品库存状态条件未应用于相关产品规则的问题。
* **ACSD-53925**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了当`catalog_product_price` dimensions-mode设置为&#x200B;*website*&#x200B;时，管理员无法通过产品轮播保存CMS块的问题。
* **ACSD-52714**(适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了将日期格式设置为&#x200B;*Y-m-d*&#x200B;时，日期过滤器在管理网格中不起作用的问题。
* **ACSD-55055**(适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 提高在购物车的购物车价格规则中加载产品属性的性能。
* **ACSD-53790**(对于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了通过REST API为单个产品创建多个RMA的问题。
* **ACSD-56090**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5) — 修复了GraphQL请求响应所有商店的数据而非专门请求的商店数据的问题。
* **ACSD-54983**(适用于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了当用户状态设置为&#x200B;*[!UICONTROL Inactive]*&#x200B;时，无法通过GraphQL请求获取公司用户UID的问题。
* **ACSD-53309**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了在选择可自定义选项时，*[!UICONTROL Regular Price]*&#x200B;标签中未完全应用税的问题。
* **ACSD-55305**(对于Adobe Commerce >=2.4.4 &lt;2.4.7) — 修复了屏幕加载器冻结&#x200B;**[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]**&#x200B;页面上的&#x200B;*[!UICONTROL Edit Company User]*&#x200B;弹出窗口的问题。
* 更新的修补程序： ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了&#x200B;*[!UICONTROL Recently Viewed]*&#x200B;产品数据在Store视图中无法正确更新的问题。
* **ACSD-54626**(对于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了无法通过[!DNL GraphQL]创建具有`NUMBER_OF_SKUS`属性的新采购订单规则(`createPurchaseOrderApprovalRule`)的问题。
* **ACSD-53845**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了`consumer max_messages` = 0时的[!DNL MySQL]连接超时问题。
* **ACSD-54890**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了由于`/tmp`磁盘空间不足导致`aggregate_sales_report_bestsellers_data`导致[!DNL MySQL]错误的问题。
* **ACSD-55112**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了在没有[!DNL Google reCAPTCHA v3]验证的情况下多次单击&#x200B;*[!UICONTROL Submit review]*&#x200B;按钮的问题。
* **ACSD-54264**(对于Adobe Commerce >=2.4.4-p5 &lt;2.4.5) || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) — 修复了错误消息&#x200B;*“您无法更新请求的属性”的问题。 当客户尝试从其他商店视图中用可转让报价结帐时，将显示行ID： store_id“*”。
* **ACSD-54418**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了固定折扣额错误地应用于动态定价捆绑包的每个子产品的问题。
* **ACSD-55238**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了保存空产品&#x200B;*[!UICONTROL Meta Description]*&#x200B;的问题。
* **ACSD-54966**(适用于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了在上一个订单失败时，无法重用每个客户限量使用的优惠券代码的问题。
* **ACSD-54060**(对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了受限制的管理员无法保存属于已分配到其他作用域的其他产品的子产品的问题。
* **ACSD-48910**(适用于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了在为订单开票和发运订单后，分配给多个来源的捆绑产品出现缺货的问题，即使该订单仍然具有非零数量。
* **ACSD-55381**(对于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了通过[!DNL GraphQL]从[!DNL B2B] *[!UICONTROL Requisition list]*&#x200B;查询`configurable_product_option_uid`和`configurable_product_option_value_uid`字段时出现的内部服务器错误。
* **ACSD-55628**(对于Adobe Commerce >=2.4.4-p2 &lt; 2.4.5) || >=2.4.5-p1 &lt; 2.4.6) — 修复了在公司注册表中上传文件的操作，以及替换店面中客户属性的文件的操作。
* 更新的修补程序：ACSD-51240、ACSD-51890、ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376**(适用于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了在将产品添加到购物车后，将产品从共享目录中删除时购物车中出现的问题。
* **ACSD-53722**(对于Adobe Commerce >=2.4.4 &lt;2.4.7) — 修复了当其他范围的计划更新生效时，捆绑产品选项价格更改为$0的问题。
* **ACSD-53643**(适用于Adobe Commerce >=2.4.3 &lt;2.4.7) — 修复了在订购禁用或缺货产品的采购订单时，订单总计不正确的问题。 通过隐藏此类采购订单的&#x200B;*[!UICONTROL Place Order]*&#x200B;按钮可修复此问题。
* **ACSD-54067**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了产品视频无法在移动设备上播放的问题。
* **ACSD-55414**(用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 在MariaDB尝试将EAV entity_id从字符串转换为整数时提高性能。
* **ACSD-51819**(对于Adobe Commerce >=2.4.4 &lt;2.4.4-p4) — 修复了可使用同一报价ID下达多个订单的问题。
* **ACSD-53118**(对于Adobe Commerce >=2.4.0 &lt;2.4.7) — 修复了以下问题：当产品具有空属性时，使用优惠券代码应用&#x200B;*[!UICONTROL Cart Price Rule]*。
* **ACSD-54324**(对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了GraphQL requisition_lists请求不考虑分页设置并返回所有结果的问题。
* 更新的修补程序： MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680**(适用于Adobe Commerce >=2.4.0 &lt;2.4.6) — 修复了无法处理为具有多个已分配来源的产品提交的B2B报价的问题。
* **ACSD-54040**(对于Adobe Commerce >=2.4.4-p5 &lt;2.4.5) || >=2.4.5-p4 &lt;2.4.6) — 修复了在启用B2B模块时，按顺序详细信息中&#x200B;*[!UICONTROL Created]*&#x200B;字段为空的问题。
* **ACSD-54319**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了&#x200B;*[!UICONTROL Product in Cart]*&#x200B;报表中产品价格为零的问题。
* **ACSD-53378**(对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 为拥有大地址簿的客户缩短结帐页面加载时间。
* **ACSD-52657**(适用于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了在使用子域的二级商店中未更新minicart的问题。
* **ACSD-53414**(对于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了受限管理员用户在其权限范围之外查看CMS页面的问题。
* **ACSD-54472**(对于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了以下问题：被拒绝公司的客户仍然可以进行身份验证，被阻止和被拒绝公司的客户仍然可以下订单。 该修补程序添加了对GraphQL端点的其他验证。
* **ACSD-52801**(适用于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 添加了在GraphQL中搜索产品时进行部分匹配的选项。
* **ACSD-55004**(对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了在上传大于`php.ini`中配置的值的导入文件时，验证器崩溃的问题。
* **ACSD-54989**(对于Adobe Commerce >=2.4.4-p5 &lt;2.4.5) || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) — 修复了当&#x200B;*[!UICONTROL Enable Purchase Orders]*&#x200B;设置为&#x200B;*[!UICONTROL Yes]*&#x200B;且&#x200B;*[!UICONTROL Purchase Order]*&#x200B;设置为&#x200B;*[!UICONTROL No]*&#x200B;时，公司管理员无法下订单的问题。
* **ACSD-54007**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了在导入客户数据时出现的错误&#x200B;*“未定义数组键“_scope”*。
* **ACSD-55031**(对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了在编译期间&#x200B;*类型“混合”不能为nullable*&#x200B;错误。
* **ACSD-54961**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了受限管理员用户无法批量更新&#x200B;*产品评论*&#x200B;状态的问题。
* **ACSD-55256**(对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了图像滑块中仅成功显示第一个图像的问题。
* 更新的修补程序：ACSD-52041、ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704**(适用于Adobe Commerce >=2.4.0 &lt;2.4.7) — 修复了在奖励点过期后错误地计算奖励点余额历史记录的问题。
* **ACSD-53583**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 改进了&#x200B;*类别产品*&#x200B;和&#x200B;*产品类别*&#x200B;索引器的部分重新索引性能。
* **ACSD-54026**(对于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了针对非授权用户的`updateCompanyRole` GraphQL请求的不正确错误消息。
* **ACSD-54106**(对于Adobe Commerce和Magento Open Source >=2.4.1 &lt;2.4.5) — 修复了按名称对土耳其语重音字符进行类别产品排序不正确的问题。
* **ACSD-52219**(适用于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了在书签视图之间频繁切换时，管理员网格保存的过滤器无法按预期工作的问题。
* **ACSD-54342**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了错误的错误消息&#x200B;*数据结构中的错误：导入没有有效数据的CSV文件时，值会混合*。
* **ACSD-54660**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 添加了新输入属性&#x200B;*sort*，以便按`sort_field`和`sort_direction`对GraphQL中的客户订单进行排序。
* **ACSD-54776**(对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了为第二个网站、商店和商店视图保存未选中的&#x200B;*[!UICONTROL Use Default Value]*&#x200B;和非默认产品字段值的问题。
* **ACSD-53998**(对于Adobe Commerce和Magento Open Source>=2.4.4-p2 &lt;2.4.5) || >=2.4.5-p1 &lt;2.4.7) — 修复了从客户帐户注销后，基于&#x200B;**[!UICONTROL Customer Segment]**&#x200B;的&#x200B;**[!UICONTROL Dynamic Block]**&#x200B;无法正常工作的问题。
* **ACSD-53204**(对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复&#x200B;*无法保存产品。使用`rest/V1/products/<sku>/media`端点向产品库添加图像的并发请求时出现*&#x200B;错误。
* **ACSD-47657**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 为AWS凭据添加了缓存机制。 凭据提供程序现在使用Magento缓存来缓存从AWS检索到的凭据以进行EC2配置。
* 更新了修补程序：ACSD-51984、ACSD-51574。

## v1.1.38 {#v1-1-38}

* **ACSD-53098**(适用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4) — 修复了在执行部分索引时，分配给共享目录的产品未显示在店面中的问题。
* **ACSD-54018**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了在构件条件中使用非全局属性的[!UICONTROL Product List]构件的性能问题。
* **ACSD-54111**(适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了以下问题：当水印图像的宽高比与产品图像不匹配时，店面不会显示产品缩略图图像。
* **ACSD-47669**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了&#x200B;*完整性约束冲突： 1452无法添加或更新子行：导入产品CSV时外键约束失败*&#x200B;错误。
* **ACSD-53347**(适用于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了价格索引器执行时间过长的问题。
* **ACSD-52287**(对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了在启用异步网格索引时，归档订单网格中的订单状态不正确的问题。
* **ACSD-52929**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了在异步模式下配置库存索引器时重新索引默认源项目的多余请求的问题。
* **ACSD-53824**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了`setup:upgrade`期间`UpdateMultiselectAttributesBackendTypes`迁移数据修补程序超出数据库事务大小限制的问题。

## v1.1.37 {#v1-1-37}

* **ACSD-52613**(对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了即使REST API没有对`Inventory_source`项目进行任何更新，缓存和索引也会被刷新的问题。
* **ACSD-51884**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了在运行resize命令后，产品图像缓存路径不正确的问题。
* **ACSD-53628**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了CSV销售订单报表显示错误的特殊字符的问题。
* **ACSD-53148**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了以下问题：GraphQL中有关将同一可配置产品添加到购物车的两个并行请求在购物车上产生了具有相同产品SKU的两个单独项目。
* **ACSD-52606**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了以下问题：用户单击&#x200B;**[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;时，显示错误消息&#x200B;*您的订单未做好取货准备*。
* **ACSD-51574**(适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了将图像替换为同名其他图像后，图像未在前端更新的问题。
* **ACSD-53728**(适用于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了产品EAV索引器需要更长时间才能完成的问题。
* **ACSD-53979**(适用于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了当欢迎消息包含单引号时主页出现的JS问题。
* **ACSD-52085**(适用于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了在产品的传送中看不到具有特殊价格的可配置产品的问题。
* **ACSD-53795**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了`indexer_update_all_views` cron作业中数据类型无效的问题。
* **ACSD-52143**(适用于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了导入产品后删除自定义选项的问题。
* **ACSD-53750**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了在多线程`catalog_product_price`重新索引期间出现&#x200B;*管道破裂或连接关闭*&#x200B;错误的问题。
* **ACSD-49843**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.0) || >=2.4.1 &lt;2.4.7) — 修复了在启用&#x200B;**[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**&#x200B;设置的情况下通过在线付款方法自动对订购的项目开票后，产品下载链接不可用的问题。
* **ACSD-47054**(对于Adobe Commerce >=2.4.2 &lt;2.4.6) — 修复了预览重新索引为所有商店运行重新索引，从而导致速度缓慢的问题。
* 添加了ACSD-46541、ACSD-47079的新版本。
* 已将ACSD-49970-v3替换为ACSD-54095。

## v1.1.36 {#v1-1-36}

* **ACSD-53239**(对于Adobe Commerce和Magento Open Source>=2.4.3 &lt; 2.4.6) — 修复了清单索引器在“按计划更新”模式下清理所有缓存的问题。
* **ACSD-50887**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了产品属性&#x200B;*[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;可以设置为&#x200B;*是*，而非&#x200B;*[!UICONTROL Use in search]*&#x200B;选项设置为&#x200B;*是*&#x200B;的问题。
* **ACSD-51846**(对于Adobe Commerce和Magento Open Source>=2.4.3-p2 &lt;2.4.6) — 修复了由于并非所有级别的REST API有效负载都经过验证而发生的&#x200B;*内部错误*&#x200B;问题。
* **ACSD-52906**(对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了以下问题：属于同一客户区段的已登录客户的X-Magento差异Cookie设置不正确，从而导致某些页面的缓存不正确。
* **ACSD-52736**(适用于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了包含可配置产品数量要求的&#x200B;*购物车价格规则*&#x200B;无法按预期工作的问题。
* **ACSD-47875**(适用于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了以下问题：管理员用户无法从管理员将产品添加到具有库存管理的特定商店视图范围内的客户购物车。
* **ACSD-53176**(对于Adobe Commerce >=2.3.7 &lt;2.4.5) — 修复了&#x200B;*包含*&#x200B;的“相关产品规则”*是*&#x200B;条件中的一个，但与产品不匹配的问题。
* **ACSD-51666**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了错误&#x200B;*会话已过期，请重新登录。在客户尝试登录后发生的*。
* 添加了MDVA-39305-v2的新版本。
* 更新了ACSD-19640的要求。

## v1.1.35 {#v1-1-35}

* **ACSD-51899**(适用于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.7) — 修复了使用之前选择的店内收取地址自动填充结账配送步骤上的默认配送地址的问题。
* **ACSD-52041**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了错误消息&#x200B;*[ERROR] [!DNL Page Builder]呈现5秒且未释放锁定的问题。保存使用[!DNL Page Builder]编辑的内容时，Chrome浏览器中会显示*。
* **ACSD-52095**(适用于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了在产品导出后CSV文件中`manage_stock`值未正确设置为0的问题。
* **ACSD-51358**(对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了以下问题：删除没有结束日期的计划更新会导致删除同一实体的其他计划更新。
* **ACSD-48070**(对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了编辑计划更新会触发异常的问题。
* **ACSD-51890**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了在没有[!DNL Google reCAPTCHA] v3验证的情况下多次单击[!UICONTROL Submit review]按钮的问题。
* **ACSD-51984**(对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了为第二个网站、商店和商店视图保存未勾选的&#x200B;*[!UICONTROL Use Default Value]*&#x200B;和&#x200B;*[!UICONTROL non-default product field]*&#x200B;值的问题。
* **ACSD-52398**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了错误&#x200B;*请求的数量不可用*，在尝试更新店面购物车中捆绑产品的数量时会发生此错误。
* **ACSD-52786**(适用于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了目录规则条件&#x200B;*SKU为*&#x200B;的问题，该条件适用于以给定SKU开始的所有产品。
* **ACSD-52921**(适用于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了在购物车中拥有缺货的可配置产品时从GraphQL请求购物车详细信息时出现内部错误的问题。
* **ACSD-51683**(适用于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了使用GraphQL时无法将可自定义选项添加到购物车的问题。
* **ACSD-52133**(适用于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了在升级后无法保存客户帐户的问题。
* **ACSD-52202**(适用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在订单履行中，当非默认库存更改为0数量时，默认库存的可销售数量错误地更改为0的问题。
* **ACSD-51265**(适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了系统中捆绑产品过多时的`catalog_product_price`重新索引性能问题。
* **ACSD-52831**(对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了在启用[!DNL Google reCAPTCHA v3 Invisible]时客户无法下可转让报价单的问题。
* **ACSD-51845**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了无法通过异步批量REST API更新具有层价格和其他属性集的后续产品的问题。
* **ACSD-52815**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了非默认来源的数量字段输入最多只支持6位数的问题，默认库存不支持8位。
* **ACSD-51149**(对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了已启用目录权限的计划导入导出使索引器失效，然后通过cron缓存刷新的问题。
* **ACSD-50815**(对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了简单产品的小数数量不能用于新的捆绑产品选项的问题。
* ACSD-47803的更新版本。
* 更新了ACSD-51892的标题。
* 更新了ACSD-51379。
* 更新了ACSD-49970-v2。

## v1.1.34 {#v1-1-34}

* **ACSD-52277**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了在Admin中创建新订单时，管理员用户在选择商店视图后未正确重定向的问题。
* **ACSD-50813**(对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了以下问题：管理员无法在具有[!UICONTROL Add Products by SKU]功能的SKU中将包含斜杠的捆绑产品添加到管理员订单中。
* **ACSD-51630**(适用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了大量系统消息导致管理员页面下载速度缓慢的问题。
* **ACSD-51853**(对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.7) — 修复了在使用[!UICONTROL Page Builder]时未应用复制的文本样式的问题。
* **ACSD-52160**(适用于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了以下问题：根据购物车价格规则，产品验证结果未根据规则条件“如果在购物车中找到/未找到项目，且所有/任何这些条件均为true”进行正确评估。
* **ACSD-51636**(对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了以下问题：公司管理员尽管拥有所有必要的角色和权限，仍无法从客户帐户部分添加新用户。
* **ACSD-51739**(对于Adobe Commerce >=2.4.6 &lt;2.4.7) — 修复了在CompanyTeam GraphQL请求中请求`structure_id`时返回错误的问题。
* **ACSD-51857**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了大型sales_order和`sales_order_item`数据库表上的`aggregate_sales_report_bestsellers_data` cron报告由于主数据查询的写入方式而性能缓慢的问题。
* **ACSD-48448**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了在订单取消期间发生争用条件问题，从而导致`inventory_reservation`表中出现重复条目的问题。
* **ACSD-52689**(适用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.6) — 修复了使用REST API无法将图像上传到Amazon S3存储的问题。
* **B2B-2674**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 将缓存功能添加到1customAttributeMetadata1 GraphQL查询。
* 添加了新版本的ACSD-44938。
* 添加了ACSD-46988的要求。

## v1.1.33 {#v1-1-33}

* **ACSD-50478**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5) — 修复数据库转储包含触发器和&#x200B;*分隔符* SQL命令时的数据库回滚命令。
* **ACSD-50512**(对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了&#x200B;*错误：可下载链接与产品无关。 请验证链接并重试。更新可下载产品暂存更新的开始日期时发生*&#x200B;错误。
* **ACSD-50949**(适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了与SKU筛选器一起使用时，高级搜索中的价格筛选器无法返回正确结果的问题。
* **ACSD-51645**(对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了在禁用扩展`Magento_OfflineShipping`的情况下保存新的购物车价格规则时引发的错误。
* **ACSD-50895**(对于Adobe Commerce >=2.4.5 &lt;2.4.7) — 修复了未配置[!DNL Google Analytics] 4 GTM时未触发[!DNL Google Analytics] 3 GTM标记的问题。
* **ACSD-51102**(适用于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了在计划更新启用目录规则时，应用于大量产品的目录规则未正确索引的问题。
* **ACSD-50368**(适用于Adobe Commerce和Magento Open Source>= 2.4.3 &lt;2.4.5) — 修复了在通过异步REST API或异步批量REST API创建客户时忽略客户的`group_id`的问题。
* **ACSD-51497**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.0) || >= 2.4.1 &lt;2.4.7) — 修复了客户无法按下拉列表类型的自定义属性对目录页面进行排序的问题。
* **ACSD-51408**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt; 2.4.7) — 修复了订单项状态错误设置为&#x200B;*[!UICONTROL Backordered]*&#x200B;的问题。
* **ACSD-51735**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 修复了当产品库存为&#x200B;*0*&#x200B;时，订单项状态被错误地设置为&#x200B;*[!UICONTROL Ordered]*&#x200B;的问题。
* **ACSD-51792**(对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了在启用[!DNL Google Tag Manager] 4时页面没有展示次数事件的问题。
* **ACSD-51471**(对于Adobe Commerce >=2.4.3 &lt;2.4.7) — 修复了以下问题：对于使用简单产品的捆绑产品，管理员用户无法为其保存计划更新，而该产品本身具有计划更新。
* **ACSD-51700**(适用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在管理员的可下载产品编辑页面上切换商店视图时发生的错误。
* **ACSD-51120**(对于Adobe Commerce >=2.3.7 &lt;2.4.3) — 修复了以下问题：对于包含通过暂存更新更新更新的CMS块的CMS页面，未清除GraphQLGET请求的缓存。
* **ACSD-51240**(对于Adobe Commerce >=2.4.4 &lt;2.4.6) — 修复了通过公司注册表进行注册时上传文件缺失的问题。
* **ACSD-51907**(对于Adobe Commerce >=2.4.2 &lt;2.4.3) — 修复了受限管理员用户无法创建包含离线退款的贷项通知单的问题。
* **ACSD-52148**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 修复了[!DNL Google V3 reCAPTCHA]管理员登录偶尔失败的问题。
* **ACSD-51431**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了即使更改日志中没有新条目，索引器状态为&#x200B;*正在工作*&#x200B;的问题。
* **ACSD-51892**(对于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了配置文件加载多次的性能问题。
* 已弃用ACSD-51114。

## v1.1.32 {#v1-1-32}

* **ACSD-49628**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了[!UICONTROL Page Builder's]多个错误阻止管理员保存没有内容权限的产品的问题。
* **ACSD-51305**(适用于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了缺货可配置子产品在GraphQL响应中不可用的问题。
* **ACSD-50621**(适用于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了在多网站环境中尝试编辑共享目录中的其他网站时，这些网站的[!UICONTROL Tier Prices]不可见的问题。
* **ACSD-51041**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.0) || >=2.4.1 &lt;2.4.6) — 提高价格索引器的性能。
* **ACSD-51379**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了通过[!UICONTROL Page Builder]对页面文本内容所做的更改未保存的问题。
* **ACSD-49480**(适用于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了仅将一个购物车价格规则应用于购物车的问题。
* **ACSD-51230**(适用于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了在处理订单中简单产品的部分退款时删除礼品卡帐户的问题。
* **ACSD-51238**(适用于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 修复了在更新可配置产品和编辑价格时删除库存来源的问题。
* **ACSD-50794**(适用于Adobe Commerce >=2.4.1 &lt;2.4.7) — 修复了通过GraphQL删除礼品消息或礼品包装时，数据库中未更新礼品消息或礼品包装详细信息的问题。
* **ACSD-51528**(对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了&#x200B;*sales_order*&#x200B;表中&#x200B;*x_forwarded_for*&#x200B;列具有null值的问题。
* **ACSD-50849**(适用于Adobe Commerce >=2.4.4 &lt;2.4.6) — 修复了在清除缓存后将新产品添加到类别导致现有产品的位置和选择不匹配的问题。
* **ACSD-51294**(对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了GTM/GA价格、数量、税务、配送和收入作为字符串发送到[!DNL Google Analytics]和GTM的问题。
* **ACSD-51204**(适用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在创建贷项通知单后完全销售的产品未返回库存的问题。
* **ACSD-51291**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.4-p4) || >=2.4.5 &lt;2.4.5-p3) — 修复了以下问题：如果管理员限制只能访问一个网站，则可以将图像/视频添加到已分配给多个网站的产品。
* 添加了新版本的ACSD-50336。
* 已更换ACSD-49970修补程序。

## v1.1.31 {#v1-1-31}

* **ACSD-50345**(对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4) || >=2.4.4-p1 &lt;2.4.6) — 修复了Recaptcha v2在提交失败的付款后未重新加载的问题。
* **ACSD-50817**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 优化了Cron作业`sales_clean_quotes`以更快地运行。
* **ACSD-49392**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.0) || >= 2.4.1 &lt;2.4.7) — 修复了在对捆绑产品进行部分退款后，订单状态更改为已关闭的问题。
* **ACSD-51036**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 修复了在并发REST API调用期间出现的争用条件导致[!UICONTROL Items Ordered]表中装运状态信息覆盖的问题。
* **ACSD-50858**(适用于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 提高加载横幅内容的性能。
* 添加了新版本的MDVA-39305-v2、ACSD-45169。
* 更新了ACSD-50260-v2修补程序。

## v1.1.30 {#v1-1-30}

* **ACSD-50336**(对于Adobe Commerce和Magento Open Source>=2.4.4-p1 &lt;2.4.4-p3) — 修复了在产品重新上架或价格更改时不会发送产品警报电子邮件的问题。
* **ACSD-50367**(适用于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了在创建不含值的多选客户地址属性时，客户地址导出无法正常工作的问题。
* **ACSD-49877**(适用于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了当视频直接链接到远程视频文件而不是流服务时，视频自动播放在移动设备[!DNL Safari]上不起作用的问题。
* **ACSD-50165**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了错误&#x200B;*无法删除该文件。 警告！unlink：从Admin刷新JS/CSS缓存时没有此类文件或目录*。
* **ACSD-49737**(适用于Adobe Commerce和Magento Open Source>=2.4.1-p1 &lt;2.4.7) — 修复了在卡付款失败后优惠券被错误地标记为使用的问题。
* **ACSD-50814**(适用于Adobe Commerce和Magento Open Source>=2.4.6 &lt;2.4.7) — 修复了管理员用户无法创建贷项通知单的问题。
* **ACSD-50116**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了管理员用户无法为子类别级别3或更低级别创建URL重写的问题。
* **ACSD-49513**(对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5) — 修复了远程存储同步因0字节文件而失败的问题。
* **ACSD-46683**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了配送价格显示&#x200B;*尚未计算的问题*。
* **ACSD-49129**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了`rest/V1/products/sku/media`产品媒体API响应中未返回&#x200B;*[!UICONTROL content]*&#x200B;属性（base64图像代码）的问题。
* **ACSD-50276**(适用于Adobe Commerce >=2.4.0 &lt;2.4.7) — 修复了创建多选客户属性后店面中无法正常使用客户注册表单的问题。
* **ACSD-50527**(对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了在保存具有空动态块的页面时发生的错误。
* **ACSD-49973**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 改进了通过GraphQL获取捆绑产品的性能。
* **ACSD-51114**(对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在启用异步索引时，随机产品从大型目录中消失的问题。 改进大型目录的异步重新索引性能。
* **B2B-2598**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.7) — 将缓存功能添加到[!UICONTROL availableStores]、[!UICONTROL countries]、[!UICONTROL country]、[!UICONTROL currency]和[!UICONTROL storeConfig]个GraphQL查询。
* 为MDVA-42806、ACSD-48627、ACSD-46815添加了新版本。
* 更新了ACSD-49773、ACSD-47179、ACSD-48300的修补程序元数据。

## v1.1.29 {#v1-1-29}

* **ACSD-49389**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.7) — 修复了在订单无法接收时通过API发送接收就绪电子邮件的问题。
* **ACSD-49822**(对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了[!UICONTROL Requisition List]页面中的更新未反映在[!UICONTROL Print Requisition List]上的问题。
* **ACSD-48771**(对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了从更早的[!DNL Page Builder]版本升级列块内容类型时出现的问题。
* **ACSD-49464**(对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了当orderId不同时，发票、装运和贷项通知单不会从存档移回的问题。
* **ACSD-49773**(适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了将AWS S3用作远程存储时产品导出失败的问题。
* **ACSD-49748**(对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了无法发送邀请的问题。
* **ACSD-49502**(对于Adobe Commerce >=2.4.3 &lt;2.4.7) — 修复了在将暂存更新应用于可下载产品后可下载链接未正确更新的问题。
* **ACSD-49527**(对于Adobe Commerce >=2.4.2 &lt;2.4.7) — 修复了GraphQL公司角色无法正确显示分页的问题。
* **ACSD-49706**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了在未选择任何值时为可视样本属性保存默认值的问题。
* **ACSD-49835**(适用于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了多选属性的存储级别上未正确保存“使用默认值”复选框值的问题。
* **ACSD-49898**(适用于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了捆绑产品的特殊价格超过1000时，产品网格引发异常的问题。
* **ACSD-50234**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.5) — 修复了使用[!DNL PayPal]下订单时，确认电子邮件中客户名称错误的问题。
* **ACSD-49960**(适用于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了按日期过滤对客户订单网格不起作用的问题。
* **ACSD-49849**(适用于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了通过GraphQL针对[!DNL PayPal Express]下达订单时，客户电子邮件被替换为[!DNL PayPal]电子邮件的问题。
* **ACSD-49839**(适用于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了以下问题：当产品在SKU中带有单引号或双引号时，共享目录定价和结构会在Admin中引发错误。
* **ACSD-49970**(对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了在启用[!DNL New Relic]报表时对GraphQL错误的不正确处理。
* **ACSD-50260**(对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了GraphQL产品搜索结果限制为仅10,000个结果的问题。
* **ACSD-48813**(对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了搜索未根据属性的搜索权重显示相关结果的问题。

## v1.1.28 {#v1-1-28}

* **ACSD-48204**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.3) — 修复了基于“是/否”属性创建的目录价格规则不考虑所选范围的问题。
* **ACSD-47704**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了捆绑产品仅显示库存产品价格的问题。
* **ACSD-49370**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了GraphQL架构中&#x200B;*日期时间*&#x200B;产品属性具有&#x200B;*FilterMatchTypeInput*&#x200B;类型的问题。
* **ACSD-48807**(适用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.7) — 修复了客户产品评价未通过GraphQL按商店评价过滤的问题。
* **ACSD-49433**(适用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在购物车中显示未结金额礼品卡默认金额的小计的问题。
* **ACSD-48866**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了在请求类别的RSS馈送时出现错误的问题。
* **ACSD-48784**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了在客户组之间错误地缓存客户区段价格的问题。
* **ACSD-48857**(对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了用户在使用页面生成器编辑后无法保存更改的问题。
* **ACSD-49065**(适用于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了报价单项目仅分配给自定义库存时无法在管理员中显示的问题。
* **ACSD-49179**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了当不同商店使用不同货币时，订单报表显示不正确金额的问题。
* **ACSD-49286**(适用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了当页面上存在多个产品小组件时，将产品两次添加到购物车的问题。
* **ACSD-49574**(适用于Adobe Commerce >=2.4.4 &lt;2.4.7) — 添加了通过GraphQL支持购物车中礼品卡产品更新的功能。
* 更新了修补程序：ACSD-48694。

## v1.1.27 {#v1-1-27}

* **ACSD-48362**(对于Adobe Commerce >=2.4.1 &lt;2.4.7) — 修复了在使用可协商报价下订单时使用默认送货地址而不是新送货地址的问题。
* **ACSD-48059**(对于Adobe Commerce >=2.3.7 &lt;2.4.7) — 修复了商家无法在类别中保存“[!UICONTROL Match product by rule]”的问题。
* **ACSD-48216**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) — 修复了[!UICONTROL inventory_source_item]表的[!UICONTROL AUTO_INCREMENT]在[!UICONTROL UPDATE]操作中增加的问题。
* **ACSD-47908**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7) — 修复了在结帐期间选择运输步骤中的源和数量时出现的错误“值应小于或等于0”。
* **ACSD-49497**(适用于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了订单在发运后仍处于处理状态并应用部分退款的问题。
* **ACSD-48694**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.3.8) || >=2.4.1 &lt;2.4.7) — 修复了错误“请求的状态更改无效”导致客户无法下订单的问题。
* **ACSD-49013**(适用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.7) — 修复了在使用批量API创建客户时，电子邮件确认未转换为网站区域设置的问题。
* **ACSD-48164**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了受限管理员无法保存网站级别值的问题。
* **ACSD-48404**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 修复了按下浏览器的“返回”按钮时，“记住类别分页=是”导致错误的问题。
* **ACSD-48634**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 在启用“[!UICONTROL Google Analytics Content Experiments]”时，修复临时更新页面上的JS错误。
* **ACSD-49042**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 修复了无法从店面订购无限延交订单产品的问题。
* 更新了修补程序：ACSD-48366、ACSD-48661。

## v1.1.26 {#v1-1-26}

* **ACSD-47937**(适用于Adobe Commerce和Magento Open Source2.4.4) || >=2.4.5 &lt;2.4.6) — 修复了由于应用程序级别的缓存而并非总是发送价格下降通知的问题。
* **ACSD-48661**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了公司的信用额度大于999时，由于验证错误，逗号分隔符阻止保存公司的问题。
* **ACSD-48773**(适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.7) — 修复了从错误商店获取奖励点数电子邮件模板的问题。
* **ACSD-48587**(适用于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.7) — 修复了在产品小组件匹配规则中HTML特殊字符导致无法显示匹配产品的问题。
* **ACSD-48212**(对于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了产品导入将产品分配给错误源的问题。
* **ACSD-47988**(适用于Adobe Commerce和Magento Open Source>=2.3.7 &lt;2.4.6) — 修复了产品导出会从页面生成器产品描述中裁切HTML标签的问题。
* **ACSD-48366**(适用于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了产品图像未显示在返股电子邮件模板上的问题。
* **ACSD-48417**(对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.7) — 修复了在为产品创建计划更改并保存另一个产品后显示SQL错误的问题。

## v1.1.25 {#v1-1-25}

* **ACSD-48058**(适用于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了将捆绑产品分配给任何网站时，产品价格重新索引无法正常工作的问题。
* **ACSD-48262**(适用于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了将“允许每页所有产品”设置设为“是”时，产品在前端不可见的问题。
* **ACSD-48293**(用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4) — 修复了子产品售出后重新上架时，复合产品缺货的问题。
* **ACSD-47520**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在创建贷项通知单时客户丢失奖励点的问题。
* **ACSD-48044**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 修复了向包含多批发运的单个订单应用多张礼品卡导致无法下订单的问题。
* **ACSD-48300**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在删除可配置产品时无法创建返回的问题。
* **ACSD-47910**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了相应实体网格中缺少订单、发票、装运和贷项通知单的问题。
* **ACSD-47292**(适用于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了将“显示缺货产品”设置为“是”时，GraphQL响应中缺货捆绑产品不可用的问题。
* **ACSD-48234**(对于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了在启用“显示缺货”选项时，目录搜索结果显示不正确的类别项计数的问题。
* **ACSD-48313**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5) — 修复了当属性值包含逗号时，无法解析“configurable_variations”列的问题。 “additional_attributes”使用相同的解析算法。
* **ACSD-48627**(适用于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6) — 修复了在发送GraphQL请求以获取购物车详细信息时，缺货的可配置产品导致错误的问题。
* 更新了修补程序：MDVA-39384。

## v1.1.24 {#v1-1-24}

* **ACSD-45168**(适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了在应用商店视图级别上覆盖&#x200B;*url_key*&#x200B;属性的产品未生成SEO友好URL的问题。
* **ACSD-46865**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了在启用异步索引时未填充装运和贷项通知单网格的问题。
* **ACSD-47004**(适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了没有VAT ID的帐单地址无法应用VAT的问题。
* **ACSD-47803**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了缺货的可配置产品样本显示为可用的问题。
* **ACSD-47137**(对于Adobe Commerce和Magento Open Source >=2.4.4 &lt;2.4.6) — 当pub/media文件夹非常大时，提高图像库的加载速度。
* **ACSD-46770**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了即使&#x200B;*电子邮件订单确认*&#x200B;未选中，仍会发送管理员订单电子邮件的问题。
* **ACSD-47955**(适用于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了GraphQL未正确显示购物车折扣的问题。
* **ACSD-46617**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了以下问题：即使小计大于配置的&#x200B;*最小订单量*，仍然&#x200B;*继续结帐*&#x200B;按钮呈灰显状态。
* **ACSD-47079**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5) — 修复了当子产品库存状态通过REST APIPOST/rest/V1/inventory/source-items更改时，复合产品（捆绑、分组和可配置）库存状态未更新的问题。
* **ACSD-47336**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复&#x200B;*出现错误。在Commerce管理员中取消通知时出现*&#x200B;错误。
* **ACSD-47559**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了“预览电子邮件模板”区域不完全可见的问题。
* **ACSD-47920**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在&#x200B;*允许来宾结帐*&#x200B;关闭时，仍可以通过Rest API作为来宾用户下达订单的问题。
* 已更换修补程序：MDVA-39305、MDVA-42855。

## v1.1.23 {#v1-1-23}

* **ACSD-47179**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了具有特定范围受限访问权限的管理员无法删除产品评论的问题。
* **ACSD-47107**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5) — 修复了目录价格规则折扣应用于自定义产品选项的问题。
* **ACSD-47232**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了无法在管理员中应用总权重条件的优惠券的问题。
* **ACSD-46519**(对于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.6) — 修复了GraphQL categoryList请求返回锚记类别的product_count不正确的问题。
* **ACSD-47027**(对于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了updateCompanyRole GraphQL请求速度缓慢的问题。
* **ACSD-47666**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了以下问题：在“管理员”>“系统”>“权限”>“用户角色”>“角色”>“角色用户”网格中，过滤器功能不起作用。
* **ACSD-47497**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了“管理”下的“配置”中不可见“服务”选项卡的问题。
* 更新了修补程序：ACSD-47743。
* 已更换修补程序：MDVA-42807。

## v1.1.22 {#v1-1-22}

* **ACSD-47444**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3) — 修复了在访问PHP 7.4上已知产品的某些非现有类别路径时，出现&#x200B;_尝试访问bool类型值上的数组偏移_&#x200B;错误的问题。
* **ACSD-47332**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了cron失败并出现错误的问题，该错误仅在00:00 UTC到00:59 UTC之间运行时报告。
* **ACSD-47280**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在特定范围上禁用共享目录功能无法正常工作的问题。
* **ACSD-47106**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了无法在公司创建页面上的新自定义属性中保存值的问题。
* 更新了修补程序：ACSD-45143。

## v1.1.21 {#v1-1-21}

* **ACSD-46809**(适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6) — 修复了在分配大量产品源时，用户遇到错误的问题。
* **ACSD-46856**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 通过“系统”>“配置”>“导入”>“高级定价”更新层价格，从而提高性能。
* **ACSD-46541**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4) — 修复了在删除订单项时管理员用户无法创建贷项通知单的问题。
* **ACSD-46581**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在购物车中选择国家/地区后估计税额合计未更新的问题。
* **ACSD-46618**(对于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了产品列表小组件为已登录的客户显示不正确的缓存价格的问题。
* **ACSD-46674**(适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6) — 修复了在客户电子邮件中将图像类型的自定义选项显示为HTML的问题。
* **ACSD-46988**(对于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6) — 修复了GraphQL“currency”API请求为自定义货币返回NULL值的问题。
* **ACSD-47076**(适用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5) — 修复了Vimeo视频无法在店面播放的问题。
* **ACSD-45071**(适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4) — 修复了在导入期间将默认源添加到产品的问题。
* **AC-3023**(对于Adobe Commerce和Magento Open Source >=2.4.0 &lt;2.4.6) — 将DHL方案更新到最新版本10.0。
* 更新了修补程序：MDVA-42584。
* 已更换修补程序：MDVA-36572、ACSD-45241。

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5*) — 修复了用户在使用商店积分退款时获得错误订单状态的问题。
* **ACSD-46703** (*用于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6*) — 修复了无法在产品编辑页面上拖放自定义选项的问题。
* **ACSD-44851** (*用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6*) — 修复了包含子类别的类别无法打开或展开的问题。
* **ACSD-46815** (*用于Adobe Commerce和Magento Open Source>=2.4.5 &lt;2.4.6*) — 修复了类别树请求限制为20个类别的问题。
* **ACSD-45675** (*用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.6*) — 修复了产品导出使用&#x200B;*默认商店视图*&#x200B;范围内的类别名称的问题。
* **ACSD-46869** (*用于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.6*) — 修复了购物车中的可配置产品未通过&#x200B;*PUTREST API*&#x200B;请求进行更新而不更改产品数量的问题。
* **MDVA-42768-V2** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了当&#x200B;*显示缺货*&#x200B;为&#x200B;*是*&#x200B;时，可配置产品将正常价格显示为&#x200B;*0*&#x200B;的问题。
* 更新了修补程序：MDVA-44562、ACSD-46213、MDVA-41305、MDVA-38346、MDVA-13203。
* 已弃用的修补程序：MDVA-42768。

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了类别树请求限制为20个类别的问题。
* **ACSD-45781** (*用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.2*) — 修复了移动设备上不显示商店前搜索字段的问题。
* **ACSD-46192** (*用于Adobe Commerce和Magento Open Source>=2.3.6 &lt;2.4.5*) — 修复了使用`async/bulk/V1/configurable-products/bySku/options`端点的问题。
* **ACSD-46404** (*用于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5*) — 修复了管理员用户在升级到2.4.4后无法登录的问题。
* 更新了修补程序：MDVA-41305、MDVA-38626、MDVA-38728、MDVA-41061-V4、MDVA-42269、MDVA-39305。

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*用于Adobe Commerce且Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了以下问题：特定存储的GraphQL产品突变返回所有可配置变体，包括那些未分配给所请求存储的变体。
* **ACSD-46146** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.6*) — 修复了管理员下订单后发送两封订单确认电子邮件的问题。
* **ACSD-45255** (*适用于Adobe Commerce >=2.4.3 &lt;2.4.6*) — 修复了受限管理员用户的“低库存报表”页面上的异常。
* **ACSD-45488** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.6*) — 修复了具有多个源的可配置产品未自动返回库存中的问题。
* **ACSD-45754** (*用于Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.6*) — 修复了将优惠券应用到购物车后未添加奖励点数的问题。
* **ACSD-45849** (*适用于Adobe Commerce >=2.4.3 &lt;2.4.4*) — 修复了应用暂存更新后视频元数据丢失的问题。
* **ACSD-45257** (*用于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.4*) — 修复了GraphQL未正确显示购物车折扣的问题。
* **ACSD-44938** (*用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4*) — 修复了无法在访客用户的GraphQL请求中应用`VAT_ID`的问题。
* 更新了修补程序：MDVA-43417。

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*用于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.4*) — 修复了在创建贷项通知单后虚拟产品的库存数量计算错误的问题。
* **ACSD-43887** (*适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了在启用公司采购订单时，结帐付款页面上显示不正确详细信息的问题。
* **ACSD-45143** (*用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.5*) — 修复了`setShippingAddressesOnCart`突变不允许将数字区码设置为&#x200B;*region*&#x200B;的问题。
* **ACSD-44591** (*用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.6*) — 修复了在未进行验证码确认的情况下下达订单时发生的错误。
* **ACSD-45520** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.6*) — 修复了当用户从购物车编辑可配置产品时，无法在产品详细信息页面上预先选择样本选项的问题。
* **ACSD-45169** (*用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.6*) — 修复了在应用暂存更新后，[!DNL Visual Merchandiser]无法显示可配置产品的正确库存和价格的问题。
* **ACSD-45424** (*用于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.6*) — 修复了在部分退款（贷项通知单）之后创建不正确的预订补偿的问题。
* **MDVA-42807** (*用于Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.6*) — 修复了自定义货币符号未显示在店面的问题。
* 更新的修补程序：MDVA-42689、AC-3022。

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (Adobe Commerce和Magento Open Source为&#x200B;*>=2.4.3 &lt;2.4.4*) — 修复了订单报表中针对受限管理员用户错误计算订单总数的问题。
* **MDVA-44940** (*用于Adobe Commerce，Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了从管理员保存类别时发生的SQL错误。
* **MDVA-44562** (*用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.2-p2*) — 修复了以下问题：尽管非默认商店视图发起了GraphQL请求，但报价项目的非默认商店ID会被默认商店ID覆盖。
* **MDVA-43167** (*适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了当管理员用户选择所有订单时，管理员订单网格批量操作不适用于多页的问题。
* **MDVA-44044** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.2-p2*) — 修复了将产品分配给新网站后无法显示在“类别”页面上的问题。
* **MDVA-42509** (*用于Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.4*) — 修复了无法快速上传CSV导致出现&#x200B;*无法发送Cookie*&#x200B;错误的问题。
* 更新的修补程序： MDVA-41061和MDVA-42584。
* 由于内部进程更改，新[!DNL Quality Patches Tool]修补程序的前缀将从&#x200B;*MDVA*&#x200B;更改为&#x200B;*ACSD*。

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了当购物车中已有最小数量的项目时，无法将其他项目添加到购物车的问题。
* **MDVA-44887** (*用于Adobe Commerce和Magento Open Source>=2.4.4 &lt;2.4.5*) — 修复了“管理”面板中的&#x200B;*未捕获的SyntaxError：意外的令牌“const”*&#x200B;错误。
* **MDVA-43718** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复&#x200B;*使用者无权访问%资源。从自定义集成访问共享目录时出现*&#x200B;错误。
* **MDVA-44660** (*用于Adobe Commerce和Magento Open Source>=2.4.2-p1 &lt;2.4.5*) — 修复了重音符号字符``` ` ```无法用于客户的名字和姓氏的问题。
* **MDVA-40896** (*用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了异步产品批量API中的&#x200B;*错误：类型错误：传递给Magento的参数3错误*。
* **MDVA-38559** (*用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3*) — 修复了具有多个订阅的客户的&#x200B;*/V1/customers/search API*&#x200B;错误。
* **MDVA-44533** (*适用于Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.4*) — 修复了将折扣错误地应用于捆绑包子产品的问题。
* 更新的修补程序： MDVA-41061和MDVA-42269。

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了&#x200B;*无法单独显示的产品*&#x200B;仍然显示在目录高级搜索结果中的问题。
* **MDVA-44100** (适用于Adobe Commerce和Magento Open Source的&#x200B;*>=2.4.3 &lt;2.4.5*) — 修复了将所有FPT分配给购物车中的最后一个产品并重置为其他产品的问题。
* **MDVA-43605** (*用于Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.5*) — 修复了在使用Rest API时，订单数据返回行总计负值的问题。
* **MDVA-43102** (*用于Adobe Commerce和Magento Open Source>=2.3.1 &lt;2.4.5*) — 修复了通过REST API进行退款时可销售数量未正确更新的问题。
* **MDVA-43178** (*适用于Adobe Commerce和Magento Open Source>=2.4.3-p2 &lt;2.4.5*) — 修复了无法在GraphQL中检索自定义商店的客户令牌的问题。
* **MDVA-43859** (*用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修复了以下问题：当已删除的客户尝试登录时，不会记录错误&#x200B;*客户ID =*&#x200B;的此类实体。
* **MDVA-44147** (*适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了GraphQL请求不返回申请列表的问题。
* **MDVA-44505** (*适用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.3*) — 修复了GraphQL应用奖励点数未更新总计，以及在下单过程中多次应用商店点数的问题。
* 更新的修补程序：MDVA-29148、MDVA-36464-V5、MDVA-42584、MDVA-39993-V2。

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*适用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.3*) — 修复了仅当“客户区段”设置为&#x200B;*全部*&#x200B;时，“相关产品规则”才能正常工作的问题。
* **MDVA-39605** (*用于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.5*) — 修复了Redis缓存TTL（过期日期）具有错误值的问题。
* **MDVA-43862** (*用于Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.5*) — 修复了由于GraphQL *UpdateCartItems突变*&#x200B;错误而导致客户无法更新购物车项目的问题。
* **MDVA-43824** (*用于Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) — 修复了取消带有折扣的订单时出现错误的问题。
* **MDVA-43451** (*用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了错误&#x200B;*未找到所请求的存储的问题。 请验证存储并重试。为特定网站配置共享目录时显示*。
* **MDVA-43491** (*用于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.5*) — 修复了在导入多商店网站的产品时，基础图像标签不更新的问题。
* **MDVA-43601** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复完全重新索引后缺少触发器的问题。
* **MDVA-42046** (*用于Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) — 修复了在更新产品时为具有日期输入字段的产品属性分配不正确值的问题。
* **MDVA-43935** (*用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修复了向上销售产品显示两次的问题。
* **MDVA-44188** (*用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了系统颁发的地址中包含`.-`的电子邮件未发送的问题。
* **MDVA-42283** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了法语区域设置的管理顺序网格中的日期时间格式无效的问题。
* 更新了修补程序：MDVA-41061-V2、MDVA-36309、MDVA-30862、MDVA-39713。
* 为[!DNL Site-Wide Analysis Tool]添加了修补程序元数据。

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (适用于Adobe Commerce的&#x200B;*且Magento Open Source>=2.3.0 &lt;2.3.6*) — 修复了用户能够编辑活动计划更新的开始时间的问题。
* **MDVA-42410** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了优惠券报表仅显示默认基础货币的问题。
* **MDVA-41136** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了`mage-cache-sessid`的过期日期未延长而导致客户数据清理的问题。
* **MDVA-39993** (*用于Adobe Commerce和Magento Open Source>=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) — 修复了通过API完成的库存更改未在前端产品页面上反映的问题。
* **MDVA-42855** (*用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了签出期间新客户地址未保存到通讯簿中的问题。
* **MDVA-42645** (*用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了在禁用商店点数功能时，管理员无法退款奖励点数的问题。
* **MDVA-43414** (*用于Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2*) — 修复了在数字SKU上运行`inventory.reservations.updateSalabilityStatus`队列使用者时发生的PHP严重错误。
* **MDVA-41628** (适用于Adobe Commerce的&#x200B;*且Magento Open Source>=2.4.0 &lt;2.4.5*) — 修复了在添加新模块时，现有受限管理员用户无法访问新资源的问题。
* **MDVA-43348** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了礼品卡GraphQL请求在`gift_card_options`包含&#x200B;*uid*&#x200B;时显示错误的问题。
* **MDVA-39546** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了在编辑期间将暂存更新的开始日期设置为比当前日期更早的日期的问题。
* **MDVA-42950** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了视频无法在产品页面上播放的问题。
* **MDVA-42689** (*适用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了在导入期间更新产品类别时Adobe Commerce引发&#x200B;*完整性约束冲突*&#x200B;错误的问题。
* **MDVA-41229** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了可配置产品导入后，前端上可用的图像未显示的问题。
* **MDVA-43731** (*用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了以下问题：当值添加到&#x200B;*要匹配的最少搜索词*&#x200B;中时，*搜索同义词*&#x200B;不再有效。
* **MDVA-43232** (*用于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.5*) — 修复了在保存类别时，按“特殊价格从最低到最高”对[!DNL Visual Merchandiser]中的产品进行排序而导致错误的问题。
* **MDVA-43726** (*用于Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.3*) — 修复了在部分重新索引后无法应用基于商店级别属性匹配的目录价格规则的问题。
* 更新了修补程序：MDVA-36464、MDVA-37478、MDVA-38608。
* 为[!DNL Site-Wide Analysis Tool]添加了修补程序元数据。

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (适用于Adobe Commerce和Magento Open Source的&#x200B;*>=2.4.3 &lt;2.4.5*) — 修复了无法通过REST API为特定网站更新产品价格属性的问题。
* **MDVA-41350** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了当具有受限访问权限的管理员用户按SKU按顺序添加产品超出其角色范围时引发异常的问题。
* **MDVA-42269** (*用于Adobe Commerce和Magento Open Source>=2.4.3-p1 &lt;2.4.5*) — 修复了由于&#x200B;*TypeError而导致管理员用户无法登录到管理员的问题： strtotime()预期参数1为字符串，但给定*&#x200B;错误为null。
* **MDVA-40830** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了在下单期间多次应用商店点数的问题。
* **MDVA-42237** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了可配置产品特殊价格在子产品价格发生更改后未更新的问题。
* **MDVA-42520** (*用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了使用&#x200B;*启用跨境贸易*&#x200B;时两次应用税率的问题。
* 更新了修补程序：MDVA-27239、MDVA-39305、MDVA-41236、MDVA-36832。
* 已弃用的修补程序：MDVA-37725。

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*用于Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.4.5*) — 修复了在更改&#x200B;*产品可见性*&#x200B;后批量属性更新仅为默认商店创建URL重写的问题。
* **MDVA-43091** (*用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了在后端从管理员订购捆绑产品时出现错误&#x200B;*的问题。您不能对此产品使用小数数量*。
* **MDVA-40816** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了相关产品规则显示规则条件中未定义类别中产品的问题。
* **MDVA-41305** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.5*) — 修复了GraphQL突变在将其添加到愿望清单后不返回可配置产品选项的问题。
* **MDVA-39181** (*用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修复了相关产品规则显示规则条件中未定义类别中产品的问题。
* **MDVA-42584** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了通过“导入”或API更改数量和库存状态后后端中可配置库存状态未更新的问题。
* **MDVA-40175** (*用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.3*) — 修复了以下问题：*单击更改配送方式*&#x200B;在重新排序过程中不会在“管理员”中显示用于选择配送方式的单选按钮。
* **MDVA-42768** (*用于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.5*) — 修复了当&#x200B;*显示缺货*&#x200B;为“是”时，可配置产品的正常价格显示为0的问题。
* **MDVA-43201** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了在特定区域设置中使用DOB属性时客户登录中发生错误的问题。
* 更新的修补程序： MDVA-35092和MDVA-33970。

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.5*) — 修复了当Adobe Commerce时区与本地环境时区不同时日期过滤器无法正常工作的问题。
* **MDVA-42657** (*适用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修复了管理员用户无法在客户区段条件中选择类别的问题。
* **MDVA-42806** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了在每次通过REST API更新现有公司时发送&#x200B;*新公司注册*&#x200B;电子邮件的问题。
* **MDVA-37984** (*用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.5*) — 修复了[!DNL Visual Merchandiser] *按规则匹配产品*&#x200B;功能无法正确筛选具有暂存更新的产品的问题。
* **MDVA-40488** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了具有缺货子产品的可配置产品无法在其正确价格范围内显示的问题。
* **MDVA-42507** (*适用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.5*) — 修复了在为购物车规则应用暂存更新后清理全页缓存的问题。
* **MDVA-39163** (*用于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.5*) — 修复了在注册新且购物车中的产品来自访客会话时配送方式不可用的问题。
* **MDVA-38626** (*用于Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.5*) — 修复了管理员用户无法使用[!DNL PayPal Payflow Pro]付款在后端下订单的问题。
* **MDVA-38666** (*用于Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.3.6*) — 修复了管理员用户无法更改客户购物车中可配置产品选项的问题。
* **MDVA-38526** (*用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修复了管理员用户无法访问[!DNL Site-Wide Analysis tool]的问题。
* 更新了修补程序：MDVA-40101。

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (适用于Adobe Commerce和Magento Open Source的&#x200B;*>=2.3.0 &lt;2.4.4*) — 修复了在设置&#x200B;*mage-messages* Cookie（如果存在）后用户收到500错误的问题，但是没有新消息。
* **MDVA-41139** (*用于Adobe Commerce和Magento Open Source>=2.4.3 &lt;2.4.4*) — 修复了在导入产品后，当简单产品的一个源的数目为0时，可配置产品出现缺货的问题。
* **MDVA-42326** (*用于Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修复了以下问题：即使启用了永久购物车，客户在会话超时后仍会在结账时遇到错误。
* **MDVA-42341** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了以下问题：如果请求具有Store标头，`categoryList` GraphQL查询不会过滤结果。
* **MDVA-38393** (*用于Adobe Commerce，且Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了在简单产品被重新命名时目录规则停止用于可配置产品的问题。
* **MDVA-39153** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了在管理员中重新排序期间折扣金额计算不正确的问题。
* 更新了修补程序：MDVA-28993、MDVA-41061、MDVA-35984。

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.3*) — 修复了管理员用户在删除网站后无法访问客户网格的问题。
* **MDVA-40311** (*用于Adobe Commerce和Magento Open Source>=2.4.2-p2 &lt;2.4.4*) — 修复了管理员用户收到错误消息&#x200B;*安全或表单密钥无效的问题。 如果已配置自定义管理路径且启用了密钥，请在登录到管理员后刷新页面*。
* **MDVA-41631** (*用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修复了以下问题：用户尝试通过GraphQL检索订单信息时，在没有可选&#x200B;*电话*&#x200B;值的情况下会遇到错误。
* **MDVA-27239** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.3.6*) — 修复了未显示交叉销售产品的问题。
* 更新了修补程序：MDVA-37068、MDVA-35254、MDVA-41164、MDVA-37916、MDVA-37478、MDVA-34551、MDVA-31791。

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*用于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.4*) — 修复了在重新索引期间前端缺少产品的问题。
* **MDVA-40120** (*用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修复了按DESC/ASC排序的GraphQL不适用于具有相同相关性或价格的产品的问题。
* **MDVA-41399** (*用于Adobe Commerce和Magento Open Source>=2.3.3 &lt;2.4.2*) — 修复了如果客户将产品添加到愿望清单，管理员用户无法访问&#x200B;*管理购物车*&#x200B;页面的问题。
* **MDVA-40609** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了`cataloginventory_stock_status`索引表中缺少禁用产品数据，显示不正确的禁用产品数量的问题。
* **MDVA-39031** (适用于Adobe Commerce和Magento Open Source的&#x200B;*>=2.4.1 &lt;2.4.4*) — 修复了即使在未分配到GraphQL的情况下，仍可以通过将产品添加到购物车的问题。
* **MDVA-41597** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了使用GraphQL将多个可配置产品添加到购物车时用户收到错误的问题。
* **MDVA-27456** (适用于Adobe Commerce和Magento Open Source的&#x200B;*>=2.3.5 &lt;2.3.7*) — 修复了用户在尝试加载[!DNL Swagger]时出现错误的问题。
* **MDVA-32776** (适用于Adobe Commerce的&#x200B;*且Magento Open Source>=2.4.0 &lt;2.4.2*) — 修复了在下订单但未发送时，库存状态未更新的问题。
* **MDVA-30862** (*用于Adobe Commerce和Magento Open Source>=2.3.4 &lt;2.4.0*) — 修复了打印的PDF发票上订购日期不正确的问题。
* 改进了[!DNL Quality Patch Tool]的索引页。 在工具的最新版本中添加了[!DNL quality patches]的方便搜索和筛选功能。
* 更新的修补程序： MDVA-33382和MDVA-39482。

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了如果以前删除了结束日期，则无法创建新更新或编辑产品的现有计划更新的问题。
* **MDVA-41046** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了具有自定义选项的简单产品可用于分配给可配置/分组产品的问题。
* **MDVA-40545** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了即使同一页面有多个节点，也仅检索到页面的第一个节点的问题。
* **MDVA-41164** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3-p1*) — 修复了管理员用户无法保存或编辑具有文件或图像类型自定义客户属性的公司的问题。
* **MDVA-39229** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了在更新目录规则暂存更新开始时间后导致出现以下错误的问题： *Cron作业staging_synchronize_entities_period出错：无法删除活动更新。*
* **MDVA-40619** (适用于Adobe Commerce和Magento Open Source的&#x200B;*>=2.3.0 &lt;2.4.4*) — 修复了尝试在CMS页面上执行内联编辑时，对CMS页面层次结构所做的更改会导致500错误的问题。
* **MDVA-41061** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了从管理员保存产品时，库存状态重置为可销售的问题。
* **MDVA-31763** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了在手动重新索引之前还原（或不应用）目录价格规则的问题。
* **MDVA-37748** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了GraphQL查询返回未分配给共享目录的产品的问题。

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了无法通过REST API同时创建同一订单的部分发票的问题。
* **MDVA-40101** (*用于Adobe Commerce和Magento Open Source>=2.3.2 &lt;2.4.0*) — 修复了在使用[!DNL PayPal Express]结帐成功下订单后无法从迷你购物车中删除商品的问题。
* **MDVA-40401** (*用于Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修复了即使下订单失败，优惠券使用值也会更改的问题。
* **MDVA-40537** (*用于Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.4.0-p1*) — 修复了在创建商店视图时，如果存在具有相同URL键的多个CMS页面，用户会收到错误的问题。
* **MDVA-37725** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.4.3-p1*) — 修复了从非默认网站发送的异步订单电子邮件包含默认网站的徽标URL的问题。
* **MDVA-39482** (*用于Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) — 修复了在启用延交订单的情况下，如果以“0”数量导入产品，则产品缺货的问题。
* **MDVA-40435** (适用于Adobe Commerce和Magento Open Source的&#x200B;*>=2.3.4 &lt;2.4.4*) — 修复了在通过GraphQL应用时，带动态价格的捆绑产品折扣不正确的问题。
* **MC-42528** (*对于Adobe Commerce和Magento Open Source>=2.4.3 &lt;=2.4.3-p1*) — 修复了`categoryList` GraphQL查询返回已分配和未分配类别的问题。
* **MDVA-29400** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 修复了与[!DNL PayPal Express Checkout]一起下重复订单的问题。
* **MDVA-26005** (适用于Adobe Commerce的&#x200B;*且Magento Open Source>=2.3.4 &lt;=2.3.5-p2*) — 修复了在类别树中为购物车价格规则条件选择类别时出现的问题。
* **MDVA-25631** (*用于Adobe Commerce和Magento Open Source>=2.3.3 &lt;=2.3.5-p2*) — 提高编辑和保存包含大量客户的客户区段的性能。

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了GraphQL搜索查询无法在管理员的常用搜索词中显示的问题。
* **MDVA-40601** (*适用于Adobe Commerce和Magento Open Source>=2.3.1 &lt;=2.4.2-p2*) — 修复了以下问题：用户尝试通过GraphQL获取有关计划的更新所更改类别的信息时出现错误。
* **MDVA-37234** (*用于Adobe Commerce和Magento Open Source>=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) — 修复了以下问题：对于同一SKU，将项目多次添加到购物车（并行请求）会为同一购物车ID创建重复的行项目。
* **MDVA-33606** (*适用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;=2.4.2-p2*) — 修复了在保存分配给层次结构的CMS页面时，用户收到&#x200B;*唯一约束冲突*&#x200B;错误的问题。
* **MDVA-31590** (*用于Adobe Commerce，Magento Open Source>=2.4.0 &lt;=2.4.1-p1*) — 修复了用户无法使用MySQL异步队列批量更新属性的问题。
* **MDVA-36309** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;=2.4.2-p2*) — 修复了在管理网格中按属性搜索产品速度缓慢的问题。

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了在从商店贷方支付订单时，使用FPT的发票显示错误的总计的问题。
* **MDVA-37364** (*用于Adobe Commerce，Magento Open Source>=2.4.0 &lt;=2.4.3*) — 修复了日期类型的自定义客户属性破坏客户的网格UI的问题。
* **MDVA-39195** (*适用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;=2.4.2-p2*) — 修复了在启用重定向到购物车时，“类别”页面上的“*添加到购物车*”按钮未启用的问题。
* **MDVA-37115** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;=2.4.2-p2*) — 修复了在可配置产品页面上显示不必要的&#x200B;*仅剩下0*&#x200B;注意事项的问题。
* **MDVA-39521** (*适用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4*) — 修复了用户无法通过GraphQL在购物车上设置电话号码为空的送货地址的问题。
* **MDVA-39384** (*用于Adobe Commerce和Magento Open Source>=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) — 修复了未保存公司用户的自定义客户属性的问题。
* **MDVA-39043** (*适用于Adobe Commerce和Magento Open Source>=2.3.4 &lt;=2.4.3*) — 修复了具有有限访问权限的管理员用户在尝试将&#x200B;*产品*&#x200B;小组件添加到CMS页面时出错的问题。
* **MDVA-39966** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) — 修复了部署错误区域设置的问题。
* **MDVA-38852** (*用于Adobe Commerce，且Magento Open Source>=2.3.0 &lt;=2.3.5-p2*) — 修复了以下问题：当有多个并行订单时，目录库存通过设计来锁定表的更新，从而显着降低性能。
* **MDVA-39986** (*适用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.3*) — 修复了用户无法使用Safari浏览器在MacOS的Admin中下达订单的问题。
* **MDVA-38447** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.4*) — 修复了以下两个问题：在GraphQL响应中返回了&#x200B;*不可单独显示*&#x200B;可配置的子产品，并使用类别过滤器优化了GraphQL产品查询的MySQL查询。
* **MDVA-40134** (*用于Adobe Commerce和Magento Open Source>=2.4.2 &lt;2.4.3*) — 修复了在启用共享目录后GraphQL未返回相关产品的问题。
* **MDVA-39935** (*用于Adobe Commerce和Magento Open Source>=2.4.1 &lt;2.4.4*) — 修复了GraphQL返回在网站级别禁用的可配置子产品的问题。

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*用于Adobe Commerce和Magento Open Source>=2.4.0 &lt;2.4.4*) — 修复了&#x200B;*调用成员函数getId()*&#x200B;错误显示在Admin的订单详细信息页面上的问题。
* **MDVA-34948** (*用于Adobe Commerce和Magento Open Source>=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) — 修复了长时间运行的查询（如`GET_LOCK`）的问题。
* **MDVA-39305** (*用于Adobe Commerce且Magento Open Source>=2.4.0 &lt;=2.4.2-p1*) — 修复了注册客户无法使用已启用的Google ReCaptcha登录的问题。
* **MDVA-37897** (*用于Adobe Commerce和Magento Open Source>=2.3.0 &lt;2.4.4*) — 修复了客户尝试使用“最近查看的”小组件中的选项添加产品时，重定向不正确的问题。

## v1.1.0 {#v1-1-0}

* 引入了修补程序类别，以改进用户体验并使客户更轻松地搜索所需的修补程序。
* `patches.json`文件已重命名为`support-patches.json`。
* **MDVA-38799** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了在创建暂存更新后未保存可下载产品的问题。
* **MDVA-37592** (*适用于Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) — 修复了按价格排序对分配给共享目录的零价格产品无法正常工作的问题。
* **MDVA-38827** (*适用于Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) — 修复了客户收到包含错误消息的订单装运电子邮件的问题。

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*用于Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) — 修复了保存CMS页面时的错误： *具有相同ID PAGE_ID的项已存在*。
* **MDVA-34680** (*用于Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) — 修复了在客户网格中客户帐户创建时间未正确过滤的问题。
* **MDVA-37068** (*适用于Adobe Commerce >=2.3.1 &lt;2.4.4*) — 修复了购物车仅包含虚拟产品时显示错误税率的问题。
* **MDVA-38608** (*用于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了重新索引未成功完成时临时表未删除的问题。
* **MDVA-38308** (*用于Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) — 修复了与将[!DNL Vimeo]视频添加到产品相关的问题。

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*适用于Adobe Commerce >=2.3.6 &lt;2.4.3*) — 修复了在使用[!DNL Paypal Payment Advanced]方法时客户未进入付款确认页面的问题。
* **MDVA-37082** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了在保存分组产品的自定义库存时导致产品在前端无库存的问题。
* **MDVA-36572** (*适用于Adobe Commerce >=2.3.5 &lt;2.4.3*) — 修复了贷项通知单更新不再导致数据库中重复产品预订更新的问题。
* **MDVA-38132** (*适用于Adobe Commerce >=2.3.3 &lt;2.4.3*) — 修复了由于&#x200B;*重定向次数过多*&#x200B;错误而无法访问管理员面板的问题。
* **MDVA-38270** (*适用于Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修复了GraphQL中订单总计中缺少礼品卡信息的问题。

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*适用于Adobe Commerce >=2.4.2 &lt;=2.4.4*) — 修复了在网站ID与商店ID不符时通过GraphQL将可配置产品添加到购物车时出现的问题。
* **MDVA-36832** (*适用于Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) — 修复了当视图宽度为768px时，页面上出现图像重复的问题。
* **MDVA-37874** (*用于Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) — 修复了以下问题：*整个购物车的固定折扣金额*&#x200B;错误地应用于包含多个选项的捆绑产品。
* **MDVA-37913** (*适用于Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) — 修复了通过API更新可下载产品时可下载链接消失的问题。
* **MDVA-34330** (*适用于Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) — 修复了订单网格中的订单未根据管理员时区进行过滤的问题。

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*适用于Adobe Commerce >=2.3.0 &lt;=2.3.7*) — 修复了以下问题：为通过REST API使用&#x200B;*帐户付款*&#x200B;付款方式下达的订单创建部分发票时，Adobe Commerce会引发错误。
* **MDVA-37362** (*适用于Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) — 修复了GraphQL响应中可配置产品选项值和变量属性值为空的问题。
* **MDVA-37288** (适用于Adobe Commerce 2.4.2 *的*) — 修复了GraphQL请求后返回错误层价格的问题。
* **MDVA-37225** (*适用于Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) — 修复了在快速创建订单期间，当导入的SKU中存在整数值时上传流程卡住的问题。
* **MDVA-37224** (*适用于Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) — 修复了客户无法针对购物车中其他产品的[!DNL PayFlow Pro]可转让报价付款的问题。
* **MDVA-36286** (*适用于Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) — 修复了当同一SKU在子类别中具有不同的位置时，页面生成器产品小组件预览中断的问题。
* **MDVA-30186** (*适用于Adobe Commerce >=2.3.4 &lt;=2.3.5-p2， >=2.4.0 &lt;=2.4.0-p1， >=2.4.2 &lt;=2.4.2-p1*) — 修复了GraphQL响应中属性选项按选项值而不是属性项计数排序的问题。

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*适用于Adobe Commerce >=2.3.0 &lt;=2.4.2*) — 修复了通过API更改旧自定义选项后保留的问题。
* **MDVA-35773** (*用于Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) — 修复了在折扣为100%的订单的发票上未将全部总计显示为零的问题。
* **MDVA-36833**(适用于Adobe Commerce 2.4.2 *的*) — 修复了在将某些产品从共享目录排除之后，搜索结果显示每页产品的随机数的问题。
* **MDVA-37182** (*用于Adobe Commerce >=2.4.1 &lt;=2.4.2*) — 修复了[!DNL Elasticsearch]版本6和版本7中获取不正确搜索结果的问题。
* **MDVA-36253** (*适用于Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) — 修复了删除项目后在迷你购物车中显示错误小计的问题。
* **MDVA-36853** (适用于Adobe Commerce 2.4.2 *的*) — 修复了在加载大型媒体集时未显示图像的问题。

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*用于Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) — 修复了类别页面上缺少捆绑产品的问题。
* **MDVA-36615** (适用于Adobe Commerce 2.4.2 *的*) — 修复了管理产品网格中产品计数不正确的问题。
* **MDVA-36464** (*适用于Adobe Commerce >=2.4.0 &lt;=2.4.2*) — 修复了电子邮件通知配置在商店视图级别无法工作的问题。
* **MDVA-36138** (*适用于Adobe Commerce ^2.3.2*) — 修复了以下问题：如果购物车中的所有项目都不符合免费送货购物车规则，则不会调整送货价格，并向客户显示完整的送货价格。
* **MDVA-36424** (*用于Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) — 修复了在后端基本URL与店面基本URL不同时，当内容被重复编辑时，附加到页面生成器元素的媒体图像消失的问题。
* **MDVA-35984** (*用于Adobe Commerce ^2.4.0*) — 修复了在为同一产品创建多个并发装运后产品数量和可销售数量不正确的问题。

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*用于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 这修复了使用类别缓存标记时GraphQL查询未缓存的问题。
* **MDVA-33168** (*用于Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修复了通过API更新产品属性时所有其他属性都更改为空值的问题。
* **MDVA-19640** (*用于Adobe Commerce >=2.3.0*) — 修复了[!DNL Advanced Reporting]未显示任何数据的问题。
* **MDVA-11189** (*用于Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修复了在导入CSV文件以更新产品库存后，`cataloginventory_stock`表中的行被删除的问题。
* **MDVA-26639** (*适用于Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) — 修复了以下问题：如果创建了新的订单确认电子邮件模板，则订单邮件中会缺少订单项。
* **MDVA-15546** (*用于Adobe Commerce >=2.3.0*) — 修复了在创建订单后，异常日志中显示&#x200B;*Column entity_id where子句不明确的*&#x200B;错误的问题。
* **MDVA-21095** (*用于Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修复了在批量属性值更新后查询`INSERT INTO search_tmp`无法结束的问题。
* **MDVA-23845** (*适用于Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) — 修复了在启用JavaScript缩小后无法预览电子邮件模板的问题。
* **MDVA-22026** (*适用于Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修复了从CSV文件导入产品（包括来自外部URL的图像）失败的问题。
* **MDVA-22383** (*适用于Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修复了保存产品耗时较长且出现分页错误的问题。
* **MC-41359** (*适用于Adobe Commerce >=2.3.6-p1 &lt;2.3.7， >=2.4.2 &lt;2.4.3*) — 修复了SameSite Cookie参数设置不正确的问题。

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*用于Adobe Commerce 2.4.1*) — 修复了页面生成器引发以下错误的问题： *启动页面生成器时出错。 请咨询您的技术支持联系人。*
* **MDVA-35356** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了取消部分开票的订单后，商店退款不正确的问题。
* **MDVA-33289** (*适用于Adobe Commerce >=2.4.0 &lt;2.4.3*) — 修复了在启用[!DNL Google Tag Manager]的情况下，帐单地址UI中会在结帐期间显示原始JavaScript代码的问题。
* **MDVA-35982** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了仅限特定网站的管理员用户无法为同一网站上的订单创建装运的问题。
* **MDVA-35155** (*适用于Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修复了在选项标题更改时无法购买捆绑产品的问题。
* **MDVA-35910** (*适用于Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修复了在禁用“以客户身份登录”功能后无法创建新客户帐户的问题。
* **MDVA-34474** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了使用API将产品添加到申购单列表的问题。
* **MDVA-34591** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了购物车规则折扣计算&#x200B;*最大数量折扣应用于*&#x200B;和&#x200B;*折扣数量步骤（购买X）*&#x200B;不正确的问题。
* **MDVA-33704** (*适用于Adobe Commerce >=2.4.0 &lt;2.4.3*) — 修复了&#x200B;*店内提货*&#x200B;配送选项配置为可用但无法显示的问题。
* **MDVA-34928** (*适用于Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) — 修复了从付款中删除商店点数后无限期显示页面加载程序的问题。
* **MDVA-35254** (*适用于Adobe Commerce >=2.3.1 &lt;2.4.3*) — 修复了签出期间验证码的问题。
* **MDVA-35569** (*适用于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了在指定状态时GraphQL响应中未填充&#x200B;*已修复的产品税*&#x200B;字段的问题。
* **MDVA-35847** (*适用于Adobe Commerce >=2.4.1 &lt;2.4.3*) — 修复了在使用自定义客户属性时“公司用户”表单中断的B2B问题。
* **MDVA-31307** (*适用于Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修复了某些类别上因缓存块的动态CSP白名单问题而出现&#x200B;*内存不足*&#x200B;错误的问题。

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*用于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 删除多个产品后，将消费者`quoteItemCleaner`的不正确&#x200B;*进行中*&#x200B;消息状态修复为正确的&#x200B;*完成*&#x200B;消息。
* **MDVA-34102** (*用于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了“产品网格”和“管理”区域的“编辑产品”页面上禁用产品的默认库存数量为零。
* **MDVA-35286** (*适用于Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修复了以下问题：如果客户在购物车中捆绑了产品，并且从“多个地址”签出切换到“网页”签出，则会出现错误。
* **MDVA-35312** (*适用于Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) — 修复了空GraphQL请求时的响应代码500。
* **MDVA-34189** (*适用于Adobe Commerce >=2.3.4 &lt;2.4.3*) — 修复了加载“管理类别”页面时[!DNL Visual Merchandiser]查询的503首字节超时。
* **MDVA-34695** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.1*) — 在删除类别后修复负数`children_count`。

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*适用于Adobe Commerce >=2.3.1 &lt;2.4.3*) — 修复了在应用计划更改后清除&#x200B;*使用默认值*&#x200B;复选框的问题。 一旦计划的更改不再有效，问题即出现。
* **MDVA-35064** (*适用于Adobe Commerce >=2.3.3 &lt;2.4.3*) — 修复了通过API创建的可配置产品无法生成URL重写的问题。
* **MDVA-34943** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了快速订单缓存之前输入的SKU的问题。
* **MDVA-35197** (*适用于Adobe Commerce >=2.3.5 &lt;2.4.0*) — 修复了在使用GraphQL添加到购物车时，如果之前添加的产品缺货，则会出现错误的问题。
* **MDVA-34850** (*适用于Adobe Commerce >=2.3.1 &lt;2.4.0*) — 修复了可配置产品的缺货选项未显示而非显示为删除的问题。
* **MDVA-34867** (*用于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了计划更新的条件字段集值未保存的问题。
* **MDVA-35092** (*适用于Adobe Commerce >=2.3.5 &lt;2.4.3*) — 修复了由于已弃用[!DNL Vimeo] API，用户无法添加[!DNL Vimeo]视频的问题。

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*适用于Adobe Commerce >=2.3.6 &lt;2.4.3*) — 修复了当匹配的产品对每个网站的价格不同时，页面生成器产品内容类型预览中断的问题。
* **MDVA-32634** (*用于Adobe Commerce ^2.3.1*) — 修复了在层次结构中移动类别后，分配给所有商店的类别的`url_path`未更改的问题。
* **MDVA-33344** (*用于Adobe Commerce ^2.3.0*) — 修复了使用硬编码的`rma_item`实体默认属性集ID而不是来自数据库的值的问题。
* **MDVA-34192** (*适用于Adobe Commerce >=2.3.4 &lt;2.4.3*) — 修复了无法使用dd/mm/yyyy格式修改/指定客户出生日期的问题。
* **MDVA-34847** (*用于Adobe Commerce ^2.3.0*) — 修复了具有自定义权限的管理员用户的管理员集合中，SQL条件的存储ID类型转换的整数。
* **MDVA-34886** (*用于Adobe Commerce ^2.3.2*) — 修复了将&#x200B;*权重*&#x200B;产品属性配置为可搜索时，搜索未返回结果的问题。

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了[!DNL PayPal Payflow Pro]付款失败并出现重定向参数列表格式错误的问题。
* **MDVA-34023** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.3*) — 修复了错误&#x200B;*没有此类地址为ID为*&#x200B;的实体在访客的浏览器中随机显示的问题。
* **MDVA-32759** (*适用于Adobe Commerce >=2.3.1 &lt;2.4.3，扩展为B2B*) — 修复了共享目录删除现有层定价的问题。
* **MDVA-33482** (*用于Adobe Commerce ^2.3.5*) — 修复了在生成针对部分发票的贷项通知单时，导致对总订单计税，而不是对该部分发票计税的问题。
* **MDVA-33393** (*用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复错误&#x200B;*提供的countryId不存在*。
* **MDVA-33632** (*适用于Adobe Commerce >=2.3.0 &lt;2.3.7*) — 修复了在尝试重新订购缺货产品时，向管理员用户显示异常消息&#x200B;*此产品缺货*&#x200B;的问题。
* **MDVA-34469** (*适用于Adobe Commerce >=2.4.1 &lt;2.4.2*) — 修复了在使用多个商店视图时，客户购物车上的GraphQL突变失败的问题。
* **MDVA-33976** (*适用于Adobe Commerce >=2.3.0 &lt;2.3.7*) — 修复了从捆绑包产品中删除第二个选项后，在店面中显示捆绑包产品缺货的问题。
* **MDVA-33894** (*适用于Adobe Commerce >=2.4.0 &lt;2.4.1，带有B2B扩展*) — 修复了快速订购功能的多个问题，包括添加和删除多个产品以及SKU区分大小写。
* **MDVA-27664** (*适用于Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修复了客户注册表单中导致显示错误的问题： *错误 — 出生日期不应晚于今天。*
* **MDVA-33970** (*适用于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了将价格属性的范围设置为网站时，贷项通知单中存在错误货币符号的问题。
* **MDVA-33992** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了B2B特价在结账过程中显示不正确的问题。
* **MDVA-34100** (*用于Adobe Commerce >=2.3.4 &lt;2.4.2，带有B2B扩展*) — 修复了无法从公司结构页面创建公司帐户的问题。

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*适用于Adobe Commerce >=2.3.3 &lt;2.3.5， >=2.4.0 &lt;2.4.2*) — 修复了从CSV文件导入产品后重复图像的问题。
* **MDVA-33382** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了从类别中删除产品后索引器失效的问题。
* **MDVA-28511** (*用于Adobe Commerce >=2.3.5 &lt;2.3.6*) — 修复了当“名称”字段包含某些字符（如重音大写字母）时，无法完成[!DNL PayPal]签出的问题。
* **MDVA-31519** (*适用于Adobe Commerce >=2.3.5 &lt;2.3.6*) — 修复了在使用全站点销售规则时来宾结账中的等待超时问题。
* **MDVA-33281** (*用于Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修复了由于SKU参数类型错误而导致`inventory:reservation:list-inconsistencies`中出现严重错误的问题。
* **MDVA-24201** (*适用于Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修复了在手动重新编制索引之前，价格无法反映计划购物车价格规则的问题。
* **MDVA-32694** (*用于Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) — 修复了管理员用户无法将产品添加到可转让报价单的问题（如果它与非默认商店相关）。
* **MDVA-33516** (*适用于Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修复了在申请列表中编辑捆绑产品会导致错误的问题。
* **MDVA-33975** (*适用于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了GraphQL请求中与价格计算相关的多个问题。

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了[!DNL PayPal]结算报表在&#x200B;**报表** > **销售** > **[!DNL PayPal]**&#x200B;结算下不可用的问题。
* **MCP-87** (*对于Adobe Commerce >=2.3.1 &lt;2.4.2*) — 改进了大型配置文件的类别产品和库存索引器的索引时间。
* **MDVA-33106** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在执行cron `run`命令后擦除重新计划产品更改的问题。
* **MDVA-19391** (*用于Adobe Commerce >=2.3.0 &lt;2.3.5*) — 修复了`analytics_collect_data`由于`catalog_category_entity_text`表中的NULL描述记录而引发错误的问题。
* **MDVA-20376** (*适用于Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修复了在下订单后登录的客户在`exception.log`中&#x200B;*没有此类客户识别码= 1*&#x200B;的实体错误的问题。
* **MDVA-23764** (*用于Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修复了`JsFooterPlugin.php`中影响动态块显示的错误。
* **MDVA-13203** (*用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在完全重新索引后出现&#x200B;*完整性约束违规search_tmp_ table*&#x200B;错误的问题。
* **MDVA-23426** (*适用于Adobe Commerce >=2.3.3 &lt;2.3.5*) — 修复了Adobe Commerce发送的通知电子邮件包含空白正文且内容被添加为附件的问题。
* **MDVA-22150** (*适用于Adobe Commerce >=2.3.1 &lt;2.3.4*) — 修复了以下问题：如果在Admin中禁用了可配置产品，则购物车中具有可配置产品且应用了优惠券的客户无法登录。
* **MDVA-32545** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在从管理员创建订单时未自动发送发票的问题。
* **MDVA-32714** (*用于Adobe Commerce >=2.3.4 &lt;2.4.1*) — 修复了客户组价格在GraphQL产品查询中不起作用的问题。

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*用于Adobe Commerce >=2.3.2 &lt;2.4.2*) — 添加&#x200B;*小计(包括 税额)*&#x200B;用于定价规则条件的选项。
* **MDVA-31236** (*适用于Adobe Commerce >=2.4.0 &lt;2.4.2*) — 修复了具有自定义资源访问权限的管理员无法设置2FA或登录的问题。
* **MDVA-30845** (*适用于Adobe Commerce >=2.3.5 &lt;2.3.7*) — 修复了&#x200B;*抱歉，当无法连接到UPS XML/USPS/DHL时，此时此订单没有报价可用*&#x200B;错误且没有其他送货方法可用的问题。
* **MDVA-32133** (*适用于Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修复了在某些情况下无法从页面生成器加载媒体集的问题。
* **MDVA-12304** (*用于Adobe Commerce >=2.3.0*) — 将最大Cookie数量从50增加到200。
* **MDVA-32632** (*适用于Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修复了订单出现在付款系统中，但未出现在Adobe Commerce中的问题。
* **MDVA-32449** (*用于Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;带有B2B扩展的2.4.2*) — 修复了订单历史记录加载非常缓慢或完全不加载的问题。
* **MDVA-32739** (*用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了启用异步电子邮件通知发送旧销售电子邮件的问题。

## v1.0.11 {#v1-0-11}

* **MC-38509** (*适用于Adobe Commerce 2.3.6、2.4.1*) — 修复了在更正&#x200B;*新建客户帐户*&#x200B;表单中的无效数据后，*创建帐户*&#x200B;按钮保持禁用状态的问题。
* **MDVA-31006**(*适用于Adobe Commerce 2.3.0、2.3.1*) — 修复了使用[!DNL Paypal Express]付款下订单后出现重复订单的问题。
* **MDVA-25602** (*适用于Adobe Commerce 2.3.0*) — 修复了[!DNL PayPal Payflow Pro]付款方法的问题，并在Chrome 80浏览器和API响应重定向到客户登录页面中将Cookie默认视为`SameSite=Lax`。

## v1.0.10 {#v1-0-10}

修补程序版本的小修复

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*适用于Adobe Commerce >=2.3.2 &lt;2.4.2*) — 修复了在使用&#x200B;*整个购物车的固定金额折扣*&#x200B;操作时，带优惠券的购物车价格规则不通过GraphQL应用的问题。
* **MDVA-30889** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在使用虚拟和简单产品作为选项开具捆绑包发票后发生错误的问题。
* **MDVA-31791** (*用于Adobe Commerce >=2.3.4 &lt;2.3.5*) — 在使用目标规则或链接的产品时，提高产品页面的性能。
* **MDVA-31168** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了产品导出CSV文件未显示以及内存分配错误的问题。
* **MDVA-32313** (*用于Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修复了使用错误的配置选项将可配置产品添加到愿望清单中的问题。
* **MDVA-31759** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在CSV导入期间，产品未使用&#x200B;*下拉列表*&#x200B;和&#x200B;*textarea*&#x200B;属性值更新的问题。
* **MDVA-32012** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了韩国和阿根廷的邮政编码无法验证的问题。
* **MDVA-31640** (*用于Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) — 修复了无法通过REST API更新特殊价格的问题。
* **MDVA-28651** (*用于Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0（带有B2B扩展*） — 修复了通过REST API加载可转让报价时出现性能问题的情况。

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.1，带有B2B扩展*) — 修复了贷项通知单网格中显示错误货币符号的问题。
* **MDVA-31295** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在完成部分订单并对项目征税时未计算奖励点数的问题。
* **MDVA-30112** (*适用于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了订单数超过&#x200B;*bunch-size*&#x200B;值的问题，Adobe Commerce将状态为&#x200B;*待处理*&#x200B;的订单视为不一致。
* **MDVA-31150** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了GETInvoice Rest API调用未返回商店信用卡和礼品卡余额的问题，当时，发票通过Rest API调用过帐，并且订单由商店信用卡和礼品卡帐户支付了一部分。
* **MDVA-30963** (*用于Adobe Commerce >=2.3.2 &lt;2.4.2*) — 修复了以下问题：产品筛选结果设置为仅包含为Admin中的&#x200B;*所有商店视图*&#x200B;范围指定的值，并且包含其值在商店视图级别被覆盖的产品。
* **MDVA-29954** (*用于Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2带有B2B扩展*) — 修复了以下问题：*新公司注册请求*&#x200B;和&#x200B;*您已链接到公司*&#x200B;电子邮件发自错误的地址。
* **MDVA-28357** (*用于Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) — 将标准分析器替换为[!DNL ElasticSearch]索引中SKU字段的关键字标记器的自定义分析器，以使通配符搜索查询适用于包含连字符(“ — ”)的SKU。

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在使用WebApi创建部分装运后，自定义订单状态更改为&#x200B;*正在处理*&#x200B;的问题。
* **MDVA-30428** (*适用于Adobe Commerce >=2.3.4 &lt;2.3.5*) — 修复了以下问题：如果将该产品分配给自定义库存源，则客户无法将产品添加到愿望清单。
* **MDVA-30594** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在配置FPT时签出期间无法保存具有多个地址的订单的问题。
* **MDVA-29148** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在通过API调用创建产品时的问题，如果有效负载中未提供值，则`\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` （如Multiselect）类型的产品自定义属性不会使用其默认值。
* **MDVA-30837** (*适用于Adobe Commerce >=2.3.1 &lt;2.3.5*) — 在免运费方法配置中添加了配置设置&#x200B;*含税金额：是/否*。 当&#x200B;*含税金额*&#x200B;设置为&#x200B;*是*&#x200B;时，最小订单金额计算为小计+税。 当&#x200B;*含税金额*&#x200B;设置为&#x200B;*否*&#x200B;时，最小订单金额计算为小计
* **MDVA-25028** (*用于Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) — 修复了在触发欺诈过滤器时，使用[!DNL PayPal Payflow Pro]下达的订单未设置为可疑欺诈状态的问题。
* **MDVA-31224** (*用于Adobe Commerce >=2.3.3 &lt;2.3.5*) — 改进捆绑产品的`catalog_product_price`重新索引操作的性能。
* **MDVA-31321** (*用于Adobe Commerce >=2.3.2 &lt;2.3.5*) — 修复选择&#x200B;*显示全部*&#x200B;时的空白页（错误）。 [!DNL Elasticsearch]返回较大的产品ID列表。 在此方案中，order by子句将转换为不正确的SQL格式。
* **MDVA-30815** (*适用于Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修复了以下问题：当您更改搜索结果页面上应显示的搜索结果数量时，Adobe Commerce会显示一个空白页。 当您更改每页查看的搜索结果数时，[!DNL Elasticsearch]现在可以正确显示类别页中的结果。
* **MDVA-30782** (*适用于Adobe Commerce >=2.3.5 &lt;2.4.2*) — 修复了在不考虑购物车规则的情况下显示动态块的问题。
* **MDVA-31021** (*用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了`module-catalog-import-export/Model/Import/Product/Option.php`中存在性能问题的情况。 如果`catalog_product_option`表中的记录数超过~100,000条，则验证单个产品的新CSV所花费的时间将少于10秒。
* **MDVA-31007** (*适用于Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修复了自定义地址属性未正确显示在“我的帐户”区域和后端的订单详细信息页面中的问题。
* **MDVA-29389** (*用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了高级报表的问题，其中`analytics_collect_data` cronjob指示： *端口必须在主机参数（如localhost：3306）中配置*。
* **MDVA-31343** (*用于Adobe Commerce >=2.3.4 &lt;2.3.6*) — 修复了在计划类别时已删除的正文类`page-layout-category-full-width`的问题。
* **MDVA-30945** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了在更新购物车`Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`时收到严重错误消息的问题。

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*用于Adobe Commerce >=2.3.4 &lt;2.4.0*) — 实现&#x200B;*最小值应与*&#x200B;功能及对[!DNL Elasticsearch]引擎的部分搜索相匹配。 解决了搜索查询中连字符的问题。
* **MDVA-30102** (*适用于Adobe Commerce >=2.3.2 &lt;=2.4.0*) — 修复了布局缓存没有TTL时Redis缓存快速增长的问题。
* **MDVA-30599** (*适用于Adobe Commerce >=2.3.4 &lt;=2.4.0*) — 修复了使用API创建的来宾引号被错误地标记为登录客户的引号的问题。
* **MDVA-29446** (*适用于Adobe Commerce >=2.3.3 &lt;=2.4.0*) — 修复了在结账期间不适用的配送方式价格显示为零的问题。
* **MDVA-30357** (*用于Adobe Commerce >=2.3.2 &lt;=2.4.0*) — 修复了在通过cron生成Sitemap时创建错误图像URL的问题。
* **MDVA-30565** (*适用于Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) — 修复了以下问题：如果启用了永久购物车，则店面结帐时&#x200B;*不会为访客客户显示此类带有cartid = 0*&#x200B;错误的实体。
* **MDVA-29787** (*适用于Adobe Commerce >=2.3.0 &lt;=2.4.0*) — 修复了当&#x200B;*是*&#x200B;条件之一用于定义要显示的产品时，相关产品的目标规则无法工作的问题。
* **MDVA-30977** (*用于Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) — 修复了重新索引后类别中缺少随机产品的问题。
* **MDVA-28202** (*适用于Adobe Commerce >=2.3.4 &lt;=2.4.2*) — 修复了在使用MSI时，分层导航无法正确筛选可配置产品的问题。
* **MDVA-28300** (*适用于Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修复了GQL请求未反映目录价格规则中的价格更改的问题。
* **MDVA-31006** (*适用于Adobe Commerce >=2.3.2 &lt;=2.4.2*) — 修复了使用[!DNL Paypal Express]付款下订单后出现重复订单的问题。

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*用于Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修复了分层导航的问题，在该问题中，如果使用[!DNL Elasticsearch]作为搜索引擎，则分层导航中不包含布尔类型产品属性的&#x200B;*No*&#x200B;值。
* **MDVA-28191** (*适用于Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修复了在通过管理员创建订单期间未加载任何付款方法的问题。
* **MDVA-29959** (*适用于Adobe Commerce >=2.3.0 &lt;=2.3.3-p1，扩展名为B2B*) — 修复了具有&#x200B;*公司*&#x200B;权限的受限制管理员用户不允许删除公司帐户的问题。
* **MDVA-30265** (*适用于Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修复了在创建发票后装运跟踪链接停止工作的问题。
* **MDVA-28409** (*用于Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修复了数据库中过期的引号数量巨大时，`sales_clean_quotes` cron作业失败并出现&#x200B;*内存不足*&#x200B;错误的问题。
* **MDVA-30593** (*适用于Adobe Commerce >=2.3.0 &lt;2.3.4*) — 修复了未清理根据“报价生存期”设置过期的报价的问题。
* **MDVA-30107** (*适用于Adobe Commerce >=2.3.0 &lt;2.3.6*) — 修复了将不同的基本URL用于商店视图时，商店切换器无法按预期工作的问题。
* **MDVA-28763** (*适用于Adobe Commerce >=2.3.2 &lt;2.3.4*) — 修复了在使用REST API多次更新产品信息后产品图像重复的问题。
* **MDVA-30284** (*用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了目录搜索索引器由于以下&#x200B;*[!DNL Elasticsearch]错误而失败的问题：已超过索引中字段总数的限制。*
* **MDVA-29042** (*适用于Adobe Commerce >=2.3.3 &lt;=2.3.4-p2，扩展名为B2B*) — 修复了在将新产品添加到共享目录后目录权限自动更改为&#x200B;*允许*&#x200B;的问题。
* **MDVA-30428** (*适用于Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修复了以下问题：如果将该产品分配给自定义库存源，则客户无法将产品添加到愿望清单。
* **MDVA-28661** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2，带有B2B扩展*) — 修复了在更改公司管理员后，“公司用户”公司帐户部分引发错误的问题。

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*适用于Adobe Commerce 2.3.1 - 2.3.4-p2*) — 修复了数据库名称太长时导致cron作业失败，进而导致前端未更新类别的问题。
* **MDVA-30106** (*用于Adobe Commerce ^2.3.0*) — 修复了结账期间付款未加载&#x200B;*JS控制台中出现*&#x200B;错误“无法读取null的属性‘长度’”的问题。
* **MDVA-28656** (*用于Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) — 修复了以下问题：如果下订单时不需要付款信息（例如，100%折扣），并且为订单创建了发票，则订单状态将更改为&#x200B;*已关闭*，而不是“完成”。
* **MDVA-30209** (*适用于Adobe Commerce 2.3.0 - 2.3.3-p1*) — 修复了客户更新其帐户信息时客户组更改为默认的问题。
* **MDVA-30123** (*用于Adobe Commerce >=2.3.4 &lt;2.4.2*) — 修复了未正确翻译GraphQL查询的属性选项标签的问题。
* **MDVA-29996** (*适用于Adobe Commerce >=2.3.3 &lt;2.4.2*) — 修复了在启用类别权限后，类别页面不会由完整页面缓存的问题。
* **MDVA-30164** (*适用于Adobe Commerce >=2.3.1 &lt;2.4.2*) — 修复了在存在自定义客户属性时无法从客户网格导出客户记录的问题。
* **MDVA-30444** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.1*) — 修复了使用GraphQL下订单时不会发送确认电子邮件的问题。
* **MDVA-30490** (*适用于Adobe Commerce 2.3.4 - 2.3.5-p2*) — 修复了以下问题：如果其中一个产品的简短描述为空，则产品比较会引发500错误页面。
* **MDVA-30232** (*适用于Adobe Commerce >=2.3.1 &lt;2.4.1*) — 修复了原始订单包含礼品卡时无法重新订购的问题。
* **MDVA-29965** (*适用于Adobe Commerce >=2.3.3 &lt;2.4.0*) — 修复了将产品添加到购物车时，客户收到“无效的表单密钥”错误的问题。
* **MDVA-30008** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.2*) — 修复了无法通过Admin API为公共目录中的产品下单的B2B问题。
* **MDVA-22469** (*适用于Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) — 修复了以下问题：升级到Adobe Commerce 2.3.3后，页面生成器在“管理”面板中无法正常工作，并且某些JS和CSS文件无法加载。
* **MC-35984** (*适用于Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修复了在为退货授权(RMA)创建配送标签后，商家无法与“退货”页面上的任何页面元素交互的问题。

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*适用于Adobe Commerce 2.3.0 - 2.3.4*) — 修复了[!DNL PayPal Payflow Pro]付款方法的问题，并在Chrome 80浏览器和API响应重定向到客户登录页面中将Cookie默认视为`SameSite=Lax`。
* **MDVA-26694** (*用于Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) — 修复了产品和目录缓存每天过期的问题，但过期时间安排不同。
* **MDVA-27825** (*适用于Adobe Commerce >=2.3.0 &lt;2.4.1*) — 修复了因内存泄漏导致导出大量数据失败的问题。
* **MDVA-29085** (*适用于Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) — 修复了通过API创建公司时未发送所需新公司电子邮件的B2B问题。
* **MDVA-29344** (*适用于Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) — 修复了页面生成器在将文本从标题元素复制到文本元素后卡住的问题。
* **MDVA-29835** (*适用于Adobe Commerce >2.3.1 &lt;2.4.2*) — 修复了礼品卡订单包含两个代码而不是一个代码的问题。
* **MDVA-30052** (*适用于Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) — 修复了私有内容（本地存储）未正确填充而导致性能问题的情况。
* **MDVA-30131** (*用于Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) — 修复了分层导航的问题，在该问题中，如果使用[!DNL Elasticsearch]作为搜索引擎，则分层导航中不包含布尔类型产品属性的&#x200B;*No*&#x200B;值。
* **MDVA-35514** (*适用于Adobe Commerce >=2.4.0 &lt;2.4.1*) — 修复了在“创建包”模式窗口中创建送货标签并将订购的产品添加到包时出现的问题。
