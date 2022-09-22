---
source-git-commit: a5777f437430bc48b87aaea65c0e101d4ecd6574
workflow-type: tm+mt
source-wordcount: '14684'
ht-degree: 0%

---
# bin/magento(Magento Open Source)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**版本**:2.4.5 <!-- app.version -->

此参考包含111个通过 `bin/magento` 命令行工具。
初始列表是使用 `bin/magento list` 命令。
使用 [&quot;添加CLI命令&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) 添加自定义CLI命令的指南。

>[!NOTE]
>
>您可以调用 `bin/magento` CLI命令使用快捷键，而不是完整命令名称。 例如，您可以调用 `bin/magento setup:upgrade` 使用 `bin/magento s:up`, `bin/magento s:upg`. 请参阅 [快捷键语法](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) 了解如何将快捷键与任何CLI命令一起使用。

>[!NOTE]
>
>此引用是从应用程序代码库生成的。 要更改内容，您可以在 [代码库](https://github.com/magento) 存储库并提交您的更改以供审核。 另一种方法是 _给我们反馈_ （在右上方查找链接）。 有关贡献准则，请参阅 [代码贡献](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `help`

显示命令帮助

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```

<!-- app.name --> <!-- command.usage -->

### `command_name`

命令名称
- 默认： `help`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--format`

输出格式（txt、xml、json或md）
- 默认： `txt`
- 需要值


### `--raw`

输出原始命令帮助
- 默认： `false`
- 不接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `list`

列表命令

```bash
bin/magento list [--raw] [--format FORMAT] [--] [<namespace>]
```

<!-- app.name --> <!-- command.usage -->

### `namespace`

命名空间名称
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

输出原始命令列表
- 默认： `false`
- 不接受值


### `--format`

输出格式（txt、xml、json或md）
- 默认： `txt`
- 需要值 <!-- options --> <!-- options.size -->

## `admin:adobe-ims:disable`

禁用Adobe IMS模块

```bash
bin/magento admin:adobe-ims:disable
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `admin:adobe-ims:enable`

启用Adobe IMS模块。

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--organization-id`, `-o`



为Adobe IMS配置设置组织ID。 启用模块时需要
- 接受值



### `--client-id`, `-c`



为Adobe IMS配置设置客户端ID。 启用模块时需要
- 接受值



### `--client-secret`, `-s`



为Adobe IMS配置设置客户端密钥。 启用模块时需要
- 接受值



### `--2fa`, `-t`



检查是否在Adobe Admin Console中为组织启用了2FA。 启用模块时需要
- 接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `admin:adobe-ims:info`

Adobe IMS模块配置信息

```bash
bin/magento admin:adobe-ims:info
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `admin:adobe-ims:status`

Adobe IMS模块的状态

```bash
bin/magento admin:adobe-ims:status
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `admin:user:create`

创建管理员

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--admin-user`

（必需）管理员用户
- 需要值


### `--admin-password`

（必需）管理员密码
- 需要值


### `--admin-email`

（必需）管理员电子邮件
- 需要值


### `--admin-firstname`

（必需）管理员名字
- 需要值


### `--admin-lastname`

（必需）管理员姓氏
- 需要值


### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `admin:user:unlock`

解锁管理员帐户

```bash
bin/magento admin:user:unlock <username>
```

<!-- app.name --> <!-- command.usage -->

### `username`

要解锁的管理员用户名
- 必需

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `app:config:dump`

创建应用程序转储

```bash
bin/magento app:config:dump [<config-types>...]
```

<!-- app.name --> <!-- command.usage -->

### `config-types`

配置类型的以空格分隔的列表，或者忽略转储所有 [范围、主题、系统、i18n]

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `app:config:import`

将数据从共享配置文件导入相应的数据存储

```bash
bin/magento app:config:import
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `app:config:status`

检查配置传播是否需要更新

```bash
bin/magento app:config:status
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `braintree:migrate`

从Magento1数据库迁移存储的信息卡

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--host`

主机名/IP。 端口是可选的
- 需要值


### `--dbname`

数据库名称
- 需要值


### `--username`

数据库用户名。 必须具有读取权限
- 需要值


### `--password`

密码
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cache:clean`

清除缓存类型

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

以空格分隔的高速缓存类型列表，或省略以应用于所有高速缓存类型。

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

添加或覆盖引导的参数
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cache:disable`

禁用缓存类型

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

以空格分隔的高速缓存类型列表，或省略以应用于所有高速缓存类型。

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

添加或覆盖引导的参数
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cache:enable`

启用缓存类型

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

以空格分隔的高速缓存类型列表，或省略以应用于所有高速缓存类型。

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

添加或覆盖引导的参数
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cache:flush`

刷新缓存类型使用的缓存存储

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

以空格分隔的高速缓存类型列表，或省略以应用于所有高速缓存类型。

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

添加或覆盖引导的参数
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cache:status`

检查缓存状态

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--bootstrap`

添加或覆盖引导的参数
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `catalog:images:resize`

创建调整大小的产品图像

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--async`, `-a`



在异步模式下调整图像大小
- 默认： `false`
- 不接受值


### `--skip_hidden_images`

请勿处理在产品页面中标记为隐藏的图像
- 默认： `false`
- 不接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `catalog:product:attributes:cleanup`

删除未使用的产品属性。

```bash
bin/magento catalog:product:attributes:cleanup
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cms:wysiwyg:restrict`

设置是强制用户HTML内容验证还是改为显示警告

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

<!-- app.name --> <!-- command.usage -->

### `restrict`

y\n
- 必需

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `config:sensitive:set`

设置敏感配置值

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

<!-- app.name --> <!-- command.usage -->

### `path`

配置路径，例如group/section/field_name
<!-- argument -->

### `value`

配置值
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--interactive`, `-i`



启用交互模式以设置所有敏感变量
- 默认： `false`
- 不接受值


### `--scope`

配置范围（如果未设置）使用“default”
- 默认： `default`
- 接受值


### `--scope-code`

配置的范围代码，默认为空字符串
- 默认：&quot;
- 接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `config:set`

更改系统配置

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

<!-- app.name --> <!-- command.usage -->

### `path`

格式为section/group/field_name的配置路径
- 必需

   <!-- argument -->

### `value`

配置值
- 必需

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--scope`

配置范围（默认、网站或存储）
- 默认： `default`
- 需要值


### `--scope-code`

范围代码（仅当范围不是“默认”时才需要）
- 需要值



### `--lock-env`, `-e`



阻止在管理员中进行修改的锁定值(将保存在app/etc/env.php中)
- 默认： `false`
- 不接受值



### `--lock-config`, `-c`



锁定值并与其他安装共享值，阻止在管理员中进行修改(将保存在app/etc/config.php中)
- 默认： `false`
- 不接受值



### `--lock`, `-l`



已弃用，请改用 — lock-env选项。
- 默认： `false`
- 不接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `config:show`

显示给定路径的配置值。 如果未指定路径，则将显示所有保存的值

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

配置路径，例如section_id/group_id/field_id
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--scope`

配置范围（如果未指定），则将使用“default”范围
- 默认： `default`
- 接受值


### `--scope-code`

范围代码（仅当范围不在时才需要） `default`)
- 默认：&quot;
- 接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cron:install`

为当前用户生成并安装crontab

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--force`, `-f`



