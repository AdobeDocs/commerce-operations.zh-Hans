---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.76
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.76中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 33361f8de36b1d3f346d216244efb413835d88ef
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.76

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.76中提供的修补程序所修复的问题。

QPT v1.1.76包含以下修补程序：
1. **[ACSD-67091](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67091.md)**：修复了最大写集大小错误，以确保通过实施两种基于数据卷的删除策略来清理目录规则产品索引。
1. **[ACSD-67370](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67370.md)**：修复了PDP/PLP上的捆绑包产品价格不正确以及多货币商店购物车页面显示错误的多个问题。
1. **[ACSD-68410](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-68410.md)**：修复了为可转让报价下订单时错误地添加或将其他购物车行合并到报价的问题。 现在，产品在退出可协商报价结账的最后一步后正确添加到购物车中。
1. **[ACSD-69086](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69086.md)**：修复了cron作业无法清除changelog表，在处理大量数据时导致[!DNL Galera Cluster]崩溃的问题。
1. **[ACSD-69115](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69115.md)**：修复了在管理分配给非默认网站的客户的购物车时，没有向管理员用户显示购物车错误的问题。
1. **[ACSD-69129](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69129.md)**：修复了以下问题：在尝试通过[!DNL REST] API更新辅助网站的层价格时，删除默认基本网站并将辅助网站用作默认网站会导致错误。
1. **[ACSD-69203](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69203.md)**：修复了在类别条件中列出了多个类别时，**[!UICONTROL Products List]**&#x200B;构件返回错误结果的问题。
1. **[ACSD-69261](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69261.md)**：修复了在部分发票中对`times_used`属性的处理不正确以及剩余数量取消方案中，配置为每位客户单次使用的购物车价格规则优惠券被多次重复使用的问题。
1. **[ACSD-69308](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69308.md)**：修复了在网站级别（而不是在`special_price`）设置&#x200B;**[!UICONTROL All Store Views]**&#x200B;时，目录价格规则不适用的问题。 修复之后，通过首先检查网站的默认商店，可正确应用目录价格规则。
1. **[ACSD-69319](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69319.md)**：修复了子产品在自定义来源下有库存时，捆绑价格未正确索引的问题。
1. **[ACSD-69325](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69325.md)**：修复了修改SKU案例导致产品在店面显示为缺货的问题。
1. **[ACSD-69331](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69331.md)**：修复了媒体集中的内容创建者无法创建仅具有`create_folder`权限的文件夹的问题。 修复后，他们可以按预期创建文件夹。
1. **[ACSD-69333](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69333.md)**：修复了允许对具有活动计划更新的产品进行SKU更改的问题。 修复后，在活动更新期间禁止SKU更改；保存失败并出现明确错误，并且禁用了管理员SKU字段。 这样可防止在暂存回滚期间由SKU更改导致的MSI库存不一致。
1. **[ACSD-69541](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69541.md)**：修复了以下问题：将[!UICONTROL Admin]中的产品数量减少到小于购物车中已有的产品数量，导致无法通过GraphQL编辑该购物车中的产品数量。

使用左侧的菜单导航到特定的修补程序页面。
