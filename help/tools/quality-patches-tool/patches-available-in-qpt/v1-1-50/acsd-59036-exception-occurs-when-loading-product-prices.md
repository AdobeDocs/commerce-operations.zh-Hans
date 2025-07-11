---
title: ACSD-59036：加载上下限均设置为$0的产品价格时出现异常
description: 应用ACSD-59036修补程序以修复Adobe Commerce问题：加载上下限均设置为*$0*的产品价格时出现异常。
feature: Categories, Products, Storefront, Search
role: Admin, Developer
exl-id: a7d05108-0b03-4eb4-84ab-0dc5601530cb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-59036：加载上下限均设置为&#x200B;*$0*&#x200B;的产品价格时出现异常

ACSD-59036修补程序修复了在加载上下限均设置为&#x200B;*$0*&#x200B;的产品价格时出现异常的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50时，此修补程序可用。 修补程序ID为ACSD-59036。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.7

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

加载上下限均设置为&#x200B;*$0*&#x200B;的产品价格时出现异常。

出现此问题的原因是，在加载具有价格范围的查询时，算法不考虑NULL值。 要解决此问题，我们可以检查上下限范围是否均为NULL，如果均为NULL，请为两个限制分配值&#x200B;*0*。 这样应可防止引发任何错误。

<u>重现步骤</u>：

1. 创建&#x200B;*13*&#x200B;简单产品。
1. 将所有&#x200B;*13*&#x200B;产品分配给类别。
1. 将一个产品的价格设置为&#x200B;*$1322.94*。
1. 将所有其他产品的价格设置为&#x200B;*$0*。
1. 将[!DNL OpenSearch]配置为搜索引擎。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]**，并将&#x200B;**[!UICONTROL PLP]**&#x200B;计数设置为&#x200B;*16*。
1. 将&#x200B;**[!UICONTROL Price Navigation Step Calculation]**&#x200B;设置为&#x200B;*自动（均衡产品计数）*。
1. 运行完全重新索引。
1. 打开&#x200B;*[!UICONTROL Category]*&#x200B;页面。

<u>预期的结果</u>：

*[!UICONTROL Category]*&#x200B;页面显示所有产品。

<u>实际结果</u>：

出现错误：

```JSON
report.CRITICAL: OpenSearch\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]"}],"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [filter]","caused_by":{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]","caused_by":{"type":"illegal_argument_exception","reason":"field name is null or empty"}}},"status":400} in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Connections/Connection.php:664
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
