---
title: ACSD-63139：当产品属性包含数千个选项值时，产品导出失败
description: 应用ACSD-63139修补程序以修复在产品属性包含数千个选项值时产品导出失败的Adobe Commerce问题。
feature: Data Import/Export
role: Admin, Developer
exl-id: 785907dc-aa3f-49e2-bd52-c3afe4393456
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63139：当产品属性包含数千个选项值时，产品导出失败

ACSD-63139修补程序修复了当产品属性包含数千个选项值时产品导出失败的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64时，此修补程序可用。 修补程序ID为ACSD-63139。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p10

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当产品属性包含数千个选项值时，产品导出会失败。

<u>重现步骤</u>：

1. 在B2B模块中安装Adobe Commerce 。
1. 使用以下内容导入大型数据库转储：
    — 约7,000种产品
    — 约450个产品属性
    — 某些属性的选项超过100个
1. 运行以下命令以安装cron（如果尚未安装）：

   ```
   bin/magento cron:install
   ```

1. 按照[!DNL RabbitMQ]先决条件[[!DNL RabbitMQ] 中的说明配置](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/rabbitmq)。
1. 打开`php.ini`文件，将内存限制设置为4G，然后重新启动PHP服务。
1. 在管理面板中，转到&#x200B;**[!UICONTROL System]** > *[!UICONTROL Data Transfer]* > **[!UICONTROL Export]**。
1. 在&#x200B;*[!UICONTROL Export Settings]*&#x200B;部分中，将&#x200B;**[!UICONTROL Entity Type]**&#x200B;设置为&#x200B;*产品*，滚动到底部并单击&#x200B;**[!UICONTROL Continue]**。
1. 运行以下命令以启动导出处理器：

   ```
   bin/magento queue:consumers:start exportProcessor --max-messages=1
   ```

<u>预期的结果</u>：

产品导出应成功完成。

<u>实际结果</u>：

产品导出过程失败并返回以下严重错误：

```
Fatal error: Allowed memory size of 4294967296 bytes exhausted (tried to allocate 12288 bytes) in /var/www/html/app/code/Magento/Catalog/Model/ResourceModel/Product/Collection.php on line 597
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
