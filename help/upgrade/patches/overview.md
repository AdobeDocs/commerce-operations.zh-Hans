---
title: 修补程序的工作方式
description: 了解Adobe Commerce的各种类型的修补程序及其工作方式。
exl-id: d7072ed4-7d51-41fe-881a-aae3b2000b55
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# 修补程序的工作方式

>[!WARNING]
>
>我们强烈建议先在暂存或开发环境中测试所有修补程序，然后再部署到生产环境。 我们还强烈建议在应用修补程序之前备份您的数据。 请参阅[备份和恢复文件系统](../../installation/tutorials/backup.md)。

修补程序（或差异）文件是包含以下内容的文本文件：

- 要更改的文件。
- 要开始更改的行号以及要更改的行数。
- 要交换的新代码。

运行修补程序程序时，会读入此文件，并对文件执行指定的更改。

有三种类型的修补程序：

- **修补程序** - Adobe在[安全中心](https://magento.com/security/patches)发布的修补程序。
- **单独的修补程序** - Adobe Commerce支持部门按单个列表创建和分发的修补程序。
- **自定义修补程序** — 可从Git提交创建的非官方修补程序。

## 修补程序

修补程序是包含影响许多商家的高影响安全性或质量修补程序的修补程序。 这些修复将应用于适用的次要版本的下一个补丁发行版本。 Adobe会根据需要发布修补程序。

您可以在[安全中心](https://magento.com/security/patches)中找到修补程序。 根据您的版本和安装类型，按照页面上的说明下载修补程序文件。 使用[命令行](../patches/apply.md#)或[编辑器](../patches/apply.md)应用热修复补丁程序。

>[!NOTE]
>
>热修复程序可能包含向后不兼容的更改。

## 单个修补程序

单个修补程序包含针对特定问题的低影响质量修复。 这些修复适用于最新支持的次要版本（例如2.4.x），但在先前支持的次要版本（例如2.3.x）中可能缺失。 Adobe会根据需要发布各个修补程序。

使用[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}应用单个修补程序。

>[!NOTE]
>
>单个修补程序不包含向后不兼容的更改。

## 自定义修补程序

有时，Adobe工程团队需要一段时间才能在Adobe Commerce编辑器版本中包含对GitHub所做的错误修复。 同时，您可以从GitHub创建修补程序，并使用[`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/)插件将其应用于基于编辑器的安装。

使用[命令行](apply.md#command-line)或[编辑器](apply.md#composer)应用自定义修补程序。

可通过多种方式创建自定义修补程序文件。 以下示例重点介绍如何通过已知的git提交创建修补程序。

要创建自定义修补程序，请执行以下操作：

1. 在本地项目中创建一个`patches/composer`目录。
1. 确定要用于修补程序的GitHub提交或拉取请求。 此示例使用链接到GitHub问题[`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede)的[#64741&rbrace;承诺。](https://github.com/magento/magento2/issues/6474)
1. 将`.patch`或`.diff`扩展附加到提交URL。 对较小的文件大小使用`.diff`。 例如：[https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. 将页面另存为`patches/composer`目录中的文件。 例如，`github-issue-6474.diff`。
1. 编辑文件并从所有路径中删除`app/code/<VENDOR>/<PACKAGE>`，使其相对于`vendor/<VENDOR>/<PACKAGE>`目录。

   >[!NOTE]
   >
   >自动删除尾随空格或添加新行的文本编辑器可能会破坏修补程序。 使用简单的文本编辑器进行这些更改。

以下示例显示删除了`app/code/Magento/Payment`的所有实例后先前提到的DIFF文件：

```diff
diff --git a/view/frontend/web/js/view/payment/iframe.js b/view/frontend/web/js/view/payment/iframe.js
index c8a6fef58d31..7d01c195791e 100644
--- a/view/frontend/web/js/view/payment/iframe.js
+++ b/view/frontend/web/js/view/payment/iframe.js
@@ -154,6 +154,7 @@ define(
              */
             clearTimeout: function () {
                 clearTimeout(this.timeoutId);
+                this.fail();

                 return this;
             },
```

## 应用修补程序

可以使用以下任一方法应用修补程序：

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [命令行](/help/upgrade/patches/apply.md#command-line)
- [Composer](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>要将修补程序应用到Adobe Commerce on Cloud Infrastructure项目，请参阅[Commerce on Cloud指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)中的&#x200B;_应用修补程序_。
