---
title: 最终验证
description: 验证是否已正确设置清漆配置以与Adobe Commerce应用程序配合使用。
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---


# 清漆结构的最终验证

现在，您正在使用 `default.vcl` Commerce为您生成的清漆，您可以执行一些最终验证以确保清漆正常工作。

## 验证HTTP响应头

使用 `curl` 或其他实用程序来查看HTTP响应标头。

首先，确保您使用 [开发人员模式](../cli/set-mode.md#change-to-developer-mode);否则，您将看不到标头。

例如，

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

重要标题：

```terminal
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>此值也可接受： `X-Magento-Cache-Debug: HIT`.

## 检查页面加载时间

如果清漆正常工作，则任何具有可缓存块的商务页面都应在150毫秒内加载。 例如，前门和 [店面](https://glossary.magento.com/storefront) [类别](https://glossary.magento.com/category) 页面。

使用浏览器检查器测量页面加载时间。

例如，要使用Chrome检查器，请执行以下操作：

1. 在Chrome中访问任何可缓存的商务页面。
1. 右键单击页面上的任意位置。
1. 在弹出菜单中，单击 **[!UICONTROL Inspect Element]**
1. 在检查器窗格中，单击 **[!UICONTROL Network]** 选项卡。
1. 刷新页面。
1. 滚动到检查器窗格的顶部，以便您能够看到所查看页面的URL。

   下图显示了加载 `magento2` 索引页。

   ![单击您正在查看的页面](../../assets/configuration/varnish-inspector.png)

   页面URL旁边会显示页面加载时间。 在这种情况下，加载时间为5毫秒。 这有助于确认清漆是否已缓存页面。

1. 要查看HTTP响应标头，请单击页面URL（在“名称”列中）。

   您可以查看HTTP标头，有关这些标头的详细信息，请参阅验证HTTP响应标头一节。

## 验证商务缓存

确保 `<magento_root>/var/page_cache` 目录为空：

1. 登录到您的Commerce服务器，或切换到 [文件系统所有者](https://glossary.magento.com/magento-file-system-owner).
1. 输入以下命令：

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. 访问一个或多个可缓存的商务页面。
1. 检查 `var/page_cache/` 目录访问Advertising Cloud的帮助。

   如果目录为空，恭喜！ 您已成功将清漆和商务配置为一起工作！

1. 如果清除了 `var/page_cache/` 目录，重新启动清漆。

>[!TIP]
>
>如果您遇到503（后端获取失败）错误，请参阅 [对503（服务不可用）错误进行故障诊断](https://support.magento.com/hc/en-us/articles/360034631211) 在 _Adobe Commerce帮助中心_.
