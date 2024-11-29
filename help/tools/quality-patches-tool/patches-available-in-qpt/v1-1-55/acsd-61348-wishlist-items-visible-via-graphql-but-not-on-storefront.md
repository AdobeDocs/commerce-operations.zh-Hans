---
title: ACSD-61348：通过GraphQL可见但不在店面显示的愿望清单项目
description: 应用ACSD-61348修补程序以修复Adobe Commerce问题，该问题导致在多网站环境中，希望列表项目通过GraphQL可见，但在店面中不可见。
feature: Customers
role: Admin, Developer
source-git-commit: b3dcce33b5710cd3c4b835f5fc7fd8f16cdc6a7f
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-61348：通过GraphQL可见但不在店面显示的愿望清单项目

ACSD-61348修补程序修复了在多网站环境中，通过GraphQL可见愿望清单项目，但店面不可见的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55时，此修补程序可用。 修补程序ID为ACSD-61348。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.6-p5

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在多网站环境中，希望列表项目可通过GraphQL查看，但不会显示在店面上。

<u>重现步骤</u>：

1. 配置两个网站。
1. 转到&#x200B;**[!UICONTROL Config Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**&#x200B;并将&#x200B;**[!UICONTROL Share Customer Accounts]**&#x200B;设置为&#x200B;*[!UICONTROL Global]*。
1. 转到&#x200B;**[!UICONTROL Config Customers]** > **[!UICONTROL Wishlist]** > **[!UICONTROL General Options]**&#x200B;并将&#x200B;**[!UICONTROL Enable Multiple Wish Lists]**&#x200B;设置为&#x200B;*是*。
1. 转到&#x200B;**[!UICONTROL Config General]** > **[!UICONTROL Web]**&#x200B;并将&#x200B;**[!UICONTROL Add Store Code to URLs]**&#x200B;设置为&#x200B;*是*。
1. 创建一个简单的产品并将其分配给第二个网站。
1. 创建客户并登录。
1. 将产品添加到愿望清单。
1. 将产品分配给默认网站。
1. 转到默认网站上的&#x200B;*[!UICONTROL Wishlist]*&#x200B;页面。

<u>预期的结果</u>：

产品在愿望清单上。

<u>实际结果</u>：

愿望清单中没有产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
