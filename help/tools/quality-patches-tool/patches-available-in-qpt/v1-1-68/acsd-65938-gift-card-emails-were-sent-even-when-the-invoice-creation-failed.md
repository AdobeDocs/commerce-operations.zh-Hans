---
title: ACSD-65938：即使发票创建失败，也发送礼品卡电子邮件
description: 应用ACSD-65938修补程序以修复在成功保存和提交发票之前发送礼品卡电子邮件的Adobe Commerce问题，确保在正确保存发票之后触发电子邮件。
feature: Orders, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: b688875cd0a7bfc07dba77254605e7055ae7cca4
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# ACSD-65938：即使发票创建失败，也发送礼品卡电子邮件

ACSD-65938修补程序解决了在成功保存和提交发票之前发送礼品卡电子邮件的问题。 通过此修复，现在仅在成功保存发票后触发电子邮件。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68时，此修补程序可用。 修补程序ID为ACSD-65938。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在确认发票已成功创建和保存之前已发送礼品卡电子邮件，这会导致即使发票创建失败也会发送电子邮件。

<u>重现步骤</u>：

1. 登录到&#x200B;**[!UICONTROL Admin]**&#x200B;面板。
2. 导航到&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Cards]** > **[!UICONTROL Gift Card General Settings]**，并将&#x200B;**[!UICONTROL Generate Gift Card Account when Order Item is]**&#x200B;设置为&#x200B;*已开发票*。
3. 创建新的礼品卡产品。
4. 将礼品车产品添加到购物车并转到&#x200B;**[!UICONTROL checkout]**。 您可以使用&#x200B;**[!UICONTROL Check/Money Order]**&#x200B;作为付款方式。
5. 下订单。
6. 修改`OrderRepository`以模拟订购过程中的异常。
7. 使用以下有效负载向`rest/default/V1/order/<ORDER_ID>/invoice`发送POST请求：

   ```
   {
     "capture": true,
     "notify": true
   }
   ```


<u>预期的结果</u>：

如果发票创建失败，则不应发送礼品卡电子邮件。

<u>实际结果</u>：

即使发票创建失败，也会发送礼品卡电子邮件。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
