---
title: ACSD-66965： [!UICONTROL Print]页面上的[!UICONTROL Requisition List]选项导致错误
description: 应用ACSD-66965修补程序以修复Adobe Commerce中[!UICONTROL Print]页面上的[!UICONTROL Requisition List]选项导致错误的问题。
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7682a326a6c703a08dd6d0fac5319ac38e1bc3c8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# ACSD-66965： **[!UICONTROL Print]**&#x200B;页面上的&#x200B;**[!UICONTROL Requisition List]**&#x200B;选项导致错误

ACSD-66965修补程序修复了&#x200B;**[!UICONTROL Print]**&#x200B;页面上的&#x200B;**[!UICONTROL Requisition List]**&#x200B;选项导致错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68时，此修补程序可用。 修补程序ID为ACSD-66965。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

由于&#x200B;**[!UICONTROL Print]**&#x200B;中的null对象引用，**[!UICONTROL Requisition List]**&#x200B;页面上的`Grid.php`选项会导致错误。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**。
1. 将&#x200B;**[!UICONTROL Enable Company]**、**[!UICONTROL Enable Shared Catalog]**&#x200B;和&#x200B;**[!UICONTROL Enable Requisition List]**&#x200B;设置为`Yes`。
1. 创建两个简单的产品。
1. 登录到店面并打开&#x200B;**[!UICONTROL My Account]**&#x200B;页面。
1. 创建申请列表。
1. 将两个产品分配给申请列表。
1. 访问申请列表并列出产品。
1. 单击&#x200B;**[!UICONTROL Print]**。

<u>预期的结果</u>：

**[!UICONTROL Print]**&#x200B;页上的&#x200B;**[!UICONTROL Requisition List]**&#x200B;选项显示打印预览，没有出现错误。

<u>实际结果</u>：

出现以下错误消息： *应用程序运行期间发生错误。 有关详细信息，请参阅异常日志。*

```
Call to a member function setCollection() on null in /vendor/magento/module-requisition-list/Block/Requisition/View/Items/Grid.php:146
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
