---
title: 运行单元测试
description: 运行在Adobe Commerce代码库中定义的单元测试。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# 运行单元测试

{{file-system-owner}}

此命令运行在Commerce 2代码库中定义的一组测试。 您可以运行所有测试或选择的测试。 只要指定了不支持的类型，程序就会终止并列出所有可用类型。 执行后，将显示一个详细报告，其中显示了测试运行和结果。

## 先决条件

在运行此命令之前，请执行以下操作 _必须_ 为true:

- 的 `Magento_Developer` 必须启用模块。 您可以按如下方式启用它：

   ```bash
   bin/magento module:enable [--force] Magento_Developer
   ```

   使用 `--force` 选项。

- 必须将系统设置为运行所需的测试。

例如，要运行集成测试，您应复制 `dev/tests/integration/etc/install-config-mysql.php.dist` to `dev/tests/integration/etc/install-config-mysql.php` 并对其进行修改以适合您的环境。

## 运行测试

命令用法：

```bash
bin/magento dev:tests:run <test>
```

要列出可用的测试类型，请执行以下操作：

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
