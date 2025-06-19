---
title: MDVA-34948：网站速度减慢
description: MDVA-34948 Adobe Commerce修补程序修复了网站速度减慢的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1后，即可使用此修补程序。 修补程序ID为MDVA-34948。 请注意，Adobe Commerce版本2.4.1中已修复此问题。
feature: Observability, Configuration
role: Admin
exl-id: 3c2a2d44-7d60-42da-a0a3-785fb61d571e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# MDVA-34948：网站速度减慢


## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云基础架构上的Adobe Commerce 2.4.0-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce内部部署和Adobe Commerce在云基础架构中2.3.6-2.3.6-p1、2.4.0-2.4.0-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

网站运行速度变慢，从而阻碍了运营。

<u>重现步骤</u>：

1. 在MySQL中运行`show processlist`。
1. 检查是否存在多个查询，例如：

```sql
   SELECT GET_LOCK(SYSTEM_CONFIG', '10');
```

<u>预期的结果</u>：

`GET_LOCK`应立即执行。

<u>实际结果</u>：

多个`GET_LOCK`查询最多卡住10秒。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅QPT[&#128279;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)中可用的修补程序部分。
