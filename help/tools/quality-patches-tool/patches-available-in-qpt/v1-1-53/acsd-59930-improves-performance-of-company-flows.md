---
title: ACSD-59930：改进公司流的性能
description: 应用ACSD-59930修补程序以解决Adobe Commerce问题：创建、保存或删除管理员在通讯簿中具有*1000*地址的公司时，管理面板中会显示*Timeout+*错误。
feature: Customers, B2B
role: Admin, Developer
exl-id: eaa6c78d-13e3-439d-90f7-70c1c96c3197
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-59930：改进公司流的性能

ACSD-59930修补程序修复了在创建、保存或删除地址簿中包含&#x200B;*1000+*&#x200B;地址的管理员的公司时，管理面板中显示&#x200B;*超时*&#x200B;错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.53时，此修补程序可用。 修补程序ID为ACSD-59930。 请注意，此问题计划在Adobe Commerce B2B-1.5.0中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.6-p4

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

提高公司创建、保存和删除流的性能。

<u>先决条件：</u>：

安装和启用Adobe Commerce B2B模块。

<u>重现步骤</u>：

1. 在&#x200B;*中创建具有* 1000+*[!UICONTROL Address Book]*&#x200B;地址的客户。
1. 创建公司并将上述客户用作管理员。
1. 保存公司。

<u>预期的结果</u>：

公司已成功创建，并且未显示超时错误。

<u>实际结果</u>：

显示超时错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
