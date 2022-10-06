---
title: 使用情况
description: 了解如何使用 [!DNL Quality Patches Tool].
source-git-commit: e35469adb1b3278cf787416e1bc829fae9979efc
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 0%

---

# 使用情况

的 [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) 提供由Adobe和Magento Open Source社区开发的各个修补程序。 它允许您应用、还原和查看有关可用于已安装版本的Adobe Commerce或Magento Open Source的所有修补程序的常规信息。 无论谁开发了修补程序，您都可以将修补程序应用于Adobe Commerce和Magento Open Source项目。 例如，您可以将社区开发的修补程序应用到Adobe Commerce项目。


看这个 [技术视频](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en) 并了解如何使用质量修补程序工具进行Adobe Commerce和Magento Open Source。

>[!INFO]
>
>请参阅 [应用单个修补程序](#apply-individual-patches) 有关将修补程序应用到Adobe Commerce或Magento Open Source项目的说明。 请参阅 [可用的修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 查看已发布修补程序的完整列表。

>[!WARNING]
>
>不建议使用 [!DNL Quality Patches Tool] 应用大量修补程序，因为这会增加代码的复杂性，并使升级到新版本变得更加困难。

## 安装

>[!INFO]
>
>如果尚未安装，则必须安装 [[!DNL Git]](https://github.com/git-guides/install-git) 或 [修补程序](https://man7.org/linux/man-pages/man1/patch.1.html) 安装之前 [!DNL Quality Patches Tool]. 添加 `magento/quality-patches` 将编辑器包添加到 `composer.json` 文件：

```bash
composer require magento/quality-patches
```

## 查看单个修补程序

要查看可用于您的Adobe Commerce或Magento Open Source版本的各个修补程序列表，请执行以下操作：

```bash
./vendor/bin/magento-patches status
```

您将看到与以下内容类似的输出：

| Id | 标题 | 类型 | 状态 | 详细信息 |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | FPC在部署期间被禁用 | 可选 | 未应用 | 受影响的组件：<br> - magento/module-page-cache |
| MCLOUD-5650 | 从文件读取后保留部署配置 | 可选 | 未应用 | 受影响的组件：<br> - magento/framework |
| MCLOUD-5684 | 分页不起作用 — product_list_limit=all | 可选 | 未应用 | 受影响的组件：- magento/module-elasticsearch |
| MCLOUD-5837 | 修复了负载平衡器问题 | 已弃用 | 已应用 | 建议替换：MC-1 <br> 受影响的组件：- magento/framework |
| BUNDLE-2554 | 设置付款信息错误 | 可选 | 未应用 | 受影响的组件： <br>- amzn/amazon-pay-module |
| MC-1 | 修复了问题1 | 可选 | 已应用 | 受影响的组件： <br> - magento/module-cms |
| MC-2 | 修复了问题2 | 可选 | 未应用 | 受影响的组件： <br> - magento/module-cms |
| MC-3 | 修复了问题3 | 可选 | 未应用 | 所需的修补程序：<br> - MC-2 <br>受影响的组件： <br>- magento/module-cms |
| MC-3-V2 | 更新了问题3的修复，取代了MC-3修补程序 | 可选 | 不适用 | 受影响的组件：  <br>- magento/module-cms |

Adobe Commerce 2.3.5。

状态表包括：

- **类型**:
   - `Optional`  — 所有来自 [!DNL Quality Patches Tool] 和 [云修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 包对于Adobe Commerce和Magento Open Source安装是可选的。
   - `Deprecated` —Adobe已弃用单个修补程序。 如果已应用修补程序，我们建议您还原该修补程序。 还原操作还会从状态表中删除修补程序。

- **状态**:
   - `Applied`  — 已应用修补程序。
   - `Not applied`  — 尚未应用修补程序。
   - `N/A`  — 由于冲突，无法定义修补程序的状态。

- **详细信息**:
   - `Affected components`  — 受影响模块的列表。
   - `Required patches`  — 必须应用的修补程序列表，才能使指示的修补程序正常工作（依赖项）。
   - `Recommended replacement`  — 建议替换已弃用修补程序的修补程序。

>[!INFO]
>
>升级到新版Adobe Commerce或Magento Open Source后，如果新版本中未包含修补程序，则必须重新应用修补程序。 请参阅 [升级后重新应用修补程序](#re-apply-patches-after-an-upgrade).

## 应用单个修补程序 {#apply-individual-patches}

>[!WARNING]
>
>最佳做法是在部署到生产之前，在暂存或开发环境中测试所有修补程序。 此外，还建议在应用修补程序之前先备份数据。 请参阅 [备份和回滚文件系统](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

要应用单个修补程序，请运行以下命令，其中 `MAGETWO-XXXX` 是状态表中指定的修补程序ID:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

您还可以通过将每个附加的修补程序ID与空格分隔开来同时应用多个修补程序：

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

在应用修补程序后，必须清除缓存，才能查看Adobe Commerce应用程序中的更改：

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>请考虑将已应用修补程序的列表保留在单独的位置。 在升级到新版Adobe Commerce或Magento Open Source后，您可能需要重新应用其中一些组件。 请参阅 [升级后重新应用修补程序](#re-apply-patches-after-an-upgrade).

## 还原单个修补程序

>[!WARNING]
>
>最佳做法是在部署到生产之前，在暂存或开发环境中测试所有修补程序。 此外，还建议在应用修补程序之前先备份数据。 请参阅 [备份和回滚文件系统](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

要还原单个修补程序，请运行以下命令，其中 `MAGETWO-XXXX` 是状态表中指定的修补程序ID:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

此外，您还可以通过将每个额外的修补程序ID分隔为一个空格来同时还原多个修补程序：

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

要还原所有已应用的修补程序，请执行以下操作：

```bash
./vendor/bin/magento-patches revert --all
```

必须在还原修补程序后清除缓存，才能查看Adobe Commerce应用程序中的更改：

```bash
./bin/magento cache:clean
```

## 获取更新

Adobe Commerce会定期发布新的单个修补程序。 您必须更新 [!DNL Quality Patches Tool] 要获取新的单个修补程序，请执行以下操作：

```bash
composer update magento/quality-patches
```

查看添加的修补程序：

>[!TIP]
>
>新的添加修补程序将显示在表格底部。

```bash
./vendor/bin/magento-patches status
```

## 升级后重新应用修补程序 {#re-apply-patches-after-an-upgrade}

升级到新版Adobe Commerce或Magento Open Source时，如果新版本中未包含修补程序，则必须重新应用修补程序。

要重新应用修补程序，请执行以下操作：

1. 更新 [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. 打开以前应用的修补程序列表，建议在 [应用单个修补程序](#apply-individual-patches).

1. 应用修补程序：

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   最佳做法是一次应用一个修补程序。

1. 清除缓存：

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >运行 `status` 命令，新版本中包含的修补程序将不再显示在可用修补程序表中。

## 记录

的 [!DNL Quality Patches Tool] 记录 `<Magento_root>/var/log/patch.log` 文件。
