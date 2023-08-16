---
title: 运行单元测试
description: 运行在Adobe Commerce代码库中定义的单元测试。
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# 运行单元测试

{{file-system-owner}}

此命令运行Commerce 2代码库中定义的一组测试。 您可以运行所有测试或您选择的测试。 每当指定了不受支持的类型时，程序都会终止并列出所有可用类型。 执行后，将显示一个详细报告，其中显示了测试运行和结果。

## 先决条件

在运行此命令之前，请执行以下命令 _必须_ 为真：

- 此 `Magento_Developer` 模块必须启用。 您可以按如下方式启用它：

  ```bash
  bin/magento module:enable [--force] Magento_Developer
  ```

  使用 `--force` 选项。

- 必须设置您的系统才能运行所需的测试。

例如，要运行集成测试，您应该复制 `dev/tests/integration/etc/install-config-mysql.php.dist` 到 `dev/tests/integration/etc/install-config-mysql.php` 并根据您的环境对其进行修改。

## 正在运行测试

命令用法：

```bash
bin/magento dev:tests:run <test>
```

列出可用的测试类型：

```bash
bin/magento dev:tests:run --help
```

示例返回：

```terminal
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

例如，要运行集成测试，请执行以下操作：

```bash
bin/magento dev:tests:run integration
```
