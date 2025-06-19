---
title: ACSD-54418：将固定折扣金额错误地添加到动态定价捆绑包的子产品中
description: 应用ACSD-54418修补程序以修复将固定折扣金额错误地应用于动态定价捆绑包的每个子产品的Adobe Commerce问题。
feature: Shopping Cart
role: Admin, Developer
exl-id: f7b57361-9056-4eec-a393-dadb65aa595b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-54418：将固定折扣金额错误地添加到动态定价捆绑包的子产品中。

ACSD-54418修补程序修复了将固定折扣额错误地应用于动态定价捆绑包的每个子产品的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.42时，此修补程序可用。 修补程序ID为ACSD-54418。 请注意，Adobe Commerce 2.4.7中已修复该问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

固定折扣金额错误地应用于动态定价捆绑的每个子产品。

<u>重现步骤</u>：

1. 使用动态定价和&#x200B;*2*&#x200B;捆绑包选项创建一个&#x200B;**[!UICONTROL bundle product]**。
1. 使用仅适用于捆绑产品&#x200B;**[!UICONTROL SKU]**&#x200B;并具有固定折扣的特定优惠券代码创建&#x200B;**[!UICONTROL cart price rule]**。
1. 将捆绑的产品添加到购物车。
1. 应用&#x200B;**[!UICONTROL coupon code]**。
1. 检查应用于购物车的折扣。

<u>预期的结果</u>：

折扣只适用于整个捆绑产品。

<u>实际结果</u>：

折扣将应用于每个捆绑子产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
