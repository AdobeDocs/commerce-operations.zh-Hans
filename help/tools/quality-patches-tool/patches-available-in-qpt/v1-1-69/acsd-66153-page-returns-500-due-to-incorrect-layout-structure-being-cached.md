---
title: ACSD-66153：由于缓存的布局结构不正确，页面返回500错误
description: 应用ACSD-66153修补程序以修复因缓存的布局结构不正确而导致页面返回500错误代码的Adobe Commerce问题。
feature: Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: 70c7255e369ef366407d539488f0d815eb93f48a
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# ACSD-66153：由于缓存的布局结构不正确，页面返回500错误

ACSD-66153修补程序修复了页面因缓存的布局结构不正确而返回500错误代码的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69时，此修补程序可用。 修补程序ID为ACSD-66153。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p10

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

由于缓存的布局结构不正确，页面返回500错误。

<u>重现步骤</u>：

1. 安装`2.4-develop`。
1. 创建并安装自定义模块：
1.1向`catalog_category_view`布局添加自定义块。
1.1通过自定义块的构造函数将`Magento\Framework\View\Result\Layout`注入自定义块。
1. 创建类别&#x200B;**[!UICONTROL shop]**。
1. 打开&#x200B;**[!UICONTROL two terminal windows]**：
   1. **终端1**：持续清除布局缓存：

      ```
      for i in {1..200}; do
        bin/magento cache:clean layout
      done
      ```

   1. **终端2**：模拟对类别页面的并发请求：

      ```
      for i in {1..200}; do
        curl -s -o /dev/null -w "Request $i: HTTP %{http_code}\n""http://your_magento_base_url/shop.html?req=$i"
      done
      ```

1. 某些请求随机失败，状态代码为500，`var/log/support_report.log`显示以下错误：

   ```
   report.CRITICAL: The element with the "root" ID wasn't found. Verify the ID and try again. [] []
   ```

<u>预期的结果</u>：

所有请求都返回200 OK。

<u>实际结果</u>：

某些请求间歇性地返回500内部服务器错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
