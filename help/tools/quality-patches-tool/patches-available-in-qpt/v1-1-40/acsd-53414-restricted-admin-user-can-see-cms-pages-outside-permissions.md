---
title: ACSD-53414：受限管理员用户可在其权限范围内查看CMS页面
description: 应用ACSD-53414修补程序以修复Adobe Commerce问题，该问题导致受限管理员用户无法看到其权限范围之外的CMS页面。
feature: CMS
role: Admin, Developer
exl-id: 86658336-679b-4fe0-9d26-56064ff0c604
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-53414：受限管理员用户可在其权限范围内查看CMS页面

ACSD-53414修补程序修复了受限管理员用户在其权限范围之外查看CMS页面的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40时，此修补程序可用。 修补程序ID为ACSD-53414。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

受限管理员用户可以查看超出其权限范围的CMS页面。

<u>重现步骤</u>：

1. 创建新网站(sub_website)、存储(sub_store)和存储(sub_storeview)。
1. 创建sub_expert角色，以允许sub_website和sub_store的范围。 仅分配以下权限： [!UICONTROL Dashboard]和[!UICONTROL Pages]。
1. 创建新的管理员用户并将其分配给sub_expert角色。
1. 将以下CSM页面分配给sub_storeview和默认的storeview。

   * [!UICONTROL 404 Not Found] >子审核
   * [!UICONTROL 503 Service Unavailable] >默认预览

1. 使用在步骤3中创建的管理员用户登录到管理员。
1. 检查CMS页面网格。

<u>预期的结果</u>：

*[!UICONTROL 503 Service Unavailable]*&#x200B;页面对Web管理员不可见。

<u>实际结果</u>：

*[!UICONTROL 503 Service Unavailable]*&#x200B;对Web管理员可见。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
