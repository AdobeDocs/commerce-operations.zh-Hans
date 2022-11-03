---
title: 优化CSS和JS资源文件
description: 了解如何通过管理员或命令行合并和缩小Adobe Commerce项目的CSS和JavaScript(JS)文件。
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 052aa61e2bb59ae11b90b5401ce6426dec9c6046
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# 优化资源文件

对于响应更快的商务网站，请优化CSS和JavaScript(JS)资源文件，并消除呈现阻止资源。

- **优化CSS和JS文件** — 通过将Adobe Commerce配置为将单独的文件合并、缩小和捆绑到单个文件中，可减少加载CSS和JavaScript(JS)文件所需的时间。
- **消除渲染阻止资源** — 考虑在内联交付关键JS和CSS功能，并推迟交付所有非关键JS/CSS样式。 有关指南，请参阅 [消除渲染阻止资源](https://web.dev/render-blocking-resources/).

## 受影响的产品和版本

[所有受支持的版本， 2.3及更高版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部
- Magento Open Source

## 合并或缩小CSS文件

通过将单个文件合并、缩小和捆绑到单个文件中，可以缩短加载CSS和JavaScript(JS)文件所花费的时间。

>[!IMPORTANT]
>
>云基础架构上的Adobe Commerce始终在生产模式下运行，否则无法进行设置，因此您必须使用命令行方法来启用合并、缩小和捆绑。

### 使用管理员

要启用CSS合并或缩小，请进入 [!UICONTROL **管理员** > **商店** > **设置** > **配置** > **高级** > **开发人员** > **CSS设置**].

### 使用命令行

要在云基础架构上的Adobe Commerce中启用CSS合并，请执行以下操作：

1. 在本地运行此命令：

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. 将更改提交到 `app/etc/config.php` 文件并重新部署。

要在云基础架构上的Adobe Commerce中启用CSS缩小，请执行以下操作：

1. 在本地运行此命令：

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. 将更改提交到 `app/etc/config.php` 文件并重新部署。

## 缩小JS文件

### 使用管理员

在 *管理员* 侧栏，转到 **商店** > **设置** > **配置** > **高级** > **开发人员** > **JavaScript设置**.

### 使用命令行

要在云基础架构上的Adobe Commerce中启用JS缩小，请执行以下操作：

1. 在本地运行此命令：

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. 将更改提交到 `app/etc/config.php` 文件并重新部署。

## 合并和捆绑JS文件

您可以在商务管理员中打开合并或捆绑（不能同时启用合并和捆绑）： [!UICONTROL **商店** > **设置** > **配置** > **高级** > **开发人员** > **JavaScript设置**].

您还可以从命令行中启用Adobe Commerce内置捆绑（基本捆绑）：

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## 其他信息

- [客户端优化设置](../../../performance/configuration.md#client-side-optimization-settings)
- [用户指南：优化资源文件](https://docs.magento.com/user-guide/system/file-optimization.html)
- [Frontend开发人员指南：CSS合并、缩小和站点性能](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
