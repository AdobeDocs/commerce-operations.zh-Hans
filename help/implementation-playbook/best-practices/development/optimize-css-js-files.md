---
title: 优化CSS和JS资源文件
description: 了解如何从管理员或命令行合并Adobe Commerce项目的CSS和JavaScript (JS)文件并进行缩小。
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: 5f4edc2e694c9bdbdffbe48b0e5d69907cbc0027
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# 优化资源文件

对于响应更迅速的Commerce站点，请优化CSS和JavaScript (JS)资源文件并消除渲染阻止资源。

- **优化CSS和JS文件** — 通过将Adobe Commerce配置为合并、缩小单独的文件并将其捆绑到单个文件中，减少加载CSS和JavaScript (JS)文件所需的时间。
- **消除渲染阻止资源** — 考虑内联提供关键JS和CSS功能，并延迟所有非关键JS/CSS样式。 有关指导，请参阅[消除渲染阻止资源](https://web.dev/render-blocking-resources/)。

## 受影响的产品和版本

[所有受支持的版本，2.3及更高版本，共](../../../release/versions.md)个：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 合并或缩小CSS文件

通过合并、缩小单独的文件并将其捆绑到单个文件中，可以缩短加载CSS和JavaScript (JS)文件所需的时间。

>[!IMPORTANT]
>
>云基础架构上的Adobe Commerce始终以生产模式运行，不能以其他方式设置它，因此您必须使用命令行方法来启用合并、缩小和捆绑功能。

如果您的部署使用HTTP/2，请勿合并或捆绑文件。 HTTP/2以异步方式下载静态文件。 在处理文件内容之前，浏览器必须下载整个合并文件。

### 使用管理员

要启用CSS合并或缩小，请转到&#x200B;[!UICONTROL **管理员** > **存储** > **设置** > **配置** > **高级** > **开发人员** > **CSS设置**]。

### 使用命令行

要在云基础架构上的Adobe Commerce中启用CSS合并，请执行以下操作：

1. 在本地运行此命令：

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. 提交对`app/etc/config.php`文件的更改并重新部署。

要在云基础架构上的Adobe Commerce中启用CSS缩小，请执行以下操作：

1. 在本地运行此命令：

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. 提交对`app/etc/config.php`文件的更改并重新部署。

## 缩小JS文件

### 使用管理员

在&#x200B;*管理员*&#x200B;侧边栏上，转到&#x200B;**商店** > **设置** > **配置** > **高级** > **开发人员** > **JavaScript设置**。

### 使用命令行

要在云基础架构上的Adobe Commerce中启用JS缩小，请执行以下操作：

1. 在本地运行此命令：

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. 提交对`app/etc/config.php`文件的更改并重新部署。

## 合并和捆绑JS文件

您可以在Commerce管理中打开合并或捆绑功能（合并和捆绑功能无法同时启用）：[!UICONTROL **存储** > **设置** > **配置** > **高级** > **开发人员** > **JavaScript设置**]。

您还可以从命令行启用Adobe Commerce内置捆绑（基本捆绑）：

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## 其他信息

- [客户端优化设置](../../../performance/configuration.md#client-side-optimization-settings)
- [用户指南：优化资源文件](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [前端开发人员指南：CSS合并、缩小和网站性能](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [高级JavaScript捆绑](../../../performance/advanced-js-bundling.md)
