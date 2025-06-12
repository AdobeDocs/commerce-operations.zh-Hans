---
title: ACSD-51408：订单项状态错误地设置为[!UICONTROL backordered]
description: 应用ACSD-51408修补程序以修复订单项状态错误设置为[!UICONTROL backordered]的Adobe Commerce问题。
feature: B2B, Orders
role: Admin
exl-id: 51abb4c6-5618-43a5-89ca-a3879be2c3c4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# ACSD-51408：订单项状态错误地设置为&#x200B;*[!UICONTROL backordered]*

ACSD-51408修补程序修复了订单项状态错误设置为[!UICONTROL backordered]的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.33时，此修补程序可用。 修补程序ID为ACSD-51408。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

订单项目状态错误地设置为&#x200B;*[!UICONTROL backordered]*。

<u>先决条件</u>：

已安装Adobe Commerce B2B和Inventory management (MSI)模块。

<u>重现步骤</u>：

1. 创建新网站、商店和商店视图。
1. 创建新源。
1. 创建链接到在步骤1中创建的新网站的新库存，并分配在步骤2中创建的源。
1. 创建公司并将其分配给在第1步中创建的新网站。
1. 创建新客户并将其分配给在步骤4中创建的公司。
1. 创建产品，将其分配给新网站，并将&#x200B;**[!UICONTROL default stock]** = *0*&#x200B;和&#x200B;**[!UICONTROL new stock]**&#x200B;设置为大于&#x200B;*0*。
1. 启用&#x200B;**[!UICONTROL backorders]**。
1. 为新网站范围启用&#x200B;**[!UICONTROL Check/Money Order]**&#x200B;付款方式。
1. 为新网站范围启用&#x200B;**[!UICONTROL Flat Rate shipping method]**。
1. 从&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]**&#x200B;创建新订单。
1. 选择在步骤5中创建的新客户。
1. 选择在步骤1中创建的新存储。
1. 选择在步骤6中创建的产品。
1. 填写订单信息，包括付款和运送方式。
1. 提交订单。
1. 检查&#x200B;*项目状态*。

<u>预期的结果</u>

可从库存中发运物料。 项目状态为&#x200B;*[!UICONTROL ordered]*。

<u>实际结果</u>

项目状态为&#x200B;*[!UICONTROL backordered]*。

>[!MORELIKETHIS]
>
>当产品库存为0时，[订单项状态错误地设置为&#x200B;*[!UICONTROL Ordered]*。](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
