---
title: ACSD-63572：如果索引器进程终止，则不会清理“catalogrule”索引器临时表
description: 应用ACSD-63572修补程序以修复因系统升级或在[!UICONTROL CLI]中停止进程而终止时，未清理索引器表的Adobe Commerce问题。
feature: System
Role: Admin, Developers
source-git-commit: 588a543a8c0bfb8067f81e7131d0a53e5cdc340a
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---


# ACSD-63572：如果索引器进程终止，则不会清除`catalogrule`索引器临时表

ACSD-63572修补程序修复了由于系统/升级或在[!UICONTROL CLI]中停止而终止进程时未清理索引器临时表的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58时，此修补程序可用。 修补程序ID为ACSD-63572。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

由于系统升级或在[!UICONTROL CLI]中停止，进程被终止时，索引器临时表未清除。

<u>重现步骤</u>：

1. 打开[!UICONTROL CLI]。
1. 运行命令： `bin/magento indexer:reindex catalogrule_rule`。
1. 在使用完成之前取消该进程： `^C`。
1. 使用以下方式重置索引器： `bin/magento indexer:reset catalogrule_rule catalogrule_product`。
1. 重复上述步骤多次。
1. 检查已在数据库中创建的以下临时表：

   ```
   catalogrule_product__temp*
   catalogrule_product_price__temp*
   ```

<u>预期的结果</u>：

当不需要旧临时表时，会将其删除。

<u>实际结果</u>：

不会删除旧的临时表。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
