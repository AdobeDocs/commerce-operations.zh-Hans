---
title: ACSD-58471：在计划了关联的目录价格规则时，无法在产品详细信息页面上加载动态内容
description: 应用ACSD-58471修补程序以修复在计划关联的目录价格规则时，在产品详细信息页面上加载动态内容失败的Adobe Commerce问题。
feature: Catalog Management
role: Admin, Developer
exl-id: 6ff68b74-67fc-400c-aa79-a1274fd19708
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-58471：在计划了关联的目录价格规则时，无法在产品详细信息页面上加载动态内容

ACSD-58471修补程序解决了在计划关联的目录价格规则时，在产品详细信息页面上加载动态内容失败的问题。 现在，系统在产品详细信息页面上正确显示与计划目录价格规则关联的动态内容。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55时，此修补程序可用。 修补程序ID为ACSD-58471。 请注意，此问题计划在Adobe Commerce 2.5.0中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
* Adobe Commerce（所有部署方法） 2.4.5-p4

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在计划目录价格规则时，产品详细信息页面上未加载动态内容。

<u>重现步骤</u>：

1. 在Commerce [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Dynamic Blocks]**&#x200B;中创建动态块。
1. 在[!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Blocks]**&#x200B;中创建静态块。 使用构件添加内容。
1. 创建产品并将CMS块添加到描述中。
1. 创建包含计划更新的目录规则，并在&#x200B;**[!UICONTROL Marketing]** >促销活动> **[!UICONTROL Catalog Products Rules]**&#x200B;中分配产品和创建的动态块。
1. 运行cron ，并检查产品详细信息页面是否显示在计划的开始时间之后的动态内容。
1. 创建没有计划更新的目录规则，并在&#x200B;**[!UICONTROL Marketing]** >促销活动> **[!UICONTROL Catalog Products Rules]**&#x200B;中分配产品和创建的动态块。
1. 运行cron ，并检查产品详细信息页面是否在计划时间之后显示动态内容。


<u>预期的结果</u>：

动态内容在计划的开始时间之后加载。

<u>实际结果</u>：

动态内容未加载。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
