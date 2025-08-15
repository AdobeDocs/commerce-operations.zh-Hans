---
title: ACP2E-3689：类别树在更深层显示并反映锚点/非锚点关系的多个问题
description: 应用ACP2E-3689补丁修复了Adobe Commerce问题，该问题导致在超过四个深度的嵌套中显示类别树，并反映锚点/非锚点关系。
feature: Categories, Page Content
role: Admin, Developer
exl-id: 8d3c484f-3f8d-4fc1-8b31-e850cb34341c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACP2E-3689：类别树在更深层显示并反映锚点/非锚点关系的多个问题

>[!NOTE]
>
>此修补程序取代了版本2.4.7及更高版本的[ACSD-62689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-62689-customer-add-categories-issue-related-product-rules-and-widgets.md)。

ACP2E-3689修补程序修复了类别树在深度超过四个嵌套和反映锚点/非锚点关系的多个问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61时，此修补程序可用。 修补程序ID为ACP2E-3689。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

较深级别(4+)的类别树无法正确显示，且反映的是锚点/非锚点关系。

<u>重现步骤</u>：

1. 设置包含超过4个级别的嵌套类别的类别树。
1. 在Admin中展开显示在不同位置的类别树：
   1. 设置[!UICONTROL Related Products Rule]并根据类别设置条件。
   1. 创建构件，在[!UICONTROL Layout Updates]中选择[!UICONTROL Anchor categories]。

<u>预期的结果</u>：

正确显示类别树的所有级别。

<u>实际结果</u>：

只有类别树的前几个级别(&lt;4)可用。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
