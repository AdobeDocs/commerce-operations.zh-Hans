---
title: ACSD-54739： *[!UICONTROL Product Stock]*状态未应用于*[!UICONTROL Related Product Rules]*
description: 应用ACSD-54739修补程序以修复未对*[!UICONTROL Related Product Rules]*应用*[!UICONTROL Product Stock]*状态的Adobe Commerce问题。
feature: Products
role: Admin, Developer
exl-id: d6d3b25d-b10e-4ccb-a9c4-b5c1c7773eb6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACSD-54739： *[!UICONTROL Related Product Rules]*&#x200B;未应用&#x200B;*[!UICONTROL Product stock]*&#x200B;状态

ACSD-54739修补程序修复了&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;未应用&#x200B;*[!UICONTROL Product stock]*&#x200B;状态的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43时，此修补程序可用。 修补程序ID为ACSD-54739。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

未对&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;应用&#x200B;*[!UICONTROL Product stock]*&#x200B;状态。

<u>重现步骤</u>：

1. 将&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;配置设置为&#x200B;*是*。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]**，并为促销规则条件设置&#x200B;*是*。
1. 创建相关的产品规则。 转至&#x200B;**[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** >添加具有属性数量的条件（选择有库存/无库存）。
1. 检查前端产品。

<u>预期的结果</u>：

由&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;匹配的有库存/无库存产品。

<u>实际结果</u>：

*[!UICONTROL Related Product Rules]*&#x200B;与有库存/无库存产品不匹配。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
