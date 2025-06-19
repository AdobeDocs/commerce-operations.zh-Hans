---
title: ACSD-60267：通过可配置的产品选项添加产品时，FPT无法正确应用
description: Adobe Commerce应用ACSD-60267修补程序以修复以下问题：当将简单产品直接添加到购物车时，会正确应用固定产品税(FPT)，但是在通过可配置产品选项选择相同产品时失败。
feature: Taxes
role: Admin, Developer
exl-id: 919b3b96-1995-4faf-aaf1-b5cbb20e46bf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-60267：通过可配置的产品选项添加产品时，FPT无法正确应用

ACSD-60267修补程序修复了在将简单产品直接添加到购物车时正确应用固定产品税(FPT)的问题，但在通过可配置产品选项选择相同产品时失败。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hans) 1.1.54时，此修补程序可用。 修补程序ID为ACSD-60267。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将带FPT的简单产品添加到购物车时，固定产品税(FPT)可正常工作；但是，通过可配置产品选择添加产品时，不会添加FPT。

<u>重现步骤</u>：

1. 导航到&#x200B;*管理员* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** > **[!UICONTROL Fixed Product Taxes]**，将&#x200B;*[!UICONTROL Enable FPT]*&#x200B;设置为&#x200B;*是*。
1. 创建FPT属性并将其分配给&#x200B;*[!UICONTROL Attribute Set]*。
1. 打开&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**。
1. 对于&#x200B;*[!UICONTROL Default Label]*，请输入标识该属性的标签。
1. 将&#x200B;*[!UICONTROL Catalog Input for Store Owner]*&#x200B;设置为&#x200B;*[!UICONTROL Fixed Product Tax]*。
1. 创建新的税和区域，并将其分配给新的&#x200B;*[!UICONTROL Tax Rule]*。
1. 创建包含两个简单产品的可配置产品。
1. 现在，为这些简单产品指定两个不同的FPT值。
1. 重新编制指数，看看店面的价格。
1. 将产品添加到购物车并检查小计。

<u>预期的结果</u>：

* *[!UICONTROL Catalog]*&#x200B;页显示包含FPT的价格。
* 购物车中的小计包括FPT。

<u>实际结果</u>：

* *[!UICONTROL Catalog]*&#x200B;页不显示包括FPT值的价格。
* 小计和摘要无效。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
