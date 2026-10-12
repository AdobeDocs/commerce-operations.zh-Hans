---
title: ACSD-63578：单击[!UICONTROL Add to Order by SKU]中的[!UICONTROL Delete]图标不会删除SKU
description: 应用ACSD-63578修补程序以修复在管理员中单击[!UICONTROL Add to Order by SKU]中的[!UICONTROL Delete]图标未删除SKU的Adobe Commerce问题。
feature: Orders
role: Admin, Developer
exl-id: 12afceb5-db3c-4783-a532-93c4c71f05f4
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '320'
ht-degree: 0%
---
# ACSD-63578：单击&#x200B;*[!UICONTROL Add to Order by SKU]*&#x200B;中的&#x200B;**[!UICONTROL Delete]**&#x200B;图标不会删除SKU

ACSD-63578修补程序修复了在管理员中单击&#x200B;*[!UICONTROL Add to Order by SKU]*&#x200B;中的&#x200B;**[!UICONTROL Delete]**&#x200B;图标未删除SKU的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58时，此修补程序可用。 修补程序ID为ACSD-63578。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p7

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

单击管理员中&#x200B;*[!UICONTROL Add to Order by SKU]*&#x200B;的&#x200B;**[!UICONTROL Delete]**&#x200B;图标不会从订单中删除该SKU。

<u>重现步骤</u>：

1. 导航到管理员> **[!UICONTROL Sales]** > **[!UICONTROL Orders]**，然后单击&#x200B;**[!UICONTROL Create New Order]**。
1. 选择客户。
1. 单击&#x200B;**[!UICONTROL Add to Order by SKU]**。
   * 输入SKU。
   * 单击&#x200B;**[!UICONTROL Add another]**&#x200B;按钮。
1. 单击&#x200B;**[!UICONTROL Delete]**&#x200B;图标。

<u>预期的结果</u>：

* 在管理员的订单中添加和删除产品。

<u>实际结果</u>：

* **[!UICONTROL Delete]**&#x200B;图标不起作用。
* 控制台中存在错误：

  `jquery.js:130 Refused to execute inline script because it violates the following Content Security Policy directive`

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
