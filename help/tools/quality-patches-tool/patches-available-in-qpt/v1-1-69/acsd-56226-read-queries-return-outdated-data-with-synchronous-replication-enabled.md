---
title: ACSD-56226：在启用“synchronous_replication”的情况下，读取查询返回过时的数据
description: 应用ACSD-56226修补程序以修复Adobe Commerce问题，该问题导致当云上的从属连接启用“synchronous_replication”标志时，读取查询返回过期数据。
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: a45cef14b7b37f1112d2ef82adf29b09d63b8e2b
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---


# ACSD-56226： READ查询返回启用`synchronous_replication`的过期数据

ACSD-56226修补程序修复了在云上为从属连接启用`synchronous_replication`标记时，读取查询返回过期数据的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69时，此修补程序可用。 修补程序ID为ACSD-56226。 请注意，此问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

启用`synchronous_replication`标记后，读取查询会返回过时的数据。 这会导致从属连接被禁用，从而导致数据库过载。

<u>重现步骤</u>：

1. 在云基础架构上的Adobe Commerce上的环境变量中将`MYSQL_USE_SLAVE_CONNECTION`设置为&#x200B;*true*。
1. 将以下配置添加到`.magento.env.yaml`以将`synchronous_replication`设置为&#x200B;*false*：

   ```
   DATABASE_CONFIGURATION:
     _merge: true
     slave_connection:
       default:
         synchronous_replication: false
   ```

1. 重新部署并执行前端操作，例如登录、添加到购物车或下订单。

<u>预期的结果</u>：

当`synchronous_replication`设置为&#x200B;*false*&#x200B;时，从属连接保持启用状态。

<u>实际结果</u>：

当`synchronous_replication`设置为&#x200B;*false*&#x200B;时，从属连接被禁用，从而导致数据库过载。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
