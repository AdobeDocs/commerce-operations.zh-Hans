---
title: ACSD-64532：设置为*false*的环境变量被视为字符串*false*，而不是布尔值*FALSE*
description: 应用ACSD-64532修补程序以修复Adobe Commerce问题，该问题导致将设置为*false*的“ENV”变量视为字符串*false*而不是“BOOLEAN”*FALSE*。
feature: Variables
role: Admin, Developer
exl-id: 7940df1f-d527-4b57-bde7-7a0216b12436
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-64532：设置为“false”的环境变量被视为字符串“false”，而不是布尔值FALSE

ACSD-64532修补程序修复了将设置为`ENV`false *的*&#x200B;变量视为字符串&#x200B;*false*&#x200B;而不是`BOOLEAN` *FALSE*&#x200B;的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62时，此修补程序可用。 修补程序ID为ACSD-64532。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
Adobe Commerce（所有部署方法） 2.4.6-p8

**与Adobe Commerce版本兼容：**
Adobe Commerce（所有部署方法） 2.4.6-p2 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

设置为`ENV`false *的*&#x200B;变量被视为字符串&#x200B;*false*，而不是`BOOLEAN` *FALSE*。

<u>重现步骤</u>：
1. 将值为`env:MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK`false *的*&#x200B;添加到云基础架构上Adobe Commerce的环境变量中。
1. 等待重新部署。
1. 运行脚本检查值：

   ```php
   <?php
   require '../app/bootstrap.php';
   $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
   $objectManager = $bootstrap->getObjectManager();
   $deploymentConfig = $objectManager->get('Magento\Framework\App\DeploymentConfig');
   $useAppLock = $deploymentConfig->get('indexer/use_application_lock');
   
   var_dump($useAppLock);
   
   $configParsedValue = $deploymentConfig->get('indexer/use_application_lock') ?: false;
   
   var_dump($configParsedValue); 
   ```

<u>预期的结果</u>：
`$configParsedValue` （方法`isUseApplicationLock()`的结果）必须返回负值才能在方法`\Magento\Indexer\Model\Mview\View\State::getStatus()`内正确解释。

<u>实际结果</u>：
`$configParsedValue`的值为&#x200B;*`string(5) false`*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：
* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
