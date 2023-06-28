---
source-git-commit: 64c453adabb092075854b2c20bf7da73c4a5146e
workflow-type: tm+mt
source-wordcount: '19899'
ht-degree: 0%

---
# bin/magento(Adobe Commerce内部部署)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->

**版本**：2.4.7-beta1

此参考包含132个命令，这些命令可通过 `bin/magento` 命令行工具。
初始列表是使用 `bin/magento list` Adobe Commerce命令。
使用 [添加CLI命令](https://developer.adobe.com/commerce/php/development/cli-commands/) 指南添加自定义CLI命令。

>[!NOTE]
>
>您可以调用 `bin/magento` CLI命令使用快捷方式，而不是完整的命令名称。 例如，您可以调用 `bin/magento setup:upgrade` 使用 `bin/magento s:up`， `bin/magento s:upg`. 参见 [快捷语法](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) 了解如何使用任何CLI命令的快捷方式。

>[!NOTE]
>
>此引用从应用程序代码库生成。 要更改内容，您可以更新中相应命令实施的源代码 [代码库](https://github.com/magento) 存储库并提交更改以供审核。 另一种方法是 _向我们提供反馈_ （在右上角找到链接）。 有关贡献准则，请参阅 [代码投稿](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

用于提供外壳完成建议的内部命令

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
```

### `--shell`, `-s`

shell类型(“bash”)

- 需要一个值

### `--input`, `-i`

输入令牌的数组（例如COMP_WORDS或argv）

- 默认： `[]`
- 需要一个值

### `--current`, `-c`

光标所在的“input”数组的索引（例如COMP_CWORD）

- 需要一个值

### `--symfony`, `-S`

完成脚本的版本

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `completion`

转储shell完成脚本

```bash
bin/magento completion [--debug] [--] [<shell>]
```


### `shell`

如果未提供shell类型（例如“bash”），则将使用“$SHELL”环境变量的值


### `--debug`

跟踪完成调试日志

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `help`

显示命令的帮助

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```


### `command_name`

命令名称

- 默认： `help`


### `--format`

输出格式（txt、xml、json或md）

- 默认： `txt`
- 需要一个值

### `--raw`

输出原始命令帮助

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `list`

列出命令

```bash
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```


### `namespace`

命名空间名称


### `--raw`

输出原始命令列表

- 默认： `false`
- 不接受值

### `--format`

输出格式（txt、xml、json或md）

- 默认： `txt`
- 需要一个值

### `--short`

跳过描述命令的参数

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `admin:adobe-ims:disable`

禁用Adobe IMS模块

```bash
bin/magento admin:adobe-ims:disable
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `admin:adobe-ims:enable`

启用Adobe IMS模块。

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

### `--organization-id`, `-o`

为Adobe IMS配置设置组织ID 。 启用模块时必需

- 接受一个值

### `--client-id`, `-c`

为Adobe IMS配置设置客户端ID。 启用模块时必需

- 接受一个值

### `--client-secret`, `-s`

为Adobe IMS配置设置客户端密钥。 启用模块时必需

- 接受一个值

### `--2fa`, `-t`

检查Adobe Admin Console中是否为“组织”启用了2FA。 启用模块时必需

- 接受一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `admin:adobe-ims:info`

Adobe IMS模块配置信息

```bash
bin/magento admin:adobe-ims:info
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `admin:adobe-ims:status`

Adobe IMS模块的状态

```bash
bin/magento admin:adobe-ims:status
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `admin:user:create`

创建管理员

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--admin-user`

（必需）管理员用户

- 需要一个值

### `--admin-password`

（必需）管理员密码

- 需要一个值

### `--admin-email`

（必需）管理员电子邮件

- 需要一个值

### `--admin-firstname`

（必需）管理员名字

- 需要一个值

### `--admin-lastname`

（必需）管理员姓氏

- 需要一个值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `admin:user:unlock`

解锁管理员帐户

```bash
bin/magento admin:user:unlock <username>
```


### `username`

要解锁的管理员用户名

- 必需

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `app:config:dump`

创建应用程序转储

```bash
bin/magento app:config:dump [<config-types>...]
```


### `config-types`

以空格分隔的配置类型列表或省略以转储所有 [范围，系统，主题， i18n]

- 默认： `[]`

- 数组

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `app:config:import`

将数据从共享配置文件导入到适当的数据存储

```bash
bin/magento app:config:import
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `app:config:status`

检查配置传播是否需要更新

```bash
bin/magento app:config:status
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `braintree:migrate`

从Magento1数据库迁移存储的卡片

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

### `--host`

主机名/IP。 端口是可选的

- 需要一个值

### `--dbname`

数据库名称

- 需要一个值

### `--username`

数据库用户名。 必须具有读取权限

- 需要一个值

### `--password`

密码

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `cache:clean`

清理缓存类型

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

以空格分隔的缓存类型列表，或省略以应用于所有缓存类型。

- 默认： `[]`

- 数组

### `--bootstrap`

添加或覆盖引导的参数

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `cache:disable`

禁用缓存类型

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

以空格分隔的缓存类型列表，或省略以应用于所有缓存类型。

- 默认： `[]`

- 数组

### `--bootstrap`

添加或覆盖引导的参数

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `cache:enable`

启用缓存类型

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

以空格分隔的缓存类型列表，或省略以应用于所有缓存类型。

- 默认： `[]`

- 数组

### `--bootstrap`

添加或覆盖引导的参数

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `cache:flush`

刷新由缓存类型使用的缓存存储

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

以空格分隔的缓存类型列表，或省略以应用于所有缓存类型。

- 默认： `[]`

- 数组

### `--bootstrap`

添加或覆盖引导的参数

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `cache:status`

检查缓存状态

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

### `--bootstrap`

添加或覆盖引导的参数

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `catalog:images:resize`

创建调整大小的产品图像

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

### `--async`, `-a`

在异步模式下调整图像大小

- 默认： `false`
- 不接受值

### `--skip_hidden_images`

不处理在产品页面中标记为隐藏的图像

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `catalog:product:attributes:cleanup`

删除未使用的产品属性。

```bash
bin/magento catalog:product:attributes:cleanup
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `cms:wysiwyg:restrict`

设置是强制执行用户HTML内容验证还是显示警告

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```


### `restrict`

y\n

- 必需

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `config:sensitive:set`

设置敏感配置值

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```


### `path`

配置路径，例如group/section/field_name


### `value`

配置值


### `--interactive`, `-i`

启用交互模式以设置所有敏感变量

- 默认： `false`
- 不接受值

### `--scope`

配置范围（如果未设置），请使用“default”

- 默认： `default`
- 接受一个值

### `--scope-code`

配置的范围代码，默认情况下为空字符串

- 默认：“
- 接受一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `config:set`

更改系统配置

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```


### `path`

格式为节/组/字段名的配置路径

- 必需

### `value`

配置值

- 必需

### `--scope`

配置范围（默认、网站或商店）

- 默认： `default`
- 需要一个值

### `--scope-code`

范围代码（仅当范围不是“default”时才需要）

- 需要一个值

### `--lock-env`, `-e`

阻止在管理员中进行修改的锁定值(将保存在app/etc/env.php中)

- 默认： `false`
- 不接受值

### `--lock-config`, `-c`

锁定并与其他安装共享值，防止在管理员中进行修改(将保存在app/etc/config.php中)

- 默认： `false`
- 不接受值

### `--lock`, `-l`

已弃用，请改用 — lock-env选项。

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `config:show`

显示给定路径的配置值。 如果未指定路径，将显示所有保存的值

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```


### `path`

配置路径，例如section_id/group_id/field_id


### `--scope`

配置范围（如果未指定），则将使用“默认”范围

- 默认： `default`
- 接受一个值

### `--scope-code`

范围代码（仅当范围不是时才需要） `default`)

- 默认：“
- 接受一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `cron:install`

为当前用户生成并安装crontab

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

### `--force`, `-f`

强制安装任务

- 默认： `false`
- 不接受值

### `--non-optional`, `-d`

仅安装非可选（默认）任务

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `cron:remove`

从crontab中删除任务

```bash
bin/magento cron:remove
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `cron:run`

按计划运行作业

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

### `--group`

仅运行来自指定组的作业

- 需要一个值

### `--exclude-group`

从指定组排除作业

- 默认： `[]`
- 接受多个值

### `--bootstrap`

添加或覆盖引导的参数

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `customer:hash:upgrade`

根据最新算法升级客户的哈希

```bash
bin/magento customer:hash:upgrade
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `deploy:mode:set`

设置应用程序模式。

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```


### `mode`

要设置的应用程序模式。 可用选项为“开发人员”或“生产”

- 必需

### `--skip-compilation`, `-s`

跳过静态内容（生成的代码、预处理的CSS和pub/static/中的资产）的清除和重新生成

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `deploy:mode:show`

显示当前应用程序模式。

```bash
bin/magento deploy:mode:show
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `dev:di:info`

提供有关命令的依赖项注入配置的信息。

```bash
bin/magento dev:di:info <class>
```


### `class`

类名

- 必需

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `dev:email:newsletter-compatibility-check`

扫描新闻稿模板以查找潜在的变量使用兼容性问题

```bash
bin/magento dev:email:newsletter-compatibility-check
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `dev:email:override-compatibility-check`

扫描电子邮件模板覆盖以查找潜在的变量使用兼容性问题

```bash
bin/magento dev:email:override-compatibility-check
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `dev:profiler:disable`

禁用Profiler。

```bash
bin/magento dev:profiler:disable
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `dev:profiler:enable`

启用Profiler。

```bash
bin/magento dev:profiler:enable [<type>]
```


### `type`

探查器类型


### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `dev:query-log:disable`

禁用数据库查询日志记录

```bash
bin/magento dev:query-log:disable
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `dev:query-log:enable`

启用数据库查询日志记录

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

### `--include-all-queries`

记录所有查询。 [true\|false]

- 默认： `true`
- 接受一个值

### `--query-time-threshold`

查询时间阈值。

- 默认： `0.001`
- 接受一个值

### `--include-call-stack`

包括调用栈栈。 [true\|false]

- 默认： `true`
- 接受一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `dev:source-theme:deploy`

收集和发布主题的源文件。

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```


### `file`

要预处理的文件（指定文件时应不带扩展名）

- 默认： `css/styles-mcss/styles-l`

- 数组

### `--type`

源文件的类型： [更少]

- 默认： `less`
- 需要一个值

### `--locale`

区域设置： [en_US]

- 默认： `en_US`
- 需要一个值

### `--area`

区域： [frontend\|adminhtml]

- 默认： `frontend`
- 需要一个值

### `--theme`

主题： [供应商/主题]

- 默认： `Magento/luma`
- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `dev:template-hints:disable`

禁用前端模板提示。 可能需要缓存刷新。

```bash
bin/magento dev:template-hints:disable
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `dev:template-hints:enable`

启用前端模板提示。 可能需要缓存刷新。

```bash
bin/magento dev:template-hints:enable
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `dev:template-hints:status`

显示前端模板提示状态。

```bash
bin/magento dev:template-hints:status
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `dev:tests:run`

运行测试

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```


### `type`

要运行的测试类型。 可用类型：all、unit、integration、integration-all、static、static-all、integrity、legacy、default

- 默认： `default`


### `--arguments`, `-c`

PHPUnit的其他参数。 示例：“ — c” — filter=MyTest&#39;”（无空格）

- 默认：“
- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `dev:urn-catalog:generate`

为IDE生成*.xsd映射的URN目录以高亮显示xml。

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```


### `path`

输出目录文件的路径。 对于PhpStorm，使用。idea/misc.xml

- 必需

### `--ide`

将生成目录的格式。 支持： [phpstorm， vscode]

- 默认： `phpstorm`
- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `dev:xml:convert`

使用XSL样式表转换XML文件

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```


### `xml-file`

要转换的XML文件的路径

- 必需

### `processor`

将应用于XML文件的XSL样式表的路径

- 必需

### `--overwrite`, `-o`

覆盖XML文件

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `downloadable:domains:add`

将域添加到可下载的域白名单

```bash
bin/magento downloadable:domains:add [<domains>...]
```


### `domains`

域名称

- 默认： `[]`

- 数组

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `downloadable:domains:remove`

从可下载的域白名单中删除域

```bash
bin/magento downloadable:domains:remove [<domains>...]
```


### `domains`

域名

- 默认： `[]`

- 数组

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `downloadable:domains:show`

显示可下载域白名单

```bash
bin/magento downloadable:domains:show
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `encryption:payment-data:update`

使用最新的加密密码重新加密已加密的信用卡数据。

```bash
bin/magento encryption:payment-data:update
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `events:create-event-provider`

在此实例的Adobe I/O事件中创建自定义事件提供程序。 如果不指定label和description选项，则必须在system app/etc/event-types.json文件中定义它们。

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]
```


```bash
bin/magento events:provider:create 
```

### `--label`

用于定义自定义提供商的标签。

- 接受一个值

### `--description`

提供商的说明。

- 接受一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `events:generate:module`

根据插件列表生成模块

```bash
bin/magento events:generate:module
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `events:info`

返回指定事件的有效负载。

```bash
bin/magento events:info [--depth [DEPTH]] [--] <event-code>
```


### `event-code`

事件代码

- 必需

### `--depth`

要返回的事件有效负载中的级别数

- 默认： `2`
- 接受一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `events:list`

显示订阅事件的列表

```bash
bin/magento events:list
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `events:list:all`

返回在指定模块中定义的可订阅事件的列表

```bash
bin/magento events:list:all <module_name>
```


### `module_name`

模块名称

- 必需

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `events:metadata:populate`

从配置列表（XML和应用程序配置）创建Adobe I/O元数据

```bash
bin/magento events:metadata:populate
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `events:subscribe`

订阅事件

```bash
bin/magento events:subscribe [-f|--force] [--fields FIELDS] [--parent PARENT] [--rules RULES] [-p|--priority] [--] <event-code>
```


### `event-code`

事件代码

- 必需

### `--force`, `-f`

强制订阅指定的事件，即使它尚未在本地定义。

- 默认： `false`
- 不接受值

### `--fields`

事件数据有效负载中的字段列表。

- 默认： `[]`
- 需要一个值

### `--parent`

具有规则的事件订阅的父事件代码。

- 需要一个值

### `--rules`

事件订阅的规则列表，其中每个规则的格式为“field\|operator\|value”。

- 默认： `[]`
- 需要一个值

### `--priority`, `-p`

加快此事件的传输。 为需要立即投放的事件指定此选项。 默认情况下，cron每分钟会发送一次事件。

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `events:sync-events-metadata`

同步此实例的事件元数据

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

### `--delete`, `-d`

删除事件元数据不再需要

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `events:unsubscribe`

删除对提供的事件的订阅

```bash
bin/magento events:unsubscribe <event-code>
```


### `event-code`

要取消订阅的事件代码

- 必需

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `i18n:collect-phrases`

发现代码库中的短语

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```


### `directory`

要分析的目录路径。 如果设置了 — magento标志，则不需要


### `--output`, `-o`

输出文件的路径（包括文件名）。 未指定文件，将默认为stdout。

- 需要一个值

### `--magento`, `-m`

使用 — magento参数解析当前Magento代码库。 如果指定了目录，则省略参数。

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `i18n:pack`

保存语言包

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```


### `source`

包含翻译的源字典文件的路径

- 必需

### `locale`

词典的目标区域设置，例如“de_DE”

- 必需

### `--mode`, `-m`

词典的存储模式 — “替换” — 用新语言包替换语言包 — “合并” — 合并语言包，默认为“替换”

- 默认： `replace`
- 需要一个值

### `--allow-duplicates`, `-d`

使用 — allow-duplicates参数可允许保存翻译的重复项。 否则，忽略参数。

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `i18n:uninstall`

卸载语言包

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```


### `package`

语言包名称

- 默认： `[]`

- 必需
- 数组

### `--backup-code`, `-b`

进行代码和配置文件备份（不包括临时文件）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `indexer:info`

显示允许的索引器

```bash
bin/magento indexer:info
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `indexer:reindex`

重新索引数据

```bash
bin/magento indexer:reindex [<index>...]
```


### `index`

以空格分隔的索引类型列表，或省略以应用于所有索引。

- 默认： `[]`

- 数组

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `indexer:reset`

将索引器状态重置为无效

```bash
bin/magento indexer:reset [<index>...]
```


### `index`

以空格分隔的索引类型列表，或省略以应用于所有索引。

- 默认： `[]`

- 数组

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `indexer:set-dimensions-mode`

设置索引器Dimension模式

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```


### `indexer`

索引器名称 [catalog_product_price|catalogpermissions_category]


### `mode`

索引器维度模式catalog_product_price none，website，customer_group，website_and_customer_group目录permissions_category none，customer_group


### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `indexer:set-mode`

设置索引模式类型

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```


### `mode`

索引器模式类型 [实时|计划]


### `index`

以空格分隔的索引类型列表，或省略以应用于所有索引。

- 默认： `[]`

- 数组

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `indexer:show-dimensions-mode`

显示索引器Dimension模式

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```


### `indexer`

以空格分隔的索引类型列表，或省略以应用于所有索引(catalog_product_price、catalogpermissions_category)

- 默认： `[]`

- 数组

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `indexer:show-mode`

显示索引模式

```bash
bin/magento indexer:show-mode [<index>...]
```


### `index`

以空格分隔的索引类型列表，或省略以应用于所有索引。

- 默认： `[]`

- 数组

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `indexer:status`

显示索引器的状态

```bash
bin/magento indexer:status [<index>...]
```


### `index`

以空格分隔的索引类型列表，或省略以应用于所有索引。

- 默认： `[]`

- 数组

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `info:adminuri`

显示Magento管理员URI

```bash
bin/magento info:adminuri
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `info:backups:list`

打印可用备份文件列表

```bash
bin/magento info:backups:list
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `info:currency:list`

显示可用货币的列表

```bash
bin/magento info:currency:list
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `info:dependencies:show-framework`

显示Magento框架的依赖项数量

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

### `--output`, `-o`

报表文件名

- 默认： `framework-dependencies.csv`
- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `info:dependencies:show-modules`

显示模块之间的依赖关系数

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

### `--output`, `-o`

报表文件名

- 默认： `modules-dependencies.csv`
- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `info:dependencies:show-modules-circular`

显示模块之间的循环依赖关系数

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

### `--output`, `-o`

报表文件名

- 默认： `modules-circular-dependencies.csv`
- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `info:language:list`

显示可用语言区域设置的列表

```bash
bin/magento info:language:list
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `info:timezone:list`

显示可用时区的列表

```bash
bin/magento info:timezone:list
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `inventory:reservation:create-compensations`

通过提供的报酬参数创建保留

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```


### `compensations`

报酬参数的列表，格式为“\”&lt;order_increment_id>：\&lt;sku>：\&lt;quantity>：\&lt;stock-id>”

- 默认： `[]`

- 数组

### `--raw`, `-r`

原始输出

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `inventory:reservation:list-inconsistencies`

显示所有具有可销售数量不一致的订单和产品

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

### `--complete-orders`, `-c`

仅显示完整订单的不一致

- 默认： `false`
- 不接受值

### `--incomplete-orders`, `-i`

仅显示不完整订单的不一致

- 默认： `false`
- 不接受值

### `--bunch-size`, `-b`

定义将一次加载多少订单

- 默认： `50`
- 接受一个值

### `--raw`, `-r`

原始输出

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `inventory-geonames:import`

下载并导入源选择算法的地理名称

```bash
bin/magento inventory-geonames:import <countries>...
```


### `countries`

要导入的国家代码列表

- 默认： `[]`

- 必需
- 数组

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `maintenance:allow-ips`

设置维护模式免除IP

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```


### `ip`

允许的IP地址

- 默认： `[]`

- 数组

### `--none`

清除允许的IP地址

- 默认： `false`
- 不接受值

### `--add`

将IP地址添加到现有列表

- 默认： `false`
- 不接受值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `maintenance:disable`

禁用维护模式

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

允许的IP地址（使用“无”清除允许的IP列表）

- 默认： `[]`
- 需要一个值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `maintenance:enable`

启用维护模式

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

允许的IP地址（使用“无”清除允许的IP列表）

- 默认： `[]`
- 需要一个值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `maintenance:status`

显示维护模式状态

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `media-content:sync`

将内容与资产同步

```bash
bin/magento media-content:sync
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `media-gallery:sync`

同步数据库中的媒体存储和媒体资产

```bash
bin/magento media-gallery:sync
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `module:config:status`

检查“app/etc/config.php”文件中的模块配置，并报告它们是否为最新版本

```bash
bin/magento module:config:status
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `module:disable`

禁用指定的模块

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

模块名称

- 默认： `[]`

- 数组

### `--force`, `-f`

绕过依赖项检查

- 默认： `false`
- 不接受值

### `--all`

禁用所有模块

- 默认： `false`
- 不接受值

### `--clear-static-content`, `-c`

清除生成的静态视图文件。 如果模块具有静态视图文件，则此为必需字段

- 默认： `false`
- 不接受值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `module:enable`

启用指定的模块

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

模块名称

- 默认： `[]`

- 数组

### `--force`, `-f`

绕过依赖项检查

- 默认： `false`
- 不接受值

### `--all`

启用所有模块

- 默认： `false`
- 不接受值

### `--clear-static-content`, `-c`

清除生成的静态视图文件。 如果模块具有静态视图文件，则此为必需字段

- 默认： `false`
- 不接受值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `module:status`

显示模块的状态

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```


### `module-names`

可选模块名称

- 默认： `[]`

- 数组

### `--enabled`

仅打印已启用的模块

- 默认： `false`
- 不接受值

### `--disabled`

仅打印禁用的模块

- 默认： `false`
- 不接受值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `module:uninstall`

卸载由编辑器安装的模块

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```


### `module`

模块名称

- 默认： `[]`

- 必需
- 数组

### `--remove-data`, `-r`

删除模块安装的数据

- 默认： `false`
- 不接受值

### `--backup-code`

进行代码和配置文件备份（不包括临时文件）

- 默认： `false`
- 不接受值

### `--backup-media`

进行媒体备份

- 默认： `false`
- 不接受值

### `--backup-db`

进行完整的数据库备份

- 默认： `false`
- 不接受值

### `--non-composer`

此处过去的所有模块都将基于非编辑器

- 默认： `false`
- 不接受值

### `--clear-static-content`, `-c`

清除生成的静态视图文件。 如果模块具有静态视图文件，则此为必需字段

- 默认： `false`
- 不接受值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `newrelic:create:deploy-marker`

检查部署队列中的条目，并创建适当的部署标记。

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```


### `message`

部署消息？

- 必需

### `change_log`

更改日志？

- 必需

### `user`

部署用户


### `revision`

修订版


### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `queue:consumers:list`

MessageQueue使用者列表

```bash
bin/magento queue:consumers:list
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `queue:consumers:restart`

重新启动MessageQueue使用者

```bash
bin/magento queue:consumers:restart
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `queue:consumers:start`

启动MessageQueue使用者

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```


### `consumer`

要启动的消费者的名称。

- 必需

### `--max-messages`

进程终止前使用者要处理的消息数。 如果未指定 — 在处理所有排队消息后终止。

- 需要一个值

### `--batch-size`

每批次的消息数。 仅适用于批处理消费者。

- 需要一个值

### `--area-code`

首选区域（global、adminhtml等）的默认值为global。

- 需要一个值

### `--single-thread`

此选项可防止同时运行一个使用者的多个副本。

- 默认： `false`
- 不接受值

### `--multi-process`

每个使用者的进程数。

- 接受一个值

### `--pid-file-path`

用于保存PID的文件路径（此选项已弃用，请改用 — 单线程）

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `remote-storage:sync`

将媒体文件与远程存储同步。

```bash
bin/magento remote-storage:sync
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `saas:resync`

将馈送数据重新同步到SaaS服务。

```bash
bin/magento saas:resync [--no-reindex] [--feed FEED] [--cleanup-feed]
```

### `--no-reindex`

仅运行将信息源数据重新提交到SaaS服务的过程。 不重新编入索引。

- 默认： `false`
- 不接受值

### `--feed`

要完全重新同步到SaaS服务的馈送名称。 可用信息源：

- 需要一个值

### `--cleanup-feed`

强制在同步之前清除馈送索引器表。

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `sampledata:deploy`

为基于编辑器的Magento安装部署示例数据模块

```bash
bin/magento sampledata:deploy [--no-update]
```

### `--no-update`

在不执行编辑器更新的情况下更新composer.json

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `sampledata:remove`

从composer.json中删除所有示例数据包

```bash
bin/magento sampledata:remove [--no-update]
```

### `--no-update`

在不执行编辑器更新的情况下更新composer.json

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `sampledata:reset`

重置所有示例数据模块以重新安装

```bash
bin/magento sampledata:reset
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `security:recaptcha:disable-for-user-forgot-password`

禁用管理员用户忘记密码表单的reCAPTCHA

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `security:recaptcha:disable-for-user-login`

禁用管理员用户登录表单的reCAPTCHA

```bash
bin/magento security:recaptcha:disable-for-user-login
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `security:tfa:google:set-secret`

设置用于生成Google OTP的密码。

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```


### `user`

用户名

- 必需

### `secret`

密码

- 必需

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `security:tfa:providers`

列出所有可用的提供程序

```bash
bin/magento security:tfa:providers
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `security:tfa:reset`

重置一个用户的配置

```bash
bin/magento security:tfa:reset <user> <provider>
```


### `user`

用户名

- 必需

### `provider`

提供程序代码

- 必需

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `server:run`

运行应用程序服务器

```bash
bin/magento server:run [-p|--port [PORT]] [-b|--background [BACKGROUND]] [-a|--area [AREA]] [-mip|--magento-init-params [MAGENTO-INIT-PARAMS]]
```

### `--port`, `-p`

要服务的端口

- 默认： `9501`
- 接受一个值

### `--background`, `-b`

背景模式标志

- 默认： `0`
- 接受一个值

### `--area`, `-a`

应用程序服务器区域

- 默认： `graphql`
- 接受一个值

### `--magento-init-params`, `-mip`

magento bootstrap初始化参数

- 默认：“
- 接受一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:backup`

对Magento应用程序代码库、介质和数据库进行备份

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code`

进行代码和配置文件备份（不包括临时文件）

- 默认： `false`
- 不接受值

### `--media`

进行媒体备份

- 默认： `false`
- 不接受值

### `--db`

进行完整的数据库备份

- 默认： `false`
- 不接受值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:config:set`

创建或修改部署配置

```bash
bin/magento setup:config:set [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--config-async CONFIG-ASYNC] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

后端前端名称（如果缺少，将自动生成）

- 需要一个值

### `--enable-debug-logging`

启用调试日志记录

- 需要一个值

### `--enable-syslog-logging`

启用syslog日志记录

- 需要一个值

### `--remote-storage-driver`

远程存储驱动程序

- 需要一个值

### `--remote-storage-prefix`

远程存储前缀

- 默认：“
- 需要一个值

### `--remote-storage-endpoint`

远程存储端点

- 需要一个值

### `--remote-storage-bucket`

远程存储段

- 需要一个值

### `--remote-storage-region`

远程存储区域

- 需要一个值

### `--remote-storage-key`

远程存储访问密钥

- 默认：“
- 需要一个值

### `--remote-storage-secret`

远程存储密钥

- 默认：“
- 需要一个值

### `--remote-storage-path-style`

远程存储路径样式

- 默认： `0`
- 需要一个值

### `--id_salt`

GraphQl盐

- 需要一个值

### `--checkout-async`

是否启用异步订单处理？ 1 — 是，0 — 否

- 需要一个值

### `--amqp-host`

Amqp服务器主机

- 默认：“
- 需要一个值

### `--amqp-port`

Amqp服务器端口

- 默认： `5672`
- 需要一个值

### `--amqp-user`

Amqp服务器用户名

- 默认：“
- 需要一个值

### `--amqp-password`

Amqp服务器密码

- 默认：“
- 需要一个值

### `--amqp-virtualhost`

Amqp virtualhost

- 默认： `/`
- 需要一个值

### `--amqp-ssl`

Amqp SSL

- 默认：“
- 需要一个值

### `--amqp-ssl-options`

Amqp SSL选项(JSON)

- 默认：“
- 需要一个值

### `--config-async`

是否启用异步管理配置保存？ 1 — 是，0 — 否

- 需要一个值

### `--consumers-wait-for-messages`

消费者是否应该等待队列中的消息？ 1 — 是，0 — 否

- 需要一个值

### `--queue-default-connection`

消息队列默认连接。 可以是“db”、“amqp”或自定义队列系统。必须安装和配置队列系统，否则将无法正确处理消息。

- 需要一个值

### `--deferred-total-calculating`

是否启用延迟总计计算？ 1 — 是，0 — 否

- 需要一个值

### `--key`

加密密钥

- 需要一个值

### `--db-host`

数据库服务器主机

- 需要一个值

### `--db-name`

数据库名称

- 需要一个值

### `--db-user`

数据库服务器用户名

- 需要一个值

### `--db-engine`

数据库服务器引擎

- 需要一个值

### `--db-password`

数据库服务器密码

- 需要一个值

### `--db-prefix`

数据库表前缀

- 需要一个值

### `--db-model`

数据库类型

- 需要一个值

### `--db-init-statements`

数据库初始命令集

- 需要一个值

### `--skip-db-validation`, `-s`

如果已指定，则将跳过数据库连接验证

- 默认： `false`
- 不接受值

### `--http-cache-hosts`

http缓存主机

- 需要一个值

### `--db-ssl-key`

用于通过SSL建立数据库连接的客户端密钥文件的完整路径

- 默认：“
- 需要一个值

### `--db-ssl-cert`

客户端证书文件的完整路径，用于通过SSL建立数据库连接

- 默认：“
- 需要一个值

### `--db-ssl-ca`

用于通过SSL建立数据库连接的服务器证书文件的完整路径

- 默认：“
- 需要一个值

### `--db-ssl-verify`

验证服务器认证

- 默认： `false`
- 不接受值

### `--session-save`

会话保存处理程序

- 需要一个值

### `--session-save-redis-host`

完全限定主机名、IP地址或绝对路径（如果使用UNIX套接字）

- 需要一个值

### `--session-save-redis-port`

Redis服务器侦听端口

- 需要一个值

### `--session-save-redis-password`

Redis服务器密码

- 需要一个值

### `--session-save-redis-timeout`

连接超时（以秒为单位）

- 需要一个值

### `--session-save-redis-persistent-id`

用于启用永久连接的唯一字符串

- 需要一个值

### `--session-save-redis-db`

Redis数据库编号

- 需要一个值

### `--session-save-redis-compression-threshold`

Redis压缩阈值

- 需要一个值

### `--session-save-redis-compression-lib`

Redis压缩库。 值：gzip（默认）、lzf、lz4、snappy

- 需要一个值

### `--session-save-redis-log-level`

Redis日志级别。 值： 0（最少详细）到7（最详细）

- 需要一个值

### `--session-save-redis-max-concurrency`

可等待一个会话锁定的最大进程数

- 需要一个值

### `--session-save-redis-break-after-frontend`

尝试破解前端会话锁定之前等待的秒数

- 需要一个值

### `--session-save-redis-break-after-adminhtml`

尝试解除管理员会话锁定前等待的秒数

- 需要一个值

### `--session-save-redis-first-lifetime`

非机器人在首次写入时会话的生命周期（以秒为单位）（使用0可禁用）

- 需要一个值

### `--session-save-redis-bot-first-lifetime`

机器人首次写入时会话的生命周期（以秒为单位）（使用0可禁用）

- 需要一个值

### `--session-save-redis-bot-lifetime`

机器人后续写入会话的生命周期（使用0禁用）

- 需要一个值

### `--session-save-redis-disable-locking`

Redis禁用锁定。 值： false（默认）、true

- 需要一个值

### `--session-save-redis-min-lifetime`

Redis最小会话生命周期，以秒为单位

- 需要一个值

### `--session-save-redis-max-lifetime`

Redis最长会话生命周期（以秒为单位）

- 需要一个值

### `--session-save-redis-sentinel-master`

Redis Sentinel主控

- 需要一个值

### `--session-save-redis-sentinel-servers`

Redis Sentinel服务器，逗号分隔

- 需要一个值

### `--session-save-redis-sentinel-verify-master`

雷迪斯·森蒂纳尔确认主控。 值： false（默认）、true

- 需要一个值

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel连接重试。

- 需要一个值

### `--cache-backend`

默认缓存处理程序

- 需要一个值

### `--cache-backend-redis-server`

Redis服务器

- 需要一个值

### `--cache-backend-redis-db`

高速缓存的数据库编号

- 需要一个值

### `--cache-backend-redis-port`

Redis服务器侦听端口

- 需要一个值

### `--cache-backend-redis-password`

Redis服务器密码

- 需要一个值

### `--cache-backend-redis-compress-data`

设置为0可禁用压缩（默认值为1，已启用）

- 需要一个值

### `--cache-backend-redis-compression-lib`

要使用的压缩库 [snappy，lzf，l4z，zstd，gzip] （留空将自动确定）

- 需要一个值

### `--cache-id-prefix`

缓存键的ID前缀

- 需要一个值

### `--allow-parallel-generation`

允许以非阻塞方式生成缓存

- 默认： `false`
- 不接受值

### `--page-cache`

默认缓存处理程序

- 需要一个值

### `--page-cache-redis-server`

Redis服务器

- 需要一个值

### `--page-cache-redis-db`

高速缓存的数据库编号

- 需要一个值

### `--page-cache-redis-port`

Redis服务器侦听端口

- 需要一个值

### `--page-cache-redis-password`

Redis服务器密码

- 需要一个值

### `--page-cache-redis-compress-data`

设置为1可压缩全页缓存（使用0可禁用）

- 需要一个值

### `--page-cache-redis-compression-lib`

要使用的压缩库 [snappy，lzf，l4z，zstd，gzip] （留空将自动确定）

- 需要一个值

### `--page-cache-id-prefix`

缓存键的ID前缀

- 需要一个值

### `--lock-provider`

锁定提供程序名称

- 需要一个值

### `--lock-db-prefix`

安装特定的锁定前缀以避免锁定冲突

- 需要一个值

### `--lock-zookeeper-host`

用于连接到Zookeeper群集的主机和端口。 例如： 127.0.0.1:2181

- 需要一个值

### `--lock-zookeeper-path`

Zookeeper将保存锁的路径。 默认路径为： /magento/locks

- 需要一个值

### `--lock-file-path`

将保存文件锁定的路径。

- 需要一个值

### `--document-root-is-pub`

要显示的标志是Pub位于根目录下，只能为true或false

- 需要一个值

### `--backpressure-logger`

背压记录器处理程序

- 需要一个值

### `--backpressure-logger-redis-server`

Redis服务器

- 需要一个值

### `--backpressure-logger-redis-port`

Redis服务器侦听端口

- 需要一个值

### `--backpressure-logger-redis-timeout`

Redis服务器超时

- 需要一个值

### `--backpressure-logger-redis-persistent`

Redis永久

- 需要一个值

### `--backpressure-logger-redis-db`

Redis数据库编号

- 需要一个值

### `--backpressure-logger-redis-password`

Redis服务器密码

- 需要一个值

### `--backpressure-logger-redis-user`

Redis服务器用户

- 需要一个值

### `--backpressure-logger-id-prefix`

键的ID前缀

- 需要一个值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:db-data:upgrade`

在数据库中安装和升级数据

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:db-declaration:generate-patch`

生成修补程序并将其放在特定文件夹中。

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```


### `module`

模块名称

- 必需

### `patch`

修补程序名称

- 必需

### `--revertable`

检查修补程序是否可还原。

- 默认： `false`
- 接受一个值

### `--type`

了解应生成的修补程序类型。 可用值： `data`， `schema`.

- 默认： `data`
- 接受一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:db-declaration:generate-whitelist`

生成允许由声明安装程序编辑的表和列的白名单

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

### `--module-name`

将生成白名单的模块的名称

- 默认： `all`
- 接受一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:db-schema:add-slave`

将与签出引号相关的表移动到单独的数据库服务器

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

从属数据库服务器主机

- 默认： `localhost`
- 需要一个值

### `--dbname`

从属数据库名称

- 需要一个值

### `--username`

从属数据库用户名

- 默认： `root`
- 需要一个值

### `--password`

从属数据库用户密码

- 接受一个值

### `--connection`

从属连接名称

- 默认： `default`
- 接受一个值

### `--resource`

从属资源名称

- 默认： `default`
- 接受一个值

### `--maxAllowedLag`

允许的最大滞后从连接（以秒为单位）

- 默认：“
- 接受一个值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:db-schema:split-quote`

将与签出引号相关的表移动到单独的DB服务器。 自2.4.2起已弃用，将删除

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

签出数据库服务器主机

- 需要一个值

### `--dbname`

签出数据库名称

- 需要一个值

### `--username`

签出数据库用户名

- 需要一个值

### `--password`

签出数据库用户密码

- 接受一个值

### `--connection`

签出连接名称

- 默认： `checkout`
- 接受一个值

### `--resource`

签出资源名称

- 默认： `checkout`
- 接受一个值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:db-schema:split-sales`

将与销售相关的表移动到单独的数据库服务器。 自2.4.2起已弃用，将删除

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

销售数据库服务器主机

- 需要一个值

### `--dbname`

销售数据库名称

- 需要一个值

### `--username`

销售数据库用户名

- 需要一个值

### `--password`

销售数据库用户密码

- 接受一个值

### `--connection`

销售连接名称

- 默认： `sales`
- 接受一个值

### `--resource`

销售资源名称

- 默认： `sales`
- 接受一个值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:db-schema:upgrade`

安装和升级数据库架构

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--convert-old-scripts`

允许将旧脚本(InstallSchema、UpgradeSchema)转换为db_schema.xml格式

- 默认： `false`
- 接受一个值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:db:status`

检查数据库架构或数据是否需要升级

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:di:compile`

生成DI配置和所有可自动生成的缺失类

```bash
bin/magento setup:di:compile
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:install`

安装Magento应用程序

```bash
bin/magento setup:install [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--config-async CONFIG-ASYNC] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

后端前端名称（如果缺少，将自动生成）

- 需要一个值

### `--enable-debug-logging`

启用调试日志记录

- 需要一个值

### `--enable-syslog-logging`

启用syslog日志记录

- 需要一个值

### `--remote-storage-driver`

远程存储驱动程序

- 需要一个值

### `--remote-storage-prefix`

远程存储前缀

- 默认：“
- 需要一个值

### `--remote-storage-endpoint`

远程存储端点

- 需要一个值

### `--remote-storage-bucket`

远程存储段

- 需要一个值

### `--remote-storage-region`

远程存储区域

- 需要一个值

### `--remote-storage-key`

远程存储访问密钥

- 默认：“
- 需要一个值

### `--remote-storage-secret`

远程存储密钥

- 默认：“
- 需要一个值

### `--remote-storage-path-style`

远程存储路径样式

- 默认： `0`
- 需要一个值

### `--id_salt`

GraphQl盐

- 需要一个值

### `--checkout-async`

是否启用异步订单处理？ 1 — 是，0 — 否

- 需要一个值

### `--amqp-host`

Amqp服务器主机

- 默认：“
- 需要一个值

### `--amqp-port`

Amqp服务器端口

- 默认： `5672`
- 需要一个值

### `--amqp-user`

Amqp服务器用户名

- 默认：“
- 需要一个值

### `--amqp-password`

Amqp服务器密码

- 默认：“
- 需要一个值

### `--amqp-virtualhost`

Amqp virtualhost

- 默认： `/`
- 需要一个值

### `--amqp-ssl`

Amqp SSL

- 默认：“
- 需要一个值

### `--amqp-ssl-options`

Amqp SSL选项(JSON)

- 默认：“
- 需要一个值

### `--config-async`

是否启用异步管理配置保存？ 1 — 是，0 — 否

- 需要一个值

### `--consumers-wait-for-messages`

消费者是否应该等待队列中的消息？ 1 — 是，0 — 否

- 需要一个值

### `--queue-default-connection`

消息队列默认连接。 可以是“db”、“amqp”或自定义队列系统。必须安装和配置队列系统，否则将无法正确处理消息。

- 需要一个值

### `--deferred-total-calculating`

是否启用延迟总计计算？ 1 — 是，0 — 否

- 需要一个值

### `--key`

加密密钥

- 需要一个值

### `--db-host`

数据库服务器主机

- 需要一个值

### `--db-name`

数据库名称

- 需要一个值

### `--db-user`

数据库服务器用户名

- 需要一个值

### `--db-engine`

数据库服务器引擎

- 需要一个值

### `--db-password`

数据库服务器密码

- 需要一个值

### `--db-prefix`

数据库表前缀

- 需要一个值

### `--db-model`

数据库类型

- 需要一个值

### `--db-init-statements`

数据库初始命令集

- 需要一个值

### `--skip-db-validation`, `-s`

如果已指定，则将跳过数据库连接验证

- 默认： `false`
- 不接受值

### `--http-cache-hosts`

http缓存主机

- 需要一个值

### `--db-ssl-key`

用于通过SSL建立数据库连接的客户端密钥文件的完整路径

- 默认：“
- 需要一个值

### `--db-ssl-cert`

客户端证书文件的完整路径，用于通过SSL建立数据库连接

- 默认：“
- 需要一个值

### `--db-ssl-ca`

用于通过SSL建立数据库连接的服务器证书文件的完整路径

- 默认：“
- 需要一个值

### `--db-ssl-verify`

验证服务器认证

- 默认： `false`
- 不接受值

### `--session-save`

会话保存处理程序

- 需要一个值

### `--session-save-redis-host`

完全限定主机名、IP地址或绝对路径（如果使用UNIX套接字）

- 需要一个值

### `--session-save-redis-port`

Redis服务器侦听端口

- 需要一个值

### `--session-save-redis-password`

Redis服务器密码

- 需要一个值

### `--session-save-redis-timeout`

连接超时（以秒为单位）

- 需要一个值

### `--session-save-redis-persistent-id`

用于启用永久连接的唯一字符串

- 需要一个值

### `--session-save-redis-db`

Redis数据库编号

- 需要一个值

### `--session-save-redis-compression-threshold`

Redis压缩阈值

- 需要一个值

### `--session-save-redis-compression-lib`

Redis压缩库。 值：gzip（默认）、lzf、lz4、snappy

- 需要一个值

### `--session-save-redis-log-level`

Redis日志级别。 值： 0（最少详细）到7（最详细）

- 需要一个值

### `--session-save-redis-max-concurrency`

可等待一个会话锁定的最大进程数

- 需要一个值

### `--session-save-redis-break-after-frontend`

尝试破解前端会话锁定之前等待的秒数

- 需要一个值

### `--session-save-redis-break-after-adminhtml`

尝试解除管理员会话锁定前等待的秒数

- 需要一个值

### `--session-save-redis-first-lifetime`

非机器人在首次写入时会话的生命周期（以秒为单位）（使用0可禁用）

- 需要一个值

### `--session-save-redis-bot-first-lifetime`

机器人首次写入时会话的生命周期（以秒为单位）（使用0可禁用）

- 需要一个值

### `--session-save-redis-bot-lifetime`

机器人后续写入会话的生命周期（使用0禁用）

- 需要一个值

### `--session-save-redis-disable-locking`

Redis禁用锁定。 值： false（默认）、true

- 需要一个值

### `--session-save-redis-min-lifetime`

Redis最小会话生命周期，以秒为单位

- 需要一个值

### `--session-save-redis-max-lifetime`

Redis最长会话生命周期（以秒为单位）

- 需要一个值

### `--session-save-redis-sentinel-master`

Redis Sentinel主控

- 需要一个值

### `--session-save-redis-sentinel-servers`

Redis Sentinel服务器，逗号分隔

- 需要一个值

### `--session-save-redis-sentinel-verify-master`

雷迪斯·森蒂纳尔确认主控。 值： false（默认）、true

- 需要一个值

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel连接重试。

- 需要一个值

### `--cache-backend`

默认缓存处理程序

- 需要一个值

### `--cache-backend-redis-server`

Redis服务器

- 需要一个值

### `--cache-backend-redis-db`

高速缓存的数据库编号

- 需要一个值

### `--cache-backend-redis-port`

Redis服务器侦听端口

- 需要一个值

### `--cache-backend-redis-password`

Redis服务器密码

- 需要一个值

### `--cache-backend-redis-compress-data`

设置为0可禁用压缩（默认值为1，已启用）

- 需要一个值

### `--cache-backend-redis-compression-lib`

要使用的压缩库 [snappy，lzf，l4z，zstd，gzip] （留空将自动确定）

- 需要一个值

### `--cache-id-prefix`

缓存键的ID前缀

- 需要一个值

### `--allow-parallel-generation`

允许以非阻塞方式生成缓存

- 默认： `false`
- 不接受值

### `--page-cache`

默认缓存处理程序

- 需要一个值

### `--page-cache-redis-server`

Redis服务器

- 需要一个值

### `--page-cache-redis-db`

高速缓存的数据库编号

- 需要一个值

### `--page-cache-redis-port`

Redis服务器侦听端口

- 需要一个值

### `--page-cache-redis-password`

Redis服务器密码

- 需要一个值

### `--page-cache-redis-compress-data`

设置为1可压缩全页缓存（使用0可禁用）

- 需要一个值

### `--page-cache-redis-compression-lib`

要使用的压缩库 [snappy，lzf，l4z，zstd，gzip] （留空将自动确定）

- 需要一个值

### `--page-cache-id-prefix`

缓存键的ID前缀

- 需要一个值

### `--lock-provider`

锁定提供程序名称

- 需要一个值

### `--lock-db-prefix`

安装特定的锁定前缀以避免锁定冲突

- 需要一个值

### `--lock-zookeeper-host`

用于连接到Zookeeper群集的主机和端口。 例如： 127.0.0.1:2181

- 需要一个值

### `--lock-zookeeper-path`

Zookeeper将保存锁的路径。 默认路径为： /magento/locks

- 需要一个值

### `--lock-file-path`

将保存文件锁定的路径。

- 需要一个值

### `--document-root-is-pub`

要显示的标志是Pub位于根目录下，只能为true或false

- 需要一个值

### `--backpressure-logger`

背压记录器处理程序

- 需要一个值

### `--backpressure-logger-redis-server`

Redis服务器

- 需要一个值

### `--backpressure-logger-redis-port`

Redis服务器侦听端口

- 需要一个值

### `--backpressure-logger-redis-timeout`

Redis服务器超时

- 需要一个值

### `--backpressure-logger-redis-persistent`

Redis永久

- 需要一个值

### `--backpressure-logger-redis-db`

Redis数据库编号

- 需要一个值

### `--backpressure-logger-redis-password`

Redis服务器密码

- 需要一个值

### `--backpressure-logger-redis-user`

Redis服务器用户

- 需要一个值

### `--backpressure-logger-id-prefix`

键的ID前缀

- 需要一个值

### `--base-url`

商店应位于的URL。 已弃用，请使用config：set以及路径web/unsecure/base_url

- 需要一个值

### `--language`

默认语言代码。 已弃用，请使用config：set以及路径general/locale/code

- 需要一个值

### `--timezone`

默认时区代码。 已弃用，请使用config：set和path general/locale/timezone

- 需要一个值

### `--currency`

默认货币代码。 已弃用，请使用config：set以及路径currency/options/base、currency/options/default和currency/options/allow

- 需要一个值

### `--use-rewrites`

使用重写。 已弃用，请使用config：set以及路径web/seo/use_rewrites

- 需要一个值

### `--use-secure`

使用安全URL。 仅当SSL可用时启用此选项。 已弃用，请使用config：set以及路径web/secure/use_in_frontend

- 需要一个值

### `--base-url-secure`

SSL连接的基本URL。 已弃用，请使用config：set以及路径web/secure/base_url

- 需要一个值

### `--use-secure-admin`

使用SSL运行管理界面。 已弃用，请使用config：set以及路径web/secure/use_in_adminhtml

- 需要一个值

### `--admin-use-security-key`

是否在Magento管理员URL和表单中使用“安全密钥”功能。 已弃用，请使用config：set和path admin/security/use_form_key

- 需要一个值

### `--admin-user`

管理员用户

- 接受一个值

### `--admin-password`

管理员密码

- 接受一个值

### `--admin-email`

管理员电子邮件

- 接受一个值

### `--admin-firstname`

管理员名字

- 接受一个值

### `--admin-lastname`

管理员姓氏

- 接受一个值

### `--search-engine`

搜索引擎。 值：elasticsearch5、elasticsearch7、elasticsearch8、opensearch

- 需要一个值

### `--elasticsearch-host`

Elasticsearch服务器主机。

- 需要一个值

### `--elasticsearch-port`

服务器端口Elasticsearch。

- 需要一个值

### `--elasticsearch-enable-auth`

设置为1可启用身份验证。 （默认值为0，已禁用）

- 需要一个值

### `--elasticsearch-username`

用户名Elasticsearch。 仅在启用HTTP身份验证时适用

- 需要一个值

### `--elasticsearch-password`

密码Elasticsearch。 仅在启用HTTP身份验证时适用

- 需要一个值

### `--elasticsearch-index-prefix`

索引前缀Elasticsearch。

- 需要一个值

### `--elasticsearch-timeout`

Elasticsearch服务器超时。

- 需要一个值

### `--opensearch-host`

OpenSearch服务器主机。

- 需要一个值

### `--opensearch-port`

OpenSearch服务器端口。

- 需要一个值

### `--opensearch-enable-auth`

设置为1可启用身份验证。 （默认值为0，已禁用）

- 需要一个值

### `--opensearch-username`

OpenSearch用户名。 仅在启用HTTP身份验证时适用

- 需要一个值

### `--opensearch-password`

OpenSearch密码。 仅在启用HTTP身份验证时适用

- 需要一个值

### `--opensearch-index-prefix`

OpenSearch索引前缀。

- 需要一个值

### `--opensearch-timeout`

OpenSearch服务器超时。

- 需要一个值

### `--cleanup-database`

在安装之前清理数据库

- 默认： `false`
- 不接受值

### `--sales-order-increment-prefix`

销售订单编号前缀

- 需要一个值

### `--use-sample-data`

使用示例数据

- 默认： `false`
- 不接受值

### `--enable-modules`

以逗号分隔的模块名称列表。 安装过程中必须包括此项。 可用的魔法参数“all”。

- 接受一个值

### `--disable-modules`

以逗号分隔的模块名称列表。 在安装过程中必须避免出现这种情况。 可用的魔法参数“all”。

- 接受一个值

### `--convert-old-scripts`

允许将旧脚本(InstallSchema、UpgradeSchema)转换为db_schema.xml格式

- 默认： `false`
- 接受一个值

### `--interactive`, `-i`

交互式Magento安装

- 默认： `false`
- 不接受值

### `--safe-mode`

在破坏性操作（如删除列）中安全安装带有转储的Magento

- 接受一个值

### `--data-restore`

从转储中恢复已删除的数据

- 接受一个值

### `--dry-run`

Magento安装将在模拟运行模式下运行

- 默认： `false`
- 接受一个值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:performance:generate-fixtures`

生成夹具

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```


### `profile`

配置文件配置文件的路径

- 必需

### `--skip-reindex`, `-s`

跳过重新索引

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:rollback`

回滚Magento应用程序代码库、媒体和数据库

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code-file`, `-c`

var/backups中的代码备份文件的基本名称

- 需要一个值

### `--media-file`, `-m`

var/备份中的媒体备份文件的基本名称

- 需要一个值

### `--db-file`, `-d`

var/备份中的db备份文件的基本名称

- 需要一个值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:static-content:deploy`

部署静态视图文件

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```


### `languages`

要为其输出静态视图文件的ISO-639语言代码列表（以空格分隔）。

- 默认： `[]`

- 数组

### `--force`, `-f`

以任意模式部署文件。

- 默认： `false`
- 不接受值

### `--strategy`, `-s`

使用指定的策略部署文件。

- 默认： `quick`
- 接受一个值

### `--area`, `-a`

仅为指定的区域生成文件。

- 默认： `all`
- 接受多个值

### `--exclude-area`

不要为指定的区域生成文件。

- 默认： `none`
- 接受多个值

### `--theme`, `-t`

仅为指定的主题生成静态视图文件。

- 默认： `all`
- 接受多个值

### `--exclude-theme`

不为指定的主题生成文件。

- 默认： `none`
- 接受多个值

### `--language`, `-l`

仅生成指定语言的文件。

- 默认： `all`
- 接受多个值

### `--exclude-language`

不生成指定语言的文件。

- 默认： `none`
- 接受多个值

### `--jobs`, `-j`

使用指定的作业数启用并行处理。

- 默认： `0`
- 接受一个值

### `--max-execution-time`

部署静态进程的最大预期执行时间（秒）。

- 默认： `900`
- 接受一个值

### `--symlink-locale`

为那些区域设置的文件创建符号链接，这些区域设置传递用于部署，但没有进行自定义。

- 默认： `false`
- 不接受值

### `--content-version`

如果在多个节点上运行部署，可以使用静态内容的自定义版本，以确保静态内容版本相同且缓存正常工作。

- 需要一个值

### `--refresh-content-version-only`

刷新静态内容的版本只能用于刷新浏览器缓存和CDN缓存中的静态内容。

- 默认： `false`
- 不接受值

### `--no-javascript`

不要部署JavaScript文件。

- 默认： `false`
- 不接受值

### `--no-js-bundle`

不部署JavaScript捆绑包文件。

- 默认： `false`
- 不接受值

### `--no-css`

不部署CSS文件。

- 默认： `false`
- 不接受值

### `--no-less`

请勿部署LESS文件。

- 默认： `false`
- 不接受值

### `--no-images`

不要部署映像。

- 默认： `false`
- 不接受值

### `--no-fonts`

不部署字体文件。

- 默认： `false`
- 不接受值

### `--no-html`

不部署HTML文件。

- 默认： `false`
- 不接受值

### `--no-misc`

请勿部署其他类型的文件（.md、.jbf、.csv等）。

- 默认： `false`
- 不接受值

### `--no-html-minify`

不要缩小HTML文件。

- 默认： `false`
- 不接受值

### `--no-parent`

不编译父主题。 仅在快速和标准策略中受支持。

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:store-config:set`

安装存储配置。 从2.2.0开始已弃用。请改用config：set

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--base-url`

商店应位于的URL。 已弃用，请使用config：set以及路径web/unsecure/base_url

- 需要一个值

### `--language`

默认语言代码。 已弃用，请使用config：set以及路径general/locale/code

- 需要一个值

### `--timezone`

默认时区代码。 已弃用，请使用config：set和path general/locale/timezone

- 需要一个值

### `--currency`

默认货币代码。 已弃用，请使用config：set以及路径currency/options/base、currency/options/default和currency/options/allow

- 需要一个值

### `--use-rewrites`

使用重写。 已弃用，请使用config：set以及路径web/seo/use_rewrites

- 需要一个值

### `--use-secure`

使用安全URL。 仅当SSL可用时启用此选项。 已弃用，请使用config：set以及路径web/secure/use_in_frontend

- 需要一个值

### `--base-url-secure`

SSL连接的基本URL。 已弃用，请使用config：set以及路径web/secure/base_url

- 需要一个值

### `--use-secure-admin`

使用SSL运行管理界面。 已弃用，请使用config：set以及路径web/secure/use_in_adminhtml

- 需要一个值

### `--admin-use-security-key`

是否在Magento管理员URL和表单中使用“安全密钥”功能。 已弃用，请使用config：set和path admin/security/use_form_key

- 需要一个值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:uninstall`

卸载Magento应用程序

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `setup:upgrade`

升级Magento应用程序、数据库数据和模式

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--keep-generated`

阻止删除生成的文件。 我们建议不要使用此选项，除非部署到生产环境。 有关更多信息，请咨询系统集成商或管理员。

- 默认： `false`
- 不接受值

### `--convert-old-scripts`

允许将旧脚本(InstallSchema、UpgradeSchema)转换为db_schema.xml格式

- 默认： `false`
- 接受一个值

### `--safe-mode`

在破坏性操作（如删除列）中安全安装带有转储的Magento

- 接受一个值

### `--data-restore`

从转储中恢复已删除的数据

- 接受一个值

### `--dry-run`

Magento安装将在模拟运行模式下运行

- 默认： `false`
- 接受一个值

### `--magento-init-params`

添加到任何命令以自定义Magento初始化参数，例如：&quot;MAGE_MODE=developer&amp;MAGE_DIRS[基础][path]=/var/www/example.com&amp;MAGE_DIRS[缓存][path]=/var/tmp/cache&quot;

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `store:list`

显示商店列表

```bash
bin/magento store:list
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `store:website:list`

显示网站列表

```bash
bin/magento store:website:list
```

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `support:backup:code`

创建代码备份

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

### `--name`

转储名称

- 接受一个值

### `--output`, `-o`

输出路径

- 接受一个值

### `--logs`, `-l`

包含日志

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `support:backup:db`

创建数据库备份

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

### `--name`

转储名称

- 接受一个值

### `--output`, `-o`

输出路径

- 接受一个值

### `--logs`, `-l`

包含日志

- 默认： `false`
- 不接受值

### `--ignore-sanitize`, `-i`

忽略清理

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `support:utility:check`

检查所需的备份实用程序

```bash
bin/magento support:utility:check [--hide-paths]
```

### `--hide-paths`

仅检查所需的控制台实用程序

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `support:utility:paths`

创建实用程序路径列表

```bash
bin/magento support:utility:paths [-f|--force]
```

### `--force`, `-f`

强制

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `theme:uninstall`

卸载主题

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```


### `theme`

主题的路径。 主题路径应指定为完整路径，即area/vendor/name。 例如，前端/Magento/空白

- 默认： `[]`

- 必需
- 数组

### `--backup-code`

进行代码备份（不包括临时文件）

- 默认： `false`
- 不接受值

### `--clear-static-content`, `-c`

清除生成的静态视图文件。

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `varnish:vcl:generate`

生成清漆VCL并将其回显到命令行

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--output-file OUTPUT-FILE]
```

### `--access-list`

可清除清漆的IP访问列表

- 默认： `localhost`
- 需要一个值

### `--backend-host`

Web后端的主机

- 默认： `localhost`
- 需要一个值

### `--backend-port`

Web后端的端口

- 默认： `8080`
- 需要一个值

### `--export-version`

清漆文件的版本

- 默认： `4`
- 需要一个值

### `--grace-period`

宽限期（以秒为单位）

- 默认： `300`
- 需要一个值

### `--output-file`

要写入vcl的文件的路径

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助\&lt;info>list\&lt;/info> 命令

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

### `--no-interaction`, `-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值