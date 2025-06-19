---
title: MDVA-43491：通过CSV导入时，基本图像标签未更新
description: MDVA-43491修补程序修复了在通过多商店网站的CSV文件导入时，“base_image_label”不会更新的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-43491。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Data Import/Export
role: Admin
exl-id: f6a5f641-aaf0-4b6e-afa9-7f436f8f59e6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-43491：通过CSV导入时，基本图像标签未更新

MDVA-43491修补程序修复了在通过多商店网站的CSV文件导入时，`base_image_label`不会更新的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-43491。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.5 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

为多商店网站使用CSV文件导入时，`base_image_label`不会更新。

<u>先决条件</u>：

一个或多个现有的非默认网站、商店和商店视图。

<u>重现步骤</u>：

1. 创建新产品。

   * 上传图像。
   * 将产品分配给新创建的网站。

1. 将产品导出为CSV。
1. 通过复制CSV文件的默认行来更新每个商店视图的`base_image_label`。
1. 导入CSV文件。 它将正确更新每个商店的标签，可在产品编辑页面上的&#x200B;**图像和视频**&#x200B;选项卡下验证这些标签。
1. 再次导出CSV文件并使用不同的值更新`base_image_label`列。
1. 再次导入CSV文件。
1. 在“管理员”中打开产品，并检查每个商店视图的标签是否已更新。

<u>预期的结果</u>：

替代文本（图像标签）将根据CSV文件使用特定于存储的值更新。

<u>实际结果</u>：

替代文本（图像标签）未使用CSV文件中的`base_image_label`值更新。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