强制安装任务
- 默认： `false`
- 不接受值



### `--non-optional`, `-d`



仅安装非可选（默认）任务
- 默认： `false`
- 不接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cron:remove`

从crontab中删除任务

```bash
bin/magento cron:remove
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `cron:run`

按计划运行作业

```bash
bin/magento cron:run [--group GROUP] [--bootstrap BOOTSTRAP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--group`

仅从指定的组运行作业
- 需要值


### `--bootstrap`

添加或覆盖引导的参数
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `customer:hash:upgrade`

根据最新算法升级客户的哈希

```bash
bin/magento customer:hash:upgrade
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `deploy:mode:set`

设置应用程序模式。

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

<!-- app.name --> <!-- command.usage -->

### `mode`

要设置的应用程序模式。 可用选项包括“开发人员”或“生产”
- 必需

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--skip-compilation`, `-s`



跳过静态内容（生成的代码、预处理的CSS以及pub/static/中的资产）的清除和重新生成
- 默认： `false`
- 不接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `deploy:mode:show`

显示当前应用程序模式。

```bash
bin/magento deploy:mode:show
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:di:info`

提供有关命令的依赖项注入配置的信息。

```bash
bin/magento dev:di:info <class>
```

<!-- app.name --> <!-- command.usage -->

### `class`

类名称
- 必需

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:email:newsletter-compatibility-check`

扫描新闻稿模板以了解潜在的变量使用兼容性问题

```bash
bin/magento dev:email:newsletter-compatibility-check
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:email:override-compatibility-check`

扫描电子邮件模板覆盖，以查找潜在的变量使用兼容性问题

```bash
bin/magento dev:email:override-compatibility-check
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:profiler:disable`

禁用探查器。

```bash
bin/magento dev:profiler:disable
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:profiler:enable`

启用探查器。

```bash
bin/magento dev:profiler:enable [<type>]
```

<!-- app.name --> <!-- command.usage -->

### `type`

探查器类型
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:query-log:disable`

禁用数据库查询日志记录

```bash
bin/magento dev:query-log:disable
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:query-log:enable`

启用数据库查询日志记录

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--include-all-queries`

记录所有查询。 [true\|false]
- 默认： `true`
- 接受值


### `--query-time-threshold`

查询时间阈值。
- 默认： `0.001`
- 接受值


### `--include-call-stack`

包括调用堆栈。 [true\|false]
- 默认： `true`
- 接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:source-theme:deploy`

收集并发布主题的源文件。

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

<!-- app.name --> <!-- command.usage -->

### `file`

要预处理的文件（文件应指定为不带扩展名）
- 默认： `css/styles-mcss/styles-l`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

源文件类型： [减少]
- 默认： `less`
- 需要值


### `--locale`

区域设置： [en_US]
- 默认： `en_US`
- 需要值


### `--area`

区域： [前端\|adminhtml]
- 默认： `frontend`
- 需要值


### `--theme`

主题： [供应商/主题]
- 默认： `Magento/luma`
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:template-hints:disable`

禁用前端模板提示。 可能需要缓存刷新。

```bash
bin/magento dev:template-hints:disable
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:template-hints:enable`

启用前端模板提示。 可能需要缓存刷新。

```bash
bin/magento dev:template-hints:enable
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:template-hints:status`

显示前端模板提示状态。

```bash
bin/magento dev:template-hints:status
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:tests:run`

运行测试

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

<!-- app.name --> <!-- command.usage -->

### `type`

要运行的测试类型。 可用类型：全部，单元，集成，全部集成，静态，静态，全部，完整性，旧版，默认
- 默认： `default`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--arguments`, `-c`



PHPUnit的其他参数。 示例：&quot;-c&#39;—filter=MyTest&#39;&quot;（无空格）
- 默认：&quot;
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:urn-catalog:generate`

为IDE生成URN到*.xsd映射的目录以突出显示xml。

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

<!-- app.name --> <!-- command.usage -->

### `path`

用于输出目录的文件路径。 对于PhpStorm，请使用。idea/misc.xml
- 必需

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--ide`

将在其中生成目录的格式。 支持： [弗斯托姆、弗斯科德]
- 默认： `phpstorm`
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `dev:xml:convert`

使用XSL样式表转换XML文件

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

<!-- app.name --> <!-- command.usage -->

### `xml-file`

要转换的XML文件的路径
- 必需

   <!-- argument -->

### `processor`

要应用于XML文件的XSL样式表的路径
- 必需

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--overwrite`, `-o`



覆盖XML文件
- 默认： `false`
- 不接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `downloadable:domains:add`

将域添加到可下载的域白名单中

```bash
bin/magento downloadable:domains:add [<domains>...]
```

<!-- app.name --> <!-- command.usage -->

### `domains`

域名

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `downloadable:domains:remove`

从可下载的域白名单中删除域

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

<!-- app.name --> <!-- command.usage -->

### `domains`

域名

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `downloadable:domains:show`

显示可下载域白名单

```bash
bin/magento downloadable:domains:show
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `encryption:payment-data:update`

使用最新加密密码重新加密加密的信用卡数据。

```bash
bin/magento encryption:payment-data:update
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `i18n:collect-phrases`

发现代码库中的短语

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

<!-- app.name --> <!-- command.usage -->

### `directory`

要解析的目录路径。 如果设置了 — magento标记，则不需要
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--output`, `-o`



输出文件的路径（包括文件名）。 未指定文件时，默认为stdout。
- 需要值



### `--magento`, `-m`



