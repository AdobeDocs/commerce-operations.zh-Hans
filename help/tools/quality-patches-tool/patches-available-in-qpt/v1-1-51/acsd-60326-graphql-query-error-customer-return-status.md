---
title: “ACSD-60326：对客户[!UICONTROL Returns]状态的GraphQL查询出错”
description: 应用ACSD-60326修补程序以修复在针对客户[!UICONTROL Returns]状态的GraphQL查询中发生错误的Adobe Commerce问题。
feature: GraphQL, Returns, Customers
role: Admin, Developer
source-git-commit: d7455f78009358bf20b07bd35122c4cab147351a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# ACSD-60326：对客户[!UICONTROL Returns]状态的GraphQL查询出错

ACSD-60326修补程序修复了GraphQL查询客户[!UICONTROL Returns]状态时出现错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51时，此修补程序可用。 修补程序ID为ACSD-60326。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

GraphQL对客户[!UICONTROL Returns]状态的查询出错。

<u>重现步骤</u>：

1. 使用示例数据初始化新实例。
1. 在&#x200B;*[!UICONTROL Admin]*&#x200B;侧边栏上，转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]**，并将&#x200B;**[!UICONTROL Enable RMA on Storefront]**&#x200B;设置为&#x200B;*是*。
1. 转到&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]**&#x200B;并填写地址。
1. 更改客户`roni_cost@example.com`的密码。
1. 登录到管理面板，为客户`roni_cost@example.com`订购以下产品：
   * *WSH12-32-Red*
   * *WSH12-32 — 紫色*
   * *WSH12-32 — 绿色*
1. 为此订单创建一个&#x200B;*[!UICONTROL Invoice]*&#x200B;和&#x200B;*[!UICONTROL Shipment]*。
1. 选择&#x200B;**[!UICONTROL Create Returns]**。
1. 转到&#x200B;**[!UICONTROL Return Items]** > **[!UICONTROL Add Items]**&#x200B;并：
   * 选择&#x200B;*WSH12-32-Red*&#x200B;和&#x200B;*WSH12-32-Purple*
   * 单击&#x200B;**[!UICONTROL Add Selected Products to returns]**：
      * 设置&#x200B;**[!UICONTROL Requested]** = *1*
      * 将&#x200B;**[!UICONTROL Return Reason]**&#x200B;设置为&#x200B;*服务*
      * 将&#x200B;**[!UICONTROL Item Condition]**&#x200B;设置为&#x200B;*已打开*
      * 将&#x200B;**[!UICONTROL Resolution]**&#x200B;设置为&#x200B;*退款*
   * 单击&#x200B;**[!UICONTROL Submit Returns]**。
1. 打开&#x200B;**[!UICONTROL Returns]**&#x200B;并选择左侧的&#x200B;**[!UICONTROL Return Items]**。
   * 为两个产品设置&#x200B;**[!UICONTROL Authorized]** = *1*
   * 将&#x200B;**[!UICONTROL Status]**&#x200B;设置为&#x200B;*WSH12-32-Purple*&#x200B;的&#x200B;*Authorized*
   * 将&#x200B;**[!UICONTROL Status]**&#x200B;设置为&#x200B;*WSH12-32-Red*&#x200B;的&#x200B;*拒绝*
   * 单击&#x200B;**[!UICONTROL Save]**
1. 创建具有相同产品的新订单。
1. 为相同产品创建&#x200B;*[!UICONTROL Invoice]*、*[!UICONTROL Shipment]*&#x200B;和&#x200B;*[!UICONTROL Returns]*。 授权并继续，直到[!UICONTROL Returns]进程结束。
1. 使用以下GraphQL查询生成客户令牌：

   ```GraphQL
    mutation {
     generateCustomerToken(email: "roni_cost@example.com", password: "password") {
       token
      }
   }
   ```

1. 使用收到的令牌进行授权并执行以下查询：

   ```
   {
   customer {
       returns(pageSize: 20, currentPage: 1) {
        total_count
           items {
               uid
               number
               status
               created_at
           }
       }
   }
   }
   ```

<u>预期的结果</u>：

查询未显示任何错误。 第二次返回的状态不是&#x200B;*null*。

<u>实际结果</u>：

查询返回内部服务器错误：

```
    {
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 8,
                    "column": 5
                }
            ],
            "path": [
                "customer",
                "returns",
                "items",
                1,
                "status"
            ]
        }
    ],
    "data": {
        "customer": {
            "returns": {
                "total_count": 2,
                "items": [
                    {
                        "uid": "MQ==",
                        "number": "000000001",
                        "status": "PARTIALLY_AUTHORIZED",
                        "created_at": "2024-07-09 10:35:55"
                    },
                    {
                        "uid": "Mg==",
                        "number": "000000002",
                        "status": null,
                        "created_at": "2024-07-09 10:50:02"
                    }
                ]
            }
        }
    }
    } 
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
