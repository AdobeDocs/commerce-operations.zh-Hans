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

以下指南参考了标准维护模式页面。 如果需要使用自定义维护页面，请参阅[创建自定义维护页面](../../upgrade/troubleshooting/maintenance-mode-options.md)主题。

Adobe Commerce使用[维护模式](../../configuration/bootstrap/application-modes.md#maintenance-mode)禁用引导。 在维护、升级或重新配置站点时，禁用引导很有用。

应用程序检测维护模式，如下所示：

* 如果`var/.maintenance.flag`不存在，则维护模式将关闭，并且应用程序将正常运行。
* 否则，维护模式将开启，除非`var/.maintenance.ip`存在。

  `var/.maintenance.ip`可以包含IP地址列表。 如果使用HTTP访问入口点，并且客户端IP地址与该列表中的某个条目相对应，则维护模式将关闭。

## 安装应用程序

使用此命令启用或禁用维护模式之前，必须[安装应用程序](../advanced.md)。

## 启用或禁用维护模式

使用`magento maintenance` CLI命令启用或禁用维护模式。

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

`--ip=<ip address>`选项是免除维护模式的IP地址（例如，执行维护的开发人员）。 要在同一命令中免除多个IP地址，请多次使用选项。

>[!NOTE]
>
>将`--ip=<ip address>`与`magento maintenance:disable`一起使用可保存IP列表以供将来使用。 要清除免除IP列表，请使用`magento maintenance:enable --ip=none`或参阅[维护免除IP地址列表](#maintain-the-list-of-exempt-ip-addresses)。

`bin/magento maintenance:status`命令显示维护模式的状态。

例如，启用没有IP地址劐免的维护模式：

```bash
bin/magento maintenance:enable
```

要为除192.0.2.10和192.0.2.11之外的所有客户端启用维护模式，请执行以下操作：

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

将应用程序置于维护模式后，必须停止所有消息队列使用者进程。
查找这些进程的一种方法是运行`ps -ef | grep queue:consumers:start`命令，然后为每个使用者运行`kill <process_id>`命令。 在多节点环境中，对每个节点重复此任务。

## 维护免除IP地址列表

要维护免除IP地址列表，您可以使用上述命令中的`[--ip=<ip list>]`选项，也可以使用以下命令：

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

`<ip address> .. <ip address>`语法是要免除的IP地址的可选空格分隔列表。

`--none`选项清除列表。

## 多存储设置

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

如果要设置多个商店，每个商店具有不同的布局和本地化内容，请将`$_GET['skin']`参数传递给目标处理器。

在以下示例中，我们使用的是`503`类型错误模板文件，该文件需要本地化的内容。

`Error_Processor`类的构造函数接受一个`skin`GET参数以更改布局：

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

这还可以添加到`.htaccess`文件中的重写规则，该规则会将`skin`参数附加到URL。

### $_GET[&#39;skin&#39;]参数

要使用`skin`参数，请执行以下操作：

1. 检查`.maintenance.flag`是否存在。
1. 请注意引用`HTTP_HOST`的主机地址或任何其他变量（如ENV变量）。
1. 检查`skin`参数是否存在。
1. 使用以下重写规则设置参数。

   以下是重写规则的一些示例：

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * 重写规则`^ %{REQUEST_URI}?skin=sub` [L]

1. 复制以下文件：

   * `pub/errors/default/503.phtml`至`pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css`至`pub/errors/sub/styles.css`

1. 编辑这些文件以在`503.phtml`文件中提供本地化内容并在`styles.css`文件中提供自定义样式。

   确保您的路径指向`errors`目录。 目录名称必须与`RewriteRule`中指示的URL参数匹配。 在上一个示例中，使用了`sub`目录，该目录被指定为`RewriteRule` (`skin=sub`)中的参数

>[!NOTE]
>
>必须为多存储设置添加[nginx](../../configuration/multi-sites/ms-nginx.md)设置。
