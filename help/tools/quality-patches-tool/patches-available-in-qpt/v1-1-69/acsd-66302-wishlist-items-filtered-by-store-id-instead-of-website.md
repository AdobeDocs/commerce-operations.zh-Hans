---
title: ACSD-66302：按商店ID而不是网站过滤的愿望清单项目
description: 应用ACSD-66302修补程序以修复Adobe Commerce问题，该问题导致在 [!DNL GraphQL] 请求中按商店ID而不是网站来过滤愿望清单项目。
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7f9a13a9a8cc666c8aa9d964da8aaff01913d35f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---


# ACSD-66302：按商店ID而不是网站过滤的愿望清单项目

ACSD-66302修补程序修复了在[!DNL GraphQL]请求中按商店ID而不是网站过滤愿望清单项目的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69时，此修补程序可用。 修补程序ID为ACSD-66302。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

未正确按商店ID（而非网站）过滤愿望清单项目。

<u>重现步骤</u>：

1. 创建一个简单的产品。
1. 创建附加存储审查。
1. 在Admin中，转到&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Wish List]** > **[!UICONTROL General Options]**，并将&#x200B;**[!UICONTROL Enable Multiple Wish Lists]**&#x200B;设置为`Yes`。
1. 转到&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]**，并将&#x200B;**[!UICONTROL Add Store Code to Urls]**&#x200B;设置为`Yes`。
1. 创建客户帐户。
1. 使用[!DNL GraphQL]请求检索客户身份验证令牌。
1. 以客户身份登录。
1. 选择&#x200B;**[!UICONTROL Default Store View]**&#x200B;并将产品添加到愿望清单。
1. 将存储视图切换到&#x200B;*测试*。
1. 确认产品仍显示在愿望清单中（正确行为）。
1. 执行以下[!DNL GraphQL]查询：

```
{
  customer {
    wishlists {
      id
      name
      items_count
      items_v2 {
        items {
          id
          product {
            uid
            name
            sku
          }
        }
      }
    }
  }
}
```

1. 在默认商店上执行查询 — 产品按预期显示。
1. 在测试存储上执行相同的查询 — 产品未显示。

<u>预期的结果</u>：

应通过[!DNL GraphQL]查询在同个网站内的所有商店视图中显示产品。

<u>实际结果</u>：

切换商店视图时，产品会从愿望清单中消失。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
