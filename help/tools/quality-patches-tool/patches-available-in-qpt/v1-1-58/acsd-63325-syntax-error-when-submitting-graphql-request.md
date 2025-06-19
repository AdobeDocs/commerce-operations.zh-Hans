---
title: ACSD-63325：语法错误：提交空 [!DNL GraphQL] 请求时出现意外的&amp；lt；EOF&amp；gt；错误
description: 应用ACSD-63325修补程序以修复在提交empty [!DNL GraphQL] 请求时发生语法错误的Adobe Commerce问题。
feature: GraphQL
Role: Admin, Developer
exl-id: a83a8c5f-a43a-4733-a601-7b92656e5325
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# ACSD-63325：提交空[!DNL GraphQL]请求时出现“语法错误：意外&lt; EOF >”错误

ACSD-63325修补程序修复了在提交空[!DNL GraphQL]请求时返回“语法错误：意外&lt; EOF >”错误和非200响应代码的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58时，此修补程序可用。 修补程序ID为ACSD-63325。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

提交空[!DNL GraphQL]请求时，出现HTTP内部服务器错误，而不是200响应代码。

<u>重现步骤</u>：

1. 发送空的GraphQL请求

   ```graphql
   curl -i -X OPTIONS http://commerce.local/graphql
   ```

<u>预期的结果</u>：

请求的响应代码为200。

```
curl -i -X OPTIONS http://commerce.local/graphql
```

<u>实际结果</u>：

出现500内部服务器错误，如下所示：

```
HTTP/1.1 500 Internal Server Error
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce： Commerce on Cloud Infrastructure指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
