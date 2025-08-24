---
title: ACSD-67347：使用优惠券代码时，订单失败并出现“无法获取锁定”错误
description: 将ACSD-67347修补程序应用于Adobe Commerce问题：当优惠券代码包含特殊字符(例如，BIT/123456)并且启用了文件锁定时，订单失败并出现“无法获取锁定”错误。
feature: Checkout, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 1a48428efbb022b53320370f68691eaed44809b3
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# ACSD-67347：排序失败，出现&#x200B;*使用优惠券代码时无法获取锁定*&#x200B;错误

ACSD-67347修补程序修复了以下问题：当优惠券代码包含特殊字符(例如，BIT/123456)并且启用了文件锁定时，订单失败并出现&#x200B;*无法获取锁定*&#x200B;错误。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69时，此修补程序可用。 修补程序ID为ACSD-67347。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p12

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5-p11 - 2.4.5-p13

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当使用带有特殊字符的优惠券并启用文件锁定时，订单失败并出现&#x200B;*无法获取锁定*&#x200B;错误。

<u>重现步骤</u>：

1. 安装2.4-develop。
1. 在`env.php`文件中设置文件锁定配置：

   ```
   'lock' => [
           'provider' => 'file',
           'config' => [
               'path' => '/Users/awijesooriya/sites/acsd15194dev/locks'
           ]
       ],
   ```

1. 使用优惠券代码格式&#x200B;*BIT/123456*&#x200B;创建包含优惠券的购物车规则。
1. 创建一个简单的产品。
1. 将产品添加到购物车并应用优惠券代码。
1. 继续结帐并下订单。

<u>预期的结果</u>：

订单成功下达，因为对创建优惠券代码没有限制。

<u>实际结果</u>：

无法下订单。 出现以下错误： *无法获取锁定。*

```
File "/Users/test/sites/test/locks/coupon_code_123/abc" cannot be opened Warning!fopen(/Users/test/sites/test/locks/coupon_code_123/abc): Failed to open stream: No such file or directory
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
