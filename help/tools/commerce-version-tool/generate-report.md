---
title: 生成修补程序状态报告
description: 了解如何使用 [!DNL Commerce Version Tool] 生成JSON或CSV格式的Adobe Commerce修补程序状态报表。
TQID: 'https://experienceleague.adobe.com/-lC-20YMpbTM3tTZjbBO5zD5gb9n7cRah5Ycy8wQoyw'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: cb0391ae368b53a795535f3adb636628a339b963
workflow-type: tm+mt
source-wordcount: 590
ht-degree: 2%

---

# 生成修补程序状态报告

使用[!DNL Commerce Version Tool] ([!DNL CVT])为Adobe Commerce安装生成修补程序状态报告。 此报表可识别已应用、缺少和未知的每月安全修补程序，默认情况下会返回JSON输出。

## 先决条件

在运行[!DNL CVT]之前，请确认：

- Target安装使用支持的Adobe Commerce版本和版本。
- `composer.lock`存在，并且与您要检查的环境匹配。
- PHP和系统`patch`二进制文件可用。
- 您可以从运行该命令的环境中读取项目文件。
- 如果您需要缓存文件和审核日志条目，该工具可以写入`var/patch_metadata/`和`var/log/`。
- 如果授权式修补程序适用于安装，则凭据可通过`COMPOSER_AUTH`或`auth.json`获得。

[!DNL CVT]工具检查`COMPOSER_AUTH`、Adobe Commerce项目`auth.json`和全局编辑器`auth.json`的授权修补凭据。

## 生成报告

从Adobe Commerce项目根目录中，运行：

```bash
php vendor/bin/patch-status
```

要检查其他Adobe Commerce安装，请使用`--root`选项：

```bash
php vendor/bin/patch-status --root=/path/to/commerce
```

## 命令选项

JSON是默认的输出格式。 扫描仪、功能板和合规性报表支持CSV输出。

| 选项 | 描述 |
| --- | --- |
| `--root=PATH` | 指定Adobe Commerce安装根的路径。 缺省值为当前目录。 |
| `--format=json\|csv` | 设置输出格式。 默认值为`json`。 |
| `--no-cache` | 绕过注册表和patch-diff缓存，强制重新进行远程获取，如果远程注册表不可用，退出时将出错。 |
| `--version`, `-V` | 打印工具版本。 |
| `--help`, `-h` | 打印帮助消息。 |

{style="table-layout:auto"}

## 查看JSON和CSV输出

以下示例显示了默认的JSON输出。

```bash
php vendor/bin/patch-status
```

```json
{
  "base_version": "2.4.7-p9",
  "installed_components": {
    "CE": "2.4.7-p9",
    "EE": "2.4.7-p9",
    "B2B": "1.5.2-p5"
  },
  "applied_patches": [
    "247p9-2026-05-001-CE",
    "247p9-2026-05-001-EE"
  ],
  "missing_patches": [
    "247p9-2026-06-001-CE",
    "247p9-2026-06-001-EE"
  ],
  "unknown_patches": [],
  "vulnerability_status": {
    "CVE-2026-12354": { "status": "PROTECTED" },
    "CVE-2026-67890": { "status": "VULNERABLE" }
  },
  "registry_source": "remote",
  "warnings": []
}
```

要生成CSV输出，请使用`--format=csv`选项：

```bash
php vendor/bin/patch-status --format=csv
```

CSV输出在每个CVE中生成一行，适用于电子表格、扫描仪、功能板和合规性工具。

## 了解报告结果

在发出安全状态声明之前，请查看丢失的修补程序和未知的修补程序。

### 修补程序状态值

修补程序状态报告按以下值对修补程序结果进行分组：

| 修补程序状态 | 含义 |
| --- | --- |
| 已应用 | [!DNL CVT]工具在Adobe Commerce代码库中检测每月的安全修补程序。 |
| 缺失 | 该修补程序适用于已安装的Adobe Commerce版本或组件，但[!DNL CVT]工具未检测到它。 |
| 未知 | 该工具无法从可用注册表、修补程序差异或检测结果确认修补程序状态。 |

{style="table-layout:auto"}

### CVE状态值

JSON输出以大写形式报告CVE状态值。

| CVE状态 | 含义 |
| --- | --- |
| `PROTECTED` | 为CVE或组件检测到适用的修补程序。 |
| `VULNERABLE` | CVE或组件缺少适用的修补程序。 |
| `UNKNOWN` | [!DNL CVT]工具无法从可用的注册表和检测数据中确定CVE状态。 |
| `NOT_APPLICABLE` | CVE适用于未安装的组件，例如Adobe Commerce Business-to-business (B2B)、Adobe Commerce Page Builder或Adobe Commerce Inventory。 |

{style="table-layout:auto"}

### 关键输出字段

报告可包括以下信息：

- **基本Adobe Commerce版本** — 从`composer.lock`中检测到已安装的基本版本。
- **注册表源** — 修补程序元数据是来自`remote`、`cache`还是`stale_cache`。
- **已安装的组件** — 从`composer.lock`检测到的Adobe Commerce包区域。
- **已应用修补程序** — 在Adobe Commerce代码库中检测到每月的安全修补程序。
- **缺少修补程序** — 每月的安全修补程序已应用，但未检测到。
- **未知的修补程序** - [!DNL CVT]工具无法分类的修补程序。
- CVE的&#x200B;**漏洞状态** - CVE覆盖范围映射到受保护、易受攻击、不适用或未知状态。
- **警告** — 可能影响报告可靠性或完整性的条件。

## 修补注册表和缓存

修补程序注册表文件包含[!DNL CVT]工具用来确定哪些修补程序适用于已安装版本的修补程序元数据。 该工具在可用时使用新的注册表缓存，在需要时获取远程注册表，如果网络不可用，可以使用失效缓存并发出警告。 仅在需要新的远程获取时才使用`--no-cache`。

## 相关主题

- [简介](intro.md)
- [故障排除](troubleshooting.md)
- [发行说明](release-notes.md)
