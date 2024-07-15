---
title: 使用情况
description: 了解如何使用 [!DNL Quality Patches Tool]。
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
feature: Configuration, Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 0%

---

# 使用情况

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches)提供了由Adobe和Magento Open Source团体开发的各个修补程序。 它允许您应用、还原和查看有关已安装Adobe Commerce版本可用的所有单个修补程序的一般信息。 无论谁开发了修补程序，您都可以将修补程序应用到Adobe Commerce项目。 例如，您可以将社区开发的修补程序应用于Adobe Commerce项目。

观看此[技术视频](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en)，了解如何使用Adobe Commerce的Quality Patches Tool。

>[!INFO]
>
>有关将修补程序应用于Adobe Commerce项目的说明，请参阅[应用单个修补程序](#apply-individual-patches)。 请参阅[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)以查看已发布修补程序的完整列表。

>[!WARNING]
>
>不建议使用[!DNL Quality Patches Tool]来应用大量修补程序，因为它会增加代码的复杂性，并使升级到新版本变得更加困难。

## 安装

>[!INFO]
>
>如果尚未安装，则必须先安装[[!DNL Git]](https://github.com/git-guides/install-git)或[修补程序](https://man7.org/linux/man-pages/man1/patch.1.html)，然后再安装[!DNL Quality Patches Tool]。 将`magento/quality-patches`编辑器包添加到您的`composer.json`文件：

```bash
composer require magento/quality-patches
```

## 查看单个修补程序

要查看适用于您的Adobe Commerce版本的各个修补程序的列表，请执行以下操作：

```bash
./vendor/bin/magento-patches status
```

您会看到类似于以下内容的输出：

| Id | 标题 | 类型 | 状态 | 详细信息 |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | 部署期间将禁用FPC | 可选 | 未应用 | 受影响的组件：<br> - magento/module-page-cache |
| MCLOUD-5650 | 从文件读取后保留部署配置 | 可选 | 未应用 | 受影响的组件：<br> - magento/framework |
| MCLOUD-5684 | 分页不起作用 — product_list_limit=all | 可选 | 未应用 | 受影响的组件： - magento/module-elasticsearch |
| MCLOUD-5837 | 修复负载平衡器问题 | 已弃用 | 已应用 | 建议的替换： MC-1 <br>受影响的组件： - magento/framework |
| BUNDLE-2554 | 设置付款信息错误 | 可选 | 未应用 | 受影响的组件： <br>- amzn/amazon-pay-module |
| MC-1 | 修复问题1 | 可选 | 已应用 | 受影响的组件： <br> - magento/module-cms |
| MC-2 | 修复了问题2 | 可选 | 未应用 | 受影响的组件： <br> - magento/module-cms |
| MC-3 | 修复问题3 | 可选 | 未应用 | 必需的修补程序： <br> - MC-2 <br>受影响的组件： <br>- magento/module-cms |
| MC-3-V2 | 更新了问题3的修复，取代了MC-3修补程序 | 可选 | 不适用 | 受影响的组件： <br>- magento/module-cms |

Adobe Commerce 2.3.5。

状态表包括：

- **类型**：
   - `Optional` — [!DNL Quality Patches Tool]和[Commerce on Cloud Infrastructure Guide > Apply patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)包中的所有修补程序对于Adobe Commerce安装都是可选的。
   - `Deprecated` —Adobe已弃用单个修补程序。 如果您已应用修补程序，我们建议您恢复它。 还原操作还会从状态表中删除修补程序。

- **状态**：
   - `Applied` — 已应用修补程序。
   - `Not applied` — 尚未应用修补程序。
   - `N/A` — 由于存在冲突，无法定义修补程序的状态。

- **详细信息**：
   - `Affected components` — 受影响的模块列表。
   - `Required patches` — 必须应用的修补程序列表才能使指定的修补程序正常工作（依赖关系）。
   - `Recommended replacement` — 建议替换已弃用修补程序的修补程序。

>[!INFO]
>
>升级到Adobe Commerce的新版本后，如果修补程序未包含在新版本中，则必须重新应用修补程序。 请参阅[升级后重新应用修补程序](#re-apply-patches-after-an-upgrade)。

## 应用单个修补程序 {#apply-individual-patches}

>[!WARNING]
>
>在部署到生产环境之前，最佳做法是在暂存或开发环境中测试所有修补程序。 还建议在应用修补程序之前备份数据。 请参阅[备份和回滚文件系统、介质和数据库](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html)。

要应用单个修补程序，请运行以下命令，其中`MAGETWO-XXXX`是在状态表中指定的修补程序ID：

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

还可以通过用空格分隔每个附加的修补程序ID来同时应用多个修补程序：

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

在应用修补程序后必须清除缓存，才能查看Adobe Commerce应用程序中的更改：

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>请考虑将已应用修补程序的列表保留在单独的位置。 升级到新版Adobe Commerce后，您可能需要重新应用其中的一些插件。 请参阅[升级后重新应用修补程序](#re-apply-patches-after-an-upgrade)。

## 还原单个修补程序

>[!WARNING]
>
>在部署到生产环境之前，最佳做法是在暂存或开发环境中测试所有修补程序。 还建议在应用修补程序之前备份数据。 请参阅[备份和回滚文件系统、介质和数据库](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html)。

要还原单个修补程序，请运行以下命令，其中`MAGETWO-XXXX`是状态表中指定的修补程序ID：

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

此外，还可以通过用空格分隔每个附加的修补程序ID来同时还原多个修补程序：

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

还原所有应用的修补程序：

```bash
./vendor/bin/magento-patches revert --all
```

还原修补程序后必须清除缓存，才能查看Adobe Commerce应用程序中的更改：

```bash
./bin/magento cache:clean
```

## 获取更新

Adobe Commerce会定期发布新的单个修补程序。 您必须更新[!DNL Quality Patches Tool]以获取新的单个修补程序：

```bash
composer update magento/quality-patches
```

查看添加的修补程序：

>[!TIP]
>
>新的添加修补程序显示在表的底部。

```bash
./vendor/bin/magento-patches status
```

## 升级后重新应用修补程序 {#re-apply-patches-after-an-upgrade}

升级到新版本的Adobe Commerce时，如果新版本中未包含修补程序，则必须重新应用修补程序。

要重新应用修补程序，请执行以下操作：

1. 更新[!DNL Quality Patches Tool]：

   ```bash
   composer update magento/quality-patches.
   ```

1. 打开[应用单个修补程序](#apply-individual-patches)中建议的先前应用的修补程序列表。

1. 应用修补程序：

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   最佳做法是逐个应用修补程序。

1. 清理缓存：

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >运行`status`命令时，新版本中包含的修补程序将不再显示在可用修补程序表中。

## 记录

[!DNL Quality Patches Tool]在`<Magento_root>/var/log/patch.log`文件中记录所有操作。
