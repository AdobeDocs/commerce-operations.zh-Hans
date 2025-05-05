---
title: ACSD-51819：使用单引号ID下达多个订单
description: 应用ACSD-51819修补程序以修复可通过同一报价ID下达多个订单的Adobe Commerce问题。
feature: Orders, Checkout
role: Admin, Developer
exl-id: dbca8790-d947-4104-bba9-b29abcfc0344
source-git-commit: 5f22591c499f0f5d349994195731c7c87512f5f0
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-51819：使用单引号ID下达多个订单

ACSD-51819修补程序修复了可以通过同一报价ID下达多个订单的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41时，此修补程序可用。 修补程序ID为ACSD-51819。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p2、2.4.5-p5、2.4.6、2.4.6-p4、2.4.7-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.4-p11、2.4.5-p3 - 2.4.5-p10、2.4.6 - 2.4.6-p8、2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

可使用同一报价ID下达多个订单。

<u>重现步骤</u>：

1. 以用户身份登录。
1. 将商品添加到购物车并继续结帐。
1. 选择任何付款方式，但不要单击&#x200B;**[!UICONTROL Place Order]**&#x200B;按钮。
1. 在其他浏览器中登录到同一帐户。
1. 继续使用相同的项目进行签出，而不单击&#x200B;**[!UICONTROL Place Order]**&#x200B;按钮。
1. 同时单击两个系统中的&#x200B;**[!UICONTROL Place Order]**&#x200B;按钮。
1. 验证在两种浏览器中下达的订单。

<u>预期的结果</u>：

仅成功处理来自一个浏览器的第一笔订单。

<u>实际结果</u>：

在两个浏览器中均下了订单。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
