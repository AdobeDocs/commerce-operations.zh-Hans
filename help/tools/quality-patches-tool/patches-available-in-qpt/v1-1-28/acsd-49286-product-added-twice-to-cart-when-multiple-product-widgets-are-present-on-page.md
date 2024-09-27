---
title: 'ACSD-49286：当存在多个产品小组件时，将产品添加到购物车两次'
description: 应用ACSD-49286修补程序以修复Adobe Commerce问题：当页面上存在多个产品小组件时，产品会向购物车中添加两次。
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49286：当存在多个产品构件时，将产品添加到购物车两次

ACSD-49286修补程序修复了当页面上存在多个产品小组件时，将产品两次添加到购物车的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28时，此修补程序可用。 修补程序ID为ACSD-49286。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当页面上存在多个产品小组件时，会将产品添加到购物车两次。

<u>重现步骤</u>：

1. 登录到管理员并转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. 在内容部分中，使用[!DNL Page Builder]单击&#x200B;**[!UICONTROL Edit]**。
1. 向&#x200B;**[!UICONTROL Content]**&#x200B;添加两个行元素。
1. 将产品添加到这两个行元素中。
1. 在第一行中，将产品外观设置为[!UICONTROL Product Grid]并选择要显示的任何类别。
1. 在第二行中，将产品外观设置为[!UICONTROL Product Carousel]并选择要显示的任何其他类别。
1. 转到店面&#x200B;**[!UICONTROL Home Page]**，并从产品网格添加一个产品。
1. 从[!UICONTROL Product Carousel]添加其他产品。

<u>预期的结果</u>：

将产品从[!UICONTROL Product Grid]添加到购物车后，产品数量不应加倍。

<u>实际结果</u>：

将产品从[!UICONTROL Product Grid]添加到购物车后，产品数量会翻倍。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。 

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
