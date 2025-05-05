---
title: 静态内容缓存
description: 了解静态内容签名以及如何启用或禁用该功能。
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# 静态内容缓存

为了提高性能，Commerce为静态资源（如图像、JavaScript和CSS文件）设置`Expires`标头。
在静态资源上设置`Expires`标头将指示浏览器在该URL上缓存资源并提供缓存版本，直至其过期。
这是缓存静态资源的常用[最佳做法](https://developer.yahoo.com/performance/rules.html#expires=)。

当浏览器缓存静态资源并且该资源在服务器上发生更改时，您必须清除浏览器缓存，以便它可以下载新版本。
如果您是网站管理员，可以手动清除浏览器缓存，但当您希望用户下载静态资源的新版本时，这不是适当的请求。

## 静态内容签名

静态内容签名是一项Commerce功能，可让您使静态资源的浏览器缓存失效。
为此，Commerce会将部署版本添加到静态文件的URL。

以下是使用版本签名的URL的示例：

```
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

当您运行命令[`setup:static-content:deploy`](../cli/static-view-file-deployment.md)以部署静态内容时，Commerce会自动更改部署版本。
这会更改静态文件的URL，并强制浏览器加载文件的新版本。

默认情况下，Commerce将启用此功能，Adobe建议保持启用此功能，以防止与提供旧静态资源的浏览器相关的问题。

静态内容签名的配置位于&#x200B;[**[!UICONTROL Stores]**>“设置”>“配置”>“**[!UICONTROL Advanced]**”>“**[!UICONTROL Developer]**”>“**[!UICONTROL Static Files Settings]**](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/tools/developer-tools#static-file-signatures)”。

- **仅限内部部署**：如果您的站点在[生产模式](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html?lang=zh-Hans#production-mode)中&#x200B;**不是**，则此配置可用。
- **云**：此配置已隐藏，因为生产模式是强制实施的；因此，您必须使用以下命令行。

![静态文件设置](../../assets/configuration/static-files-settings.png)

确定状态：

```bash
bin/magento config:show dev/static/sign
```

启用或禁用静态内容签名：

```bash
bin/magento config:set dev/static/sign <value>
```

其中`<value>`为1（启用）或0（禁用）。

## 版本签名

Commerce将版本签名作为路径组件直接附加到静态视图文件的基本URL之后，以保持静态资源中相对URL的完整性。
这还会强制浏览器将相对URL解析为正确的签名源，同时保持其内容与签名值的存在/不存在无关。

当浏览器从服务器请求已签名的源时，服务器使用URL重写从URL中删除签名组件。

## 部署期间的使用情况

升级或修改静态资源后，必须运行`setup:static-content:deploy`命令以部署版本并更新静态内容，这会强制浏览器加载更新的资源。

如果将代码部署在单独的服务器上，并使用代码存储库将其移至生产服务器以减少停机时间，则还必须将文件`pub/static/deployed_version.txt`添加到存储库中。
此文件包含所部署静态内容的新版本。
