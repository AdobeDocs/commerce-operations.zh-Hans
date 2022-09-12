---
title: 常用命令
description: 查看常见Commerce CLI命令和用法的采样。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---


# 常用命令

下面总结了一些可用的命令。

**显示命令的完整列表**:

```bash
bin/magento list
```

帮助命令示例：

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

命令仅以摘要形式显示；有关命令的详细信息，请单击“命令”列中的链接。

| 命令 | 描述 |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | 管理缓存 |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | 管理索引器 |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | 运行Commerce Cron作业 |
| [`magento setup:di:compile`](../cli/code-compiler.md) | 汇编所有不存在的代理和工厂；以及预编译一个商店和网站的类定义、继承信息和插件定义。 |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | 模块依赖关系、循环依赖关系和商务框架依赖关系。 |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | 创建翻译字典或翻译包 |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | 部署静态视图文件 |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | 从LESS创建CSS |
| [`magento dev:tests:run`](../cli/unit-tests.md) | 运行自动测试 |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | 更新布局XML文件以匹配新的可扩展样式表语言转换(XSLT)样式表 |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | 生成要用于性能测试的数据。 |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | 安装商务应用程序后，安装可选的示例数据。<br><br>有关示例数据的更多详细信息，请参阅 [可选示例数据](../../installation/sample-data/overview.md). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | 管理后端配置 |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | 创建/编辑/解锁管理员用户。 |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug/) | 启用/禁用开发人员模板提示。 |

## 常见参数

以下参数对所有命令都是通用的。 这些命令可以在安装商务软件之前或之后运行：

| 长版本 | 短版本 | 含义 |
|--- |--- |--- |
| `--help` | `-h` | 获取任何命令的帮助。 例如， `./magento help setup:install` 或 `./magento help setup:config:set`. |
| `--quiet` | `-q` | 安静模式；无输出。 |
| `--no-interaction` | `-n` | 无交互式问题。 |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 详细程度。 例如， `--verbose=3` 或 `-vvv` 显示调试详细程度，这是最详细的输出。 默认为 `--verbose=1` 或 `-v`. |
| `--version` | `-V` | 显示此应用程序版本 |
| `--ansi` | n/a | 强制ANSI输出 |
| `--no-ansi` | n/a | 禁用ANSI输出 |
