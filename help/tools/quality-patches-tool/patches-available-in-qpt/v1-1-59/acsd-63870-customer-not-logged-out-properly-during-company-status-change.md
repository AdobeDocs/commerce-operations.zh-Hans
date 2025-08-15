---
title: ACSD-63870：客户在公司状态更改期间未正确注销
description: 应用ACSD-63870修补程序以修复在活跃客户会话期间公司状态更改时公司客户无法正确注销的Adobe Commerce问题。
feature: Customers, B2B, Companies
role: Admin, Developer
exl-id: 4488f3cb-bb34-491e-8821-c2e98ff69429
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63870：客户在公司状态更改期间未正确注销

ACSD-63870修补程序解决了在活动客户会话期间公司状态更改时公司客户无法正确注销的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59时，此修补程序可用。 修补程序ID为ACSD-63870。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在活动客户会话期间更改公司状态时客户注销失败。

<u>重现步骤</u>：

1. 启用B2B功能。
1. 创建一个简单的产品。
1. 创建新公司并将其标记为&#x200B;*活动*。
1. 以公司用户身份登录并将产品添加到购物车。
1. 继续结帐，直到[!UICONTROL Shipping Address]步骤。 请勿输入地址。
1. 转到管理员并将公司状态更改为&#x200B;*未决批准*。
1. 返回前端并填写送货地址。

<u>预期的结果</u>：

客户已注销。

<u>实际结果</u>：

* 用户收到&#x200B;*发生错误*&#x200B;错误。
* `var/log/exception.log`包含：

  ```
  report.CRITICAL: InvalidArgumentException: Incorrect theme identification key in /home/lib/internal/Magento/Framework/View/Design/Theme/FlyweightFactory.php:60
  ```


## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 安装修补程序后所需的其他步骤

（本节为可选内容；在应用修补程序后，可能需要执行一些步骤来修复此问题。） 

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
