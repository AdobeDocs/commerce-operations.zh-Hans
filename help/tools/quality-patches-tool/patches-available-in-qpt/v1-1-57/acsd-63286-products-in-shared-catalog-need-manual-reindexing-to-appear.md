---
title: ACSD-63286：分配给共享目录的产品需要手动重新索引才能显示
description: 应用ACSD-63286修补程序以修复Adobe Commerce问题，该问题导致在执行手动重新索引之前，通过API分配到共享目录的产品不会显示在店面上。
feature: Products, REST
role: Admin, Developer
exl-id: 0435c06e-337e-4320-acc6-fa79a3b34008
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-63286：分配给共享目录的产品需要手动重新索引才能显示

ACSD-63286修补程序修复了以下问题：在执行手动重新索引之前，通过API分配到共享目录的产品不会显示在店面上。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57时，此修补程序可用。 修补程序ID为ACSD-63286。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当通过API将产品分配给共享目录时，在运行部分索引器和消费者cron作业后，它们不会出现在前端。 但是，在手动完全重新索引后，它们确实会显示。

<u>重现步骤</u>：

1. 将[!DNL RabbitMQ]设置为队列服务。
1. 创建共享目录并为其分配公司。
1. 创建简单产品并将其分配给类别。
1. 执行部分重新索引。

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. 使用以下API请求将创建的产品分配给共享目录`pub/rest/all/V1/sharedCatalog/<id>/assignProducts`：

   ```
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. 执行以下cron以清除队列并执行部分重新索引。

   ```
   bin/magento cron:run --group=consumers
   ```

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. 以公司用户身份登录到前端。
1. 选中前端类别页面。 新分配的产品不可见。
1. 执行手动重新索引：

   ```
   bin/magento index:reindex
   ```

<u>预期的结果</u>：

产品出现在前端，无需手动重新索引。

<u>实际结果</u>：

只有在手动重新索引后，产品才会出现在前端。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
