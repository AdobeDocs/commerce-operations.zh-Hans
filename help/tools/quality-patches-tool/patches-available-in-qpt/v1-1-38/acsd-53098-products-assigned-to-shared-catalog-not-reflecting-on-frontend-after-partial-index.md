---
title: 'ACSD-53098：共享目录中的产品不会在前端反映'
description: 应用ACSD-53098修补程序以修复分配至共享目录的产品在执行部分索引时未在前端反映的Adobe Commerce问题。
feature: B2B, Catalog Management, Categories, Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-53098：共享目录中的产品不会在前端反映

ACSD-53098修补程序修复了分配给共享目录的产品在执行部分索引时未在前端反映的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.38时，此修补程序可用。 修补程序ID为ACSD-53098。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

部分索引器先执行cron作业，接着执行消费者cron作业后，通过API分配到共享目录的产品不会出现在前端。

<u>重现步骤</u>：

1. 将[!DNL RabbitMQ]设置为队列服务。
1. 将索引器切换到&#x200B;**[!UICONTROL Update on Schedule]**&#x200B;模式。
1. 创建共享目录并将其分配给公司。
1. 创建简单产品并将其分配给类别。 执行部分重新索引：

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. 使用以下API请求将创建的产品分配给共享目录。

   ```
   pub/rest/all/V1/sharedCatalog/<id>/assignProducts
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. 执行以下cron以清除队列，并执行部分重新索引：

   `bin/magento cron:run --group=consumers`

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. 以公司用户的身份登录到前端。
1. 选中前端类别页面。

<u>预期的结果</u>：

新分配的产品会显示在前端。

<u>实际结果</u>：

新分配的产品不会出现在前端。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
