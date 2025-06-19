---
title: ACSD-54319：产品价格在*[!UICONTROL Products in Carts]*报表中显示为零
description: 应用ACSD-54319修补程序以修复Adobe Commerce问题，该问题导致产品价格在*[!UICONTROL Products in Carts]*报表中显示为零
feature: Reporting, Products
role: Admin, Developer
exl-id: 10052d32-99f8-4b45-9fe9-a4c45bcaaa44
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-54319：产品价格在&#x200B;*[!UICONTROL Products in Carts]*&#x200B;报表中显示为零

ACSD-54319修补程序修复了&#x200B;*[!UICONTROL Products in Carts]*&#x200B;报表中产品价格为零的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40时，此修补程序可用。 修补程序ID为ACSD-54319。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品价格在&#x200B;*[!UICONTROL Products in Carts]*&#x200B;报表中显示为零。

<u>重现步骤</u>：

1. 从&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]**&#x200B;将&#x200B;**[!UICONTROL Catalog Price Scope]**&#x200B;设置为&#x200B;**[!UICONTROL Website]**。
1. 从&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL All Stores]**&#x200B;创建第二个网站。
1. 从&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;创建产品。
1. 仅将此产品分配给第二个网站。
1. 将产品从第二个网站添加到购物车。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > **[!UICONTROL Products In Carts]**&#x200B;网格。
1. 检查&#x200B;*[!UICONTROL Products In Carts]*&#x200B;网格中的&#x200B;*[!UICONTROL Price]*&#x200B;列。

<u>预期的结果</u>：

*[!UICONTROL Products in Carts]*&#x200B;报表网格中的产品价格不为零。

<u>实际结果</u>：

*[!UICONTROL Products in Carts]*&#x200B;报表网格中的产品价格为零。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
