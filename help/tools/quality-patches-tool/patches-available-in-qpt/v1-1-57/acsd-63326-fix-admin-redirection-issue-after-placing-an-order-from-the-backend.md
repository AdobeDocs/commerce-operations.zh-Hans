---
title: ACSD-63326：修复了从后端下订单后的管理员重定向问题
description: 应用ACSD-63326修补程序以修复Adobe Commerce问题，该问题导致管理员在后端下订单后重定向到损坏的页面。
feature: Orders, Admin Workspace
role: Admin, Developer
source-git-commit: 47603deecdf5ac3e6be18efeef38cba52ec936ec
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63326：修复了从后端下订单后的管理员重定向问题

ACSD-63326修补程序修复了从后端下订单后将管理员重定向到断开页面的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57时，此修补程序可用。 修补程序ID为ACSD-63326。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.7-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.2 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

成功从后端为客户下达订单后，管理员将被重定向到布局中断的页面。

<u>重现步骤</u>：

1. 导航到“管理员”面板中的&#x200B;**[!UICONTROL Customers]**&#x200B;部分。
1. 选择任意客户并单击&#x200B;**[!UICONTROL Edit]**。
1. 在客户详细信息页面上，单击顶部菜单中的&#x200B;**[!UICONTROL Create Order]**。
1. 选择[!UICONTROL FR French]商店并将任何可用产品添加到该订单。
1. 在结账时填写所需的详细信息，然后单击&#x200B;**[!UICONTROL Get shipping methods and rates]**。
1. 单击&#x200B;**[提交订单]**&#x200B;以下订单。

<u>预期的结果</u>：

系统会将管理员重定向至订单确认或感谢页面，页面布局正确。

<u>实际结果</u>：

管理员将被重定向到布局不完整的页面。 仅在刷新页面后更正布局。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
