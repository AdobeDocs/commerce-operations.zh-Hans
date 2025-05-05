---
title: ACSD-63244：解决管理面板JavaScript问题，包括 [!DNL Google Maps] 渲染和控制台错误
description: ACSD-63244修补程序修复了管理面板中的多个JavaScript问题，包括 [!DNL Google Maps] 渲染问题以及反复出现的“Uncated TypeError”问题。在浏览器控制台中，_each不是函数错误。
feature: Admin Workspace
role: Admin, Developer
exl-id: 1985c845-219e-4af4-8f70-62dd57722494
source-git-commit: 6b623811440238deee7a7fe859d887830f89782c
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# ACSD-63244：解决管理面板JavaScript问题，包括[!DNL Google Maps]渲染和控制台错误

ACSD-63244修补程序修复了管理面板中的多个JavaScript问题，包括浏览器控制台中的[!DNL Google Maps]渲染问题和重复出现的`Uncaught TypeError: this._each is not a function`错误。 此修补程序在[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56中可用。修补程序ID为ACSD-63244。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.4、2.4.4-p9、2.4.6-p7、2.4.7

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

* 浏览器控制台中出现`Uncaught TypeError: this._each is not a function`错误，管理用户界面功能中断。
* JavaScript错误导致[!DNL Google Maps]无法正确呈现。

<u>重现步骤</u>：

1. 加载Adobe Commerce管理UI。
1. 打开浏览器控制台并执行以下脚本：

   ```
   Object.values([] || {}).forEach((function(e) {  
   e("dd")  
   }));  
   ```

<u>预期的结果</u>：

默认JS库中可用的JavaScript函数可正确执行且无错误。

<u>实际结果</u>：

浏览器控制台中会显示JavaScript错误：

```
Uncaught TypeError: this._each is not a function
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
