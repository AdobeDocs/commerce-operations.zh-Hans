---
title: ACSD-47137：提高图像库加载速度“pub/media”文件夹大
description: 当“pub/media”文件夹非常大时，应用ACSD-47137修补程序以提高图像库的加载速度。
feature: Cache, Catalog Management, Categories, Media
role: Admin
exl-id: 8a5dd930-1940-486e-96db-ee1b166cf312
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-47137：提高`pub/media`文件夹大时的图像库加载速度

当`pub/media`文件夹非常大时，ACSD-47137修补程序可提高图像库的加载速度。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24时，此修补程序可用。 修补程序ID为ACSD-47137。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当`pub/media`文件夹非常大时，图像库的加载速度缓慢。

<u>重现步骤</u>：

1. 前往Adobe Commerce管理员> **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]**&#x200B;至&#x200B;_否_。
1. 清除配置缓存。
1. 注销并以管理员用户身份再次登录。
1. 在管理员侧边栏中，转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Categories]**&#x200B;并选择根类别。
1. 展开&#x200B;**[!UICONTROL Content]**&#x200B;部分并单击&#x200B;**[!UICONTROL Select from Gallery]**。

加载页面时，Adobe Commerce发送`media_gallery/directories/gettree`请求以加载媒体文件夹树。

<u>预期的结果</u>：

`media_gallery/directories/gettree`请求应仅从必要的目录加载内容，而不是从`pub/media/`文件夹循环整个路径列表。

<u>实际结果</u>：

当`pub/media/`文件夹包含大量内容时，`media_gallery/directories/gettree`请求需要很长时间才能加载。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
