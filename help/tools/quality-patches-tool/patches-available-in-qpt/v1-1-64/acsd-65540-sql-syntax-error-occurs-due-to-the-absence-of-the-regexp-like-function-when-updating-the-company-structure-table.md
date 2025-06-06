---
title: ACSD-65540：由于company_structure更新中缺少REGEXP_LIKE函数而发生SQL错误
description: 应用ACSD-65540修补程序以修复由于公司结构更新中缺少REGEXP_LIKE函数而发生SQL错误的Adobe Commerce问题。
feature: B2B
role: Admin, Developer
source-git-commit: 105bc9bd1b234a7cc582f072f4ede03b82cc81bc
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---


# ACSD-65540：由于`company_structure`更新中缺少`REGEXP_LIKE`函数，因此出现SQL错误

ACSD-65540修补程序修复了由于`company_structure`更新中缺少`REGEXP_LIKE`函数而发生SQL错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64时，此修补程序可用。 修补程序ID为ACSD-65540。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce B2B（所有部署方法） 1.5.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce B2B（所有部署方法） 1.5.2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

由于`company_structure`更新中缺少`REGEXP_LIKE`函数，因此出现SQL语法错误。

<u>重现步骤</u>：

1. 将[!DNL B2B]更新到版本1.5.2。
1. 运行以下命令：

```
bin/magento setup:upgrade
```

<u>预期的结果</u>：

升级成功完成。

<u>实际结果</u>：

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^331(/.+)?$'))
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
