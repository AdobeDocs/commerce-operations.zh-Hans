---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.58
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.58中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
exl-id: 61bf8b82-f897-41f6-8524-5aa74c6440f1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.58

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.58中提供的修补程序所修复的问题。

QPT v1.1.58包含以下修补程序：

1. **ACSD-48570**：修复了以下问题：当[!UICONTROL Admin]将存储代码添加到URL **启用了**&#x200B;时，单击&#x200B;*重置密码链接无法访问重置密码页面*，该问题以前导致显示登录页面或404页面。
1. **ACSD-62118**：修复了使用Purchase Order方法下达`sales_order_tax_item`订单时[!DNL B2B]表未完全更新的问题。
1. **ACSD-63067**：修复了以下问题：所有产品数量都未正确突出显示，并且当只有一个数量不正确时，将为分组产品中的所有产品显示消息&#x200B;*[!DNL Please specify the quantity of product(s).]*。
1. **ACSD-63090**：修复了在将产品添加到购物车后，当产品被删除时购物车商品被删除的问题。
1. **ACSD-63182**：修复了在保存启用了&#x200B;**[!DNL MSI]** *的*&#x200B;的重复捆绑产品时出现错误的问题。
1. **ACSD-63283**：修复了以下问题：从礼品注册表中订购物品会导致异常，以及礼品注册表的更新中包含不属于注册表的物品。
1. **ACSD-63299**：修复了店面未显示可配置产品的特殊价格的问题。
1. **ACSD-63325**：修复了在提交空`Syntax Error: Unexpected <EOF>`请求时发生[!DNL GraphQL]错误的问题。
1. **ACSD-63329**：修复了在通过&#x200B;**[!UICONTROL Date]**&#x200B;创建产品时，未设置具有&#x200B;**[!UICONTROL Date and Time]**&#x200B;或[!DNL REST API]输入类型的属性的默认值的问题。
1. **ACSD-63572**：修复了在索引器进程终止时未清理`CatalogRule`索引器临时表的问题。
1. **ACSD-63578**：修复了单击&#x200B;**[!UICONTROL Delete]**&#x200B;中&#x200B;**[!UICONTROL Add to Order by SKU]**&#x200B;的[!UICONTROL Admin]按钮未删除[!DNL SKU]的问题。

使用左侧的菜单导航到特定的修补程序页面。
