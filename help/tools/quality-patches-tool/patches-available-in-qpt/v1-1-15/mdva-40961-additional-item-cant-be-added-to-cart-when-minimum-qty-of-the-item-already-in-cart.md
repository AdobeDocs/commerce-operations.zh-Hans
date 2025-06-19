---
title: MDVA-40961：当购物车中已有最小数量的项目时，无法将其他项目添加到购物车
description: MDVA-40961修补程序修复了当购物车中已有最小项目数量时，无法将其他项目添加到购物车的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15后，即可使用此修补程序。 修补程序ID为MDVA-40961。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Orders, Shopping Cart
role: Admin
exl-id: b5191919-062d-4ddd-84e2-a4801501724d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-40961：当购物车中已有最小数量的项目时，无法将其他项目添加到购物车

MDVA-40961修补程序修复了当购物车中已有最小项目数量时，无法将其他项目添加到购物车的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15后，即可使用此修补程序。 修补程序ID为MDVA-40961。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当购物车中已有最小商品数量时，无法将其他商品添加到购物车中。

<u>重现步骤</u>：

1. 将简单产品设置为购物车&#x200B;**中允许有多个**&#x200B;最小数量（例如，两个）。
1. 打开店面上的产品，然后将其中两个添加到购物车中。
1. 停留在产品页面上，并将此产品的另一个添加到购物车中。

<u>预期的结果</u>：

第三个产品可以添加到购物车，因为它已经包含最小数量。

<u>实际结果</u>：

您收到以下错误消息： *您购买的最少是2*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
