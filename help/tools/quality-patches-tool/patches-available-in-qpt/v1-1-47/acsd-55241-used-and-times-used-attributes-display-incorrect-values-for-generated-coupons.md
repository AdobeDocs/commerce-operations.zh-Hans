---
title: “ACSD-55241：**已使用**和**已使用次数**属性显示的已生成优惠券值不正确”
description: 应用ACSD-55241修补程序以修复Adobe Commerce问题，该问题导致**已使用**和**使用次数**属性显示生成的赠券的值不正确
feature: Price Rules
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# ACSD-55241： **已使用**&#x200B;和&#x200B;**已使用次数**&#x200B;属性显示生成的赠券的值不正确

ACSD-55241修补程序修复了&#x200B;**已使用**&#x200B;和&#x200B;**已使用次数**&#x200B;属性显示生成的优惠券的值不正确的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.47时，此修补程序可用。 修补程序ID为ACSD-55241。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

**已使用**&#x200B;和&#x200B;**已使用次数**&#x200B;属性显示的已生成优惠券值不正确。

<u>重现步骤</u>：

1. 从&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]**&#x200B;创建&#x200B;**[!UICONTROL Cart Price Rules]**&#x200B;并在下订单时添加任何匹配的条件（示例：小计大于&#x200B;*5$*）

   * 应用任何折扣。
   * 选择&#x200B;**[!UICONTROL Auto Coupon]**。
   * 它将通过&#x200B;**管理优惠券代码**&#x200B;生成几个优惠券代码。
   * 重新索引并清理缓存。

1. 创建&#x200B;**[!UICONTROL customer account]**&#x200B;并登录到前端。
1. 在购物车中添加一个数量超过&#x200B;*2*&#x200B;的产品，然后应用一个优惠券。
1. 单击&#x200B;**[!UICONTROL Check Out with Multiple Addresses]**。
1. 为每个数量选择单独的地址，下订单，然后完成结帐流程。
1. 观察管理员的订单总额并查看应用的折扣。
1. 使用其他优惠券再次下订单。
1. 运行`php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &`命令以更新优惠券代码用法。

<u>预期的结果</u>：

正确的计数应显示在管理员中&#x200B;**[!UICONTROL cart price rule]**&#x200B;的&#x200B;**已用时间**&#x200B;和&#x200B;**已用**&#x200B;列中，其中&#x200B;**[!UICONTROL manage coupon]**&#x200B;的&#x200B;**是**&#x200B;值。

<u>实际结果</u>：

在优惠券网格的&#x200B;**已使用时间**&#x200B;列中，已使用优惠券代码计数不会更新，如果您下订单时带有多个配送地址，**已使用**&#x200B;列将显示&#x200B;*否*&#x200B;值。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
