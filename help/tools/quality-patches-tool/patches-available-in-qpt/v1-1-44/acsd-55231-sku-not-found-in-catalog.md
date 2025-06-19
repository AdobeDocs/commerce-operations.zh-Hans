---
title: ACSD-55231：使用快速订购功能时出现“未找到SKU”错误
description: Adobe Commerce应用ACSD-55231修补程序以修复以下问题：当尝试使用快速订购功能将产品添加到购物车时，出现*“在目录中未找到SKU”*错误。
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: f0a04773-7395-4945-a72b-5a6a018bc94e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# ACSD-55231：使用快速订购功能时出现“未找到SKU”错误

ACSD-55231修补程序修复了以下问题：当您尝试使用快速订购功能将产品添加到购物车时，出现&#x200B;*“在目录中找不到SKU”*&#x200B;错误。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44时，此修补程序可用。 修补程序ID为ACSD-55231。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

获取&#x200B;*”在使用快速订购功能搜索要添加到购物车的产品时，在目录“*”中找不到SKU错误。

<u>重现步骤</u>：

1. 安装Adobe Commerce和B2B模块。
1. 导航到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]**&#x200B;并设置：
   * **[!UICONTROL Enable company]**： *是*
   * **[!UICONTROL Enable Shared Catalog]**： *是*
   * **[!UICONTROL Enable Quick Order]**： *是*
1. 保存上述配置。
1. 转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]**&#x200B;并创建新共享目录。
1. 导航到&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL All Customers]**&#x200B;并创建新客户：
   * 在“组”字段中，选择最近创建的共享目录并将&#x200B;*[!UICONTROL Allow remote shopping assistance]*&#x200B;设置为&#x200B;*是*。
1. 生成带有SKU *p12*&#x200B;的简单产品，将其与类别&#x200B;*c1*&#x200B;关联，然后在[!UICONTROL Product in Shared Catalog]部分中选择新创建的共享目录。
1. 运行：

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. 刷新管理页面。
1. 导航到&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL All Customers]**&#x200B;并编辑之前创建的客户。
1. 单击&#x200B;**[!UICONTROL Login as customer]**。
1. 转到&#x200B;**[!UICONTROL Quick order]**。
1. 搜索&#x200B;*p12* SKU并单击&#x200B;**[!UICONTROL Product Suggestion]**。
1. 将此产品添加到购物车并下订单。
1. 返回&#x200B;**[!UICONTROL Quick Order]**，再次搜索SKU *p12*，然后单击&#x200B;**[!UICONTROL Product Suggestion]**。

<u>预期的结果</u>：

您可以使用快速订购功能将产品添加到购物车。

<u>实际结果</u>：

无法使用快速订购功能将产品添加到购物车并获取&#x200B;*。搜索产品SKU时，在目录“*”中找不到SKU出错。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
