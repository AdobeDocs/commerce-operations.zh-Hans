---
title: MDVA-31590：无法使用MySQL异步队列批量更新属性
description: MDVA-31590修补程序解决了用户无法使用MySQL异步队列批量更新属性的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3后，即可使用此修补程序。 修补程序ID为MDVA-31590。 请注意，Adobe Commerce 2.4.2中已修复此问题。
feature: Attributes, Services
role: Admin
exl-id: f8d1c3bd-e995-41ef-89e1-93eec6e8b1f1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# MDVA-31590：无法使用MySQL异步队列批量更新属性

MDVA-31590修补程序解决了用户无法使用MySQL异步队列批量更新属性的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3时，此修补程序可用。 修补程序ID为MDVA-31590。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.0

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0-2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户无法使用MySQL异步批量更新属性。

<u>重现步骤</u>：

1. 在后端的产品网格上，执行批量操作以更新几个产品的属性值。
   * 检查产品并从“操作”下拉列表中选择&#x200B;**更新属性**。
1. 设置所需属性的值并将产品分配给网站并保存。
1. 重新加载页面后，它将显示如下消息：
   *任务“更新N个选定产品的属性”：已计划更新1个项目。*
1. 等待几秒钟，然后重新加载后端页面。

<u>预期的结果</u>：

1. 页面显示已成功更新的消息，例如： *1个项目已成功更新。*
1. 相关产品的属性值已更新。
1. 在DB中，新记录同时在`magento_bulk`表和`magento_operation`表中创建（与批量相关的操作）。
1. 在`queue_message`表中创建了新记录（与队列`product_action_attribute.update`和/或`product_action_attribute.website.update`相关）。
1. `queue_message_status`表具有状态为“4”的记录。
1. `system.log`中没有错误。

<u>实际结果</u>：

1. 该页面仍会显示如下消息：
   *任务“更新N个选定产品的属性”：已计划更新1个项目。*
1. 产品的属性值会更新。
1. 已在`message_bulk`表中创建新记录，但`magento_operation`表中没有相关记录。
1. 在`queue_message`和`queue_message_status`表中创建了新记录。
1. `queue_message_status`表具有错误状态的记录（状态值“6”）。
1. `system.log`包含类似于以下内容的错误：

   ```sql
   *main.CRITICAL: Message has been rejected: SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'operation_key' cannot be null, query was: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?) [] []*
   ```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的Quality Patches Tool[!DNL Quality Patches Tool]，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅QPT[中可用的](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)修补程序部分。