使用 — magento参数解析当前Magento代码库。 如果指定了目录，请忽略参数。
- 默认： `false`
- 不接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `i18n:pack`

保存语言包

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

<!-- app.name --> <!-- command.usage -->

### `source`

包含翻译的源字典文件的路径
- 必需

   <!-- argument -->

### `locale`

字典的目标区域设置，例如“de_DE”
- 必需

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--mode`, `-m`



字典的保存模式 — “replace” — 将语言包替换为新的语言包 — “merge” — 合并语言包，默认情况下为“replace”
- 默认： `replace`
- 需要值



### `--allow-duplicates`, `-d`



使用 — allow-duplicates参数可保存转换的重复项。 否则，请忽略参数。
- 默认： `false`
- 不接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `i18n:uninstall`

卸载语言包

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

<!-- app.name --> <!-- command.usage -->

### `package`

语言包名称

- 默认： `[]`
- 必需

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--backup-code`, `-b`



备份代码和配置文件（不包括临时文件）
- 默认： `false`
- 不接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `indexer:info`

显示允许的索引器

```bash
bin/magento indexer:info
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `indexer:reindex`

重新索引数据

```bash
bin/magento indexer:reindex [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

索引类型的空格分隔列表，或省略以应用于所有索引。

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `indexer:reset`

将索引器状态重置为无效

```bash
bin/magento indexer:reset [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

索引类型的空格分隔列表，或省略以应用于所有索引。

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `indexer:set-dimensions-mode`

设置索引器Dimension模式

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

<!-- app.name --> <!-- command.usage -->

### `indexer`

索引器名称 [catalog_product_price]
<!-- argument -->

### `mode`

索引器维模式catalog_product_price none，website，customer_group，website_and_customer_group
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `indexer:set-mode`

设置索引模式类型

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

<!-- app.name --> <!-- command.usage -->

### `mode`

索引器模式类型 [实时|计划]
<!-- argument -->

### `index`

索引类型的空格分隔列表，或省略以应用于所有索引。

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `indexer:show-dimensions-mode`

显示索引器Dimension模式

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

<!-- app.name --> <!-- command.usage -->

### `indexer`

索引类型的空格分隔列表，或省略以应用于所有索引(catalog_product_price)

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `indexer:show-mode`

显示索引模式

```bash
bin/magento indexer:show-mode [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

索引类型的空格分隔列表，或省略以应用于所有索引。

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `indexer:status`

显示索引器的状态

```bash
bin/magento indexer:status [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

索引类型的空格分隔列表，或省略以应用于所有索引。

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `info:adminuri`

显示Magento管理员URI

```bash
bin/magento info:adminuri
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `info:backups:list`

打印可用备份文件的列表

```bash
bin/magento info:backups:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `info:currency:list`

显示可用货币列表

```bash
bin/magento info:currency:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `info:dependencies:show-framework`

显示对Magento框架的依赖项数

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



报表文件名
- 默认： `framework-dependencies.csv`
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `info:dependencies:show-modules`

显示模块之间的依赖关系数

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



报表文件名
- 默认： `modules-dependencies.csv`
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `info:dependencies:show-modules-circular`

显示模块之间的循环依赖关系数

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



报表文件名
- 默认： `modules-circular-dependencies.csv`
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `info:language:list`

显示可用语言区域设置列表

```bash
bin/magento info:language:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `info:timezone:list`

显示可用时区列表

```bash
bin/magento info:timezone:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `inventory:reservation:create-compensations`

通过提供的报酬参数创建保留

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

<!-- app.name --> <!-- command.usage -->

### `compensations`

格式为“”的报酬参数列表&lt;order_increment_id>:&lt;sku>:&lt;quantity>:&lt;stock-id>&quot;

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--raw`, `-r`



原始输出
- 默认： `false`
- 不接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `inventory:reservation:list-inconsistencies`

显示所有订单和产品，且符合可售数量不一致

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--complete-orders`, `-c`



仅显示完整订单的不一致情况
- 默认： `false`
- 不接受值



### `--incomplete-orders`, `-i`



仅显示未完成订单的不一致情况
- 默认： `false`
- 不接受值



### `--bunch-size`, `-b`



定义一次加载的订单数
- 默认： `50`
- 接受值



### `--raw`, `-r`



原始输出
- 默认： `false`
- 不接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `inventory-geonames:import`

为源选择算法下载和导入地理名称

```bash
bin/magento inventory-geonames:import <countries>...
```

<!-- app.name --> <!-- command.usage -->

### `countries`

要导入的国家/地区代码列表

- 默认： `[]`
- 必需

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `maintenance:allow-ips`

设置维护模式豁免IP

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

<!-- app.name --> <!-- command.usage -->

### `ip`

允许的IP地址

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--none`

清除允许的IP地址
- 默认： `false`
- 不接受值


### `--add`

将IP地址添加到现有列表
- 默认： `false`
- 不接受值


### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `maintenance:disable`

禁用维护模式

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--ip`

允许的IP地址（使用“无”清除允许的IP列表）
- 默认： `[]`
- 需要值


### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `maintenance:enable`

启用维护模式

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--ip`

允许的IP地址（使用“无”清除允许的IP列表）
- 默认： `[]`
- 需要值


### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `maintenance:status`

显示维护模式状态

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `media-content:sync`

将内容与资产同步

```bash
bin/magento media-content:sync
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `media-gallery:sync`

同步数据库中的媒体存储和媒体资产

```bash
bin/magento media-gallery:sync
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `module:config:status`

检查“app/etc/config.php”文件和报告中的模块配置是否为最新

```bash
bin/magento module:config:status
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `module:disable`

禁用指定的模块

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

<!-- app.name --> <!-- command.usage -->

### `module`

模块的名称

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--force`, `-f`



绕过依赖项检查
- 默认： `false`
- 不接受值


### `--all`

禁用所有模块
- 默认： `false`
- 不接受值



### `--clear-static-content`, `-c`



清除生成的静态视图文件。 如果模块具有静态视图文件，则需要
- 默认： `false`
- 不接受值


### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `module:enable`

启用指定的模块

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

<!-- app.name --> <!-- command.usage -->

### `module`

模块的名称

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--force`, `-f`



绕过依赖项检查
- 默认： `false`
- 不接受值


### `--all`

启用所有模块
- 默认： `false`
- 不接受值



### `--clear-static-content`, `-c`



清除生成的静态视图文件。 如果模块具有静态视图文件，则需要
- 默认： `false`
- 不接受值


### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `module:status`

显示模块的状态

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

<!-- app.name --> <!-- command.usage -->

### `module-names`

可选模块名称

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--enabled`

仅打印已启用的模块
- 默认： `false`
- 不接受值


### `--disabled`

仅打印禁用的模块
- 默认： `false`
- 不接受值


### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `module:uninstall`

卸载由编辑器安装的模块

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

<!-- app.name --> <!-- command.usage -->

### `module`

模块的名称

- 默认： `[]`
- 必需

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--remove-data`, `-r`



删除模块安装的数据
- 默认： `false`
- 不接受值


### `--backup-code`

备份代码和配置文件（不包括临时文件）
- 默认： `false`
- 不接受值


### `--backup-media`

进行媒体备份
- 默认： `false`
- 不接受值


### `--backup-db`

完成数据库备份
- 默认： `false`
- 不接受值


### `--non-composer`

所有将在此过去的模块都将基于非编辑器
- 默认： `false`
- 不接受值



### `--clear-static-content`, `-c`



清除生成的静态视图文件。 如果模块具有静态视图文件，则需要
- 默认： `false`
- 不接受值


### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `newrelic:create:deploy-marker`

检查部署队列中的条目，并创建相应的部署标记。

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

<!-- app.name --> <!-- command.usage -->

### `message`

部署消息？
- 必需

   <!-- argument -->

### `change_log`

更改日志？
- 必需

   <!-- argument -->

### `user`

部署用户
<!-- argument -->

### `revision`

修订
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `queue:consumers:list`

MessageQueue使用者列表

```bash
bin/magento queue:consumers:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `queue:consumers:start`

启动MessageQueue使用者

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```

<!-- app.name --> <!-- command.usage -->

### `consumer`

要启动的消费者的名称。
- 必需

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--max-messages`

用户在处理结束前要处理的消息数。 如果未指定 — 在处理所有排队的消息后终止。
- 需要值


### `--batch-size`

每批消息的数量。 仅适用于批量客户。
- 需要值


### `--area-code`

首选区域（全局、管理员等）默认为全局。
- 需要值


### `--single-thread`

此选项可防止同时运行一个使用者的多个副本。
- 默认： `false`
- 不接受值


### `--multi-process`

每个消费者的进程数。
- 接受值


### `--pid-file-path`

用于保存PID的文件路径（此选项已弃用，请改用单线程）
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `remote-storage:sync`

将媒体文件与远程存储同步。

```bash
bin/magento remote-storage:sync
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `sampledata:deploy`

为基于编辑器的Magento安装部署示例数据模块

```bash
bin/magento sampledata:deploy [--no-update]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-update`

在不执行编辑器更新的情况下更新composer.json
- 默认： `false`
- 不接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `sampledata:remove`

从composer.json中删除所有示例数据包

```bash
bin/magento sampledata:remove [--no-update]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-update`

在不执行编辑器更新的情况下更新composer.json
- 默认： `false`
- 不接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `sampledata:reset`

重置所有示例数据模块以重新安装

```bash
bin/magento sampledata:reset
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `security:recaptcha:disable-for-user-forgot-password`

为管理员用户禁用reCAPTCHA忘记密码表单

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `security:recaptcha:disable-for-user-login`

为管理员用户登录表单禁用reCAPTCHA

```bash
bin/magento security:recaptcha:disable-for-user-login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `security:tfa:google:set-secret`

设置用于Google OTP生成的密钥。

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

<!-- app.name --> <!-- command.usage -->

### `user`

用户名
- 必需

   <!-- argument -->

### `secret`

密码
- 必需

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `security:tfa:providers`

列出所有可用的提供程序

```bash
bin/magento security:tfa:providers
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `security:tfa:reset`

为一个用户重置配置

```bash
bin/magento security:tfa:reset <user> <provider>
```

<!-- app.name --> <!-- command.usage -->

### `user`

用户名
- 必需

   <!-- argument -->

### `provider`

提供程序代码
- 必需

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:backup`

备份Magento应用程序代码库、媒体和数据库

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--code`

备份代码和配置文件（不包括临时文件）
- 默认： `false`
- 不接受值


### `--media`

进行媒体备份
- 默认： `false`
- 不接受值


### `--db`

完成数据库备份
- 默认： `false`
- 不接受值


### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:config:set`

创建或修改部署配置

```bash
bin/magento setup:config:set [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--backend-frontname`

后端Frontname（如果缺少，将自动生成）
- 需要值


### `--enable-debug-logging`

启用调试日志记录
- 需要值


### `--enable-syslog-logging`

启用Syslog日志记录
- 需要值


### `--remote-storage-driver`

远程存储驱动程序
- 需要值


### `--remote-storage-prefix`

远程存储前缀
- 默认：&quot;
- 需要值


### `--remote-storage-endpoint`

远程存储端点
- 需要值


### `--remote-storage-bucket`

远程存储段
- 需要值


### `--remote-storage-region`

远程存储区域
- 需要值


### `--remote-storage-key`

远程存储访问密钥
- 默认：&quot;
- 需要值


### `--remote-storage-secret`

远程存储密钥
- 默认：&quot;
- 需要值


### `--remote-storage-path-style`

远程存储路径样式
- 默认： `0`
- 需要值


### `--amqp-host`

Amqp服务器主机
- 默认：&quot;
- 需要值


### `--amqp-port`

Amqp服务器端口
- 默认： `5672`
- 需要值


### `--amqp-user`

Amqp服务器用户名
- 默认：&quot;
- 需要值


### `--amqp-password`

Amqp服务器密码
- 默认：&quot;
- 需要值


### `--amqp-virtualhost`

Amqp virtualhost
- 默认： `/`
- 需要值


### `--amqp-ssl`

Amqp SSL
- 默认：&quot;
- 需要值


### `--amqp-ssl-options`

Amqp SSL选项(JSON)
- 默认：&quot;
- 需要值


### `--consumers-wait-for-messages`

消费者是否应等待队列中的消息？ 1 — 是，0 — 否
- 需要值


### `--queue-default-connection`

消息队列默认连接。 可以是“db”、“amqp”或自定义队列系统。必须安装和配置队列系统，否则无法正确处理消息。
- 需要值


### `--key`

加密密钥
- 需要值


### `--db-host`

数据库服务器主机
- 需要值


### `--db-name`

数据库名称
- 需要值


### `--db-user`

数据库服务器用户名
- 需要值


### `--db-engine`

数据库服务器引擎
- 需要值


### `--db-password`

数据库服务器密码
- 需要值


### `--db-prefix`

数据库表前缀
- 需要值


### `--db-model`

数据库类型
- 需要值


### `--db-init-statements`

数据库初始命令集
- 需要值



### `--skip-db-validation`, `-s`



如果已指定，则会跳过数据库连接验证
- 默认： `false`
- 不接受值


### `--http-cache-hosts`

http缓存主机
- 需要值


### `--db-ssl-key`

客户端密钥文件的完整路径，以通过SSL建立数据库连接
- 默认：&quot;
- 需要值


### `--db-ssl-cert`

客户端证书文件的完整路径，以通过SSL建立数据库连接
- 默认：&quot;
- 需要值


### `--db-ssl-ca`

服务器证书文件的完整路径，以通过SSL建立数据库连接
- 默认：&quot;
- 需要值


### `--db-ssl-verify`

验证服务器认证
- 默认： `false`
- 不接受值


### `--session-save`

会话保存处理程序
- 需要值


### `--session-save-redis-host`

完全限定的主机名、 IP地址或绝对路径（如果使用UNIX套接字）
- 需要值


### `--session-save-redis-port`

Redis服务器侦听端口
- 需要值


### `--session-save-redis-password`

密文服务器密码
- 需要值


### `--session-save-redis-timeout`

连接超时（以秒为单位）
- 需要值


### `--session-save-redis-persistent-id`

用于启用永久连接的唯一字符串
- 需要值


### `--session-save-redis-db`

Redis数据库编号
- 需要值


### `--session-save-redis-compression-threshold`

Redis压缩阈值
- 需要值


### `--session-save-redis-compression-lib`

Redis压缩库。 值：gzip（默认）、lzf、lz4、snappy
- 需要值


### `--session-save-redis-log-level`

红色日志级别。 值：0（最少详细）到7（最详细）
- 需要值


### `--session-save-redis-max-concurrency`

可等待一个会话锁定的最大进程数
- 需要值


### `--session-save-redis-break-after-frontend`

尝试为前端会话断开锁定之前需要等待的秒数
- 需要值


### `--session-save-redis-break-after-adminhtml`

尝试为管理员会话断开锁定之前需要等待的秒数
- 需要值


### `--session-save-redis-first-lifetime`

首次写入时非机器人会话的生命周期（以秒为单位）（使用0表示禁用）
- 需要值


### `--session-save-redis-bot-first-lifetime`

首次写入时的机器人会话的生命周期（以秒为单位）（使用0禁用）
- 需要值


### `--session-save-redis-bot-lifetime`

后续写入时机器人的会话生命周期（使用0禁用）
- 需要值


### `--session-save-redis-disable-locking`

雷迪斯禁用锁定。 值：false（默认），true
- 需要值


### `--session-save-redis-min-lifetime`

Redis最小会话生命周期，以秒为单位
- 需要值


### `--session-save-redis-max-lifetime`

Redis最大会话生命周期，以秒为单位
- 需要值


### `--session-save-redis-sentinel-master`

雷迪斯哨兵主控
- 需要值


### `--session-save-redis-sentinel-servers`

Redis Sentinel服务器，以逗号分隔
- 需要值


### `--session-save-redis-sentinel-verify-master`

雷迪斯哨兵确认主控。 值：false（默认）， true
- 需要值


### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel连接重试。
- 需要值


### `--cache-backend`

默认缓存处理程序
- 需要值


### `--cache-backend-redis-server`

Redis服务器
- 需要值


### `--cache-backend-redis-db`

高速缓存的数据库编号
- 需要值


### `--cache-backend-redis-port`

Redis服务器侦听端口
- 需要值


### `--cache-backend-redis-password`

密文服务器密码
- 需要值


### `--cache-backend-redis-compress-data`

设置为0可禁用压缩（默认为1，已启用）
- 需要值


### `--cache-backend-redis-compression-lib`

要使用的压缩库 [snappy，lzf，l4z，zstd，gzip] （留空以自动确定）
- 需要值


### `--cache-id-prefix`

缓存键的ID前缀
- 需要值


### `--allow-parallel-generation`

允许以非阻塞方式生成缓存
- 默认： `false`
- 不接受值


### `--page-cache`

默认缓存处理程序
- 需要值


### `--page-cache-redis-server`

Redis服务器
- 需要值


### `--page-cache-redis-db`

高速缓存的数据库编号
- 需要值


### `--page-cache-redis-port`

Redis服务器侦听端口
- 需要值


### `--page-cache-redis-password`

密文服务器密码
- 需要值


### `--page-cache-redis-compress-data`

设置为1可压缩完整页面缓存（使用0可禁用）
- 需要值


### `--page-cache-redis-compression-lib`

要使用的压缩库 [snappy，lzf，l4z，zstd，gzip] （留空以自动确定）
- 需要值


### `--page-cache-id-prefix`

缓存键的ID前缀
- 需要值


### `--lock-provider`

锁定提供程序名称
- 需要值


### `--lock-db-prefix`

安装特定的锁定前缀以避免锁定冲突
- 需要值


### `--lock-zookeeper-host`

用于连接到Zookeeper群集的主机和端口。 例如：127.0.0.1:2181
- 需要值


### `--lock-zookeeper-path`

Zookeeper将保存锁的路径。 默认路径为：/magento/locks
- 需要值


### `--lock-file-path`

保存文件锁定的路径。
- 需要值


### `--document-root-is-pub`

显示为Pub的标志位于根上，只能为true或false
- 需要值


### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:db-data:upgrade`

在数据库中安装和升级数据

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:db-declaration:generate-patch`

生成修补程序并将其放在特定文件夹中。

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

<!-- app.name --> <!-- command.usage -->

### `module`

模块名称
- 必需

   <!-- argument -->

### `patch`

修补程序名称
- 必需

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--revertable`

检查修补程序是否可还原。
- 默认： `false`
- 接受值


### `--type`

了解应生成哪种类型的修补程序。 可用值： `data`, `schema`.
- 默认： `data`
- 接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:db-declaration:generate-whitelist`

生成允许由声明安装程序编辑的表和列的白名单

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--module-name`

将在其中生成白名单的模块的名称
- 默认： `all`
- 接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:db-schema:upgrade`

安装和升级数据库架构

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--convert-old-scripts`

允许将旧脚本(InstallSchema、UpgradeSchema)转换为db_schema.xml格式
- 默认： `false`
- 接受值


### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:db:status`

检查数据库架构或数据是否需要升级

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:di:compile`

生成DI配置和所有可自动生成的缺失类

```bash
bin/magento setup:di:compile
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:install`

安装Magento应用程序

```bash
bin/magento setup:install [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--backend-frontname`

后端Frontname（如果缺少，将自动生成）
- 需要值


### `--enable-debug-logging`

启用调试日志记录
- 需要值


### `--enable-syslog-logging`

启用Syslog日志记录
- 需要值


### `--remote-storage-driver`

远程存储驱动程序
- 需要值


### `--remote-storage-prefix`

远程存储前缀
- 默认：&quot;
- 需要值


### `--remote-storage-endpoint`

远程存储端点
- 需要值


### `--remote-storage-bucket`

远程存储段
- 需要值


### `--remote-storage-region`

远程存储区域
- 需要值


### `--remote-storage-key`

远程存储访问密钥
- 默认：&quot;
- 需要值


### `--remote-storage-secret`

远程存储密钥
- 默认：&quot;
- 需要值


### `--remote-storage-path-style`

远程存储路径样式
- 默认： `0`
- 需要值


### `--amqp-host`

Amqp服务器主机
- 默认：&quot;
- 需要值


### `--amqp-port`

Amqp服务器端口
- 默认： `5672`
- 需要值


### `--amqp-user`

Amqp服务器用户名
- 默认：&quot;
- 需要值


### `--amqp-password`

Amqp服务器密码
- 默认：&quot;
- 需要值


### `--amqp-virtualhost`

Amqp virtualhost
- 默认： `/`
- 需要值


### `--amqp-ssl`

Amqp SSL
- 默认：&quot;
- 需要值


### `--amqp-ssl-options`

Amqp SSL选项(JSON)
- 默认：&quot;
- 需要值


### `--consumers-wait-for-messages`

消费者是否应等待队列中的消息？ 1 — 是，0 — 否
- 需要值


### `--queue-default-connection`

消息队列默认连接。 可以是“db”、“amqp”或自定义队列系统。必须安装和配置队列系统，否则无法正确处理消息。
- 需要值


### `--key`

加密密钥
- 需要值


### `--db-host`

数据库服务器主机
- 需要值


### `--db-name`

数据库名称
- 需要值


### `--db-user`

数据库服务器用户名
- 需要值


### `--db-engine`

数据库服务器引擎
- 需要值


### `--db-password`

数据库服务器密码
- 需要值


### `--db-prefix`

数据库表前缀
- 需要值


### `--db-model`

数据库类型
- 需要值


### `--db-init-statements`

数据库初始命令集
- 需要值



### `--skip-db-validation`, `-s`



如果已指定，则会跳过数据库连接验证
- 默认： `false`
- 不接受值


### `--http-cache-hosts`

http缓存主机
- 需要值


### `--db-ssl-key`

客户端密钥文件的完整路径，以通过SSL建立数据库连接
- 默认：&quot;
- 需要值


### `--db-ssl-cert`

客户端证书文件的完整路径，以通过SSL建立数据库连接
- 默认：&quot;
- 需要值


### `--db-ssl-ca`

服务器证书文件的完整路径，以通过SSL建立数据库连接
- 默认：&quot;
- 需要值


### `--db-ssl-verify`

验证服务器认证
- 默认： `false`
- 不接受值


### `--session-save`

会话保存处理程序
- 需要值


### `--session-save-redis-host`

完全限定的主机名、 IP地址或绝对路径（如果使用UNIX套接字）
- 需要值


### `--session-save-redis-port`

Redis服务器侦听端口
- 需要值


### `--session-save-redis-password`

密文服务器密码
- 需要值


### `--session-save-redis-timeout`

连接超时（以秒为单位）
- 需要值


### `--session-save-redis-persistent-id`

用于启用永久连接的唯一字符串
- 需要值


### `--session-save-redis-db`

Redis数据库编号
- 需要值


### `--session-save-redis-compression-threshold`

Redis压缩阈值
- 需要值


### `--session-save-redis-compression-lib`

Redis压缩库。 值：gzip（默认）、lzf、lz4、snappy
- 需要值


### `--session-save-redis-log-level`

红色日志级别。 值：0（最少详细）到7（最详细）
- 需要值


### `--session-save-redis-max-concurrency`

可等待一个会话锁定的最大进程数
- 需要值


### `--session-save-redis-break-after-frontend`

尝试为前端会话断开锁定之前需要等待的秒数
- 需要值


### `--session-save-redis-break-after-adminhtml`

尝试为管理员会话断开锁定之前需要等待的秒数
- 需要值


### `--session-save-redis-first-lifetime`

首次写入时非机器人会话的生命周期（以秒为单位）（使用0表示禁用）
- 需要值


### `--session-save-redis-bot-first-lifetime`

首次写入时的机器人会话的生命周期（以秒为单位）（使用0禁用）
- 需要值


### `--session-save-redis-bot-lifetime`

后续写入时机器人的会话生命周期（使用0禁用）
- 需要值


### `--session-save-redis-disable-locking`

雷迪斯禁用锁定。 值：false（默认），true
- 需要值


### `--session-save-redis-min-lifetime`

Redis最小会话生命周期，以秒为单位
- 需要值


### `--session-save-redis-max-lifetime`

Redis最大会话生命周期，以秒为单位
- 需要值


### `--session-save-redis-sentinel-master`

雷迪斯哨兵主控
- 需要值


### `--session-save-redis-sentinel-servers`

Redis Sentinel服务器，以逗号分隔
- 需要值


### `--session-save-redis-sentinel-verify-master`

雷迪斯哨兵确认主控。 值：false（默认）， true
- 需要值


### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel连接重试。
- 需要值


### `--cache-backend`

默认缓存处理程序
- 需要值


### `--cache-backend-redis-server`

Redis服务器
- 需要值


### `--cache-backend-redis-db`

高速缓存的数据库编号
- 需要值


### `--cache-backend-redis-port`

Redis服务器侦听端口
- 需要值


### `--cache-backend-redis-password`

密文服务器密码
- 需要值


### `--cache-backend-redis-compress-data`

设置为0可禁用压缩（默认为1，已启用）
- 需要值


### `--cache-backend-redis-compression-lib`

要使用的压缩库 [snappy，lzf，l4z，zstd，gzip] （留空以自动确定）
- 需要值


### `--cache-id-prefix`

缓存键的ID前缀
- 需要值


### `--allow-parallel-generation`

允许以非阻塞方式生成缓存
- 默认： `false`
- 不接受值


### `--page-cache`

默认缓存处理程序
- 需要值


### `--page-cache-redis-server`

Redis服务器
- 需要值


### `--page-cache-redis-db`

高速缓存的数据库编号
- 需要值


### `--page-cache-redis-port`

Redis服务器侦听端口
- 需要值


### `--page-cache-redis-password`

密文服务器密码
- 需要值


### `--page-cache-redis-compress-data`

设置为1可压缩完整页面缓存（使用0可禁用）
- 需要值


### `--page-cache-redis-compression-lib`

要使用的压缩库 [snappy，lzf，l4z，zstd，gzip] （留空以自动确定）
- 需要值


### `--page-cache-id-prefix`

缓存键的ID前缀
- 需要值


### `--lock-provider`

锁定提供程序名称
- 需要值


### `--lock-db-prefix`

安装特定的锁定前缀以避免锁定冲突
- 需要值


### `--lock-zookeeper-host`

用于连接到Zookeeper群集的主机和端口。 例如：127.0.0.1:2181
- 需要值


### `--lock-zookeeper-path`

Zookeeper将保存锁的路径。 默认路径为：/magento/locks
- 需要值


### `--lock-file-path`

保存文件锁定的路径。
- 需要值


### `--document-root-is-pub`

显示为Pub的标志位于根上，只能为true或false
- 需要值


### `--base-url`

应在上提供商店的URL。 已弃用，请使用config:set中包含路径web/unsecure/base_url
- 需要值


### `--language`

默认语言代码。 已弃用，请使用config:set中包含路径常规/区域设置/代码
- 需要值


### `--timezone`

默认时区代码。 已弃用，请使用config:set（包含路径常规/区域设置/时区）
- 需要值


### `--currency`

默认货币代码。 已弃用，请使用config:set with path currency/options/base、currency/options/default和currency/options/allow
- 需要值


### `--use-rewrites`

使用重写。 已弃用，请使用config:set中包含路径web/seo/use_rewrites
- 需要值


### `--use-secure`

使用安全URL。 仅当SSL可用时，才启用此选项。 已弃用，请使用config:set（路径为web/secure/use_in_frontend）
- 需要值


### `--base-url-secure`

SSL连接的基本URL。 已弃用，请使用config:set与路径web/secure/base_url一起使用
- 需要值


### `--use-secure-admin`

使用SSL运行管理界面。 已弃用，请使用config:set并路径web/secure/use_in_adminhtml
- 需要值


### `--admin-use-security-key`

是否在Magento管理URL和表单中使用“安全密钥”功能。 已弃用，请使用config:set和路径admin/security/use_form_key
- 需要值


### `--admin-user`

管理员用户
- 接受值


### `--admin-password`

管理员密码
- 接受值


### `--admin-email`

管理员电子邮件
- 接受值


### `--admin-firstname`

管理员名字
- 接受值


### `--admin-lastname`

管理员姓氏
- 接受值


### `--search-engine`

搜索引擎。 值：elasticsearch5, elasticsearch6, elasticsearch7
- 需要值


### `--elasticsearch-host`

Elasticsearch服务器主机。
- 需要值


### `--elasticsearch-port`

Elasticsearch服务器端口。
- 需要值


### `--elasticsearch-enable-auth`

设置为1可启用身份验证。 （默认为0，禁用）
- 需要值


### `--elasticsearch-username`

Elasticsearch用户名。 仅在启用HTTP身份验证时适用
- 需要值


### `--elasticsearch-password`

Elasticsearch密码。 仅在启用HTTP身份验证时适用
- 需要值


### `--elasticsearch-index-prefix`

Elasticsearch索引前缀。
- 需要值


### `--elasticsearch-timeout`

Elasticsearch服务器超时。
- 需要值


### `--cleanup-database`

在安装前清理数据库
- 默认： `false`
- 不接受值


### `--sales-order-increment-prefix`

销售订单编号前缀
- 需要值


### `--use-sample-data`

使用示例数据
- 默认： `false`
- 不接受值


### `--enable-modules`

以逗号分隔的模块名称列表。 必须在安装过程中包含该参数。 可用的魔术参数“all”。
- 接受值


### `--disable-modules`

以逗号分隔的模块名称列表。 在安装过程中必须避免出现这种情况。 可用的魔术参数“all”。
- 接受值


### `--convert-old-scripts`

允许将旧脚本(InstallSchema、UpgradeSchema)转换为db_schema.xml格式
- 默认： `false`
- 接受值



### `--interactive`, `-i`



交互式Magento安装
- 默认： `false`
- 不接受值


### `--safe-mode`

在破坏性操作（如删除列）上安全安装包含转储的Magento
- 接受值


### `--data-restore`

从转储中恢复已删除的数据
- 接受值


### `--dry-run`

Magento安装将以干式运行模式运行
- 默认： `false`
- 接受值


### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:performance:generate-fixtures`

生成夹具

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

<!-- app.name --> <!-- command.usage -->

### `profile`

配置文件配置文件的路径
- 必需

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--skip-reindex`, `-s`



跳过重新索引
- 默认： `false`
- 不接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:rollback`

回滚Magento应用程序代码库、媒体和数据库

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--code-file`, `-c`



var/backups中代码备份文件的基名
- 需要值



### `--media-file`, `-m`



var/backups中介质备份文件的基名
- 需要值



### `--db-file`, `-d`



var/backups中数据库备份文件的基名
- 需要值


### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:static-content:deploy`

部署静态视图文件

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

<!-- app.name --> <!-- command.usage -->

### `languages`

输出静态视图文件的ISO-639语言代码的空格分隔列表。

- 默认： `[]`

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--force`, `-f`



以任何模式部署文件。
- 默认： `false`
- 不接受值



### `--strategy`, `-s`



使用指定的策略部署文件。
- 默认： `quick`
- 接受值



### `--area`, `-a`



仅为指定区域生成文件。
- 默认： `all`
- 接受多个值


### `--exclude-area`

请勿为指定区域生成文件。
- 默认： `none`
- 接受多个值



### `--theme`, `-t`



仅为指定的主题生成静态视图文件。
- 默认： `all`
- 接受多个值


### `--exclude-theme`

请勿为指定的主题生成文件。
- 默认： `none`
- 接受多个值



### `--language`, `-l`



仅为指定语言生成文件。
- 默认： `all`
- 接受多个值


### `--exclude-language`

请勿为指定语言生成文件。
- 默认： `none`
- 接受多个值



### `--jobs`, `-j`



使用指定数量的作业启用并行处理。
- 默认： `0`
- 接受值


### `--max-execution-time`

部署静态进程的预期最长执行时间（以秒为单位）。
- 默认： `900`
- 接受值


### `--symlink-locale`

为这些区域设置的文件创建符号链接，这些文件将传递用于部署，但没有自定义设置。
- 默认： `false`
- 不接受值


### `--content-version`

如果在多个节点上运行部署，则可以使用静态内容的自定义版本，以确保静态内容版本相同且缓存工作正常。
- 需要值


### `--refresh-content-version-only`

刷新静态内容的版本只能用于刷新浏览器缓存和CDN缓存中的静态内容。
- 默认： `false`
- 不接受值


### `--no-javascript`

请勿部署JavaScript文件。
- 默认： `false`
- 不接受值


### `--no-js-bundle`

请勿部署JavaScript包文件。
- 默认： `false`
- 不接受值


### `--no-css`

请勿部署CSS文件。
- 默认： `false`
- 不接受值


### `--no-less`

请勿部署LESS文件。
- 默认： `false`
- 不接受值


### `--no-images`

请勿部署图像。
- 默认： `false`
- 不接受值


### `--no-fonts`

请勿部署字体文件。
- 默认： `false`
- 不接受值


### `--no-html`

请勿部署HTML文件。
- 默认： `false`
- 不接受值


### `--no-misc`

请勿部署其他类型的文件（.md、.jbf、.csv等）。
- 默认： `false`
- 不接受值


### `--no-html-minify`

请勿缩小HTML文件。
- 默认： `false`
- 不接受值


### `--no-parent`

请勿编译父主题。 仅在快速和标准策略中受支持。
- 默认： `false`
- 不接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:store-config:set`

安装存储配置。 自2.2.0起已弃用。请改用config:set

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--base-url`

应在上提供商店的URL。 已弃用，请使用config:set中包含路径web/unsecure/base_url
- 需要值


### `--language`

默认语言代码。 已弃用，请使用config:set中包含路径常规/区域设置/代码
- 需要值


### `--timezone`

默认时区代码。 已弃用，请使用config:set（包含路径常规/区域设置/时区）
- 需要值


### `--currency`

默认货币代码。 已弃用，请使用config:set with path currency/options/base、currency/options/default和currency/options/allow
- 需要值


### `--use-rewrites`

使用重写。 已弃用，请使用config:set中包含路径web/seo/use_rewrites
- 需要值


### `--use-secure`

使用安全URL。 仅当SSL可用时，才启用此选项。 已弃用，请使用config:set（路径为web/secure/use_in_frontend）
- 需要值


### `--base-url-secure`

SSL连接的基本URL。 已弃用，请使用config:set与路径web/secure/base_url一起使用
- 需要值


### `--use-secure-admin`

使用SSL运行管理界面。 已弃用，请使用config:set并路径web/secure/use_in_adminhtml
- 需要值


### `--admin-use-security-key`

是否在Magento管理URL和表单中使用“安全密钥”功能。 已弃用，请使用config:set和路径admin/security/use_form_key
- 需要值


### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:uninstall`

卸载Magento应用程序

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `setup:upgrade`

升级Magento应用程序、数据库数据和模式

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--keep-generated`

阻止删除生成的文件。 除了部署到生产外，我们不鼓励使用此选项。 有关详细信息，请咨询系统集成商或管理员。
- 默认： `false`
- 不接受值


### `--convert-old-scripts`

允许将旧脚本(InstallSchema、UpgradeSchema)转换为db_schema.xml格式
- 默认： `false`
- 接受值


### `--safe-mode`

在破坏性操作（如删除列）上安全安装包含转储的Magento
- 接受值


### `--data-restore`

从转储中恢复已删除的数据
- 接受值


### `--dry-run`

Magento安装将以干式运行模式运行
- 默认： `false`
- 接受值


### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache”
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `store:list`

显示商店列表

```bash
bin/magento store:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `store:website:list`

显示网站列表

```bash
bin/magento store:website:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `theme:uninstall`

卸载主题

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

<!-- app.name --> <!-- command.usage -->

### `theme`

主题路径。 主题路径应指定为完整路径，即区域/供应商/名称。 例如，前端/Magento/空白

- 默认： `[]`
- 必需

- 数组 <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--backup-code`

执行代码备份（不包括临时文件）
- 默认： `false`
- 不接受值



### `--clear-static-content`, `-c`



清除生成的静态视图文件。
- 默认： `false`
- 不接受值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size -->

## `varnish:vcl:generate`

生成清漆VCL并回声到命令行

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--output-file OUTPUT-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--access-list`

可清除清漆的IP访问列表
- 默认： `localhost`
- 需要值


### `--backend-host`

Web后端的主机
- 默认： `localhost`
- 需要值


### `--backend-port`

Web后端的端口
- 默认： `8080`
- 需要值


### `--export-version`

清漆文件的版本
- 默认： `4`
- 需要值


### `--grace-period`

宽限期（以秒为单位）
- 默认： `300`
- 需要值


### `--output-file`

要写入vcl的文件路径
- 需要值



### `--help`, `-h`



显示此帮助消息
- 默认： `false`
- 不接受值



### `--quiet`, `-q`



不输出任何消息
- 默认： `false`
- 不接受值



### `--verbose`, `-v|-vv|-vvv`



增加消息的密集度：正常输出为1，较详细输出为2，调试为3
- 默认： `false`
- 不接受值



### `--version`, `-V`



显示此应用程序版本
- 默认： `false`
- 不接受值


### `--ansi`

强制ANSI输出
- 默认： `false`
- 不接受值


### `--no-ansi`

禁用ANSI输出
- 默认： `false`
- 不接受值



### `--no-interaction`, `-n`



不要问任何交互式问题
- 默认： `false`
- 不接受值 <!-- options --> <!-- options.size --> <!-- commands --> <!-- file -->