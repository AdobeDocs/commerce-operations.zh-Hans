---
title: 'ACSD-56741：使用自定义MySQL触发器解决数据库设置错误'
description: 应用ACSD-56741修补程序以修复Adobe Commerce问题，该问题导致在“setup：upgrade”期间出现错误消息*尝试访问null类型的值上的阵列偏移*，这是因为数据库中存在与索引和 [!DNL MView]无关的自定义MySQL触发器。
feature: Install
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-56741：使用自定义MySQL触发器解决数据库设置错误

ACSD-56741修补程序修复了以下问题：由于数据库中存在与索引和[!DNL MView]无关的自定义MySQL触发器，在`setup:upgrade`期间出现错误消息&#x200B;*尝试访问null*&#x200B;类型的值的数组偏移。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48时，此修补程序可用。 修补程序ID为ACSD-56741。 请注意，该问题计划在Adobe Commerce 2.5.0中修复

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

由于数据库中的自定义MySQL触发器与索引和[!DNL MView]无关，因此在`setup:upgrade`期间出现错误消息&#x200B;*尝试访问类型为null*&#x200B;的值上的数组偏移。

<u>重现步骤</u>：

1. 运行`php bin/magento indexer:set-mode schedule`。

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. 运行`php bin/magento c:f`。
1. 运行`php bin/magento setup:upgrade`。

<u>预期的结果</u>：

安装程序升级完成，没有出现错误。

<u>实际结果</u>：

安装程序升级退出，并出现以下错误消息：

*警告：正在尝试访问类型为null*&#x200B;的值上的数组偏移。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
