---
title: MDVA-40134：启用共享目录后，GraphQL未返回相关产品
description: MDVA-40134修补程序修复了在启用共享目录后，GraphQL未返回相关产品的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-40134。 请注意，Adobe Commerce 2.4.3中已修复此问题。
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
exl-id: 5d31e042-4396-40ce-8bf1-63ad9a55214d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-40134：启用共享目录后，GraphQL未返回相关产品

MDVA-40134修补程序修复了在启用共享目录后，GraphQL未返回相关产品的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-40134。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

启用共享目录后，GraphQL不会返回相关产品。

<u>先决条件</u>：

必须安装B2B模块。
必须只使用示例数据清空实例。

<u>重现步骤</u>：

1. 转到&#x200B;**商店** > **配置** > **常规** > **B2B功能**&#x200B;并启用&#x200B;**公司和共享目录**。
1. 转到&#x200B;**目录** > **共享目录**&#x200B;并将所有产品添加到&#x200B;**常规目录**。
1. 使用样本数据修改Joust Duffle Bag (SKU 24-MB01)。
1. 在&#x200B;**相关产品**&#x200B;下，添加两个饺子包（ID 7和13）。
1. 发送&#x200B;**Post**&#x200B;请求：

<pre>{
  products(filter： {sku： {eq： "24-MB01"}}，sort： {name： ASC}) {
    项目{
      related_products {
        uid
        name
      }
    }
  }
}</pre>

<u>预期的结果</u>：

GraphQL响应中将显示相关产品。

<u>实际结果</u>：

用户收到以下错误：

<pre>Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor：：getStoreId()的返回值必须是int类型，null返回{"exception"："[object] (GraphQL\\Error\\Error(code： 0)： Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor：：getStoreId()的返回值必须是int类型，返回的是null </pre>

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
