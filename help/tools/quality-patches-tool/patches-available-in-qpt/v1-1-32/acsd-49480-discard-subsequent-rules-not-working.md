---
title: 'ACSD-49480：放弃后续规则不起作用'
description: 应用ACSD-49480修补程序以修复[!UICONTROL Cart Price Rule - Discard Subsequent Rules]无法按预期工作的Adobe Commerce问题。
feature: Price Rules
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-49480： [!UICONTROL Cart Price Rule - Discard Subsequent Rules]未按预期工作

ACSD-49480修补程序修复了[!UICONTROL Cart Price Rule - Discard Subsequent Rules]无法按预期工作的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.32时，此修补程序可用。 修补程序ID为ACSD-49480。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

[!UICONTROL Cart Price Rule - Discard Subsequent Rules]未按预期工作。

<u>重现步骤</u>：

1. 使用优惠券代码（将其命名为&#x200B;*TEST*）创建一个&#x200B;**[!UICONTROL Cart Price Rule]**，该代码为&#x200B;**[!UICONTROL Actions]**&#x200B;选项卡中的&#x200B;*产品ID 1*&#x200B;提供$10折扣，其中[!UICONTROL Discard Subsequent Rules]设置为&#x200B;*[!UICONTROL Yes]*，[!UICONTROL Priority]设置为&#x200B;*1*。
1. 创建另一个不含优惠券代码的&#x200B;**[!UICONTROL Cart Price Rule]**，该代码在&#x200B;**[!UICONTROL Actions]**&#x200B;选项卡中为&#x200B;*产品ID 2*&#x200B;提供$5的折扣，其中[!UICONTROL Priority]设置为&#x200B;*2*。 在本例中，我们假设这是针对&#x200B;*产品ID 2*&#x200B;的全球销售。
1. 转到前端网站并将&#x200B;*产品ID 1*&#x200B;和&#x200B;*产品ID 2*&#x200B;添加到购物车中。
1. 应用&#x200B;*TEST*&#x200B;优惠券代码。

<u>预期的结果</u>

* *折扣1*&#x200B;应用于&#x200B;*产品ID 1*。
* *折扣2*&#x200B;应用于&#x200B;*产品ID 2*。

<u>实际结果</u>

* 仅&#x200B;*折扣1*&#x200B;应用于&#x200B;*产品ID 1*。
* *折扣2*&#x200B;不适用于&#x200B;*产品ID 2*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
