---
title: ACSD-56635：将帐户共享设置为 [!DNL Global]时，导入的客户重复
description: 应用ACSD-56635修补程序以修复Adobe Commerce问题，该问题导致在使用导入且帐户共享设置为 [!DNL Global]时，导入的客户使用相同的电子邮件地址重复。
feature: Customers, Attributes
role: Admin, Developer
exl-id: 73abec4a-03b0-45d4-bfc6-f3c6862e733c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-56635：帐户共享设置为[!DNL Global]时，导入的客户使用相同的电子邮件地址重复

ACSD-56635修补程序修复了在帐户共享设置为[!DNL Global]的情况下使用导入时，导入的客户使用相同的电子邮件地址重复的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48时，此修补程序可用。 修补程序ID为ACSD-56635。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

帐户共享设置为[!DNL Global]时，导入的客户使用相同的电子邮件地址重复。

<u>重现步骤</u>：

1. 在Adobe Commerce （2.4 — 开发b2b） **[!UICONTROL Admin]**&#x200B;下，访问&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**。
1. 将&#x200B;*[!UICONTROL Share Customer Accounts]*&#x200B;设置设置为&#x200B;*[!DNL Global]*。
1. 创建多个网站和商店：

   * ws1 > s11， s12 > sw111， sw122
   * ws2 > s21， s22 > sw211， sw212

1. 在&#x200B;*主网站*&#x200B;下从管理员创建新客户，电子邮件地址用作<adb@yormail.com>。
1. 在&#x200B;**[!UICONTROL Admin]**&#x200B;下，导航到&#x200B;**[!UICONTROL System]** > **[!UICONTROL Import]**。
1. 选择&#x200B;**[!UICONTROL Customer Entity Type]**&#x200B;作为&#x200B;*[!UICONTROL Customers Main File]*。
1. 在其他网站上使用与<adb@yormail.com>相同的电子邮件地址，例如ws1。 请参阅下面给出的示例CSV文件customer.csv 。
1. 完成导入以查看在&#x200B;*ws1*&#x200B;网站下创建的新用户使用相同的电子邮件地址。

customer.csv内容：

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>预期结果</u>：

会更新具有相同电子邮件地址的导入客户，而不是进行重复。

<u>实际结果</u>：

使用客户导入时，会使用相同的电子邮件地址创建重复客户。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)：搜索修补程序[!DNL Quality Patches Tool]。
