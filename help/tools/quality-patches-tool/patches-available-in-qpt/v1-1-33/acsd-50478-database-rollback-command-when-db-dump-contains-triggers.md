---
title: ACSD-50478：备份网格和数据库回滚命令中回滚操作的JS问题
description: 应用ACSD-50478补丁程序，修复备份网格中回滚操作的JS问题，以及数据库回滚命令在数据库转储包含触发器和*分隔符* SQL命令时的情况。
exl-id: 2f47fbf6-44fc-487c-91fe-6e2e52fcdb2b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-50478：备份网格和数据库回滚命令中回滚操作的JS问题

ACSD-50478修补程序修复了备份网格中回滚操作的JS问题，以及数据库回滚命令在数据库转储包含触发器和&#x200B;*分隔符* SQL命令的情况下出现的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33时，此修补程序可用。 修补程序ID为ACSD-50478。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.4-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

备份网格中的回滚操作的JS问题，以及数据库回滚命令在数据库转储包含触发器和&#x200B;*分隔符* SQL命令的情况下出现的问题。

<u>重现步骤</u>：

1. 将索引器设置为[!UICONTROL Update on Schedule]模式，以便在数据库中创建触发器。
1. 从命令行启用备份功能：

   `bin/magento config:set system/backup/functionality_enabled 1`

1. 转到&#x200B;**系统** > **工具** > **备份**&#x200B;并生成数据库备份。
1. 打开浏览器控制台；您将看到以下错误：

   ```
   Uncaught SyntaxError: Unexpected token '&' (at (index):606:32)
   
   function eventListener8jtGaqtgG2 () {
   
           return backup.rollback(&#039;db&#039;, &#039;1678391644&#039;);
   ```

1. 尝试从命令行导入DB：

   `bin/magento setup:rollback --db-file="<filename>"`

1. 出现以下错误：

   ```
   Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'delimiter' at line 1, query was: delimiter ;;
   ```

<u>预期的结果</u>：

从管理员和命令行都能成功还原数据库。

<u>实际结果</u>：

您观察到了步骤4和步骤6中提到的错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
