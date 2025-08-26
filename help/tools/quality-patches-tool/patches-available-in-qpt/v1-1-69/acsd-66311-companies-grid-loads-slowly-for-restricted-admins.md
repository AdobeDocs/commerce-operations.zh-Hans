---
title: ACSD-66311：受限制的管理用户的公司网格加载缓慢
description: 应用ACSD-66311修补程序以修复Adobe Commerce问题，该问题导致对访问受限网站的管理员用户使用公司网格加载缓慢。
role: Admin, Developer
feature: B2B
type: Troubleshooting
source-git-commit: 841e660136354800dd9758d8c10e86c966be3a1e
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 2%

---


# ACSD-66311：受限制的管理用户的公司网格加载缓慢

ACSD-66311修补程序修复了网站访问受限的管理员用户公司网格加载缓慢的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69时，此修补程序可用。 修补程序ID为ACSD-66311。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7-p4 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对于网站访问受限的管理员用户，公司网格加载缓慢。

<u>重现步骤</u>：

1. 使用&#x200B;**[!UICONTROL B2B features]**&#x200B;安装Adobe Commerce。
1. 创建2个包含商店/视图的额外网站（除主网站之外）：
   * 主网站（在安装期间创建）
   * 网址2 → Store 2 → StoreView 2
   * 网址3 → Store 3 → StoreView 3
1. 创建&#x200B;**[!UICONTROL Admins in Scope]**&#x200B;用户角色：
   * 范围：只有两个商店： *主网站* + *网站3/商店3*。
   * 资源：仅&#x200B;*仪表板* + *公司*。
1. 创建角色为&#x200B;**[!UICONTROL Admins in Scope]**&#x200B;的管理员用户，例如&#x200B;**adminscope**。
1. 生成特定的分布式客户和公司数据：
   1. **分配给网站的客户**

      | 网站ID | 客户数量 |
      |------------|---------------------|
      | 1 | 600,000 |
      | 2 | 1,500 |
      | 3 | 500 |


   1. 运行以下查询以验证分配：

      ```
           SELECT website_id, COUNT(*) 
           FROM customer_entity 
           GROUP BY website_id; 
      ```

   1. **分配给公司的客户**

      | 客户数量 | 公司数量 |
      |---------------------|---------------------|
      | 1 | 4,500 |
      | 2 | ~1,000 |
      | ~595k | 1 |

   1. 运行以下查询以验证分配：

      ```
            SELECT customer_count, COUNT(*) AS number_of_companies
            FROM (
      
            选择company_id，COUNT(customer_id) AS customer_count
            FROM company_advanced_customer_entity
            按company_id分组
)作为子查询
GROUP BY customer_count
ORDER BY客户计数；
```

1. 重新索引所有数据以生成&#x200B;**customer_grid_flat**&#x200B;中的条目。
1. 以&#x200B;**adminscope**&#x200B;身份登录。
1. 转到&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL Companies]**。

<u>预期的结果</u>：

页面加载不足1秒。

<u>实际结果</u>：

加载页面需要14分钟以上的时间。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
