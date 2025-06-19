---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.54
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.54中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
exl-id: 1496d15e-edf9-4be0-8e14-ebb2de6f12fe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.54

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.54中提供的修补程序所修复的问题。

QPT v1.1.54包含以下修补程序：

1. **ACSD-60267**：修复了以下问题：将带FPT的简单产品直接添加到购物车时，修复的产品税(FPT)正确适用，但在通过可配置产品选项选择这些产品时失败。
1. **ACSD-61103**：修复了客户通过API端点成功登录后，`customer_entity`表中的故障计数未重置为零的问题。
1. **ACSD-61134**：修复了在购物者通过取消选中&#x200B;*[!UICONTROL My billing and shipping address are the same]*&#x200B;复选框更新其帐单地址时，在结账工作流中自动取消选择[!DNL Braintree Vault]付款方式的问题。
1. **ACSD-61199**：修复了在编辑具有现有层次结构的CMS页面时，CMS页面层次结构选项卡未显示正确树结构的问题。
1. **ACSD-61200**：修复了销售中&#x200B;*[!UICONTROL Total Amount]*&#x200B;和&#x200B;*[!UICONTROL Total Amount Actual]*&#x200B;的计算缺少&#x200B;*[!UICONTROL Discount Tax Compensation Amount]*&#x200B;和&#x200B;*[!UICONTROL Shipping Discount Tax Compensation Amount]*&#x200B;而导致销售订单数据不一致的问题。
1. **ACSD-61522**：修复了在来宾客户的&#x200B;*[!UICONTROL First Name]*&#x200B;和&#x200B;*[!UICONTROL Last Name]*&#x200B;字段中输入电子邮件地址并发送无效订单确认电子邮件的问题。
1. **ACSD-61756**：提高了`AdvancedSalesRule`筛选器的性能。
1. **ACSD-61799**：修复了在将多个具有固定折扣的购物车规则应用于报价时错误计算总折扣的问题。
1. **ACSD-61845**：修复了在仅使用&#x200B;*text/html*&#x200B;接受标头发送请求时发生的错误。
1. **ACSD-62056**：修复了在安装MSI时可配置产品的图像上传失败的问题。
1. **ACSD-62485**：修复了在创建公司时`async.operations.all`消费者停止工作的问题。

使用左侧的菜单导航到特定的修补程序页面。
