---
title: ACSD-62951：修复了通过REST API发送的[!UICONTROL Credit Memo]电子邮件中缺少的项目和总数
description: 应用ACSD-62951修补程序以修复发送[!UICONTROL Credit Memo]电子邮件时未包含订单项和总数的Adobe Commerce问题。
feature: REST
role: Admin, Developer
exl-id: e0c6d4c1-ecaf-46e7-af2d-05a148970d71
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-62951：修复了通过REST API发送的&#x200B;*[!UICONTROL Credit Memo]*&#x200B;电子邮件中缺少的项目和总数

ACSD-62951修补程序修复了在未包含订单项和总数的情况下发送[!UICONTROL Credit Memo]电子邮件的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57时，此修补程序可用。 修补程序ID为ACSD-62951。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.5-p10

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过REST API *[!UICONTROL Credit Memo]*&#x200B;创建贷项通知单时发送的`POST V1/order/:orderId/refund`电子邮件不包括订单项和总计。

<u>重现步骤</u>：

1. 创建包含任何产品的订单。
1. 装运订单并为其开票。 确保已发送发票电子邮件，其中包含产品详细信息。
1. 使用API客户端生成管理令牌。
1. 使用令牌通过REST API创建贷项通知单。
   1. 终结点： `POST V1/order/:orderId/refund`
   1. 请求有效负载：

      ```
      {  
          "notify": true,  
          "items": [  
              {  
                  "order_item_id": 1,  
                  "qty": 1  
              }  
          ]  
      }  
      ```

<u>预期的结果</u>：

*[!UICONTROL Credit Memo]*&#x200B;电子邮件应包含已退款的项目和总计

<u>实际结果</u>：

*[!UICONTROL Credit Memo]*&#x200B;电子邮件不包含任何项目或总计，导致信息不完整。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
