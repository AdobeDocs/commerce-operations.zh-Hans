---
title: 静态内容缓存
description: 了解静态内容签名以及如何启用或禁用该功能。
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: d099d60bcf3c960b2e40b48c386041d8865cfb50
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# 静态内容缓存

为了提高性能，Commerce为静态资源(如图像、JavaScript和CSS文件)设置`Expires`标头。
在静态资源上设置`Expires`标头可告知浏览器在该URL缓存资源并提供缓存的版本，直到它过期为止。
这是用于缓存静态资源的常见[最佳实践](https://developer.yahoo.com/performance/rules.html#expires=)。

当浏览器缓存静态资源并且该资源在服务器上发生更改时，您必须清除浏览器缓存，以便它可以下载新版本。
如果您是网站管理员，则手动清除浏览器缓存是可行的，但在您希望用户下载静态资源的新版本时，这不是针对用户发出的适当请求。

## 静态内容签名

静态内容签名是一项Commerce功能，它允许您使静态资源的浏览器缓存失效。
Commerce通过向静态文件的URL添加部署版本来实现这一点。

以下是使用版本签名的URL示例：

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

当您运行命令[`setup:static-content:deploy`](../cli/static-view-file-deployment.md)以部署静态内容时，Commerce会自动更改部署版本。
这会更改静态文件的URL，并强制浏览器加载文件的新版本。

默认情况下，Commerce将启用此功能，Adobe建议保持启用此功能，以防止与提供旧静态资源的浏览器相关的问题。

静态内容签名的配置位于&#x200B;[**[!UICONTROL Stores]**>设置>配置>**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html)中。

- **仅限内部部署**：如果您的站点在[生产模式](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#production-mode)中是&#x200B;**而不是**，则此配置可用。
- **Cloud**：此配置是隐藏的，因为生产模式是强制实施的；因此，您必须使用命令行，如下所示。

![静态文件设置](../../assets/configuration/static-files-settings.png)

确定状态：

```bash
bin/magento config:show dev/static/sign
```

启用或禁用静态内容签名：

```bash
bin/magento config:set dev/static/sign <value>
```

其中`<value>`为1（已启用）或0（已禁用）。

## 版本签名

Commerce会将版本签名作为路径组件直接附加到静态视图文件的基本URL之后，以保持静态资源中相对URL的完整性。
这还会强制浏览器将相对URL解析为正确的签名源，同时保持其内容与签名值的存在/不存在无关。

当浏览器从服务器请求已签名的源时，服务器使用URL重写从URL中删除签名组件。

## 部署期间的使用情况

升级或修改静态资源后，必须运行`setup:static-content:deploy`命令以部署版本并更新静态内容，从而强制浏览器加载更新的资源。

如果您在单独的服务器上部署代码，并使用代码存储库将其移至生产环境以减少停机时间，则还必须将文件`pub/static/deployed_version.txt`添加到存储库。
此文件包含已部署静态内容的新版本。
