---
title: ACSD-65848：管理员中的类别加载速度非常慢
description: 应用ACSD-65848修补程序以修复使用子选择计算类别中产品总数的Adobe Commerce问题，该问题会延迟类别加载时间。
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8a614c40a1c0134a0528b74cbd434e7ca96c933a
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---


# ACSD-65848：管理员中的类别加载速度非常慢

ACSD-65848修补程序修复了使用子选择计算类别中产品总数的问题，该子选择会延迟类别加载时间。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66时，此修补程序可用。 修补程序ID为ACSD-65848。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

管理员类别查看/编辑页面在加载时会遇到严重延迟。 延迟是由用于计算某个类别中产品总数的方法导致的，此方法依赖于子选择查询。 重构此逻辑以改用连接可提高性能并减少加载时间。

<u>重现步骤</u>：

1. 使用版本2.4.8创建新的Adobe Commerce云实例。
1. 创建2,500个类别和至少10,000个产品：
   1. 将`setup/performance-toolkit`目录复制到`./var`，以便编辑配置文件。
   1. 打开`small.xml`配置文件并将其更新为包括2,500个类别和250,000个产品（以匹配商家的设置）。
   1. 运行以下命令生成夹具：

      ```bash
      bin/magento 
      setup:performance:generate-fixtures var/setup/performance-toolkit/profiles/ce/small.xml
      ```

1. 创建产品和类别后，请确保将所有类别都设置为锚点。 运行此SQL查询：

   ```sql
   UPDATE catalog_category_entity_int 
   SET value = 1 
   WHERE attribute_id = (
   SELECT attribute_id 
   FROM eav_attribute 
   WHERE attribute_code = 'is_anchor'
   );
   ```

1. 在“管理”面板中，创建更深入的类别结构：
   * 将“类别2”移到“类别1”下，使其在树中更深入嵌套。
1. 尝试使用如下所示的URL在“管理员”面板中打开类别页面：
   ```/admin/catalog/category/edit/id/xx/```

<u>预期的结果</u>：

在几秒内首次尝试时会打开每个类别页面。

<u>实际结果</u>：

打开类别页面需要一分钟以上的时间。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
