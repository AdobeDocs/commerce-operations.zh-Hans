---
title: 获取Adobe Commerce软件
description: 了解如何下载Adobe Commerce和Magento Open Source软件。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# 获取Adobe Commerce软件

您是全球24万商户中信任我们电子商务软件的一员。 我们收集了一些信息来帮助您开始安装。

## 如何获取软件

查看令人兴奋的新增功能和版本的可用性，并了解如何在我们的 [产品可用性页面](https://devdocs.magento.com/release/availability.html).

请参阅下表，了解安装Adobe Commerce或Magento Open Source的入门信息。

<table>
    <tbody>
        <tr>
            <th>用户需求</th>
            <th>描述</th>
            <th>高级安装和升级步骤</th>
            <th>入门链接</th>
        </tr>
    <tr>
        <td><p>集成商、打包程序</p></td>
        <td><p>希望完全控制所有已安装的组件，能够访问应用程序服务器，而且技术性很强，可能会将Magento Open Source重新打包到其他组件中。</p>
        </td>
        <td><ol><li>创建编辑器 <em>项目</em> ，其中包含要使用的组件列表。</li>
            <li>使用编辑器更新包依赖关系；使用 <code>composer create-project</code> 来得到作曲家的暗喻。</li>
            <li>使用 <a href="../advanced.md">命令行</a>.</li>
        <li>使用  <a href="../../upgrade/implementation/perform-upgrade.md">命令行</a>.</li></ol></td>
        <td><p><a href="../composer.md">获取元数据包</a></p></td>
    </tr>
    <tr>
        <td><p>参与开发人员</p></td>
        <td><p>导致Magento Open Source代码库、文件错误和自定义应用程序。 技术性极强，拥有自己的开发服务器，了解编辑器和GitHub。</p>
            <p>您 <em>无法</em> 在生产环境中使用该应用程序。</p>
      <p>您必须使用 <a href="../../upgrade/developer/git-installs.md">编辑器和Git命令</a>.</p></td>
        <td><ol><li>克隆GitHub存储库。</li>
            <li>使用编辑器来更新包依赖项。</li>
            <li>使用 <a href="../advanced.md">命令行</a>.</li>
            <li>使用 <a href="../../upgrade/developer/git-installs.md">编辑器和Git命令</a>.</li>
            <li>在 <code>app/code</code> 目录访问Advertising Cloud的帮助。</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">克隆GitHub存储库</a></p></td>
    </tr>
    </tbody>
</table>

## 有用信息

使用页面左侧的链接可导航安装每个部分中的主题。

## 所需的服务器权限

UNIX系统需要 `root` 安装和配置软件（如Web服务器PHP）的权限。 如果需要安装此软件，请确保 `root` 访问权限。

做 *not* 在web服务器docroot中安装应用程序，作为 `root` 用户，因为web服务器可能无法与这些文件进行交互。

您需要 `root` 创建权限 [文件系统所有者](file-system/overview.md) 并将该所有者添加到Web服务器的组。 使用文件系统所有者运行 `bin/magento` 命令行中的命令和设置cron作业（为您安排任务）。
