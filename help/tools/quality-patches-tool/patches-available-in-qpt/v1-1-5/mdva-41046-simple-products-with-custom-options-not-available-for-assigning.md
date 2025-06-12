---
title: MDVA-41046：具有自定义选项的简单产品不可用于分配
description: MDVA-41046修补程序解决了具有自定义选项的简单产品无法分配给可配置/分组产品的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5后，即可使用此修补程序。 修补程序ID为MDVA-41046。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: Products
role: Developer
exl-id: 7fd7a9db-f834-4aea-a9d7-6e9535c037c8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-41046：具有自定义选项的简单产品不可用于分配

MDVA-41046修补程序解决了具有自定义选项的简单产品无法分配给可配置/分组产品的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5时，此修补程序可用。 修补程序ID为MDVA-41046。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

具有自定义选项的简单产品无法分配给可配置/分组的产品。

<u>重现步骤</u>：

1. 创建一个带有可自定义选项的简单产品，并为可配置属性设置一个值。
   * 使用&#x200B;*Color*&#x200B;作为可配置属性，并选择&#x200B;*Yellow*&#x200B;作为颜色值。
1. 保存简单产品。
1. 现在，转到创建可配置产品页面。
1. 执行“创建配置”向导，并确保选择&#x200B;*黄色*&#x200B;作为属性颜色。
1. 不保存可配置产品，从选择下拉列表中选择“选择其他产品”选项。
1. 这将打开按颜色属性黄色过滤的产品网格。 现在，选择之前使用可自定义选项创建的简单产品。
1. 保存可配置产品。

<u>预期的结果</u>：

带有自定义选项的简单产品可用于在步骤6中进行分配（在网格中可见）。

<u>实际结果</u>：

配置部分为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修补程序部分。
