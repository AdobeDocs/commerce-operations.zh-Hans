---
title: ACSD-57086：来自启用了条款和条件的非默认网站的订单处理不正确
description: 应用ACSD-57086修补程序以修复以下问题：来自启用了条款和条件的非默认网站的订单无法正确处理。Adobe Commerce
feature: Orders
role: Admin, Developer
exl-id: d9f2ef50-12c4-4a2d-b140-dfd0e8948fd3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# ACSD-57086：来自启用了条款和条件的非默认网站的订单处理不正确

ACSD-57086修补程序修复了从启用了条款和条件的非默认网站下单的订单无法正确处理的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49时，此修补程序可用。 修补程序ID为ACSD-57086。 请注意，此问题已在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在使用具有AsyncOrder处理的多商店设置时，由于队列使用者代码中的范围处理问题，对主网站以外的任何网站/商店下达的订单会被拒绝。

<u>重现步骤</u>：

1. 安装[!DNL RabbitMQ]并执行`bin/magento setup:upgrade`以创建[!DNL RabbitMQ]的队列。
1. 使用以下方式配置AsyncOrder处理：

   ```bash
   bin/magento setup:config:set --checkout-async 1
   ```

1. 创建辅助网站、商店和商店视图。
1. 创建在两个网站之间共享的产品。
1. 启用条款和条件：
   1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**。
   1. 将&#x200B;*[!UICONTROL Enable Terms And Conditions]*&#x200B;设置为&#x200B;*是*。
1. 为两个网站配置条款和条件：
   1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Terms And Conditions]** > **[!UICONTROL Add New Condition]**。
   1. 使用以下设置：
      * *[!UICONTROL Condition Name]*： *任何内容*
      * *[!UICONTROL Status]*： *[!UICONTROL Enabled]*
      * *[!UICONTROL Applied]*： *[!UICONTROL Manually]*
      * *[!UICONTROL Store View]*： *[!UICONTROL Default Store View]*
   1. 为第二个网站/商店视图创建另一个条件。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL All Stores]**&#x200B;更改默认网站。 单击第二个网站，选中&#x200B;*[!UICONTROL Set as Default]*&#x200B;并保存。
1. 使用以下方式清除缓存：

   ```bash
   bin/magento cache:clear
   ```

1. 转到店面并将产品添加到购物车。 继续结帐并下单（您应会在付款方式步骤中看到一个复选框来接受条款和条件）。
1. 下订单后返回到“管理员”，并将默认网站更改回原始主网站并保存。
1. 清除缓存：

   ```bash
   bin/magento cache:clear
   ```

1. 运行以下命令以启动队列使用者：

   ```bash
   bin/magento queue:cons:start placeOrderProcessor
   ```

<u>预期的结果</u>：

订单已履行；不会自动拒绝。

<u>实际结果</u>：

订单状态为&#x200B;*已拒绝*，注释如下：

*未下订单。 首先，同意条款和条件，然后再次尝试下订单。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
