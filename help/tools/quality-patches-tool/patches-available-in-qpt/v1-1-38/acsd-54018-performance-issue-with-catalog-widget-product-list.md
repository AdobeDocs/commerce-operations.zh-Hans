---
title: ACSD-54018：目录小部件产品列表出现性能问题
description: 应用ACSD-54018修补程序以修复在添加具有条件和属性类型布尔值的目录小部件产品列表时页面加载缓慢的Adobe Commerce问题。
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 2fb7ca37-78cc-45f4-86a3-d922cf4d1457
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
subfeature_v2:
  - id: ed510963-0b8c-4764-86f6-f3c7735bc334
    internal-label: Page Builder
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
source-wordcount: '463'
ht-degree: 0%
---
# ACSD-54018：目录小部件产品列表出现性能问题

ACSD-54018修补程序修复了在添加具有条件和属性类型布尔值的目录小部件产品列表时页面加载缓慢的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.38时，此修补程序可用。 修补程序ID为ACSD-54018。 请注意，Adobe Commerce 2.4.6中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

添加具有条件和属性类型布尔值的目录小部件产品列表时，页面加载缓慢。

<u>重现步骤</u>：

1. 生成10万个产品。
1. 创建范围设置为[!UICONTROL Store View]的bool属性。
1. 将属性分配给所有属性集。
   * 将属性值&#x200B;*是*&#x200B;分配给所有产品。
1. 现在转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**，然后选择所有10万个产品。
   * 选择&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**。
   * 将bool属性设置为&#x200B;*是*&#x200B;并保存。
   * 如果您已在此步骤中注销，请查看&#x200B;*注释*。
1. 转到CLI并运行`php bin/magento queue:con:start product_action_attribute.update`。
   * 确保所有产品的属性都已更新。
1. 现在转到&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Pages]**&#x200B;并创建新页面。
1. 打开&#x200B;**[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**。
1. 选择&#x200B;*[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*。
1. 将条件&#x200B;*[!UICONTROL Created attribute]*&#x200B;设置为&#x200B;*[!UICONTROL Yes]*&#x200B;并保存。
1. 转到前端并打开创建的页面。
1. 禁用全页缓存并阻止html缓存。
1. 检查页面加载速度。
1. 重新加载页面几次，并计算平均加载时间。

<u>预期的结果</u>：

页面加载速度快。

<u>实际结果</u>：

加载页面需要5 - 10秒。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
