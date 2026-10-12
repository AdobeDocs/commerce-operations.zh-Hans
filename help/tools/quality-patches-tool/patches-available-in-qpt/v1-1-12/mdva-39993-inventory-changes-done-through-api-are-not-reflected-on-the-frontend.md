---
title: MDVA-39993：通过API完成的库存更改未反映在店面上
description: MDVA-39993修补程序解决了通过API完成的清单更改未反映在店面中的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-39993。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: REST, Inventory, Orders, Storefront
role: Admin
exl-id: 5fa13635-bd58-470b-a4d5-e50cda8a46e3
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%
---
# MDVA-39993：通过API完成的库存更改未反映在店面上

MDVA-39993修补程序解决了通过API完成的清单更改未反映在店面中的问题。 安装[Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-39993。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.5 - 2.3.7-p2和2.4.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过API完成的库存更改不会反映在店面产品页面上。

<u>先决条件</u>：

已安装清单模块。

<u>重现步骤</u>：

1. 确保队列设置为在cron安装并运行的情况下执行，并且cron已安装和运行。
1. 创建具有两种颜色（黑色和红色）以及两种尺寸（M和L）的可配置产品(COC001)。
1. 选择无库存(COC001-Red-M)。
1. 在店面中加载可配置的产品页面，然后尝试单击每个颜色。 当您单击&#x200B;**红色**&#x200B;时，应该取消大小&#x200B;**M**，因为它没有库存。
1. 使用以下API端点和有效负载生成COC001-Red-M备货：

   ```json
   POST http://{domain}/rest/V1/inventory/source-items
   
   {
     "sourceItems": [
       {
         "sku": "COC001-Red-M",
         "source_code": "default",
         "quantity": 1000,
         "status": 1
       }
     ]
   }
   ```

1. 从后端检查此简单产品，验证它是否已更新为有货。
1. 从前端加载可配置产品，然后单击每个颜色。 单击&#x200B;**红色**&#x200B;时，请注意大小&#x200B;**M**。

<u>预期的结果</u>：

没有划出COC001-Red-M选项，因为我们已经通过API将其更新为库存。

<u>实际结果</u>：

COC001-Red-M期权仍被剔除，尽管它有存货。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
