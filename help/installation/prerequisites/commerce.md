---
title: 获取Adobe Commerce软件
description: 了解如何下载Adobe Commerce软件。
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# 获取Adobe Commerce软件

全世界有24万商家信任我们的电子商务软件，你们就是其中之一。 我们已收集了一些信息以帮助您开始安装。

## 如何获取软件

查看令人兴奋的新功能和版本的可用性，并了解如何在我们的[产品可用性页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/release/product-availability)上获取这些功能和版本。

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
        <td><ol><li>创建包含要使用的组件列表的编辑器<em>项目</em>。</li>
            <li>使用编辑器更新包依赖关系；使用<code>composer create-project</code>获取编辑器中继包。</li>
            <li>使用<a href="../advanced.md">命令行</a>安装应用程序。</li>
        <li>使用<a href="../../upgrade/implementation/perform-upgrade.md">命令行</a>升级应用程序和扩展。</li></ol></td>
        <td><p><a href="../composer.md">获取隐喻</a></p></td>
    </tr>
    <tr>
        <td><p>参与开发人员</p></td>
        <td><p>产生Magento Open Source代码库、文件错误并自定义应用程序。 技术含量高，拥有自己的开发服务器，了解Composer和GitHub。</p>
            <p>您<em>无法</em>在生产环境中使用该应用程序。</p>
      <p>您必须使用<a href="../../upgrade/developer/git-installs.md">编辑器和Git命令</a>进行升级。</p></td>
        <td><ol><li>克隆GitHub存储库。</li>
            <li>使用编辑器更新包依赖关系。</li>
            <li>使用<a href="../advanced.md">命令行</a>安装应用程序。</li>
            <li>使用<a href="../../upgrade/developer/git-installs.md">编辑器和Git命令</a>升级应用程序。</li>
            <li>自定义<code>app/code</code>目录下的代码。</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">克隆GitHub存储库</a></p></td>
    </tr>
    </tbody>
</table>

## 有用信息

使用页面左侧的链接可浏览安装各个部分的主题。

## 所需的服务器权限

UNIX系统需要`root`权限才能安装和配置诸如Web服务器PHP之类的软件。 如果需要安装此软件，请确保您具有`root`访问权限。

请&#x200B;*不*&#x200B;在Web服务器docroot中以`root`用户身份安装应用程序，因为Web服务器可能无法与这些文件交互。

您需要`root`权限才能创建[文件系统所有者](file-system/overview.md)并将该所有者添加到Web服务器的组中。 使用文件系统所有者从命令行运行`bin/magento`命令并设置cron作业，这些作业为您安排任务。
