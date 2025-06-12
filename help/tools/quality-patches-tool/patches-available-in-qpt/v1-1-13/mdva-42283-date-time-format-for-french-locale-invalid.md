---
title: MDVA-42283：法语区域设置的日期时间格式无效
description: MDVA-42283修补程序修复了法语区域设置的管理顺序网格中的日期 — 时间格式无效的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-42283。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: CMS
role: Admin
exl-id: ed99519d-03e2-444b-9cd1-e5c6e6d2ac2d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-42283：法语区域设置的日期时间格式无效

MDVA-42283修补程序修复了法语区域设置的管理顺序网格中的日期 — 时间格式无效的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-42283。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

法语区域设置的管理顺序网格中的日期时间格式无效。

<u>重现步骤</u>：

1. 创建订单、客户、CMS页面或CMS块。
1. 转到&#x200B;**管理员** > **帐户设置**，并将管理员的界面区域设置设置为&#x200B;**法语（加拿大）**/**法语（加拿大）(fr_CA)**&#x200B;或&#x200B;**巴西葡萄牙语(pt_BR)**。
1. 观察任何“订单”、“发运”、“贷项通知单”、“客户”、“CMS页”或“CMS块网格”的“日期”列中的值。

<u>预期的结果</u>：

日期采用实体实际编辑页面上显示的格式。

<u>实际结果</u>：

日期时间值不正确。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
