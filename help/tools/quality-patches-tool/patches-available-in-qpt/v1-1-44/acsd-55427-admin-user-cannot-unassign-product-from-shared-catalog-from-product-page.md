---
title: ACSD-55427：管理员无法从产品页面上的**[!UICONTROL Product in Shared Catalogs]**中取消分配产品
description: 应用ACSD-55427修补程序以修复无法从**[!UICONTROL Product in Shared Catalogs]**中取消分配产品的Adobe Commerce问题。
feature: Products, B2B
role: Admin, Developer
exl-id: 974347fd-351d-4a4b-a9ca-a534daf3fbd7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-55427：管理员无法从产品页面上的&#x200B;**[!UICONTROL Product in Shared Catalogs]**&#x200B;中取消分配产品

ACSD-55427修补程序修复了以下问题：在Commerce管理中，无法从产品页面上的&#x200B;**[!UICONTROL Product in Shared Catalogs]**&#x200B;取消分配产品。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44时，此修补程序可用。 修补程序ID为ACSD-55427。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

您不能在Commerce管理员的目录中的产品页面上从&#x200B;**[!UICONTROL Product in Shared Catalogs]**&#x200B;取消分配产品。

<u>重现步骤</u>：

先决条件：安装了Adobe Commerce并启用了B2B和&#x200B;**[!UICONTROL Shared Catalogs]**。
1. 创建产品。
1. 导航到共享目录仪表板，然后打开默认的共享目录。
1. 将产品分配给默认目录，并设置低于产品价格的价格。
1. 保存共享目录。
1. 运行[!UICONTROL CRON]以更新使用者/索引器。
1. 打开产品，然后从&#x200B;**[!UICONTROL Product in Shared Catalogs]**&#x200B;部分下删除该产品。

<u>预期的结果</u>：

应从&#x200B;**[!UICONTROL Product in Shared Catalogs]**&#x200B;部分下删除产品。

<u>实际结果</u>：

产品仍显示在&#x200B;**[!UICONTROL Product in Shared Catalogs]**&#x200B;部分中。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
