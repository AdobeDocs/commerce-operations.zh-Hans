---
title: ACSD-62689：无法在深度4之后添加[!UICONTROL Related Product Rules]中的类别和小部件
description: 应用ACSD-62689修补程序以修复Adobe Commerce问题，该问题导致客户在深度嵌套四次后无法在[!UICONTROL Related Product Rules]和小组件中添加类别。
feature: Categories
role: Admin, Developer
exl-id: 2506744a-01c8-462b-9a27-cd0bdb5664f9
source-git-commit: 7aefd4f20580529a9da14776368bf2c3bbb3ff3c
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-62689：无法在深度4之后添加&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;中的类别和小部件

>[!NOTE]
>
>此修补程序已被[ACP2E-3689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3689-issues-with-category-tree-display-reflect-anchor-non-anchor-relationships.md)替换。

ACSD-62689修补程序修复了客户无法在深度嵌套四次之后在&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;和小组件中添加类别的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57时，此修补程序可用。 修补程序ID为ACSD-62689。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

客户无法在深度4次嵌套后添加&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;中的类别和小部件。

<u>重现步骤</u>：

1. 在默认根类别下创建两个名为&#x200B;*[!UICONTROL Anchor]*&#x200B;和&#x200B;*[!UICONTROL Non-Anchor]*&#x200B;的类别。
   * 确保已为&#x200B;*[!UICONTROL Non-Anchor]*&#x200B;类别禁用&#x200B;*[!UICONTROL Is Anchor]*&#x200B;标志。
1. 转到&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Widgets]**&#x200B;并创建构件。
1. 在&#x200B;*[!UICONTROL Layout Updates]*&#x200B;下，选择&#x200B;*[!UICONTROL Display on]*&#x200B;字段中的&#x200B;**[!UICONTROL Non-Anchor Categories]**。
1. 单击&#x200B;**[!UICONTROL Specific Categories]**。
1. 单击类别选择图标。
1. 展开根类别。
1. 检查类别。 两者都应禁用，且不可选。
1. 在&#x200B;*[!UICONTROL Layout Updates]*&#x200B;下，选择&#x200B;*[!UICONTROL Display on]*&#x200B;字段中的&#x200B;**[!UICONTROL Anchor Categories]**。 然后执行步骤5和6。
1. 检查类别。 两者都应启用并可选择。

<u>预期的结果</u>：

在步骤7中，只能选择&#x200B;*[!UICONTROL Non-Anchor]*&#x200B;类别。 在步骤9中，*[!UICONTROL Anchor]*&#x200B;类别应为可选项。

<u>实际结果</u>：

在步骤7中，两个类别均不可选。 在步骤9中，两个类别均可选择。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。

