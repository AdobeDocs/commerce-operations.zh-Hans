---
title: 静态内容缓存
description: 了解静态内容签名以及如何启用或禁用该功能。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# 静态内容缓存

为了提高性能，Commerce会设置 `Expires` 静态资源（如图像、JavaScript和CSS文件）的标头。
设置 `Expires` 静态资源上的标头会告知浏览器在该URL上缓存资源，并在该URL过期之前提供缓存的版本。
这是常见的 [最佳实践](https://developer.yahoo.com/performance/rules.html#expires=) 用于缓存静态资源。

当浏览器缓存静态资源并且该资源在服务器上发生更改时，必须清除浏览器缓存，以便它能够下载新版本。
如果您是网站管理员，则可以手动清除浏览器缓存，但是当您希望用户下载静态资源的新版本时，这不是向用户发出的合适请求。

## 静态内容签名

静态内容签名是一项商务功能，允许您使静态资源的浏览器缓存失效。
Commerce通过向静态文件的URL添加部署版本来完成此操作。

以下是一个使用版本签名的URL示例：

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

运行命令时 [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) 要部署静态内容， Commerce会自动更改部署版本。
这会更改静态文件的URL，并强制浏览器加载新版本的文件。

默认情况下，Commerce会启用此功能，并且Adobe建议保持启用此功能，以防止出现与浏览器提供旧静态资源相关的问题。

您可以在 [**[!UICONTROL Stores]**>设置>配置>**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html).

![静态文件设置](../../assets/configuration/static-files-settings.png)

确定状态：

```bash
bin/magento config:show dev/static/sign
```

启用或禁用静态内容签名：

```bash
bin/magento config:set dev/static/sign <value>
```

其中 `<value>` 为1（已启用）或0（已禁用）。

## 版本签名

商务会将版本签名作为路径组件直接附加到静态视图文件的基本URL之后，以保留跨静态资源的相对URL的完整性。
这还会强制浏览器将相对URL解析为正确的已签名源，同时保持其内容与签名值的存在/不存在无关。

当浏览器从服务器请求签名源时，服务器会使用URL重写从URL中删除签名组件。

## 部署期间的使用情况

升级或修改静态资源后，必须运行 `setup:static-content:deploy` 命令来部署版本和更新静态内容，这会强制浏览器加载更新的资源。

如果您在单独的服务器上部署代码并使用代码存储库将其移动到生产环境以减少停机时间，则还必须添加该文件 `pub/static/deployed_version.txt` 到存储库。
此文件包含已部署静态内容的新版本。
