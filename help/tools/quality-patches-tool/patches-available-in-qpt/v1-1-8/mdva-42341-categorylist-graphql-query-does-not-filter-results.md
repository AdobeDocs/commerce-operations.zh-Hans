---
title: MDVA-42341：“categoryList”GraphQL查询不筛选结果
description: MDVA-42341修补程序解决了当请求具有Store标头时，“categoryList”GraphQL查询不会筛选结果的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8后，即可使用此修补程序。 修补程序ID为MDVA-42341。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: GraphQL, Categories
role: Admin
exl-id: 56b81385-6db0-4e62-8e2b-bccfc9e0a581
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-42341：“categoryList”GraphQL查询不筛选结果

MDVA-42341修补程序解决了当请求具有Store标头时，“categoryList”GraphQL查询不会筛选结果的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8时，此修补程序可用。 修补程序ID为MDVA-42341。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果请求具有商店标头，则“categoryList”GraphQL查询不会筛选结果。

<u>重现步骤</u>：

1. 创建新的根类别并将其命名为&#x200B;**root2**。
1. 再创建一个网站/商店/商店，并将&#x200B;**root2**&#x200B;分配给新商店。
1. 在默认根类别= category1下创建新类别。
1. 使用GraphQL请求，获取第二个网站的类别列表（使用标题存储= new）。

<pre>
<code class="language-graphql">
&lbrace;
  categoryList(filters: {name: {match: "category1"}}) &lbrace;
    uid
    level
    name
    breadcrumbs &lbrace;
      category_uid
      category_name
      category_level
      category_url_key
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>预期的结果</u>：

响应时不列出默认根类别中的类别，因为我们使用的是“new”存储标头。

<u>实际结果</u>：

默认根类别中的类别在结果中可用。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
