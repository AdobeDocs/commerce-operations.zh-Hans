---
title: ACSD-51291：受限管理员可以将图像/视频添加到分配给多个网站的产品
description: 应用ACSD-51291修补程序以修复Adobe Commerce问题，该问题导致限制只能访问一个网站的管理员可以将图像/视频添加到分配给多个网站的产品。
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: a4edd034-f718-4559-9993-11609f0d0efa
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%
---
# ACSD-51291：受限管理员可以将图像/视频添加到分配给多个网站的产品

ACSD-51291修补程序修复了以下问题：有权访问一个网站的受限管理员可以向分配给多个网站的产品添加图像/视频。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.32时，此修补程序可用。 修补程序ID为ACSD-51291。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.4-p3、2.4.5 - 2.4.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

有权访问一个网站的受限管理员可以将图像/视频添加到分配给多个网站的产品。

<u>重现步骤</u>

1. 以管理员身份登录。
1. 创建第二个网站、商店和商店视图。
1. 使用仅用于第二个网站、商店和商店视图的资源创建第二个管理员角色。
1. 再创建一个管理员，并将其分配给新的受限管理员角色。
1. 创建新产品，并将其分配给默认网站和新网站。
1. 从主管理员配置文件注销。
1. 以新的受限管理员身份登录。
1. 编辑已创建的产品，该产品已分配给这两个网站。
1. 打开&#x200B;**[!UICONTROL Images and Videos]**&#x200B;选项卡。

<u>预期的结果</u>：

* 将显示以下消息：

  *只有当管理员有权访问产品所分配到的所有网站时，才允许受限管理员对图像或视频执行操作。*

* **[!UICONTROL Add Video]**&#x200B;按钮未处于活动状态。

<u>实际结果</u>：

受限管理员可以添加图像和视频，即使将产品分配给它无权访问的网站也是如此。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
