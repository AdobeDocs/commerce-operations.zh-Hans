---
title: '[!DNL Commerce Version Tool]疑难解答'
description: 了解如何对 [!DNL Commerce Version Tool] Composer检测、内部模拟运行检查、注册表缓存、JSON输出和审核日志问题进行故障诊断。
TQID: 'https://experienceleague.adobe.com/JwRSy7pfM89WoifYUzTVPhR-WrDIvj2A2B8SaEnmyWM'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 1222
ht-degree: 0%

---

# [!DNL Commerce Version Tool]疑难解答

使用此页面可解决以下常见的[!DNL Commerce Version Tool] ([!DNL CVT])问题：编辑器检测、注册表加载、内部模拟运行修补程序检测、输出生成和审核日志记录。

## 快速疑难解答步骤

如果[!DNL CVT]工具未返回预期的修补程序状态报告：

- 确认Target安装使用的是受支持的Adobe Commerce版本和版本。
- 确认`composer.lock`存在并且与您要检查的环境匹配。
- 确认PHP和系统`patch`二进制文件可用。
- 确认[!DNL CVT]可以读取修补程序注册表文件。
- 在输出中查看`warnings`、`missing_patches`和`unknown_patches`。
- 如果日志文件已创建，请检查`var/log/patch_status.log`以了解运行中的审核摘要。

>[!TIP]
>
> 当您需要了解为何无法对修补程序进行分类时，日志文件非常有用。 对于每个未知修补程序，日志将记录正向和反向练习的原始输出，包括任何错误或隐藏式故障。
>
> 如果在获取注册表或修补程序文件时遇到问题，请检查报告中的警告字段。 这些详细信息不会显示在日志中。

## 常见问题和解决方案

### 无法检测到基本版本

如果[!DNL CVT]工具找不到Adobe Commerce基本版本，请检查以下条件：

**检查：**

- `composer.lock`缺失。
- `patch-status`命令在Adobe Commerce项目根目录之外运行（或`--root`指向错误的路径），因此未找到`composer.lock`。
- `composer.lock`存在但不是有效的JSON，或无法读取。
- `composer.lock`不包含任何可识别的基本包(`magento/product-enterprise-edition`、`magento/product-community-edition`、`magento/magento2-base`)。

**警告消息：**

如果`composer.lock`存在但无法读取、无法解析或不包含可识别的基本包，则该工具会在警告输出字段中发送以下字符串之一：

```shell-session
No recognized Commerce base package found in composer.lock
composer.lock exists but could not be read
composer.lock could not be parsed as JSON
```

>[!NOTE]
>
> 如果完全缺少`composer.lock`，该工具将报告`base_version: "unknown"`，其中&#x200B;**没有任何警告消息**。 始终直接检查输出中的`base_version`。 不要依靠警告来查找此问题。

上述任何情况均表明刀具无法检测基本版本。 工具退出，代码为`1`，并且不执行修补程序检测。

**操作：**

- 从[!DNL Adobe Commerce]项目根目录运行`patch-status`命令，或传递正确的`--root`。
- 确认`composer.lock`存在、当前和有效的JSON。
- 确认安装使用的是支持的Adobe Commerce版本，因此`composer.lock`包含可识别的基本包之一。

### 没有修补程序应用于已安装的版本

如果[!DNL CVT]报告有效的`base_version`，但`applied_patches`、`missing_patches`和`unknown_patches`为空，则当前修补程序注册表不包含所安装的版本。

**检查：**

- 修补程序注册表文件中未表示已安装的[!DNL Adobe Commerce]版本。 例如，比注册表的最新条目更新的版本。

**警告消息：**

```shell-session
No patches found in registry for installed component versions (CE=2.4.7-p9)
```

此警告与“无法检测到基本版本”不同。 `base_version`正确，工具退出`0`，注册表中没有任何可比较的内容。

**操作：**

- 确认输出中的`base_version`符合您的预期。
- 确认`registry_source`是`remote`或最近的`cache`，而不是旧的。
- 如果该版本应包含在内，请联系Adobe Commerce支持。

### 无法获取修补程序注册表

如果[!DNL CVT]工具无法获取最新的修补程序注册表文件，请检查网络和缓存设置：

**检查：**

- 网络不可用。
- Adobe修补程序端点请求超时。
- 已使用`--no-cache`，无法访问远程注册表。
- `PATCH_REGISTRY_URL`指向不可用的注册表或不是有效的HTTPS URL。
- 如果[!DNL CVT]工具无法获取最新的修补程序注册表文件，请检查网络和缓存设置：

>[!NOTE]
>
>如果注册表文件丢失或过期，该工具将从远程主机下载最新的注册表。

**警告消息：**

此工具在此方案的警告输出字段中发送以下字符串：

```shell-session
Remote registry fetch failed (HTTP 403). Check PATCH_REGISTRY_URL (if set) and network connectivity.
Remote registry response was not valid JSON; ignoring.
Could not load remote registry. Using cached registry (3 hours old). CVE coverage may be incomplete.
Patch registry could not be loaded.
Could not fetch remote registry and --no-cache was set; aborting.
```

过时的缓存消息包括以小时为单位的实际时间，例如`(3 hours old)`。

`patch registry could not be loaded`和`could not fetch remote registry`警告指示工具退出时未运行修补程序检测。

**操作：**

