---
title: ACSD-65777：“MediaGallery”GraphQL请求中缺少产品图像类型的“types”字段
description: 应用ACSD-65777修补程序以修复Adobe CommerceGraphQL请求中的“MediaGallery”产品图像类型缺少“types”字段的问题。
feature: GraphQL, Media
role: Admin, Developer
type: Troubleshooting
exl-id: 20866963-54a3-4859-9c2d-716945e37156
source-git-commit: 5bcafd22647f9a87596c4f2d852bda76a5d6427b
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# ACSD-65777：**[!UICONTROL types]** GraphQL请求中的产品图像类型缺少`MediaGallery`字段

ACSD-65777修补程序修复了&#x200B;**[!UICONTROL types]** GraphQL请求中产品映像类型缺少`MediaGallery`字段的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66时，此修补程序可用。 修补程序ID为ACSD-65777。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过&#x200B;**[!UICONTROL types]** GraphQL请求获取媒体数据时，产品图像类型缺少`MediaGallery`字段。

<u>重现步骤</u>：

1. 创建产品。
1. 将图像上传到产品。
1. 使用以下GraphQL获取媒体数据。

   ```
   query{
     products(search:"",filter:{sku:{eq:"p1"}})\{
       items{
         media_gallery{
           disabled
           label
           position
           url
         }
         media_gallery_entries\{
           types
         }
       }
     }
   }
   ```

<u>预期的结果</u>：

`media_gallery` GraphQL界面应包含&#x200B;**[!UICONTROL types]**&#x200B;字段。

<u>实际结果</u>：

`media_gallery`不包含媒体&#x200B;**[!UICONTROL types]**&#x200B;字段。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
