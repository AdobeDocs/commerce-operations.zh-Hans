---
title: 'ACSD-54887：客户购物车在客户会话过期后清空'
description: 应用ACSD-54887修补程序以修复在启用[!UICONTROL Persistent Shopping Cart]的客户会话过期后客户购物车被清除的Adobe Commerce问题。
feature: Shopping Cart
role: Admin, Developer
source-git-commit: 52742cbc2098958f8e4cddf8534e0c2bf79d5c3e
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---


# ACSD-54887：在客户会话过期后清除客户购物车

ACSD-54887修补程序修复了在启用[!UICONTROL Persistent Shopping Cart]后客户会话过期后客户购物车被清空的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50时，此修补程序可用。 修补程序ID为ACSD-54887。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.4-p8、2.4.5-p3 - 2.4.5-p7和2.4.6-p1 - 2.4.6-p5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在启用[!UICONTROL Persistent Shopping Cart]的客户会话过期后清除客户购物车。

<u>重现步骤</u>：

1. 启用[!UICONTROL Persistent Shopping Cart]。 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** = *是*。

   在启用持久性的情况下登录（注意：在弹出授权中不可用，但仅在直接[!UICONTROL Sign in]页面上可用）。

1. 将产品添加到购物车。
1. 继续结帐并选择付款方式。
1. 使会话过期（删除`PHPSESSID`）。
1. 刷新页面。 请注意，报价已立即转换为来宾报价，因为已选择付款方式，并且删除了[!UICONTROL Persistent Cart] Cookie。
1. 使会话过期（删除`PHPSESSID`）。
1. 刷新页面。 查看购物车是否为空。
1. 再次登录。

<u>预期的结果</u>：

当您再次登录时，购物车上有产品。

<u>实际结果</u>：

再次登录时购物车为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。

