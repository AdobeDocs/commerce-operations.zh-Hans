---
title: 命令行工具
description: 使用商务命令行工具运行安装和配置任务。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# 命令行工具

Commerce有一个命令行界面(CLI)—`<magento_root>/bin/magento` — 运行安装和配置任务，包括：

- 安装商务（及相关任务，例如更新数据库架构、创建部署配置）
- 清除缓存
- 管理索引，包括重新索引
- 创建翻译字典和翻译包
- 为插件生成不存在的类（如工厂和截取器），为对象管理器生成依赖项注入配置
- 部署静态视图文件
- 从更少创建CSS

其他优势包括：

- 单个命令(`<magento_root>/bin/magento list`)列出所有可用的安装和配置命令。
- 基于Symfony的一致用户界面。
- CLI是可扩展的，因此第三方开发人员可以“插入”到它。 这样可消除用户的学习曲线，从而带来额外的好处。
- 禁用模块的命令不显示。

本主题讨论如何使用CLI配置Adobe Commerce和Magento Open Source软件。 有关安装Commerce的信息，请参阅 [安装流程](../../installation/overview.md) 在 _安装指南_.

## 先决条件

在开始使用CLI之前，请确保：

1. 您的系统符合 [系统要求](../../installation/system-requirements.md) 在 _安装指南_.
1. 您已完成 [先决条件](../../installation/prerequisites/overview.md) 在 _安装指南_.
1. 登录到商务服务器后，切换到有权写入商务文件系统的用户。 请参阅 [切换到文件系统所有者](../../installation/prerequisites/file-system/overview.md) 在 _安装指南_.

## 运行命令

对于bash shell，请使用以下语法切换到文件系统所有者并同时输入命令：

```bash
su <file system owner> -s /bin/bash -c <command>
```

如果文件系统所有者不允许登录，您可以使用以下代码：

```bash
sudo -u <file system owner> <command>
```

**从任何目录运行CLI命令**:

添加 `<magento_root>/bin` 到系统 `PATH`.

CentOS的bash shell示例：

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

（可选）您可以运行以下内容：

- `cd <magento_root>/bin` 以 `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` 是web服务器docroot的子目录
