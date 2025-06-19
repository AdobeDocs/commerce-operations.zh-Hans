---
title: ACSD-62971：使用非数字数量值导入库存来源会导致数量设置为0
description: 应用ACSD-62971修补程序以修复Adobe Commerce问题，该问题导致在“数量”列中导入具有非数字值的库存源导致数量设置为0。
feature: Data Import/Export, Inventory
role: Admin, Developer
exl-id: ece23153-4932-4ac5-b46e-49327a8e84a1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-62971：使用非数字数量值导入库存来源会导致数量设置为0

ACSD-62971修补程序修复了以下问题：在“quantity”列中导入具有非数字值的库存源会导致数量设置为0。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56时，此修补程序可用。 修补程序ID为ACSD-62971。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

修复了导入&#x200B;**[!UICONTROL Quantity]**&#x200B;列中具有非数字值的库存源导致数量设置为0的问题。

<u>重现步骤</u>：

1. 创建&#x200B;**[!UICONTROL Simple Product]**，数量为100
1. 使用数量不正确(“abc”)的文件执行&#x200B;**[!UICONTROL Stock Sources]**&#x200B;导入

   ```table
   source_code    sku    status    quantity
     default     simple    1         abc
   ```

1. 检查导入后的数量。

<u>预期的结果</u>：
导入数据验证应该失败。

<u>实际结果</u>：
简单产品的数量已变为0，产品将更新为[!UICONTROL Out of Stock]。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
