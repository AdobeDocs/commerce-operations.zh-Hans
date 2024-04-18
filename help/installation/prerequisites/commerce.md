---
title: 获取Adobe Commerce软件
description: 了解如何下载Adobe Commerce软件。
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# 获取Adobe Commerce软件

全世界有24万商家信任我们的电子商务软件，你们就是其中之一。 我们已收集了一些信息以帮助您开始安装。

## 如何获取软件

查看令人兴奋的新增功能和版本的可用性，并了解如何将其添加到我们的 [产品可用性页面](https://devdocs.magento.com/release/availability.html).

请参阅下表，了解如何开始安装Adobe Commerce。

<table>
    <tbody>
        <tr>
            <th>用户需求</th>
            <th>描述</th>
            <th>高级安装和升级步骤</th>
            <th>开始使用链接</th>
        </tr>
    <tr>
        <td><p>Integrator， packager</p></td>
        <td><p>希望完全控制已安装的所有组件，有权访问应用程序服务器，技术含量高，可能会将Magento Open Source与其他组件重新打包。</p>
        </td>
        <td><ol><li>创建编辑器 <em>项目</em> ，其中包含要使用的组件列表。</li>
            <li>使用编辑器更新包依赖项；使用 <code>composer create-project</code> 来获取“作曲者”的比喻。</li>
            <li>使用安装应用程序 <a href="../advanced.md">命令行</a>.</li>
        <li>使用升级应用程序和扩展  <a href="../../upgrade/implementation/perform-upgrade.md">命令行</a>.</li></ol></td>
        <td><p><a href="../composer.md">获取隐喻</a></p></td>
    </tr>
    <tr>
        <td><p>参与开发人员</p></td>
        <td><p>提供Magento Open Source代码库、文件错误和自定义应用程序。 技术含量高，拥有自己的开发服务器，了解Composer和GitHub。</p>
            <p>您 <em>无法</em> 在生产环境中使用应用程序。</p>
      <p>您必须使用进行升级 <a href="../../upgrade/developer/git-installs.md">Composer和Git命令</a>.</p></td>
        <td><ol><li>克隆GitHub存储库。</li>
            <li>使用编辑器更新包依赖关系。</li>
            <li>安装应用程序，使用 <a href="../advanced.md">命令行</a>.</li>
            <li>使用升级应用程序 <a href="../../upgrade/developer/git-installs.md">Composer和Git命令</a>.</li>
            <li>在下自定义代码 <code>app/code</code> 目录。</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">克隆GitHub存储库</a></p></td>
    </tr>
    </tbody>
</table>

## 有用信息

使用页面左侧的链接可浏览安装各个部分的主题。

## 所需的服务器权限

UNIX系统需要 `root` 安装和配置软件（如Web服务器PHP）的权限。 如果需要安装此软件，请确保您已 `root` 访问权限。

Do *非* 在web服务器docroot中安装应用程序，作为 `root` 用户，因为Web服务器可能无法与这些文件交互。

您需要 `root` 权限以创建 [文件系统所有者](file-system/overview.md) 并将该所有者添加到Web服务器的组中。 使用文件系统所有者运行 `bin/magento` 命令行中的命令和设置cron作业的命令，这些作业为您安排任务。
