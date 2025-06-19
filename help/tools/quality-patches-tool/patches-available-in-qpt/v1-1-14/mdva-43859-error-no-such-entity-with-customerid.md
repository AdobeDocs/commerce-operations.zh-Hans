---
title: MDVA-43859：删除的客户登录时，出现“没有记录具有customerId =”的此类实体”错误
description: MDVA-43859修补程序修复了以下问题：当删除的客户尝试登录时，不会记录具有customerId=*的此类实体。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14后，即可使用此修补程序。 修补程序ID为MDVA-43859。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Variables
role: Admin
exl-id: b8451b08-978a-44a2-8664-4369e832423b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# MDVA-43859：删除的客户登录时，出现“没有记录具有customerId =”的此类实体”错误

MDVA-43859修补程序修复了以下问题：当删除的客户尝试登录时，不会记录错误&#x200B;*customerId =*&#x200B;的此类实体。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14时，此修补程序可用。 修补程序ID为MDVA-43859。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

错误&#x200B;*当已删除的客户尝试登录时，不会记录customerId =*&#x200B;的此类实体。

<u>重现步骤</u>：

1. 从前端创建客户帐户。
1. 注销并登录到在步骤1中创建的客户帐户。
1. 在其他浏览器中加载后端，然后转到客户网格。
1. 删除在第一步中创建的客户。
1. 切换回第一个浏览器并尝试注销。

<u>预期的结果</u>：

客户将被重定向到登录页面，并且不会出现任何错误。

<u>实际结果</u>：

客户收到以下错误： *没有具有customerId =*&#x200B;的此类实体。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
