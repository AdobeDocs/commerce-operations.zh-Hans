---
title: ACSD-66179：取消付款类型为[!UICONTROL Not Capture]的发票会导致404错误页
description: 应用ACSD-66179修补程序以修复Adobe Commerce问题，该问题导致取消付款类型为[!UICONTROL Not Capture]的发票时出现404错误页。
feature: Orders, Payments
role: Admin, Developer
type: Troubleshooting
source-git-commit: 02a446114be0f9c1ff8d4532cb13a94f1ef64ed2
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# ACSD-66179：取消付款类型为[!UICONTROL Not Capture]的发票会导致404错误页

ACSD-66179修补程序修复了取消使用&#x200B;*[!UICONTROL Not Capture]*&#x200B;付款类型创建的发票导致404错误页面的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68时，此修补程序可用。 修补程序ID为ACSD-66179。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4-p11 - 2.4.4-p14、2.4.5-p10 - 2.4.5-p13、2.4.6-p8 - 2.4.6-p11、2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

取消使用&#x200B;*[!UICONTROL Not Capture]*&#x200B;付款类型创建的发票会导致404错误页。

<u>重现步骤</u>：

1. 使用付款方法（如PayPal Express Checkout）创建订单。
1. 创建发票。 将&#x200B;**[!UICONTROL Amount]**&#x200B;设置为&#x200B;*[!UICONTROL Not Capture]*，并提交发票。
1. 打开创建的发票并选择&#x200B;**[!UICONTROL Cancel]**。

<u>预期的结果</u>：

1. 已成功取消发票。
1. 显示成功消息： *您已取消发票。*

<u>实际结果</u>：

显示404错误页面： *找不到页面。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
