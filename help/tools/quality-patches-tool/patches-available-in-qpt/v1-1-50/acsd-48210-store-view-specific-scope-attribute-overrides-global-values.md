---
title: ACSD-48210：存储视图特定的范围属性将覆盖全局值
description: 应用ACSD-48210修补程序以修复在特定存储视图中更新*[!UICONTROL Website Scope]*属性会覆盖全局范围内的属性值这一Adobe Commerce问题。
feature: Products, Attributes
role: Admin, Developer
exl-id: 944089c6-2f05-4c51-86ea-ede124bff80b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-48210：存储视图特定的作用域属性覆盖全局值

ACSD-48210修补程序修复了在特定存储视图内更新&#x200B;*[!UICONTROL Website Scope]*&#x200B;属性时覆盖全局范围内的属性值的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50时，此修补程序可用。 修补程序ID为ACSD-48210。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

更新特定存储视图中的&#x200B;*[!UICONTROL Website Scope]*&#x200B;属性时，将覆盖全局范围中的属性值。

导入产品价格时，如果多个行共享相同的`SKU`和`store_view_code`，则会导致&#x200B;*[!UICONTROL All Store View]*&#x200B;和&#x200B;*[!UICONTROL Default Store]*&#x200B;范围内的价格更新不正确。 修改特定商店视图中的网站范围属性不再覆盖全局范围中的属性值。
<u>重现步骤</u>：

1. 将&#x200B;*[!UICONTROL Catalog Price Scope]*&#x200B;配置为&#x200B;*[!UICONTROL Website]*。
1. 创建名为&#x200B;*SP01*&#x200B;的简单产品并将价格设置为&#x200B;*$84.50*。
1. 使用以下提供的CSV导入产品：

   ```
   sku,store_view_code,price
   SP01,default,99.99
   SP01,default,86.59
   ```

1. 检查&#x200B;*[!UICONTROL All Store View]*&#x200B;和&#x200B;*[!UICONTROL Default Store]*&#x200B;范围中的产品价格。

<u>预期的结果</u>：

* 第一个非空值用于&#x200B;*[!UICONTROL Default Store]*&#x200B;范围。
* *[!UICONTROL All Store View]*&#x200B;范围保持不变。

<u>实际结果</u>：

* *[!UICONTROL All Store View]*&#x200B;范围价格更改为&#x200B;*$86.59*。
* *[!UICONTROL Default Store]*&#x200B;范围价格更改为&#x200B;*$86.59*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
