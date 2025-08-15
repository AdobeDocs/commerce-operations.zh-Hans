---
title: ACSD-62671： [!DNL GraphQL] 第一次尝试时未返回更新的地址
description: 应用ACSD-62671修补程序以修复Adobe Commerce问题，该问题导致 [!DNL GraphQL] 请求在第一次尝试时未返回最新的地址信息。
feature: GraphQL
role: Admin, Developer
exl-id: afd75ad2-e801-4f8a-b68f-526ca5168413
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-62671： [!DNL GraphQL]在第一次尝试时未返回更新的地址

ACSD-62671修补程序修复了[!DNL GraphQL]请求在第一次尝试时未返回最新地址信息的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57时，此修补程序可用。 修补程序ID为ACSD-62671。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用[!DNL GraphQL Application Server]时，客户地址请求未返回最新数据。

<u>重现步骤</u>：

1. 安装并启动[!DNL GraphQL Application Server]。
1. 确保已启用`graphQL_query_resolver_result`缓存类型。
1. 使用[!DNL GraphQL]可以：

   * 创建客户。
   * 生成令牌。
   * 使用令牌为上述客户创建多个地址。

1. 发送[!DNL GraphQL]请求以获取客户的地址。
1. 向客户添加新地址。
1. 在监视响应中返回的地址计数时，多次重复步骤#4中的请求。

<u>预期的结果</u>：

[!DNL GraphQL]响应包含正确数量的客户地址。

<u>实际结果</u>：

有时，[!DNL GraphQL]响应中返回的地址数不正确。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
