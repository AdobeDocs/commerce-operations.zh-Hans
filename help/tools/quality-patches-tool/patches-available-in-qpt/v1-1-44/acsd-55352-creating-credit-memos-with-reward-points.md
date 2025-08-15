---
title: ACSD-55352：创建具有奖励积分的贷项通知单
description: 应用ACSD-55352补丁以修复Adobe Commerce问题，其中在使用客户奖励点创建部分贷项通知单后，订单状态更改为*closed*，贷项通知单选项从管理订单页中消失。
feature: Checkout, Orders
role: Admin, Developer
exl-id: bee0c4be-11ec-4dcb-9b3c-7af26676cee9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-55352：创建具有奖励积分的贷项通知单

ACSD-55352修补程序修复了以下问题：使用客户奖励积分创建部分贷项通知单后，订单状态更改为&#x200B;*closed*，并且贷项通知单选项从管理订单页面中消失。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44时，此修补程序可用。 修补程序ID为ACSD-55352。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

创建包含客户奖励积分的部分贷项通知单后，订单状态将更改为&#x200B;*已关闭*，贷项通知单选项将从管理订单页中消失。

<u>重现步骤</u>：

1. 登录到Adobe Commerce管理员。
2. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**。
3. 添加两个费率：
   * *[!UICONTROL First]*：
      * *[!UICONTROL Direction]* = *指向货币*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*：
      * *[!UICONTROL Direction]* = *货币到点*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. 创建一个简单的产品，其价格为&#x200B;*$100*，数量为&#x200B;*数量*： *100*。
5. 从店面创建客户。
6. 再次转到后端： **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** >添加&#x200B;*100*&#x200B;并保存客户。
7. 转到店面，并以客户之前创建的身份登录。
8. 将产品添加到购物车，数量为&#x200B;*1&rbrace;：* 10 *。*
9. 转到&#x200B;**[!UICONTROL Checkout]**&#x200B;并在出现提示时使用可用的&#x200B;*100*&#x200B;奖励积分并下订单。
10. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]**&#x200B;并发送该订单。
11. 转到[!UICONTROL Credit Memo]并将&#x200B;*退款数量*&#x200B;更新为&#x200B;*8*。
12. 勾选&#x200B;**[!UICONTROL Refund Reward Points]**&#x200B;复选框，然后单击&#x200B;**[!UICONTROL Refund offline]**。
13. 尝试使用[!UICONTROL Credit Memo]从订单中退款其余两个产品。

<u>预期的结果</u>：

* 管理员创建[!UICONTROL Credit Memo]以返回其余两个产品。
* 订单状态为&#x200B;*已完成*。

<u>实际结果</u>：

* 无法创建更多[!UICONTROL Credit Memo]。
* 订单状态为&#x200B;*已关闭*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
