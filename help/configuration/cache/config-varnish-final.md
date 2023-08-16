---
title: 最终验证
description: 验证您的Varnish配置是否已正确设置以用于Adobe Commerce应用程序。
feature: Configuration, Cache
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 清漆配置的最终验证

现在您正在使用 `default.vcl` 由Commerce为您生成，您可以执行一些最终验证以确保Varnish正常工作。

## 验证HTTP响应标头

使用 `curl` 或者另一个实用程序，当您在Web浏览器中访问任何Commerce页面时查看HTTP响应标头。

首先，确保使用 [开发者模式](../cli/set-mode.md#change-to-developer-mode)；否则，您将看不到标头。

例如，

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

重要标头：

```terminal
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>此值也可以接受： `X-Magento-Cache-Debug: HIT`.

## 检查页面加载时间

如果Varnish运行正常，则任何包含可缓存块的Commerce页面都应在150毫秒内加载。 此类页面的示例包括前门和店面类别页面。

使用浏览器检查器测量页面加载时间。

例如，使用Chrome检查器：

1. 在Chrome中访问任何可缓存的Commerce页面。
1. 右键单击页面上的任意位置。
1. 在弹出菜单中，单击 **[!UICONTROL Inspect Element]**
1. 在检查器窗格中，单击 **[!UICONTROL Network]** 选项卡。
1. 刷新页面。
1. 滚动到检查器窗格的顶部，以便查看正在查看的页面的URL。

   下图显示了一个加载 `magento2` 索引页。

   ![单击您正在查看的页面](../../assets/configuration/varnish-inspector.png)

   页面加载时间显示在页面URL旁边。 在这种情况下，加载时间为5毫秒。 这有助于确认Varnish是否缓存了页面。

1. 要查看HTTP响应标头，请单击页面URL（在名称列中）。

   您可以查看HTTP标头，有关更多详细信息，请参阅验证HTTP响应标头一节。

## 验证商务缓存

确保 `<magento_root>/var/page_cache` 目录为空：

1. 登录到您的Commerce服务器或切换到文件系统所有者。
1. 输入以下命令：

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. 访问一个或多个可缓存的Commerce页面。
1. 查看 `var/page_cache/` 目录。

   如果目录为空，恭喜您！ 您已成功将Varnish和Commerce配置为协同工作！

1. 如果您已清除 `var/page_cache/` 目录，重新启动Varnish。

>[!TIP]
>
>如果您遇到503（后端提取失败）错误，请参阅 [503（服务不可用）错误故障诊断](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshooting-503-errors.html) 在 _Adobe Commerce帮助中心_.