- 网络连接可用时重新运行`patch-status`命令。
- 如果扫描可接受过时缓存警告，则允许[!DNL CVT]工具使用缓存的注册表。
- 除非需要新的远程获取，否则请删除`--no-cache`。
- 确认如果要重用注册表缓存，则[!DNL CVT]工具可以写入`var/patch_metadata/`。

### 无法获取或验证修补程序差异

如果[!DNL CVT]工具无法测试一个或多个适用的修补程序，请检查patch-diff访问权限：

**检查：**

- 无法从Adobe修补程序端点下载修补程序差异。
- 缺少经过身份验证的修补程序下载所需的凭据或凭据无效。
- `PATCH_DIFF_BASE_URL`指向不可用的patch-diff源或不是有效的HTTPS URL。
- 缓存的修补程序差异缺失或无法读取。
- 对于下载的修补程序差异，SHA-256验证失败。
- [!DNL CVT]工具无法写入`var/patch_metadata/.patch_diffs/`。

**警告消息：**

此工具在此方案的警告输出字段中发送以下字符串：

```shell-session
Patch 247p9-2026-05-001-EE requires authentication. Set credentials via COMPOSER_AUTH or auth.json.
Could not fetch patch 247p9-2026-05-001-EE (HTTP 401). Check credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch 247p9-2026-05-001-EE (HTTP 404).
Could not fetch or verify patch 247p9-2026-05-001-EE. Check network connectivity and credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch file for 247p9-2026-05-001-EE.
SHA-256 verification failed for patch 247p9-2026-05-001-EE; discarding download.
```

每封邮件中的修补程序ID是实际的注册表项ID，例如`247p9-2026-05-001-EE`。 `SHA-256 verification failed`表示新下载的修补程序文件与其预期的校验和不匹配。 该工具放弃它而不进行缓存，并对此运行的修补程序`unknown`进行分类。 检测到损坏的&#x200B;*local*&#x200B;缓存条目，并在同一运行中无警告地重新获取该条目。 在这两种情况下，均无需手动清理缓存。

**操作：**

- 请确认网络连接并重试该命令。
- 确认已配置经过身份验证的修补程序下载所需的凭据。
- 确认[!DNL CVT]工具可以写入`var/patch_metadata/.patch_diffs/`。
- 如果修补程序仍被分类为未知，则保留警告和输出详细信息。

### 报告缺失或未知的修补程序

如果报告包含意外的`missing_patches`或`unknown_patches`值，请查看安装和输出详细信息：

**检查：**

- 每月应用修补程序时未按顺序进行。
- 缺少特定于组件的修补程序，例如Adobe Commerce企业到企业(B2B)或Adobe Commerce Page Builder。
- `composer.lock`报告需要修补程序的已安装组件版本。
- 补丁程序差异不可用，或检测结果无结论。

**警告消息：**

此工具在此方案的警告输出字段中发送以下字符串：

```shell-session
No file_name or sha256 for 247p9-2026-05-001-EE
Registry entry '247p9-2026-05-001-EE' requires unknown patch '247p9-2026-04-001-EE'; skipping.
descendant diffs unavailable for 247p9-2026-06-001-EE; dry-run for 247p9-2026-05-001-EE may be inaccurate
Failed to reverse-apply 247p9-2026-06-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
Failed to forward-apply prerequisite 247p9-2026-04-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
```

当您在警告中遇到`may be inaccurate`时，模拟测试仍会运行，但置信度会降低。 修补程序仍可以在`applied_patches`或`missing_patches`中分类，不一定是`unknown_patches`。

特别是对于未知的修补程序，`var/log/patch_status.log`记录原始修补程序试运行输出（正向和反向），指示哪些文件和块不匹配。

如果您遇到“未找到修补程序”警告，请参阅[对于已安装的版本](#no-patches-apply-to-the-installed-version)不应用任何修补程序，以获得指导。

**操作：**

- 查看`applied_patches`、`missing_patches`和`unknown_patches`字段。
- 确认缺少的修补程序是否适用于已安装的版本和组件。
- 将结果与相关安全修补程序发行说明进行比较。
- 确认检查的代码库与要报告的已部署环境相匹配。
- 如果未知状态阻止修正计划，请联系Adobe Commerce支持。

### 未生成输出

如果[!DNL CVT]工具已完成，但缺少预期的JSON或CSV输出，请检查命令语法和终端输出：

**操作：**

- 如果不需要输出CSV，则使用默认的JSON输出。
- 使用`--format=csv`生成CSV输出。
- 确认运行[!DNL CVT]工具的Shell、脚本或扫描仪未重定向或丢弃命令输出。
- 检查`stderr`以查看`patch-status:`错误消息。
- 如果将输出重定向到文件，例如`patch-status > report.json`，请确认外壳程序具有对该目标的写入权限。 该工具仅写入`stdout`。
- 确认[!DNL CVT]工具可以写入`var/log/patch_status.log`。
- 重新运行命令并捕获终端输出以进行故障排除。

## 获取帮助

在联系Adobe Commerce支持时，仅提供调查问题所需的详细信息。

包括：

- Adobe Commerce版本和版本
- [!DNL CVT]工具版本
- 来自[!DNL CVT]工具输出的注册表源
- 相关的`applied_patches`、`missing_patches`和`unknown_patches`值
- 相关警告
- 错误消息或命令输出

在共享的日志或附件中不包括密钥、凭据、私钥或不相关的客户数据。

## 相关主题

- [简介](intro.md)
- [生成修补程序状态报告](generate-report.md)
- [发行说明](release-notes.md)
