---
title: ACSD-48164：受限管理员无法保存网站级别的值
description: 应用ACSD-48164修补程序以修复受限管理员无法保存网站级别值的Adobe Commerce问题。
feature: Admin Workspace
role: Admin
exl-id: 1ad4758e-7ecc-48d0-8313-1163188cbe73
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48164：受限管理员无法保存网站级别的值

ACSD-48164修补程序修复了受限管理员无法保存网站级别值的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27时，此修补程序可用。 修补程序ID为ACSD-48164。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

受限管理员无法保存网站级别的值。

<u>重现步骤</u>：

1. 在[!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]**&#x200B;中创建新网站、商店和商店视图。
1. 在[!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]**&#x200B;中创建新管理员角色。

   * 转到&#x200B;**[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]**，选择新网站，然后将此角色分配给任何管理员用户。

1. 选择任意产品并仅分配新网站。 请勿选择默认网站。
1. 以步骤2中分配的管理员用户身份登录，通过更改任何网站级别属性（如&#x200B;*[!UICONTROL Status]*、*[!UICONTROL Tax Class]*）在&#x200B;**[!UICONTROL All Store View]**&#x200B;范围内编辑产品，并将产品设置为新产品。
1. 保存产品。

<u>预期的结果</u>：

与角色范围关联到一个网站的管理员用户可以使用&#x200B;*[!UICONTROL All Store View]*&#x200B;范围保存网站级别的产品属性。

<u>实际结果</u>：

此时会显示保存产品的成功消息，但产品属性值保持不变。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
