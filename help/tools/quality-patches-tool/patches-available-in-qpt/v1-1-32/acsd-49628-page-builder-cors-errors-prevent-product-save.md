---
title: ACSD-49628： [!DNL Page Builder] CORS错误阻止产品保存
description: 应用ACSD-49628修补程序以修复Adobe Commerce问题，该问题导致 [!DNL Page Builder] CORS错误阻止产品保存。
feature: Categories, Page Builder, Products
role: Admin
exl-id: 5bceddfa-5fbf-4ebe-a233-de7720764849
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-49628： [!DNL Page Builder] CORS错误阻止产品保存

ACSD-49628修补程序修复了[!DNL Page Builder] CORS错误阻止管理员保存产品的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.32时，此修补程序可用。 修补程序ID为ACSD-49628。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

[!DNL Page Builder] CORS错误阻止保存产品。

<u>重现步骤</u>：

1. 以管理员身份登录。
1. 创建具有以下权限的用户角色：

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]**。
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]**。

1. 不添加任何&#x200B;*[!UICONTROL Content]*&#x200B;权限。
1. 创建另一个管理员用户，并将上面创建的角色分配给此用户。
1. 创建产品并注销。
1. 以第二个管理员身份登录。
1. 尝试编辑并保存产品。

<u>预期的结果</u>：

第二个管理员能够保存产品，但如果没有任何&#x200B;*[!UICONTROL Content]*&#x200B;权限，**[!UICONTROL Edit with Page Builder]**&#x200B;按钮不会向管理员显示。

<u>实际结果</u>：

第二个管理员无法保存产品，因为有多个[!DNL Page Builder]错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
