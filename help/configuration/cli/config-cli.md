---
title: 命令行工具
description: 使用Commerce命令行工具运行安装和配置任务。
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# 命令行工具

Commerce具有一个命令行界面(CLI)—`<magento_root>/bin/magento` — 用于运行安装和配置任务，包括：

- 安装Commerce（以及更新数据库架构、创建部署配置等相关任务）
- 清除缓存
- 管理索引，包括重新编制索引
- 创建翻译词典和翻译包
- 为插件生成不存在的类（如工厂和侦听器），为对象管理器生成依赖项注入配置
- 部署静态视图文件
- 从更少内容创建CSS

其他优势包括：

- 单个命令(`<magento_root>/bin/magento list`)列出了所有可用的安装和配置命令。
- 基于Symfony的一致用户界面。
- CLI是可扩展的，因此第三方开发人员可以“插入”到其中。 这还有消除用户学习曲线的额外好处。
- 禁用模块的命令不显示。

本主题讨论如何使用CLI配置Adobe Commerce软件。 有关安装Commerce的信息，请参阅&#x200B;_安装指南_&#x200B;中的[安装流程](../../installation/overview.md)。

## 先决条件

在开始使用CLI之前，请确保：

1. 您的系统符合&#x200B;_安装指南_&#x200B;中的[系统要求](../../installation/system-requirements.md)中讨论的要求。
1. 您已完成&#x200B;_安装指南_&#x200B;中的[先决条件](../../installation/prerequisites/overview.md)中讨论的所有先决条件任务。
1. 登录到Commerce服务器后，切换到有权写入Commerce文件系统的用户。 请参阅&#x200B;_安装指南_&#x200B;中的[切换到文件系统所有者](../../installation/prerequisites/file-system/overview.md)。

## 正在运行命令

对于bash shell，请使用以下语法切换到文件系统所有者，同时输入命令：

```bash
su <file system owner> -s /bin/bash -c <command>
```

如果文件系统所有者不允许登录，您可以使用以下方法：

```bash
sudo -u <file system owner> <command>
```

**要从任何目录运行CLI命令**：

将`<magento_root>/bin`添加到您的系统`PATH`。

CentOS的bash shell示例：

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

（可选）您可以运行以下命令：

- `cd <magento_root>/bin`并作为`./magento <command name>`运行
- `<magento_root>/bin/magento <command name>`
- `<magento_root>`是Web服务器docroot的子目录
