---
title: ACSD-59952：删除与其他共享目录具有相同组ID的共享目录时出错
description: 应用ACSD-59952修补程序以修复Adobe Commerce问题，该问题导致在删除与另一个共享目录具有相同“customer_group_id”的共享目录时引发错误。
feature: B2B, REST
role: Admin, Developer
exl-id: 11cba2e6-dd62-4063-a38c-b98ea70a72e9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-59952：删除与其他共享目录具有相同组ID的共享目录时出错

ACSD-59952修补程序修复了在删除与其他共享目录具有相同`customer_group_id`的共享目录时引发的错误。 它还可防止用户创建此类共享目录。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52时，此修补程序可用。 修补程序ID为ACSD-59952。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

无法创建与另一共享目录具有相同`customer_group_id`的新共享目录。 但是，在执行此操作时，尝试删除具有相同`customer_group_id`的共享目录会引发错误。

<u>先决条件</u>：

安装Adobe Commerce B2B模块。

<u>重现步骤</u>：

1. 使用以下REST API调用创建分配给同一`customer_group_id`的多个共享目录：

   ```REST
   {
       "sharedCatalog": {
           "name": "test1",
           "description": "test",
           "customer_group_id": 1,
           "type": 0,
           "created_at": "03:11:00",
           "created_by": 1,
           "store_id": 0,
           "tax_class_id": 3
       }
   }
   ```

1. 尝试使用以下REST API调用删除任何共享目录：

   ```REST
   /rest/default/V1/sharedCatalog/4
   ```

<u>预期的结果</u>：

* 无法创建分配给同一`customer_group_id`的多个共享目录。
* 上述案例中的共享目录已成功删除。

<u>实际结果</u>：

* 可以创建分配给同一`customer_group_id`的多个共享目录。
* 尝试删除具有相同`customer_group_id`的共享目录时返回以下错误： *无法删除共享目录*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：我们支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用我们的支持知识库中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查您的Adobe Commerce问题是否有可用的修补程序。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
