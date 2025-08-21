---
title: ACSD-62415： Adobe Commerce后端加载[!UICONTROL Categories]非常慢
description: 应用ACSD-62415修补程序以修复Adobe Commerce问题：当存在大量锚点类别时，[!UICONTROL Categories]面板中的[!UICONTROL Admin]页面的性能加载非常慢。
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8040414630cf3c992e0d68d5693990f8f50fdbcb
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# ACSD-62415：当存在锚点类别时，Adobe Commerce后端加载&#x200B;**[!UICONTROL Categories]**&#x200B;的速度非常慢

ACSD-62415修补程序修复了在存在大量锚点类别时，**[!UICONTROL Categories]**&#x200B;面板中&#x200B;**[!UICONTROL Admin]**&#x200B;页面的性能加载非常缓慢的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68时，此修补程序可用。 修补程序ID为ACSD-62415。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当存在大量锚点类别时，**[!UICONTROL Categories]**&#x200B;面板中的&#x200B;**[!UICONTROL Admin]**&#x200B;页面加载非常慢。

<u>重现步骤</u>：

1. 生成3000个锚点类别。
1. 在&#x200B;**[!UICONTROL Catalog]**&#x200B;面板中打开&#x200B;**[!UICONTROL Categories]** > **[!UICONTROL Admin]**&#x200B;页面。

<u>预期的结果</u>：

**[!UICONTROL Categories]**&#x200B;页面会快速加载，查询不应重复1K次。

<u>实际结果</u>：

加载需要7到20秒，并且查询运行超过1,000次。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
