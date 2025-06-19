---
title: ACP2E-3841：当使用子选择条件并启用免费配送时，多配送产品的购物车价格规则无法正确应用
description: 应用ACP2E-3841补丁以修复以下问题：当使用子选择条件并启用免费运送时，Adobe Commerce问题导致无法正确应用多配送产品的购物车价格规则。
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 73979b71-9b15-4a4b-a1c9-37d3213c177f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACP2E-3841：当使用子选择条件并启用免费配送时，多配送产品的购物车价格规则无法正确应用

ACP2E-3841修补程序修复了以下问题：当使用子选择条件并启用了免费运送时，多配送产品的购物车价格规则无法正确应用。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64时，此修补程序可用。 修补程序ID为ACP2E-3841。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p9

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.7-p5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用子选择条件并启用免费配送时，多配送产品的购物车价格规则无法正确应用。

<u>先决条件</u>：

**设置：**
1. **[!UICONTROL Free Shipping]** = *已启用*
1. **[!UICONTROL Minimum Order Amount]** = *99999999*

**所需类别：**
1. 类别测试1
1. 类别测试2

**所需产品：**
1. 产品测试1：
   1. 类别：类别测试1
   1. 价格：45美元
1. 产品测试2：
   1. 类别：类别测试2
   1. 价格：56.25美元 

      **（价格必须与此处显示的相同，以确保测试正常工作。）**

**购物车价格规则：**

以管理员身份登录，然后转到&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add new rule]**。 使用以下值：

**[!UICONTROL Rule Information]：**
1. **[!UICONTROL Rule Name]**：免费试用
1. **[!UICONTROL Active]**： *是*
1. **[!UICONTROL Websites]**： *主网站*
1. **[!UICONTROL Customer Groups]**： *未登录，常规，批发，Retailer*
1. **[!UICONTROL Coupon]**： *没有优惠券*
1. **[!UICONTROL Uses per Customer]**： *0*
1. **[!UICONTROL Priority]**： *1*

**[!UICONTROL Conditions]：**

**[!UICONTROL If ALL of these conditions are TRUE:]**


**[!UICONTROL If total amount (incl. tax) equals or greater than 100 for a subselection of items in cart matching ALL of these conditions:]**


**[!UICONTROL Category is]** *5,12,13*

操作：

**[!UICONTROL Percent of product price discount]** = *10*

<u>重现步骤</u>：

1. 登录商店前面。
2. 添加产品测试1。
3. 添加两个数量的产品测试2。
4. 访问购物车。
5. 选择&#x200B;**[!UICONTROL Check Out with Multiple Addresses]**。

<u>预期的结果</u>：

没有错误。

<u>实际结果</u>：

*500错误*

*消息：已弃用的功能：从float 112.5到int的隐式转换在/app/code/Magento/SalesRule/Model/Rule/Condition/Product/Subselect.php第214*&#x200B;行中失去精度

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
