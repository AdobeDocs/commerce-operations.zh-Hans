---
title: ACSD-65750： [!DNL GraphQL] "route"查询在 [!DNL Page Builder] 产品内容类型中返回不按顺序的产品
description: 应用ACSD-65750修补程序以修复Adobe Commerce问题，该问题导致GraphQL“route”查询在 [!DNL Page Builder] Products内容类型中返回产品按顺序排列。
feature: GraphQL, Page Builder, Products
role: Admin, Developer
type: Troubleshooting
exl-id: 3aee28e1-1293-42d0-a62c-5021e8f75518
source-git-commit: 2d6debf4d426a0473eb77919c2307afdc77bf937
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-65750： [!DNL GraphQL]“route”查询在[!DNL Page Builder]产品内容类型中返回不按顺序的产品

ACSD-65750修补程序修复了[!DNL GraphQL]“route”查询在[!DNL Page Builder]产品内容类型中返回产品乱序的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66时，此修补程序可用。 修补程序ID为ACSD-65750。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7-p1 - 2.4.8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用[!DNL GraphQL] Products内容类型时，[!DNL Page Builder]“route”查询未按正确的排序顺序返回产品。

<u>重现步骤</u>：

1. 在目录中创建新的类别和某些产品，并将这些产品链接到此类别。
1. 导航到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Categories]**，编辑创建的类别，然后打开&#x200B;**[!UICONTROL Products in Category]**&#x200B;选项卡。
1. 为此类别中的每个产品设置自定义&#x200B;**[!UICONTROL Position]**。
1. 保存类别并运行重新索引。
1. 导航到&#x200B;**[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**&#x200B;并单击&#x200B;**[!UICONTROL Add New Page]**。
1. 展开&#x200B;**[!UICONTROL Content]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Edit with Page Builder]**。
1. 将&#x200B;**[!UICONTROL Row]**&#x200B;元素拖动到内容区域，然后将&#x200B;**[!UICONTROL Products]**&#x200B;元素拖动到行中。
1. 按如下方式配置Products元素：
   * **[!UICONTROL Select Products By]**： *类别*
   * **[!UICONTROL Category]**： *选择新创建的类别*
   * **[!UICONTROL Sort By]**： *位置*
1. 切换到&#x200B;**[!UICONTROL Search Engine Optimization]**&#x200B;选项卡，并将&#x200B;**[!UICONTROL URL Key]**&#x200B;设置为&#x200B;*test-widget*。
1. 保存页面。
1. 发出以下[!DNL GraphQL]请求：

```
query {
  route(url: "/test-widget") {
    relative_url
    redirect_code
    type
    ... on CmsPage {
      identifier
      content
      __typename
    }
    ... on ProductInterface {
      uid
      __typename
    }
    ... on CategoryInterface {
      uid
      __typename
    }
    __typename
  }
}
```

<u>预期的结果</u>：

系统会按照产品类别位置定义的顺序返回产品。

<u>实际结果</u>：

系统返回产品的顺序与它们在GraphQL响应中的类别位置不匹配。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
