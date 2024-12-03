---
title: ACSD-62485：“async.operations.all”使用者在创建公司时停止工作
description: 应用ACSD-62485修补程序以修复以下Adobe Commerce问题：创建B2B公司后，“async.operations.all”使用者停止工作。
feature: B2B, Companies
role: Admin, Developer
exl-id: 99d20555-fe55-4a04-a067-5a2b104811f5
source-git-commit: 9d0925ae06c3ccf9ed6b2d89cec07f8f5fe2f94f
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# ACSD-62485：创建公司后，`async.operations.all`使用者停止工作

ACSD-62485修补程序修复了在创建B2B公司时`async.operations.all`使用者停止工作的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54时，此修补程序可用。 修补程序ID为ACSD-62485。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p7

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p7、2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果在使用者仍在运行时异步创建B2B公司，`async.operations.all`使用者将停止处理消息。

<u>先决条件</u>：

B2B模块已安装和启用。

<u>重现步骤</u>：

1. 创建两个客户。
1. 发送REST批量请求以创建两家公司，并将创建的客户分配为公司管理员。
1. 使用以下命令启动消费者：

   ``` bin/magento queue:consumer:start async.operations.all --max-messages=20000 ```

<u>预期的结果</u>：

用户处理了20,000条消息并成功结束。

<u>实际结果</u>：

使用者在执行后立即停止工作。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
