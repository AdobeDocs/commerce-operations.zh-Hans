---
title: MDVA-42237：可配置产品特殊价格未更新
description: MDVA-42237修补程序修复了可配置产品的特殊价格在子产品价格发生更改后未更新的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11后，即可使用此修补程序。 修补程序ID为MDVA-42237。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Admin Workspace, Configuration, Orders, Personalization, Products
role: Admin
exl-id: 1bae9a14-d6c1-4ee3-85aa-5d80ef479385
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-42237：可配置产品特殊价格未更新

MDVA-42237修补程序修复了可配置产品的特殊价格在子产品价格发生更改后未更新的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11时，此修补程序可用。 修补程序ID为MDVA-42237。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

可配置产品的特殊价格在子产品价格发生更改后不会更新。

<u>重现步骤</u>：

1. 转到&#x200B;**管理员** > **系统** > **索引管理**，为所有索引将&#x200B;**索引模式**&#x200B;设置为&#x200B;**按计划更新**。
1. 创建一个简单的产品并为其子产品设置特殊价格，以创建一个可配置的产品。
1. 查看店面是否反映了特价。
1. 使用GraphQL取消特价，然后重新检查店面的产品价格。

<u>预期的结果</u>：

店面不再显示特价。

<u>实际结果</u>：

店面没有更新价格。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
