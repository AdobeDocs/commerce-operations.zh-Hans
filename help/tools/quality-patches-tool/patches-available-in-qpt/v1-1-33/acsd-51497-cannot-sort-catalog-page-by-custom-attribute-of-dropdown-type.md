---
title: 'ACSD-51497：无法按“下拉列表”类型的自定义属性对目录页面排序'
description: 应用ACSD-51497修补程序以修复客户无法按下拉类型的自定义属性对目录页面进行排序的Adobe Commerce问题。
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-51497：无法按&#x200B;*Dropdown*&#x200B;类型的自定义属性对目录页面进行排序

ACSD-51497修补程序修复了客户无法按&#x200B;*下拉列表*&#x200B;类型的自定义属性对目录页面进行排序的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33时，此修补程序可用。 修补程序ID为ACSD-51497。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.3.7-p4、2.4.1 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

客户无法按&#x200B;*Dropdown*&#x200B;类型的自定义属性对目录页面进行排序。

<u>重现步骤</u>

1. 创建大约六个简单产品并将它们分配给单个类别。
1. 创建产品属性，以将其添加为列表页面上的排序选项。

   * 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]**。
   * 在&#x200B;**[!UICONTROL Properties]**&#x200B;选项卡中，设置以下内容：

      * *[!UICONTROL Default Label]* = *测试*
      * 商店所有者的&#x200B;*[!UICONTROL Catalog Input Type]* = *下拉列表*
      * *[!UICONTROL Options]*：

         * *第一个*
         * *秒*
         * *第三*
         * *第四*

   * 在&#x200B;**[!UICONTROL Storefront Properties]**&#x200B;选项卡中，设置以下内容：

      * *[!UICONTROL Used for sorting in product listing]* = *是*
      * 将所有其他选项保留为&#x200B;*默认值*。

1. 将&#x200B;*test*&#x200B;属性分配给&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**&#x200B;中设置的&#x200B;*Default*&#x200B;属性。
1. 将产品配置为具有&#x200B;*test*&#x200B;属性值。

   * SKU： s00001，测试：第四
   * SKU： s00002，测试：第三
   * SKU： s00003，测试：秒
   * SKU：s00004，测试：第一个
   * SKU： s00005，测试：第四
   * SKU： s00006，测试：第三

1. 重新索引并清除缓存。
1. 转到店面上的类别。
1. 按&#x200B;*test*&#x200B;属性排序。

<u>预期的结果</u>：

产品按&#x200B;*test*&#x200B;属性排序。

<u>实际结果</u>：

产品未按&#x200B;*test*&#x200B;属性排序。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
