---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.55
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.55中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
exl-id: a4895d1b-e8d0-458e-81c8-4b892c116de6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.55

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.55中提供的修补程序所修复的问题。

QPT v1.1.55包含以下修补程序：

1. **ACSD-58383**：修复了以下问题：通过[!DNL REST API]同时执行两个相同请求并发出退款，会创建重复的贷项通知单。
1. **ACSD-58471**：修复了在计划关联的目录价格规则时，在产品详细信息页面上加载动态内容失败的问题。
1. **ACSD-58566**：修复了在查询[!DNL GraphQL]突变中的`created_at`字段时`addPurchaseOrderComment`返回内部服务器错误的问题。
1. **ACSD-58685**：修复了在禁用电子邮件通信时启动的销售电子邮件在重新启用电子邮件通信后仍会发送的问题。
1. **ACSD-58735**：修复了受限管理员无法在关联网站的[!UICONTROL Admin]中查看客户帐户页面上的放弃购物车的问题。
1. **ACSD-58828**：修复了以下问题：如果任何必填字段留空，则需要在客户端验证消息旁边显示服务器端验证消息&#x200B;*地址*。 服务器端验证将不显示空必填字段的消息，客户端验证将处理错误通知，声明&#x200B;*这是必填字段。*
1. **ACSD-60344**：修复了在使用具有自动审批的&#x200B;**[!UICONTROL Purchase Order]**&#x200B;时发送重复订单确认电子邮件的问题。
1. **ACSD-61348**：修复了在多网站环境中，通过[!DNL GraphQL]可见愿望清单项目，但店面不可见的问题。
1. **ACSD-61534**：修复了无法使用`bin/magento config:set`命令设置设计配置，以及通过表单操作更改锁定值的问题。 现在，无法更新从[!DNL CLI]中设置的带`--lock-env`或`--lock-conf`的锁定值。
1. **ACSD-61785**：修复了无法通过`reward_warning_notification`突变和[!DNL GraphQL]调用更新[!DNL REST API]属性的问题，使其行为与`reward_update_notification`保持一致。
1. **ACSD-62591**：修复了在配置&#x200B;**[!UICONTROL User Agent Rules]**&#x200B;时主题无法正确切换的问题。
1. **ACSD-62793**：修复了导出数据中的`datetime`属性不包含时间组件的问题。 此外，如果&#x200B;*[!UICONTROL Fields Enclosure]*&#x200B;启用了&#x200B;**，则`additional_attributes`列中的属性值将用双引号括起来。
1. **ACSD-62332**：修复了产品列表[!DNL GraphQL]查询仅限于10,000个产品中的`total_count`的问题。 此外，修复了在通过[!DNL Live Search]查询时，*将搜索条件中的当前页面设置为* 1 *而不是页面* 2[!DNL GraphQL]的问题。

使用左侧的菜单导航到特定的修补程序页面。
