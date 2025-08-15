---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.35
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.35中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin
exl-id: 5ffbade4-c95e-4b59-9262-1b141614c753
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.35

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.35中提供的修补程序所修复的问题。

QPT v1.1.35包含以下修补程序：

1. **ACSD-51899**：修复了使用先前选择的店内收取地址自动填充结账配送步骤上的默认配送地址的问题。
1. **ACSD-52041**：修复了错误消息&#x200B;*[ERROR] [!DNL Page Builder]呈现5秒而没有释放锁定的问题*。 保存使用[!DNL Chrome]编辑的内容时显示在[!DNL Page Builder]浏览器中。
1. **ACSD-52095**：修复了在产品导出后，CSV文件中的`manage_stock`值未正确设置为0的问题。
1. **ACSD-51358**：修复了删除没有结束日期的计划更新会导致为同一实体删除其他计划更新的问题。
1. **ACSD-48070**：修复了编辑计划更新会触发异常的问题。
1. **ACSD-51890**：修复了在没有[!UICONTROL Submit review] reCAPTCHA v3验证的情况下多次单击[!DNL Google]按钮的问题。
1. **ACSD-51984**：修复了以下问题：未选中&#x200B;*使用默认值和非默认产品字段值*&#x200B;未为第二个网站、商店和商店视图保存。
1. **ACSD-52398**：修复了错误&#x200B;*请求的数量不可用*，在尝试更新店面购物车中捆绑产品的数量时发生此错误。
1. **ACSD-52786**：修复了从给定SKU开始将目录规则条件SKU应用于所有产品的问题。
1. **ACSD-52921**：修复了在购物车中有缺货的可配置产品时从GraphQL请求购物车详细信息时出现内部错误的问题。
1. **ACSD-51683**：修复了使用GraphQL时无法将可自定义选项添加到购物车的问题。
1. **ACSD-52133**：修复了在升级后无法保存客户帐户的问题。
1. **ACSD-52202**：修复了在订单履行时将非默认库存更改为0数量时，默认库存的可销售数量错误地更改为0的问题。
1. **ACSD-51265**：修复了系统中捆绑产品过多时，`catalog_product_price`重新索引性能的问题。
1. **ACSD-52831**：修复了启用[!DNL Google reCAPTCHA v3 Invisible]后客户无法下可转让报价单的问题。
1. **ACSD-51845**：修复了无法通过异步批量REST API更新具有层价格和不同属性集的后续产品的问题。
1. **ACSD-52815**：修复了非默认来源的数量字段输入最多只支持6位数的问题，默认库存则支持8位。
1. **ACSD-51149**：修复了以下问题：启用了[!UICONTROL Scheduled ImportExport]的[!UICONTROL Catalog Permissions]使索引器失效，然后由cron缓存刷新。
1. **ACSD-50815**：修复了简单产品的小数数量不能用于新的捆绑产品选项的问题。
1. **ACSD-52399**：修复了可销售数量为0的可配置产品选项在产品页面上显示&#x200B;*库存中*&#x200B;的问题。

使用左侧的菜单导航到特定的修补程序页面。
