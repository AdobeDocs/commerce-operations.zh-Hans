---
title: ACSD-54680：无法处理具有多个已分配来源的产品的B2B报价
description: 应用ACSD-54680修补程序以修复无法处理具有多个已分配来源的产品的B2B报价的Adobe Commerce问题。
feature: B2B
role: Admin, Developer
exl-id: c5307785-a4c6-4d0c-9009-0d0caee97b3d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-54680：无法处理具有多个已分配来源的产品的B2B报价。

ACSD-54680修补程序修复了无法处理具有多个已分配源的产品的B2B报价的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.40时，此修补程序可用。 修补程序ID为ACSD-54680。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

无法处理具有多个已分配来源的产品的B2B报价。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]**&#x200B;并创建两个新源： **Source 1**&#x200B;和&#x200B;**Source 2**。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]**&#x200B;并创建新库存： **库存A**，将其分配给主网站，然后将&#x200B;**Source 1**&#x200B;和&#x200B;**Source 2**&#x200B;分配给它。
1. 创建简单产品，分配&#x200B;**Source 1**&#x200B;和&#x200B;**Source 2**，并为每个源设置数量= *2*。 （因此，产品的可销售数量应为&#x200B;*4*）。
1. 创建公司帐户。
1. 转到&#x200B;**[!UICONTROL Storefront]**&#x200B;并登录到公司帐户。
1. 将简单产品添加到购物车，其数量= *4*。
1. 打开&#x200B;*[!UICONTROL Shopping cart]*&#x200B;并单击&#x200B;**[!UICONTROL Request a quote]**&#x200B;按钮。
1. 添加评论和报价名称，然后单击&#x200B;**[!UICONTROL Send a Request]**&#x200B;按钮。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**。
1. 打开最近提交的报价。

<u>预期的结果</u>：

引用项包含订购的产品。

<u>实际结果</u>：

引用页面中的项目部分为空，无法处理报价。
`var/log/system.log`包含

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
