---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.57
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.57中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
exl-id: 3e252a71-f35f-4046-9353-169060451ffe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.57

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.57中提供的修补程序所修复的问题。

QPT v1.1.57包含以下修补程序：

1. **ACSD-57570**：修复了以下问题：具有特定商店访问权限的受限管理员用户无法始终查看产品所分配的所有共享目录，或无法查看客户，从而导致系统中出现不一致的情况。
1. **ACSD-58325**：修复了[!UICONTROL Import]按钮在验证错误后仍可用的问题。
1. **ACSD-59083**：修复了某些数据库更新操作导致&#x200B;_未找到基表或视图的问题_&#x200B;错误（如果[!DNL mview]更新同时运行）。
1. **ACSD-61622**：修复了响应中缺少[!DNL FedEx]帐户特定费率的问题。 ACSD-61622取代了从 [!DNL SOAP] 迁移到 [!DNL RESTful API]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/fedex-shipping-method-integration-migration-soap-restful-api)的[[!DNL FedEx] 送货方法集成中记录的修复。
1. **ACSD-61895**：修复了类别[!DNL GraphQL]查询返回具有&#x200B;*允许*&#x200B;权限的类别的问题，即使根类别没有&#x200B;*允许*&#x200B;权限。
1. **ACSD-62212**：修复了[!UICONTROL Forgot Password]电子邮件内容未翻译为商店视图语言的问题。
1. **ACSD-62481**：修复了即使启用了[!UICONTROL Persistence]，客户的购物车也变空的问题。
1. **ACSD-62629**：修复了[!UICONTROL Widgets]中使用的产品列表不遵循类别条件的问题。
1. **ACSD-62635**：修复了[!DNL GraphQL]产品查询中无法正确显示多商店相关产品的问题。
1. **ACSD-62671**：修复了[!DNL GraphQL]请求在第一次尝试时未返回最新地址信息的问题。
1. **ACSD-62689**：修复了客户无法在深度4之后在[!UICONTROL Related Product Rules]和[!UICONTROL Widgets]中添加类别的问题。
1. **ACSD-62708**：修复了在应用[!UICONTROL ACP2E-3430]的修复后，管理员中的[!DNL TinyMCE] 7编辑器字体大小显示为[!UICONTROL pt]而非[!UICONTROL px]的问题。 现在，您还可以在[!UICONTROL px]中设置[!UICONTROL pt]的字体大小。
1. **ACSD-62758**：修复了URL包含所选选项时，[!UICONTROL Configurable Product]详细信息页面上产品视频无法正确呈现的问题。
1. **ACSD-62951**：修复了发送[!UICONTROL Credit Memo]电子邮件而不包含项目和总数的问题。
1. **ACSD-62965**：修复了下单[!DNL GraphQL response]中未包含&#x200B;*LocalizedException*&#x200B;消息的问题。
1. **ACSD-63286**：修复了在执行手动重新索引之前，通过API分配到共享目录的产品未显示在店面中的问题。
1. **ACSD-63326**：修复了从后端下订单后，管理员被重定向到损坏页面的问题。


使用左侧的菜单导航到特定的修补程序页面。
