---
title: 启用或禁用维护模式
description: 按照以下步骤自定义客户在Adobe Commerce或Magento Open Source部署停止以进行维护时看到的内容。
source-git-commit: bc025217ed7bc2195c0a2d919139abe13d184259
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---


# 启用或禁用维护模式

以下指南参考了标准维护模式页面。 如果您需要使用自定义维护页面，请参阅 [创建自定义维护页面](../../upgrade/troubleshooting/maintenance-mode-options.md) 主题。

Adobe Commerce和Magento Open Source使用 [维护模式](../../configuration/bootstrap/application-modes.md#maintenance-mode) 禁用引导。 在您维护、升级或重新配置网站时，禁用引导会很有帮助。

应用程序检测维护模式如下：

* 如果 `var/.maintenance.flag` 不存在，维护模式已关闭，并且应用程序正常运行。
* 否则，维护模式为开启，除非 `var/.maintenance.ip` 存在。

   `var/.maintenance.ip` 可以包含IP地址列表。 如果使用HTTP访问入口点，并且客户端IP地址与该列表中的一个条目相对应，则维护模式将关闭。

## 安装应用程序

在使用此命令启用或禁用维护模式之前，您必须 [安装应用程序](../advanced.md).

## 启用或禁用维护模式

使用 `magento maintenance` 用于启用或禁用维护模式的CLI命令。

命令用法：

```bash
bin/magento maintenance:enable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:disable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:status
```

的 `--ip=<ip address>` option是要从维护模式中豁免的IP地址（例如，执行维护的开发人员）。 要在同一命令中排除多个IP地址，请多次使用选项。

>[!NOTE]
>
>使用 `--ip=<ip address>` with `magento maintenance:disable` 保存IP列表供以后使用。 要清除免税IP的列表，请使用 `magento maintenance:enable --ip=none` 或查看 [维护免除的IP地址列表](#maintain-the-list-of-exempt-ip-addresses).

的 `bin/magento maintenance:status` 命令显示维护模式的状态。

例如，要启用不免除IP地址的维护模式，请执行以下操作：

```bash
bin/magento maintenance:enable
```

要为除192.0.2.10和192.0.2.11之外的所有客户端启用维护模式，请执行以下操作：

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

将应用程序置于维护模式后，必须停止所有消息队列使用者进程。
要找到这些进程，一种方法是运行 `ps -ef | grep queue:consumers:start` 命令，然后运行 `kill <process_id>` 命令。 在多节点环境中，在每个节点上重复此任务。

## 维护免除的IP地址列表

要维护免除的IP地址列表，您可以使用 `[--ip=<ip list>]` 选项，或者您可以使用以下选项：

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

的 `<ip address> .. <ip address>` 语法是要免除的可选IP地址列表，以空格分隔。

的 `--none` 选项会清除列表。

## 多商店设置

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

如果要设置多个商店（每个商店的布局和本地化内容各不相同），请传递 `$_GET['skin']` 参数。

在以下示例中，我们使用 `503` 键入错误模板文件，该文件需要本地化内容。

的构造函数 `Error_Processor` 类接受 `skin` GET参数来更改布局：

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

此外，也可以将其添加到 `.htaccess` 附加 `skin` 参数。

### $_GET[“skin”] 参数

使用 `skin` 参数：

1. 检查 `.maintenance.flag` 存在。
1. 请注意主机地址，该地址指 `HTTP_HOST`，或任何其他变量（如ENV变量）。
1. 检查 `skin` 参数存在。
1. 使用以下重写规则设置参数。

   以下是重写规则的一些示例：

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. 复制以下文件：

   * `pub/errors/default/503.phtml` to `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` to `pub/errors/sub/styles.css`

1. 编辑这些文件以在 `503.phtml` 文件和自定义样式 `styles.css` 文件。

   确保路径指向 `errors` 目录访问Advertising Cloud的帮助。 目录名称必须与 `RewriteRule`. 在上一个示例中， `sub` 目录，该目录在 `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>的 [nginx](../../configuration/multi-sites/ms-nginx.md) 必须为多商店设置添加设置。
