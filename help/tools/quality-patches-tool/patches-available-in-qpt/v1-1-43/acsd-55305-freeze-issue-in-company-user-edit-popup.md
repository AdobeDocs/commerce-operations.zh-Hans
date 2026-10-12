---
title: ACSD-55305：在[!UICONTROL My Account]中编辑公司用户时弹出窗口冻结
description: 应用ACSD-55305修补程序以修复Adobe Commerce问题，该问题导致[!UICONTROL My Account] &gt； [!UICONTROL Company Structure]页面上的[!UICONTROL Edit Company User]弹出窗口因屏幕上的加载器而冻结。
feature: Companies, B2B
role: Admin, Developer
exl-id: eeb2b136-022f-42d5-85e2-85537f4677d6
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%
---
# ACSD-55305：在[!UICONTROL My Account]中编辑公司用户时弹出窗口冻结

ACSD-55305修补程序修复了[!UICONTROL My Account]> [!UICONTROL Company Structure]页面上的[!UICONTROL Edit Company User]弹出窗口因屏幕上的加载器而冻结的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.43时，此修补程序可用。 修补程序ID为ACSD-55305。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

尝试使用&#x200B;*[!UICONTROL My Account]* > *[!UICONTROL Company Structure]*&#x200B;页面上的&#x200B;*[!UICONTROL Edit Company User]*&#x200B;弹出窗口时出现错误，因为该窗口会因屏幕上显示的加载器而冻结。

<u>重现步骤</u>：

1. 创建一个B2B公司。
1. 为客户创建多选属性。
1. 为新创建的公司管理员属性分配一个值。
1. 以公司管理员身份登录。
1. 转到[!UICONTROL account dashboard]并导航到&#x200B;**[!UICONTROL Company Structure]**。
1. 选择用户。
1. 单击&#x200B;**[!UICONTROL Edit Selected]**。

<u>预期的结果</u>：

表单弹出窗口会准确显示，并提供编辑公司信息的选项。

<u>实际结果</u>：

此时会出现表单弹出窗口，且无法进行任何编辑。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
