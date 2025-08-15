---
title: MDVA-40262：GraphQL查询不会显示在管理员的常用搜索词中
description: 40262于MDVA的Adobe Commerce质量修补程序修复了GraphQL搜索查询无法在管理员的常用搜索词中显示的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3后，即可使用此修补程序。 修补程序ID为MDVA-40262。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: Admin Workspace, GraphQL, Search
role: Admin
exl-id: 9442ac86-e632-4ab3-8cb3-d29487a1ecbe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# MDVA-40262：GraphQL查询不会显示在管理员的常用搜索词中

40262于MDVA的Adobe Commerce质量修补程序修复了GraphQL搜索查询无法在管理员的常用搜索词中显示的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3时，此修补程序可用。 修补程序ID为MDVA-40262。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.2 - 2.4.3

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

GraphQL查询不会显示在管理员的常用搜索词中。

<u>先决条件</u>：

必须安装示例数据。

<u>重现步骤</u>：

1. 转到&#x200B;**商店** > **配置** > **目录** > **SEO** > **常用搜索词**&#x200B;并设置为启用。
1. 运行以下GraphQL查询：

<pre>
<code class="language-graphql">
&lbrace;
  products(
    search: "jackets"
    filter: { price: { to: "50" } }
    pageSize: 20
   ) &lbrace;
    total_count
    items &lbrace;
      name
      sku
    &rbrace;
    page_info &lbrace;
      page_size
      current_page
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>预期的结果</u>：

运行GraphQL查询以搜索产品后，应将搜索查询添加到常用搜索词中。

<u>实际结果</u>：

搜索查询未添加到常用搜索词。

## 应用修补程序

要应用单个修补程序，请根据您的部署类型使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Adobe Commerce质量修补程序的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的Quality Patches Tool[!DNL Quality Patches Tool]，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅QPT[中可用的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修补程序部分。
