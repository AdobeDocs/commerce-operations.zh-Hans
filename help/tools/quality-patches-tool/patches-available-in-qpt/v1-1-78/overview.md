---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.78
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.78中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: a26830c032f09a41f857afe2f10b8886fbe495e5
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.78

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.78中提供的修补程序所修复的问题。

QPT v1.1.78包含以下修补程序：

1. **[ACP2E-4456](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4456.md)**：修复了使用GraphQL突变取消订单时无法将完全使用礼品卡支付的订单转换为“已关闭”状态的问题。
1. **[ACP2E-4452](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4452.md)**：修复了[!UICONTROL Quick Order]页面上的产品价格包含税的问题，无论显示税配置如何。
1. **[ACP2E-4513](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4513.md)**：修复了未从系统中删除过期验证码图像的问题。
1. **[ACP2E-4448](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4448.md)**：修复了在Redis中断期间所做的配置更改在Redis恢复后未反映出来，从而导致保留过时值的问题。
1. **[ACP2E-4416](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4416.md)**：修复了在管理员中创建客户奖励点时未初始化的问题。
1. **[ACP2E-4431](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4431.md)**：修复了在重新索引过程中删除与目标规则匹配的[!UICONTROL Related Products]的问题。
1. **[ACP2E-4419](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4419.md)**：修复了在店面成功进行reCAPTCHA v2（“我不是机器人”）验证后，礼品卡在结账时未正确应用的问题。
1. **[ACP2E-4507](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4507.md)**：修复了以下问题：[!UICONTROL Password Options]配置未应用于通过GraphQL突变进行的客户密码重置请求。
1. **[ACP2E-4522](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4522.md)**：修复了在同时运行多个购物车合并或报价保存请求时，`quote_coupons`表中发生间歇性重复键错误的问题。
1. **[ACP2E-4528](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4528.md)**：修复了客户地址中的城市验证问题，该问题现在允许使用正斜杠(/)字符并拒绝无效字符，如！、&#39;、#和？。
1. **[ACP2E-4535](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4535.md)**：修复了提交忘记密码表单导致会话被销毁或重新生成（PHPSESSID更改）并且访客购物车被清除的问题。
1. **[ACP2E-4591](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4591.md)**：修复了基于“首次购买者”等订单计数的客户区段在通过REST API下订单时未更新的问题。
1. **[ACP2E-4540](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4540.md)**：修复了Fotorama库未正确加载，导致仅显示附加的第一个图像的问题。
1. **[ACP2E-4555](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4555.md)**：修复了包含“。”的现代电话号码的问题。 或“/”未正确验证。
1. **[ACP2E-4565](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4565.md)**：修复了在使用X-Adobe-Company标头时，GraphQL公司查询返回“当前客户未获得授权”的问题。
1. **[ACP2E-4609](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4609.md)**：修复了当某些引号包含已删除的产品时，“我的引号”页面不显示引号的问题。
1. **[ACP2E-4613](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4613.md)**：修复了大型媒体目录结构导致gettree响应缓慢，从而导致&#x200B;**[!UICONTROL Media Gallery]**&#x200B;目录树的加载时间延长的问题。
1. **[ACP2E-4628](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4628.md)**：修复了将“帐户共享”设置为“全局”时，导入具有大写电子邮件地址的客户会导致未定义数组键值错误的问题。
1. **[ACP2E-4763](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4763.md)**：修复了将目录价格设置为“含税”时，由于应用了两次税，GraphQL customerOrders查询返回夸大的`original_price_including_tax`和`original_row_total_including_tax`值的问题。
1. **[ACP2E-4732](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4732.md)**：修复了当changelog表中的`version_id`列达到其最大值时，具有大量更新的客户停止部分索引的问题。
1. **[ACP2E-4665](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4665.md)**：修复了在通过REST API请求时，产品库中包含视频的可配置产品的子产品未列出的问题。
1. **[ACSD-60989](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acsd-60989.md)**：修复了通过声明性架构修改带有外键的列会在MariaDB上导致错误的问题。

使用左侧的菜单导航到特定的修补程序页面。
