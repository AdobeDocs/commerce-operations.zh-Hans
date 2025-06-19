---
title: ACSD-50813：管理员无法添加包含斜杠的捆绑产品
description: 应用ACSD-50813修补程序以修复Adobe Commerce性能问题，该问题导致管理员无法通过*Add Products by SKU*功能在SKU中添加包含斜杠('/')的捆绑产品，进而导致管理员订单无法处理。
exl-id: ff6fa673-bac1-4ef8-a427-60c2f56068f3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-50813：管理员无法添加包含斜杠的捆绑产品

ACSD-50813修补程序修复了以下问题：管理员无法在具有&#x200B;*[!UICONTROL Add Products by SKU]*&#x200B;功能的SKU中将包含斜杠(`/`)的捆绑产品添加到管理员订单中。 安装[!DNL Quality Patches Tool (QPT)] 1.1.34时，此修补程序可用。 修补程序ID为ACSD-50813。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

管理员无法在具有&#x200B;*[!UICONTROL Add Products by SKU]*&#x200B;功能的SKU中将包含斜杠(`/`)的捆绑产品添加到管理员订单中。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**。
1. 创建一个简单的产品。
1. 创建新的捆绑产品。
1. 在SKU中间添加斜杠(`/`)（示例： *Bu/ndle*）。
1. 添加一个捆绑选项，其中&#x200B;**[!UICONTROL Input Type]** = *[!UICONTROL Dropdown]*。
1. 为选项至少分配一个简单产品。
1. 转到&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Orders]**，然后创建新订单。
1. 单击&#x200B;**[!UICONTROL Add Products by SKU]**。
1. 输入您的SKU，然后单击&#x200B;**[!UICONTROL Add to Order]**。
1. 打开浏览器控制台。
1. 单击&#x200B;**[!UICONTROL Configure]**。

<u>预期的结果</u>：

没有错误。

<u>实际结果</u>：

控制台中出现JS错误：

*未捕获错误：语法错误，无法识别的表达式： div[id=sku_bu/ndle]*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
