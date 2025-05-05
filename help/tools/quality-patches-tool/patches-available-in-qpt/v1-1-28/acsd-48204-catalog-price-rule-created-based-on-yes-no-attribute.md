---
title: ACSD-48204：根据*是/否*属性创建的目录价格规则不考虑选定的范围
description: 应用ACSD-48204补丁程序，以修复基于*是/否*属性创建的目录价格规则不考虑所选范围的Adobe Commerce问题。
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
exl-id: 69f2b35c-856e-4f96-ae2f-fb0c64d5eb94
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-48204：基于&#x200B;*是/否*&#x200B;属性创建的目录价格规则不考虑选定的范围

ACSD-48204修补程序修复了基于&#x200B;*是/否*&#x200B;属性创建的目录价格规则未考虑所选范围的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28时，此修补程序可用。 修补程序ID为ACSD-48204。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

基于&#x200B;*是/否*&#x200B;属性创建的目录价格规则不考虑所选范围。

<u>重现步骤</u>：

1. 创建两个网站（默认网站和W2网站）。
1. 创建&#x200B;*是/否*&#x200B;类型的产品属性。
   * 设置[!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. 基于具有两个变体（V1和V2）的任意属性创建可配置产品。
   * 将&#x200B;*是/否*&#x200B;属性添加到可配置的变体属性集
   * 对于变体(V1)之一，在非默认网站(W2)上将值设置为&#x200B;*[!UICONTROL Yes]*
1. 创建目录规则：
   * 应用于两个网站
   * 条件： *是/否*&#x200B;属性值是&#x200B;*[!UICONTROL Yes]*
   * 折扣= 50%
1. 在非默认网站(W2)上打开可配置产品。
1. 检查V1变量是否应用了50%的折扣。
1. 在Adobe Commerce管理员中打开V1变体。
   * 切换到默认网站
   * 不做更改并保存产品
1. 刷新可配置产品的店面页面。

<u>预期的结果</u>：

由于未进行任何更改，V1变量仍应用50%的折扣。

<u>实际结果</u>：

折扣将消失。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
