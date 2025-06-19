---
title: ACSD-57315：每次单击获取按钮时， [!DNL PayPal Payflow Pro] 中都会创建新事务
description: 应用ACSD-57315修补程序以修复Adobe Commerce问题，该问题导致每次在[!UICONTROL Admin]中的查看事务屏幕上单击获取按钮时， [!DNL PayPal Payflow Pro] 中都会创建一个新事务。
feature: Payments
role: Admin, Developer
exl-id: 1fb8a5af-fda1-4c24-859d-d45424bde12f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-57315：每次单击获取按钮时，[!DNL PayPal Payflow Pro]中都会创建新事务

ACSD-57315修补程序修复了每次在[!UICONTROL Admin]中的查看事务屏幕上单击获取按钮时，[!DNL PayPal Payflow Pro]中都会创建一个新事务的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.48时，此修补程序可用。 修补程序ID为ACSD-57315。 请注意，该问题计划在Adobe Commerce 2.5.0中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

每次在[!UICONTROL Admin]中的查看事务屏幕上单击获取按钮时，[!DNL PayPal Payflow Pro]中都会创建一个新事务。

<u>重现步骤</u>：

1. 配置[!DNL PayPal Payflow Pro]。
1. 将事务方法设置为&#x200B;*[!UICONTROL Sale]*。
1. 使用&#x200B;*信用卡*&#x200B;下订单。
1. 从[!UICONTROL Admin]打开事务。
1. 单击&#x200B;**[!UICONTROL Fetch]**&#x200B;按钮。
1. 检查[!DNL PayPal]帐户以查找与下订单相关的交易记录。

<u>预期的结果</u>：

未创建新的付款交易记录。

<u>实际结果</u>：

为已支付的订单创建新的付款交易记录。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
