---
title: ACSD-54040：启用B2B模块时，订单详细信息中的[!UICONTROL Created]字段为空
description: Adobe Commerce应用ACSD-54040修补程序以修复以下问题：启用B2B模块后，订单详细信息页面上的[!UICONTROL Created]字段为空。
feature: B2B
role: Admin, Developer
exl-id: 09fc1e0f-2e02-4cfc-9a7a-7c6aacd9fee0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-54040：启用B2B模块时，订单详细信息中的&#x200B;*[!UICONTROL Created]*&#x200B;字段为空。

ACSD-54040修补程序修复了启用B2B模块后，订单详细信息页面上的&#x200B;*[!UICONTROL Created]*&#x200B;字段保持空白的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40时，此修补程序可用。 修补程序ID为ACSD-54040。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4-p5、2.4.4-p6、2.4.5-p4、2.4.5-p5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

启用B2B模块后，订单详细信息页面上的&#x200B;*[!UICONTROL Created]*&#x200B;字段保持空白。

<u>重现步骤</u>：

1. 在B2B模块中安装Adobe Commerce 。
1. 创建新客户并下订单。
1. 转到前端上的订单详细信息并检查&#x200B;*[!UICONTROL Created]*&#x200B;字段。

<u>预期的结果</u>：

*[!UICONTROL Created]*&#x200B;字段显示创建订单的日期。

<u>实际结果</u>：

*[!UICONTROL Created]*&#x200B;字段为空

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
