---
title: B2B-2674：向customAttributeMetadata GraphQL查询添加了缓存功能
description: 应用B2B-2674修补程序以向customAttributeMetadata GraphQL查询添加缓存功能。
feature: Attributes, B2B, Cache, GraphQL
role: Admin
exl-id: b49633f3-b144-405f-a21d-726e222a7bfe
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# B2B-2674：向`customAttributeMetadata` GraphQL查询添加了缓存功能

B2B-2674修补程序向`customAttributeMetadata`个GraphQL查询添加了缓存功能。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30时，此修补程序可用。 修补程序ID为B2B-2674。 请注意，该问题计划在Adobe Commerce 2.4.7-beta1中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

`customAttributeMetadata` GraphQL查询不可缓存。

<u>先决条件</u>：

* 服务器正在指向[!DNL Varnish]代理到Adobe Commerce后端。
* 配置设置`system/full_page_cache/caching_application`设置为&#x200B;*2* ([!DNL Varnish])，或转到Adobe Commerce管理员> **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** >并将其设置为[!DNL Varnish]。

应用修补程序后，请运行以下步骤以确保缓存功能现在可用：

1. 使用任意字段将`GET`请求发送到上面列出的GraphQL查询。
1. 重新发送请求，且不做任何更改；您会发现它速度更快。 请注意，该请求未发送到后端，但已由[!DNL Varnish]作为缓存命中完全处理。
1. 如果需要进一步验证，请注释掉[VCL](https://github.com/magento/magento2/blob/2.4-develop/app/code/Magento/PageCache/etc/varnish6.vcl#L239)中存在的`X-Magento-Debug`标头的未设置，然后重新启动[!DNL Varnish]并再次运行上述步骤。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
