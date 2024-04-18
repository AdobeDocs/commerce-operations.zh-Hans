---
title: 启用或禁用维护模式
description: 按照以下步骤自定义客户在Adobe Commerce部署因维护而停止时看到的内容。
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# 启用或禁用维护模式

以下指南参考了标准维护模式页面。 如果您需要使用自定义维护页面，请参阅 [创建自定义维护页面](../../upgrade/troubleshooting/maintenance-mode-options.md) 主题。

Adobe Commerce使用 [维护模式](../../configuration/bootstrap/application-modes.md#maintenance-mode) 以禁用引导。 在维护、升级或重新配置站点时，禁用引导很有用。

应用程序检测维护模式，如下所示：

* 如果 `var/.maintenance.flag` 不存在，维护模式已关闭且应用程序运行正常。
* 否则，维护模式将开启，除非 `var/.maintenance.ip` 已存在。

  `var/.maintenance.ip` 可以包含IP地址列表。 如果使用HTTP访问入口点，并且客户端IP地址与该列表中的某个条目相对应，则维护模式将关闭。

## 安装应用程序

使用此命令启用或禁用维护模式之前，必须 [安装应用程序](../advanced.md).

## 启用或禁用维护模式

使用 `magento maintenance` CLI命令启用或禁用维护模式。

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

此 `--ip=<ip address>` 选项是一个免除维护模式的IP地址（例如，执行维护的开发人员）。 要在同一命令中免除多个IP地址，请多次使用选项。

>[!NOTE]
>
>使用 `--ip=<ip address>` 替换为 `magento maintenance:disable` 保存IP列表供以后使用。 要清除免除IP列表，请使用 `magento maintenance:enable --ip=none` 或查看 [维护免除IP地址列表](#maintain-the-list-of-exempt-ip-addresses).

此 `bin/magento maintenance:status` 命令显示维护模式的状态。

例如，启用没有IP地址劐免的维护模式：

```bash
bin/magento maintenance:enable
```

要为除192.0.2.10和192.0.2.11之外的所有客户端启用维护模式，请执行以下操作：

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

将应用程序置于维护模式后，必须停止所有消息队列使用者进程。
查找这些流程的一种方法是运行 `ps -ef | grep queue:consumers:start` 命令，然后运行 `kill <process_id>` 命令。 在多节点环境中，对每个节点重复此任务。

## 维护免除IP地址列表

要维护免除IP地址列表，您可以使用 `[--ip=<ip list>]` 选项，或者可以使用以下命令：

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

此 `<ip address> .. <ip address>` 语法是可免除的IP地址的可选列表（以空格分隔）。

此 `--none` 选项清除列表。

## 多存储设置

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

如果要设置多个商店，且每个商店具有不同的布局和本地化内容，请传递 `$_GET['skin']` 参数到目标处理器。

在以下示例中，我们使用 `503` 键入错误模板文件，此文件需要本地化的内容。

的构造函数 `Error_Processor` 类接受 `skin` 用于更改布局的GET参数：

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

这还可以添加到中的重写规则 `.htaccess` 附加文件 `skin` URL参数。

### $_GET[&#39;外观&#39;] 参数

要使用 `skin` 参数：

1. 检查 `.maintenance.flag` 已存在。
1. 记下主机地址，该地址指 `HTTP_HOST`或任何其他变量（例如ENV变量）。
1. 检查 `skin` 参数存在。
1. 使用以下重写规则设置参数。

   以下是重写规则的一些示例：

   * Rewritecond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * Rewritecond `%{HTTP_HOST} ^sub.example.com$`
   * Rewritecond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * 重写规则 `^ %{REQUEST_URI}?skin=sub` [L]

1. 复制以下文件：

   * `pub/errors/default/503.phtml` 到 `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` 到 `pub/errors/sub/styles.css`

1. 编辑这些文件以在 `503.phtml` 中的文件和自定义样式 `styles.css` 文件。

   确保您的路径指向 `errors` 目录。 目录名称必须与 `RewriteRule`. 在上一个示例中， `sub` 使用directory ，它在 `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>此 [恩金克斯](../../configuration/multi-sites/ms-nginx.md) 必须为多存储设置添加设置。
