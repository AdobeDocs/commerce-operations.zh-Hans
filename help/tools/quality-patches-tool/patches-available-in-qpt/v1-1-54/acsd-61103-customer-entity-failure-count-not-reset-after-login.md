---
title: ACSD-61103：客户通过API成功登录后，故障计数不会重置为零
description: 应用ACSD-61103修补程序以修复Adobe Commerce问题：在客户通过API端点成功登录后，“customer_entity”表中的故障计数不会重置为零。
feature: GraphQL, REST, Customers
role: Admin, Developer
exl-id: 9f5aac1f-c8a3-4255-8ebc-2268283b3384
source-git-commit: acb5ff9656d7391de1e9b936909ce5a8a73d5d67
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61103：客户通过API成功登录后，故障计数不会重置为零

ACSD-61103修补程序解决了客户通过API端点成功登录后，`customer_entity`表中的故障计数未重置为零的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54时，此修补程序可用。 修补程序ID为ACSD-61103。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

即使客户通过API端点成功登录，`customer_entity`表中的失败计数也不会重置为零。

<u>重现步骤</u>：

1. 创建客户帐户。
1. 使用不正确的详细信息，通过API生成客户令牌。
1. 在`customer_entity`数据库表中为上述客户检查`failures_num`列。
1. 使用正确的详细信息，通过API生成客户令牌。
1. 在`customer_entity`数据库表中为上述客户检查`failures_num`列。

<u>预期的结果</u>：

在使用正确的凭据通过API生成客户令牌后，`failures_num`列应重置为0。

<u>实际结果</u>：

在使用正确的凭据通过API生成客户令牌后，`failures_num`列未重置为0。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。