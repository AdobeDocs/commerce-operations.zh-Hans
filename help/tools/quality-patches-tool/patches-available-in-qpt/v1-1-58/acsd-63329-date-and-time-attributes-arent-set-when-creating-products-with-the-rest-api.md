---
title: ACSD-63329：使用REST API创建产品时，未设置日期和时间属性
description: 应用ACSD-63329修补程序以修复使用REST API创建产品时，未设置日期和时间字段默认值的Adobe Commerce问题。
feature: REST
Role: Admin, Developers
exl-id: d8e7917b-07a5-465b-944b-fd6168dea63c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63329：使用REST API创建产品时，未设置日期和时间字段的默认值

ACSD-63329修补程序修复了在使用REST API创建新产品时，没有为日期和时间字段设置默认值的问题：`/rest/default/V1/products`。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58时，此修补程序可用。 修补程序ID为ACSD-63329。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用REST API创建产品时，没有为日期和时间字段设置默认值： `/rest/default/V1/products`

<u>重现步骤</u>：

1. 创建&#x200B;**[!UICONTROL Product]**&#x200B;特性，将其默认值设置为`12/31/2020`，并将&#x200B;**[!UICONTROL Catalog Input Type for Store Owner]**&#x200B;设置为&#x200B;***[!UICONTROL Date]***&#x200B;或&#x200B;***[!UICONTROL Date and Time]***。
1. 创建另一个文本类型属性，并将默认值设置为&#x200B;***测试值***。
1. 使用对`/rest/all/V1/products/`的REST API POST请求创建新产品。

   ```
       {
           "product": {
               "sku": "testsku2",
               "name": "Test Api Product 2",
               "attribute_set_id": 4,
               "price": 100,
               "status": 1,
               "visibility": 4,
               "type_id": "simple",
               "weight": 20,
               "extension_attributes": {
                   "website_ids": [
                       1
                   ]
               }
           }
       }
   ```

1. 检查为上述属性保存的值。

<u>预期的结果</u>：

使用API创建产品时，默认值应保存在&#x200B;**[!UICONTROL Date/Datetime]**&#x200B;类型属性中。

<u>实际结果</u>：

已为&#x200B;**[!UICONTROL Text]**&#x200B;属性保存默认值，但不为&#x200B;**[!UICONTROL Date type]**&#x200B;属性保存默认值。 **[!UICONTROL Date]**&#x200B;属性的值为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
