---
title: ACSD-48417：创建计划更改后出现SQL错误
description: 应用ACSD-48417修补程序以修复Adobe Commerce问题，该问题导致在为产品创建计划更改并保存另一个产品后显示SQL错误。
feature: Storage
role: Admin
exl-id: c8e7c7aa-ac53-4218-8c3c-ea2240af17c9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-48417：创建计划更改后出现SQL错误

ACSD-48417修补程序修复了在为产品创建计划更改并保存另一个产品后显示SQL错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26时，此修补程序可用。 修补程序ID为ACSD-48417。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.1-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

创建产品的计划更改并保存另一个产品后，出现SQL错误。

<u>重现步骤</u>：

1. 安装Magento 2.4开发EE +示例数据。
1. 转到管理面板> **[!UICONTROL Catalog]** > **[!UICONTROL Products]**。
1. 编辑任何产品（例如，Joust Duffle Bag [SKU： 24-MB01]）。
1. 计划新的更新：
   * 选择&#x200B;**[!UICONTROL Save as a New Update]**
   * 更新名称：“更新1”
   * 开始日期：当前时间+1分钟
   * 结束日期：当前时间+1小时
   * 将产品名称修改为：“Joust Duffle Bag 2”
   * 保存产品。
1. 转到CLI并执行cron，然后等待直至应用计划。

   ```
   bin/magento cron:run && bin/magento cron:run
   ```

1. 再次转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;并编辑任何可配置的产品（例如，Chaz Kangeroo Hoodie [SKU： MH01]）。

   * 禁用所有变体。 转到操作列> **[!UICONTROL Select]** > **[!UICONTROL Disable Product]**。
   * 保存可配置的一个。

<u>预期的结果</u>：

保存产品时没有错误。

<u>实际结果</u>：

出现以下错误：

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
