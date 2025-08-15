---
title: ACSD-64627：无法在[!UICONTROL Company Structure]中保存自定义客户属性
description: 应用ACSD-64627修补程序以修复在[!UICONTROL Company Structure]内添加或编辑用户时无法保存自定义客户属性的Adobe Commerce问题。
feature: B2B
role: Admin, Developer
exl-id: 8e7dd72e-c21e-46cf-8e2b-9dccedfd8b04
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-64627：无法在[!UICONTROL Company Structure]中保存自定义客户属性

ACSD-64627修补程序修复了在&#x200B;**[!UICONTROL Company Structure]**&#x200B;页面中添加或编辑用户时无法保存自定义客户属性的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63时，此修补程序可用。 修补程序ID为ACSD-64627。 请注意，该问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3、2.4.7-p4、2.4.8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6-p8、2.4.7-p3、2.4.7-p4、2.4.8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在&#x200B;**[!UICONTROL Company Structure]**&#x200B;页面上添加或编辑用户时，自定义客户属性不会保存。

<u>重现步骤</u>：

1. 安装启用了B2B功能的Adobe Commerce实例。
1. 创建名为&#x200B;*custom_upload*&#x200B;且将&#x200B;**[!UICONTROL Input Type]**&#x200B;设置为&#x200B;*[!UICONTROL File (attachment)]*&#x200B;的新客户属性。
1. 创建另一个名为&#x200B;*image_attachment*&#x200B;的客户属性，并将&#x200B;**[!UICONTROL Input Type]**&#x200B;设置为&#x200B;*[!UICONTROL Image File]*。
1. 将&#x200B;**[!UICONTROL Show on Storefront]**&#x200B;设置为&#x200B;*是*&#x200B;以使这两个属性在店面中均可见。 选择所有表单：
   * 客户注册
   * 客户帐户编辑
   * 管理员签出
1. 创建和激活新公司。
1. 以公司管理员身份登录到店面。
1. 导航到&#x200B;**[!UICONTROL Customer Account]** > **[!UICONTROL Company Structure]**&#x200B;或&#x200B;**[!UICONTROL Customer Account]** > **[!UICONTROL Company Users]**。
1. 单击&#x200B;**[!UICONTROL Add New User]**。
1. 单击&#x200B;**[!UICONTROL Upload]** custom_upload *属性的*。
1. 单击&#x200B;**[!UICONTROL Select file]** image_attachment *属性的*。

<u>预期的结果</u>：

文件资源管理器会打开两个属性。 保存时，将存储值并成功上传文件。

<u>实际结果</u>：

按钮无响应。 不会打开文件资源管理器或保存数据。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
