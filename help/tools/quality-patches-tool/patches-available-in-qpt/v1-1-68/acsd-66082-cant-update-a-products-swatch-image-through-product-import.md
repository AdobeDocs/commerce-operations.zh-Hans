---
title: ACSD-66082：无法通过产品导入更新产品的样本图像
description: 应用ACSD-66082补丁以修复Adobe Commerce的问题，该问题导致在将swatch_image字段设置为EMPTY_VALUE以取消设置样本图像的情况下上传CSV文件会导致导入过程失败并出现错误。
feature: Products, Data Import/Export, Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: bdd15514c6b6ece6c7f33a41267357b4a24261f1
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# ACSD-66082：无法通过产品导入更新产品的样本图像

ACSD-66082修补程序修复了无法通过产品导入更新产品的样本图像的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68时，此修补程序可用。 修补程序ID为ACSD-66082。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果上传CSV文件时将`swatch_image`字段设置为`EMPTY_VALUE`以取消设置样本图像，则会导致导入过程失败并出现错误。

<u>重现步骤</u>：

1. 创建一个简单的产品。 转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**。 单击&#x200B;**[!UICONTROL Add Product]**&#x200B;按钮旁边的向下箭头并选择&#x200B;**[!UICONTROL Simple Product]**。 将其&#x200B;**[!UICONTROL SKU]**&#x200B;设置为&#x200B;*ABC*。
1. 将名为&#x200B;*testing.png*&#x200B;的PNG图像上载到`var/import/images/`。
1. 创建包含以下内容的CSV文件：

   ```
   sku,swatch_image,swatch_image_label
   ABC,testing.png,testing
   ```

1. 转到&#x200B;**[!UICONTROL System]** > **[!UICONTROL Import]**&#x200B;以通过调整以下设置导入文件：
   * **[!UICONTROL Entity type]**： *产品*
   * **[!UICONTROL Import Behavior]**： *添加/更新*
   * 单击&#x200B;**[!UICONTROL Choose File]**&#x200B;以选择在上一步中创建的CSV文件进行导入。 导入成功，样本即被添加。
1. 使用以下内容更新CSV：

   ```
   sku,swatch_image,swatch_image_label
   ABC,__EMPTY__VALUE__,__EMPTY__VALUE__
   ```

1. 重复导入过程。

<u>预期的结果</u>：

样本图像未设置。

<u>实际结果</u>：

导入过程引发错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
