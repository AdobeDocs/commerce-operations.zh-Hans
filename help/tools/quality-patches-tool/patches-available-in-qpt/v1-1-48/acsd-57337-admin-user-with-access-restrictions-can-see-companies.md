---
title: ACSD-57337：具有访问限制的管理员用户可查看*公司*网格中的所有公司
description: 应用ACSD-57337修补程序以修复Adobe Commerce问题，该问题导致对特定网站具有访问限制的管理员用户可以在*公司*网格中查看所有网站中的公司。
feature: Companies, B2B, Configuration
role: Admin, Developer
exl-id: 7a05d335-5ed8-460e-80c4-dbc51d06c5bd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-57337：具有访问限制的管理员用户可查看&#x200B;*公司*&#x200B;网格中的所有公司

ACSD-57337修补程序修复了具有特定网站访问限制的管理员用户可查看&#x200B;*公司*&#x200B;网格中所有网站的公司的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48时，此修补程序可用。 修补程序ID为ACSD-57337。 请注意，该问题计划在Adobe Commerce 2.5.0中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对特定网站具有访问限制的管理员用户可以在&#x200B;*公司*&#x200B;网格中查看所有网站中的公司。

<u>重现步骤</u>：

1. 创建其他网站、商店和商店评论。
1. 创建一些分配给不同网站的公司。
1. 创建管理员用户角色，并将角色范围设置为已创建的网站。
1. 创建管理员，并将其分配给已创建的角色。
1. 使用新管理员登录。
1. 打开&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL Companies]**&#x200B;并观察公司列表。

<u>预期的结果</u>：

已分配到其他网站的公司在&#x200B;*公司*&#x200B;网格中可见。

<u>实际结果</u>：

所有公司在&#x200B;*公司*&#x200B;网格中均可见。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
