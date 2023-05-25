---
source-git-commit: ad7f05eaa5f144b5a8616307d65be635a0c499eb
workflow-type: tm+mt
source-wordcount: '29786'
ht-degree: 0%

---
# magento-cloud(云基础架构上的Adobe Commerce)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**版本**：1.42.0

此参考包含134个命令，这些命令可通过 `magento-cloud` 命令行工具。
初始列表是使用 `magento-cloud list` 云基础架构上的Adobe Commerce中的命令。

>[!NOTE]
>
>此引用从应用程序代码库生成。 要更改内容，您可以更新中相应命令实施的源代码 [代码库](https://github.com/magento) 存储库并提交更改以供审核。 另一种方法是 _向我们提供反馈_ （在右上角找到链接）。 有关贡献准则，请参阅 [代码投稿](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_completion`

BASH完成挂钩。

```bash
_completion [-g|--generate-hook] [-p|--program PROGRAM] [-m|--multiple] [--shell-type [SHELL-TYPE]]
```

### `--generate-hook`, `-g`

生成设置此应用程序完成情况的BASH代码。

- 默认： `false`
- 不接受值

### `--program`, `-p`

应触发完成的程序名称 &lt;comment>（默认为绝对应用程序路径）&lt;/comment>.

- 需要一个值

### `--multiple`, `-m`

生成的挂接可用于多个应用程序。

- 默认： `false`
- 不接受值

### `--shell-type`

设置壳类型（zsh或bash）。 否则，将自动确定。

- 接受一个值


## `bot`

Magento云机器人

```bash
magento-cloud bot [--party] [--parrot]
```

### `--party`



- 默认： `false`
- 不接受值

### `--parrot`



- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `clear-cache`

清除CLI缓存

```bash
magento-cloud clear-cache
```


```bash
clearcache
```


```bash
cc
```

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `decode`

对编码字符串(如MAGENTO_CLOUD_VARIABLES)进行解码

```bash
magento-cloud decode [-P|--property PROPERTY] [--] <value>
```


### `value`

要解码的变量值

- 必需

### `--property`, `-P`

要在变量中查看的属性

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `docs`

打开联机文档

```bash
magento-cloud docs [--browser BROWSER] [--pipe] [--] [<search>]...
```


### `search`

搜索词

- 默认： `[]`

- 数组

### `--browser`

用于打开URL的浏览器。 将0设置为none。

- 需要一个值

### `--pipe`

将URL输出到stdout。

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `help`

显示命令的帮助

```bash
magento-cloud help [--format FORMAT] [--raw] [--] [<command_name>]
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

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `legacy-migrate`

从旧文件结构迁移

```bash
magento-cloud legacy-migrate [--no-backup]
```

### `--no-backup`

请勿创建项目的备份。

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `list`

列出命令

```bash
magento-cloud list [--raw] [--format FORMAT] [--all] [--] [<namespace>]
```


### `command`

要执行的命令

- 必需

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

### `--all`

显示所有命令，包括隐藏的命令

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `multi`

在多个项目上执行命令

```bash
magento-cloud multi [-p|--projects PROJECTS] [--continue] [--sort SORT] [--reverse] [--] <cmd> (<cmd>)...
```


### `cmd`

要执行的命令

- 默认： `[]`

- 必需
- 数组

### `--projects`, `-p`

项目ID列表，以逗号和/或空格分隔

- 需要一个值

### `--continue`

即使遇到异常，仍继续运行命令

- 默认： `false`
- 不接受值

### `--sort`

用于对项目选项列表进行排序的属性

- 默认： `title`
- 需要一个值

### `--reverse`

反转项目选项的顺序

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `web`

打开Web用户界面

```bash
magento-cloud web [--browser BROWSER] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--browser`

用于打开URL的浏览器。 将0设置为none。

- 需要一个值

### `--pipe`

将URL输出到stdout。

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `welcome`

欢迎使用Magento云

```bash
magento-cloud welcome
```

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `winky`



```bash
magento-cloud winky
```

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `activity:cancel`

取消活动

```bash
magento-cloud activity:cancel [--type TYPE] [--exclude-type EXCLUDE-TYPE] [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

活动ID 默认为最近的可取消活动。


### `--type`

按类型筛选（在选择默认活动时）。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。 %字符可用作该类型的通配符，例如“%var%”，用于选择变量相关的活动。

- 默认： `[]`
- 需要一个值

### `--exclude-type`

按类型排除（在选择默认活动时）。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。 %字符可用作通配符以排除类型。

- 默认： `[]`
- 需要一个值

### `--all`, `-a`

检查所有环境上的近期活动（在选择默认活动时）

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `activity:get`

查看有关单个活动的详细信息

```bash
magento-cloud activity:get [-P|--property PROPERTY] [--type TYPE] [--exclude-type EXCLUDE-TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<id>]
```


### `id`

活动ID 默认为最近活动。


### `--property`, `-P`

要查看的属性

- 需要一个值

### `--type`

按类型筛选（在选择默认活动时）。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。 %字符可用作该类型的通配符，例如“%var%”，用于选择变量相关的活动。

- 默认： `[]`
- 需要一个值

### `--exclude-type`

按类型排除（在选择默认活动时）。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。 %字符可用作通配符以排除类型。

- 默认： `[]`
- 需要一个值

### `--state`

按状态筛选（在选择默认活动时）：in_progress、pending、complete或cancelled。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--result`

按结果筛选（选择默认活动时）：成功或失败

- 需要一个值

### `--incomplete`, `-i`

仅包括未完成的活动（在选择默认活动时）。 这是一个缩写 &lt;info>—state=in_progress，pending&lt;/info>

- 默认： `false`
- 不接受值

### `--all`, `-a`

检查所有环境上的近期活动（在选择默认活动时）

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `activity:list`

获取环境或项目的活动列表

```bash
magento-cloud activity:list [-t|--type TYPE] [-x|--exclude-type EXCLUDE-TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
activities
```


```bash
act
```

### `--type`, `-t`

按类型筛选活动如果列表作为单个值（例如“a，b，c”）提供，则它将被逗号和/或空格拆分。 %字符可用作该类型的通配符，例如“%var%”，用于选择变量相关的活动。

- 默认： `[]`
- 需要一个值

### `--exclude-type`, `-x`

按类型排除活动。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。 %字符可用作通配符以排除类型。

- 默认： `[]`
- 需要一个值

### `--limit`

限制显示的结果数量

- 默认： `10`
- 需要一个值

### `--start`

将仅列出在此日期之前创建的活动

- 需要一个值

### `--state`

按状态筛选活动： in_progress、pending、complete或canceled。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--result`

按结果筛选活动：成功或失败

- 需要一个值

### `--incomplete`, `-i`

仅列出未完成的活动

- 默认： `false`
- 不接受值

### `--all`, `-a`

列出所有环境中的活动

- 默认： `false`
- 不接受值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：id*、created*、description*、progress*、state*、result*、completed、environments、type （* =默认列）。 字符“+”可用作默认列的占位符。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `activity:log`

显示活动的日志

```bash
magento-cloud activity:log [--refresh REFRESH] [-t|--timestamps] [--type TYPE] [--exclude-type EXCLUDE-TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

活动ID 默认为最近活动。


### `--refresh`

活动刷新间隔（秒）。 设置为0可禁用刷新。

- 默认： `3`
- 需要一个值

### `--timestamps`, `-t`

在每条消息旁边显示时间戳

- 默认： `false`
- 不接受值

### `--type`

按类型筛选（在选择默认活动时）。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。 %字符可用作该类型的通配符，例如“%var%”，用于选择变量相关的活动。

- 默认： `[]`
- 需要一个值

### `--exclude-type`

按类型排除（在选择默认活动时）。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。 %字符可用作通配符以排除类型。

- 默认： `[]`
- 需要一个值

### `--state`

按状态筛选（在选择默认活动时）：in_progress、pending、complete或cancelled。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--result`

按结果筛选（选择默认活动时）：成功或失败

- 需要一个值

### `--incomplete`, `-i`

仅包括未完成的活动（在选择默认活动时）。 这是一个缩写 &lt;info>—state=in_progress，pending&lt;/info>

- 默认： `false`
- 不接受值

### `--all`, `-a`

检查所有环境上的近期活动（在选择默认活动时）

- 默认： `false`
- 不接受值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `api:curl`

在Magento云API上运行经过身份验证的cURL请求

```bash
magento-cloud api:curl [-X|--request REQUEST] [-d|--data DATA] [--json JSON] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [--] [<path>]
```


### `path`

API路径


### `--request`, `-X`

要使用的请求方法

- 需要一个值

### `--data`, `-d`

要发送的数据

- 需要一个值

### `--json`

要发送的JSON数据

- 需要一个值

### `--include`, `-i`

在输出中包含标头

- 默认： `false`
- 不接受值

### `--head`, `-I`

仅获取标头

- 默认： `false`
- 不接受值

### `--disable-compression`

不要使用curl —compressed标志

- 默认： `false`
- 不接受值

### `--enable-glob`

启用curl通配（删除 — globoff标志）

- 默认： `false`
- 不接受值

### `--fail`, `-f`

失败，错误响应中没有输出

- 默认： `false`
- 不接受值

### `--header`, `-H`

额外的标头

- 默认： `[]`
- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `app:config-get`

查看应用程序的配置

```bash
magento-cloud app:config-get [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

### `--property`, `-P`

要查看的配置属性

- 需要一个值

### `--refresh`

是否刷新缓存

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--identity-file`, `-i`

[已弃用选项，不再使用]

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `app:list`

列出项目中的应用程序

```bash
magento-cloud apps [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
apps
```

### `--refresh`

是否刷新缓存

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：名称*、类型*、磁盘、路径、大小（* =缺省列）。 字符“+”可用作默认列的占位符。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `auth:api-token-login`

使用API令牌登录Magento云

```bash
magento-cloud auth:api-token-login
```

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `auth:browser-login`

通过浏览器登录Magento云

```bash
magento-cloud login [-f|--force] [--browser BROWSER] [--pipe]
```


```bash
login
```

### `--force`, `-f`

再次登录，即使已登录

- 默认： `false`
- 不接受值

### `--browser`

用于打开URL的浏览器。 将0设置为none。

- 需要一个值

### `--pipe`

将URL输出到stdout。

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `auth:info`

显示您的帐户信息

```bash
magento-cloud auth:info [--no-auto-login] [-P|--property PROPERTY] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--] [<property>]
```


### `property`

要查看的帐户属性


### `--no-auto-login`

跳过自动登录。 如果未登录，则不会输出任何内容，并且退出代码将为0（假定没有其他错误）。

- 默认： `false`
- 不接受值

### `--property`, `-P`

要查看的帐户属性（替代语法）

- 需要一个值

### `--refresh`

是否刷新缓存

- 默认： `false`
- 不接受值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `auth:logout`

注销Magento Cloud

```bash
magento-cloud logout [-a|--all] [--other]
```


```bash
logout
```

### `--all`, `-a`

从所有本地会话注销

- 默认： `false`
- 不接受值

### `--other`

从其他本地会话注销

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `auth:password-login`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已弃用 ]&lt;/>使用用户名和密码登录Magento云

```bash
magento-cloud auth:password-login
```


```bash
auth:login
```

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `auth:token`

获取OAuth 2访问令牌以获取MagentoCloud API的请求

```bash
magento-cloud auth:token [-H|--header] [-W|--no-warn]
```

### `--header`, `-H`

为令牌添加前缀“Authorization： Bearer ”，以发出RFC 6750标头

- 默认： `false`
- 不接受值

### `--no-warn`, `-W`

禁止默认打印到stderr的警告。 此选项比重定向stderr更可取，因为这样会隐藏其他可能有用的消息。

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `blackfire:setup`

为项目设置Blackfire.io集成

```bash
magento-cloud blackfire:setup [--server_id SERVER_ID] [--server_token SERVER_TOKEN] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

### `--server_id`

服务器ID

- 需要一个值

### `--server_token`

服务器令牌

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `blue-green:conclude`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ALPHA ]&lt;/>完成蓝/绿部署

```bash
magento-cloud blue-green:conclude [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `blue-green:deploy`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ALPHA ]&lt;/>执行蓝/绿部署

```bash
magento-cloud blue-green:deploy [--routing-percentage ROUTING-PERCENTAGE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--routing-percentage`

设置最新版本的工艺路线百分比

- 默认： `100`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `blue-green:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ALPHA ]&lt;/>启用蓝/绿部署

```bash
magento-cloud blue-green:enable [-%|--routing-percentage ROUTING-PERCENTAGE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--routing-percentage`, `-%`

设置最新版本的工艺路线百分比

- 默认： `100`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `certificate:add`

将SSL证书添加到项目

```bash
magento-cloud certificate:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

### `--cert`

证书文件的路径

- 需要一个值

### `--key`

证书私钥文件的路径

- 需要一个值

### `--chain`

证书链文件的路径

- 默认： `[]`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `certificate:delete`

从项目中删除证书

```bash
magento-cloud certificate:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <id>
```


### `id`

证书ID（或其开头）

- 必需

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `certificate:get`

查看证书

```bash
magento-cloud certificate:get [-P|--property PROPERTY] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--] <id>
```


### `id`

证书ID（或其开头）

- 必需

### `--property`, `-P`

要查看的证书属性

- 需要一个值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `certificate:list`

列出项目证书

```bash
magento-cloud certificate:list [--domain DOMAIN] [--exclude-domain EXCLUDE-DOMAIN] [--issuer ISSUER] [--only-auto] [--no-auto] [--ignore-expiry] [--only-expired] [--no-expired] [--pipe-domains] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
certificates
```


```bash
certs
```

### `--domain`

按域名筛选（不区分大小写的搜索）

- 需要一个值

### `--exclude-domain`

排除证书，按域名匹配（搜索不区分大小写）

- 需要一个值

### `--issuer`

按颁发者筛选

- 需要一个值

### `--only-auto`

仅显示自动配置的证书

- 默认： `false`
- 不接受值

### `--no-auto`

仅显示手动添加的证书

- 默认： `false`
- 不接受值

### `--ignore-expiry`

显示已过期和未过期的证书

- 默认： `false`
- 不接受值

### `--only-expired`

仅显示过期的证书

- 默认： `false`
- 不接受值

### `--no-expired`

仅显示未过期的证书（默认）

- 默认： `false`
- 不接受值

### `--pipe-domains`

仅返回证书涵盖的域名列表

- 默认： `false`
- 不接受值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：已创建、域、过期、ID、颁发者。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `commit:get`

显示提交详细信息

```bash
magento-cloud commit:get [-P|--property PROPERTY] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--] [<commit>]
```


### `commit`

承诺SHA。 这还可以接受父项提交的“HEAD”、脱字符号(^)或波状符号(~)后缀。

- 默认： `HEAD`


### `--property`, `-P`

要显示的提交属性。

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--format`

已弃用

- 需要一个值

### `--columns`

已弃用

- 默认： `[]`
- 需要一个值

### `--no-header`

已弃用

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `commit:list`

列表提交

```bash
magento-cloud commits [--limit LIMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<commit>]
```


```bash
commits
```


### `commit`

起始Git承诺SHA。 这还可以接受父项提交的“HEAD”、脱字符号(^)或波状符号(~)后缀。


### `--limit`

要显示的提交数量。

- 默认： `10`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：作者、日期、sha、概要。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `db:dump`

创建远程数据库的本地转储

```bash
magento-cloud db:dump [--schema SCHEMA] [-f|--file FILE] [-d|--directory DIRECTORY] [-z|--gzip] [-t|--timestamp] [-o|--stdout] [--table TABLE] [--exclude-table EXCLUDE-TABLE] [--schema-only] [--charset CHARSET] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```


```bash
sql-dump
```


```bash
environment:sql-dump
```

### `--schema`

要转储的架构。 省略以使用默认架构（通常为“main”）。

- 需要一个值

### `--file`, `-f`

转储的自定义文件名

- 需要一个值

### `--directory`, `-d`

转储的自定义目录

- 需要一个值

### `--gzip`, `-z`

使用gzip压缩转储

- 默认： `false`
- 不接受值

### `--timestamp`, `-t`

向转储文件名添加时间戳

- 默认： `false`
- 不接受值

### `--stdout`, `-o`

输出到STDOUT而不是文件

- 默认： `false`
- 不接受值

### `--table`

要包含的表

- 默认： `[]`
- 需要一个值

### `--exclude-table`

要排除的表

- 默认： `[]`
- 需要一个值

### `--schema-only`

仅转储架构，无数据

- 默认： `false`
- 不接受值

### `--charset`

转储的字符集编码

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--relationship`, `-r`

要使用的服务关系

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `db:size`

估计数据库的磁盘使用量

```bash
magento-cloud db:size [-B|--bytes] [-C|--cleanup] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE]
```

### `--bytes`, `-B`

以字节为单位显示大小。

- 默认： `false`
- 不接受值

### `--cleanup`, `-C`

检查是否可以清除表并显示建议（仅限InnoDb）。

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--relationship`, `-r`

要使用的服务关系

- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：max、percent_used、used。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `db:sql`

在远程数据库上运行SQL

```bash
magento-cloud sql [--raw] [--schema SCHEMA] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [--] [<query>]
```


```bash
sql
```


```bash
environment:sql
```


### `query`

要执行的SQL语句


### `--raw`

生成非表格式的原始输出

- 默认： `false`
- 不接受值

### `--schema`

要使用的架构。 省略以使用默认架构（通常为“main”）。 传递空字符串以不使用任何架构。

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--relationship`, `-r`

要使用的服务关系

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `domain:add`

向项目添加新域

```bash
magento-cloud domain:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

域名

- 必需

### `--cert`

此域的证书文件的路径

- 需要一个值

### `--key`

所提供证书的私钥文件的路径。

- 需要一个值

### `--chain`

提供的证书的证书链文件的路径

- 默认： `[]`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `domain:delete`

从项目中删除域

```bash
magento-cloud domain:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

域名

- 必需

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `domain:get`

显示域的详细信息

```bash
magento-cloud domain:get [-P|--property PROPERTY] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--] [<name>]
```


### `name`

域名


### `--property`, `-P`

要查看的域属性

- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `domain:list`

获取所有域的列表

```bash
magento-cloud domains [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
domains
```

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：name*、ssl*、created_at*、updated_at （* =缺省列）。 字符“+”可用作默认列的占位符。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `domain:update`

更新域

```bash
magento-cloud domain:update [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

域名

- 必需

### `--cert`

此域的证书文件的路径

- 需要一个值

### `--key`

所提供证书的私钥文件的路径。

- 需要一个值

### `--chain`

提供的证书的证书链文件的路径

- 默认： `[]`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:activate`

激活环境

```bash
magento-cloud environment:activate [--parent PARENT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```


### `environment`

要激活的环境

- 默认： `[]`

- 数组

### `--parent`

在激活之前设置新的环境父级

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:branch`

分支环境

```bash
magento-cloud branch [--title TITLE] [--type TYPE] [--force] [--no-clone-parent] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-i|--identity-file IDENTITY-FILE] [--] [<id>] [<parent>]
```


```bash
branch
```


### `id`

新环境的ID（分支名称）


### `parent`

新环境的父级


### `--title`

新环境的标题

- 需要一个值

### `--type`

新环境的类型

- 需要一个值

### `--force`

即使分支无法本地签出，仍创建新环境

- 默认： `false`
- 不接受值

### `--no-clone-parent`

不克隆父分支的数据

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:checkout`

查看环境

```bash
magento-cloud checkout [-i|--identity-file IDENTITY-FILE] [--] [<id>]
```


```bash
checkout
```


### `id`

要签出的环境的ID。 例如：“sprint2”


### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:curl`

在环境的API上运行经过身份验证的cURL请求

```bash
magento-cloud environment:curl [-X|--request REQUEST] [-d|--data DATA] [--json JSON] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


### `path`

API路径


### `--request`, `-X`

要使用的请求方法

- 需要一个值

### `--data`, `-d`

要发送的数据

- 需要一个值

### `--json`

要发送的JSON数据

- 需要一个值

### `--include`, `-i`

在输出中包含标头

- 默认： `false`
- 不接受值

### `--head`, `-I`

仅获取标头

- 默认： `false`
- 不接受值

### `--disable-compression`

不要使用curl —compressed标志

- 默认： `false`
- 不接受值

### `--enable-glob`

启用curl通配（删除 — globoff标志）

- 默认： `false`
- 不接受值

### `--fail`, `-f`

失败，错误响应中没有输出

- 默认： `false`
- 不接受值

### `--header`, `-H`

额外的标头

- 默认： `[]`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:delete`

删除一个或多个环境

```bash
magento-cloud environment:delete [--delete-branch] [--no-delete-branch] [--type TYPE] [-t|--only-type ONLY-TYPE] [--exclude EXCLUDE] [--exclude-type EXCLUDE-TYPE] [--inactive] [--merged] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```


```bash
environment:deactivate
```


### `environment`

要删除的环境。 %字符可用作通配符。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`

- 数组

### `--delete-branch`

删除Git分支（非活动环境）

- 默认： `false`
- 不接受值

### `--no-delete-branch`

请勿删除Git分支（非活动环境）

- 默认： `false`
- 不接受值

### `--type`

删除某个类型的所有环境（添加到任何其他选定的环境）如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--only-type`, `-t`

仅删除特定类型的环境如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--exclude`

不删除的环境。 %字符可用作通配符。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--exclude-type`

不删除的环境类型如果列表作为单个值（例如“a，b，c”）给出，则列表将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--inactive`

删除所有非活动环境（添加到任何其他选定的环境）

- 默认： `false`
- 不接受值

### `--merged`

删除所有合并的环境（添加到任何其他选定的环境）

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:http-access`

更新环境的HTTP访问设置

```bash
magento-cloud httpaccess [--access ACCESS] [--auth AUTH] [--enabled ENABLED] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```


```bash
httpaccess
```

### `--access`

访问限制，格式为“permission：address”。 使用0可清除所有地址。

- 默认： `[]`
- 需要一个值

### `--auth`

采用“username：password”格式的HTTP基本身份验证凭据。 使用0可清除所有凭据。

- 默认： `[]`
- 需要一个值

### `--enabled`

是否应启用访问控制：1表示启用，0表示禁用

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:info`

读取或设置环境的属性

```bash
magento-cloud environment:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```


```bash
environment:metadata
```


### `property`

属性的名称


### `value`

为属性设置新值


### `--refresh`

是否刷新缓存

- 默认： `false`
- 不接受值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:init`

从公共Git存储库初始化环境

```bash
magento-cloud environment:init [--profile PROFILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <url>
```


### `url`

Git存储库的URL

- 必需

### `--profile`

配置文件的名称

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:list`

获取环境列表

```bash
magento-cloud environment:list [-I|--no-inactive] [--pipe] [--refresh REFRESH] [--sort SORT] [--reverse] [--type TYPE] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
environments
```


```bash
env
```

### `--no-inactive`, `-I`

不显示非活动环境

- 默认： `false`
- 不接受值

### `--pipe`

输出环境ID的简单列表。

- 默认： `false`
- 不接受值

### `--refresh`

是否刷新列表。

- 默认： `1`
- 需要一个值

### `--sort`

排序依据的属性

- 默认： `title`
- 需要一个值

### `--reverse`

按反向（降序）排序

- 默认： `false`
- 不接受值

### `--type`

按环境类型筛选列表。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：id*、title*、status*、type*、created、machine_name、updated （* =默认列）。 字符“+”可用作默认列的占位符。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:logs`

读取环境的日志

```bash
magento-cloud log [--lines LINES] [--tail] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [--] [<type>]
```


```bash
log
```


```bash
logs
```


### `type`

日志类型，如“访问”或“错误”


### `--lines`

要显示的行数

- 默认： `100`
- 需要一个值

### `--tail`

持续跟踪日志

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--worker`

工作人员姓名

- 需要一个值

### `--instance`, `-I`

实例ID

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:merge`

合并环境

```bash
magento-cloud merge [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```


```bash
merge
```


### `environment`

要合并的环境


### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:push`

将代码推送到环境

```bash
magento-cloud push [--target TARGET] [-f|--force] [--force-with-lease] [-u|--set-upstream] [--activate] [--parent PARENT] [--type TYPE] [--no-clone-parent] [-W|--no-wait] [--wait] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-i|--identity-file IDENTITY-FILE] [--] [<source>]
```


```bash
push
```


### `source`

源引用：分支名称或提交哈希

- 默认： `HEAD`


### `--target`

目标分支名称

- 需要一个值

### `--force`, `-f`

允许非快速转发更新

- 默认： `false`
- 不接受值

### `--force-with-lease`

如果远程跟踪分支是最新的，则允许非快速转发更新

- 默认： `false`
- 不接受值

### `--set-upstream`, `-u`

将目标环境设置为源分支的上游

- 默认： `false`
- 不接受值

### `--activate`

在推送之前激活环境

- 默认： `false`
- 不接受值

### `--branch`

已弃用：别名 — activate

- 默认： `false`
- 不接受值

### `--parent`

设置新环境父级（仅用于 — activate）

- 需要一个值

### `--type`

设置环境类型（仅用于 — activate ）

- 需要一个值

### `--no-clone-parent`

不克隆父分支的数据（仅用于 — activate）

- 默认： `false`
- 不接受值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:redeploy`

重新部署环境

```bash
magento-cloud redeploy [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```


```bash
redeploy
```

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:relationships`

显示环境关系

```bash
magento-cloud relationships [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<environment>]
```


```bash
relationships
```


### `environment`

环境


### `--property`, `-P`

要查看的关系属性

- 需要一个值

### `--refresh`

是否刷新关系

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:scp`

使用scp将文件复制到当前环境或从当前环境复制文件

```bash
magento-cloud scp [-r|--recursive] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...
```


```bash
scp
```


### `files`

要复制的文件。 使用remote：前缀定义远程位置。

- 默认： `[]`

- 数组

### `--recursive`, `-r`

递归复制整个目录

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--worker`

工作人员姓名

- 需要一个值

### `--instance`, `-I`

实例ID

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:set-remote`

设置要映射到分支的远程环境

```bash
magento-cloud environment:set-remote <environment> [<branch>]
```


### `environment`

环境计算机名称。 设置为0可删除分支的映射

- 必需

### `branch`

要映射的Git分支（默认为当前分支）


### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:ssh`

SSH到当前环境

```bash
magento-cloud ssh [--pipe] [--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE] [--] [<cmd>]...
```


```bash
ssh
```


### `cmd`

在环境中运行的命令。

- 默认： `[]`

- 数组

### `--pipe`

仅输出SSH URL。

- 默认： `false`
- 不接受值

### `--all`

输出所有SSH URL（对于每个应用程序）。

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--worker`

工作人员姓名

- 需要一个值

### `--instance`, `-I`

实例ID

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:synchronize`

同步环境的代码和/或来自其父级的数据

```bash
magento-cloud sync [--rebase] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<synchronize>]...
```


```bash
sync
```


### `synchronize`

要同步的内容：“代码”、“数据”或两者

- 默认： `[]`

- 数组

### `--rebase`

通过重新基准而不是合并来同步代码

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:url`

获取环境的公共URL

```bash
magento-cloud url [-1|--primary] [--browser BROWSER] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
url
```

### `--primary`, `-1`

仅返回主路由的URL

- 默认： `false`
- 不接受值

### `--browser`

用于打开URL的浏览器。 将0设置为none。

- 需要一个值

### `--pipe`

将URL输出到stdout。

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `environment:xdebug`

在环境中打开通往Xdebug的隧道

```bash
magento-cloud xdebug [--port PORT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```


```bash
xdebug
```

### `--port`

本地端口

- 默认： `9000`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--worker`

工作人员姓名

- 需要一个值

### `--instance`, `-I`

实例ID

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `integration:activity:get`

查看有关单个集成活动的详细信息

```bash
magento-cloud integration:activity:get [-P|--property PROPERTY] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<integration>] [<activity>]
```


### `integration`

集成ID。 保留为空将从列表中选择。


### `activity`

活动ID 默认为最新的集成活动。


### `--property`, `-P`

要查看的属性

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

[已弃用选项，未使用]

- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `integration:activity:list`

获取集成的活动列表

```bash
magento-cloud i:act [--type TYPE] [-x|--exclude-type EXCLUDE-TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


```bash
i:act
```


```bash
integration:activities
```


### `id`

集成ID。 保留为空将从列表中选择。


### `--type`

按类型筛选活动。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--exclude-type`, `-x`

按类型排除活动。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。 %字符可用作通配符以排除类型。

- 默认： `[]`
- 需要一个值

### `--limit`

限制显示的结果数量

- 默认： `10`
- 需要一个值

### `--start`

将仅列出在此日期之前创建的活动

- 需要一个值

### `--state`

按状态筛选活动。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--result`

按结果筛选活动

- 需要一个值

### `--incomplete`, `-i`

仅列出未完成的活动

- 默认： `false`
- 不接受值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：id*、created*、description*、type*、state*、result*、completed （* =默认列）。 字符“+”可用作默认列的占位符。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

[已弃用选项，未使用]

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `integration:activity:log`

显示集成活动的日志

```bash
magento-cloud integration:activity:log [-t|--timestamps] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<integration>] [<activity>]
```


### `integration`

集成ID。 保留为空将从列表中选择。


### `activity`

活动ID 默认为最新的集成活动。


### `--timestamps`, `-t`

在每条消息旁边显示时间戳

- 默认： `false`
- 不接受值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

[已弃用选项，未使用]

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `integration:add`

将集成添加到项目

```bash
magento-cloud integration:add [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--license-key LICENSE-KEY] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [--category CATEGORY] [--index INDEX] [--sourcetype SOURCETYPE] [--protocol PROTOCOL] [--syslog-host SYSLOG-HOST] [--syslog-port SYSLOG-PORT] [--facility FACILITY] [--message-format MESSAGE-FORMAT] [--auth-mode AUTH-MODE] [--auth-token AUTH-TOKEN] [--verify-tls VERIFY-TLS] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

### `--type`

集成类型(“bitbucket”、“bitbucket_server”、“github”、“gitlab”、“webhook”、“health.email”、“health.pagerduty”、“health.slack”、“health.webhook”、“script”、“newrelic”、“splunk”、“sumologic”、“syslog”)

- 需要一个值

### `--base-url`

服务器安装的基本URL

- 需要一个值

### `--username`

Bitbucket服务器用户名

- 需要一个值

### `--token`

集成的身份验证或访问令牌

- 需要一个值

### `--key`

Bitbucket OAuth使用者密钥

- 需要一个值

### `--secret`

Bitbucket OAuth使用者密码

- 需要一个值

### `--license-key`

New Relic日志许可证密钥

- 需要一个值

### `--server-project`

项目（例如“namespace/repo”）

- 需要一个值

### `--repository`

要跟踪的存储库（例如“所有者/存储库”）

- 需要一个值

### `--build-merge-requests`

GitLab：将合并请求作为环境构建

- 默认： `true`
- 需要一个值

### `--build-pull-requests`

将每个拉取请求构建为一个环境

- 默认： `true`
- 需要一个值

### `--build-draft-pull-requests`

构建草稿拉取请求

- 默认： `true`
- 需要一个值

### `--build-pull-requests-post-merge`

根据合并后的状态构建拉取请求

- 默认： `false`
- 需要一个值

### `--build-wip-merge-requests`

GitLab：构建WIP合并请求

- 默认： `true`
- 需要一个值

### `--merge-requests-clone-parent-data`

GitLab：克隆合并请求的数据

- 默认： `true`
- 需要一个值

### `--pull-requests-clone-parent-data`

为拉取请求克隆父环境的数据

- 默认： `true`
- 需要一个值

### `--resync-pull-requests`

重新同步每个内部版本上的拉取请求环境数据

- 默认： `false`
- 需要一个值

### `--fetch-branches`

从远程获取所有分支（作为非活动环境）

- 默认： `true`
- 需要一个值

### `--prune-branches`

删除远程上不存在的分支

- 默认： `true`
- 需要一个值

### `--url`

集成的URL或API端点

- 需要一个值

### `--shared-key`

Webhook： JWS共享密钥

- 需要一个值

### `--file`

包含要上载的脚本的本地文件的名称

- 需要一个值

### `--events`

要执行操作的事件列表，例如environment.push

- 默认： `*`
- 需要一个值

### `--states`

要执行操作的状态列表，例如pending、in_progress、complete

- 默认： `complete`
- 需要一个值

### `--environments`

要包含的环境ID

- 默认： `*`
- 需要一个值

### `--excluded-environments`

要排除的环境ID

- 默认： `[]`
- 需要一个值

### `--from-address`

[可选] 警报电子邮件的自定义发件人地址

- 需要一个值

### `--recipients`

收件人电子邮件地址

- 默认： `[]`
- 需要一个值

### `--channel`

Slack渠道

- 需要一个值

### `--routing-key`

PagerDuty路由密钥

- 需要一个值

### `--category`

Sumo逻辑类别，用于筛选

- 需要一个值

### `--index`

Splunk索引

- 需要一个值

### `--sourcetype`

Splunk事件源类型

- 需要一个值

### `--protocol`

Syslog传输协议(&#39;tcp&#39;、&#39;udp&#39;、&#39;tls&#39;)

- 默认： `tls`
- 需要一个值

### `--syslog-host`

Syslog中继/收集器主机

- 需要一个值

### `--syslog-port`

Syslog中继/收集器端口

- 需要一个值

### `--facility`

Syslog工具

- 默认： `1`
- 需要一个值

### `--message-format`

Syslog消息格式（“rfc3164”或“rfc5424”）

- 默认： `rfc5424`
- 需要一个值

### `--auth-mode`

身份验证模式（“prefix”或“structured_data”）

- 默认： `prefix`
- 需要一个值

### `--auth-token`

身份验证令牌

- 需要一个值

### `--verify-tls`

是否应启用HTTPS证书验证（推荐）

- 默认： `true`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `integration:delete`

从项目中删除集成

```bash
magento-cloud integration:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

集成ID。 保留为空将从列表中选择。


### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `integration:get`

查看集成的详细信息

```bash
magento-cloud integration:get [-P|--property [PROPERTY]] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<id>]
```


### `id`

集成ID。 保留为空将从列表中选择。


### `--property`, `-P`

要查看的集成属性

- 接受一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `integration:list`

查看项目集成的列表

```bash
magento-cloud integrations [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
integrations
```

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：id、摘要、类型。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `integration:update`

更新集成

```bash
magento-cloud integration:update [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--license-key LICENSE-KEY] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [--category CATEGORY] [--index INDEX] [--sourcetype SOURCETYPE] [--protocol PROTOCOL] [--syslog-host SYSLOG-HOST] [--syslog-port SYSLOG-PORT] [--facility FACILITY] [--message-format MESSAGE-FORMAT] [--auth-mode AUTH-MODE] [--auth-token AUTH-TOKEN] [--verify-tls VERIFY-TLS] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

要更新的集成的ID


### `--type`

集成类型(“bitbucket”、“bitbucket_server”、“github”、“gitlab”、“webhook”、“health.email”、“health.pagerduty”、“health.slack”、“health.webhook”、“script”、“newrelic”、“splunk”、“sumologic”、“syslog”)

- 需要一个值

### `--base-url`

服务器安装的基本URL

- 需要一个值

### `--username`

Bitbucket服务器用户名

- 需要一个值

### `--token`

集成的身份验证或访问令牌

- 需要一个值

### `--key`

Bitbucket OAuth使用者密钥

- 需要一个值

### `--secret`

Bitbucket OAuth使用者密码

- 需要一个值

### `--license-key`

New Relic日志许可证密钥

- 需要一个值

### `--server-project`

项目（例如“namespace/repo”）

- 需要一个值

### `--repository`

要跟踪的存储库（例如“所有者/存储库”）

- 需要一个值

### `--build-merge-requests`

GitLab：将合并请求作为环境构建

- 默认： `true`
- 需要一个值

### `--build-pull-requests`

将每个拉取请求构建为一个环境

- 默认： `true`
- 需要一个值

### `--build-draft-pull-requests`

构建草稿拉取请求

- 默认： `true`
- 需要一个值

### `--build-pull-requests-post-merge`

根据合并后的状态构建拉取请求

- 默认： `false`
- 需要一个值

### `--build-wip-merge-requests`

GitLab：构建WIP合并请求

- 默认： `true`
- 需要一个值

### `--merge-requests-clone-parent-data`

GitLab：克隆合并请求的数据

- 默认： `true`
- 需要一个值

### `--pull-requests-clone-parent-data`

为拉取请求克隆父环境的数据

- 默认： `true`
- 需要一个值

### `--resync-pull-requests`

重新同步每个内部版本上的拉取请求环境数据

- 默认： `false`
- 需要一个值

### `--fetch-branches`

从远程获取所有分支（作为非活动环境）

- 默认： `true`
- 需要一个值

### `--prune-branches`

删除远程上不存在的分支

- 默认： `true`
- 需要一个值

### `--url`

集成的URL或API端点

- 需要一个值

### `--shared-key`

Webhook： JWS共享密钥

- 需要一个值

### `--file`

包含要上载的脚本的本地文件的名称

- 需要一个值

### `--events`

要执行操作的事件列表，例如environment.push

- 默认： `*`
- 需要一个值

### `--states`

要执行操作的状态列表，例如pending、in_progress、complete

- 默认： `complete`
- 需要一个值

### `--environments`

要包含的环境ID

- 默认： `*`
- 需要一个值

### `--excluded-environments`

要排除的环境ID

- 默认： `[]`
- 需要一个值

### `--from-address`

[可选] 警报电子邮件的自定义发件人地址

- 需要一个值

### `--recipients`

收件人电子邮件地址

- 默认： `[]`
- 需要一个值

### `--channel`

Slack渠道

- 需要一个值

### `--routing-key`

PagerDuty路由密钥

- 需要一个值

### `--category`

Sumo逻辑类别，用于筛选

- 需要一个值

### `--index`

Splunk索引

- 需要一个值

### `--sourcetype`

Splunk事件源类型

- 需要一个值

### `--protocol`

Syslog传输协议(&#39;tcp&#39;、&#39;udp&#39;、&#39;tls&#39;)

- 默认： `tls`
- 需要一个值

### `--syslog-host`

Syslog中继/收集器主机

- 需要一个值

### `--syslog-port`

Syslog中继/收集器端口

- 需要一个值

### `--facility`

Syslog工具

- 默认： `1`
- 需要一个值

### `--message-format`

Syslog消息格式（“rfc3164”或“rfc5424”）

- 默认： `rfc5424`
- 需要一个值

### `--auth-mode`

身份验证模式（“prefix”或“structured_data”）

- 默认： `prefix`
- 需要一个值

### `--auth-token`

身份验证令牌

- 需要一个值

### `--verify-tls`

是否应启用HTTPS证书验证（推荐）

- 默认： `true`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `integration:validate`

验证现有集成

```bash
magento-cloud integration:validate [-p|--project PROJECT] [--] [<id>]
```


### `id`

集成ID。 保留为空将从列表中选择。


### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `local:build`

在本地构建当前项目

```bash
magento-cloud build [-a|--abslinks] [-s|--source SOURCE] [-d|--destination DESTINATION] [-c|--copy] [--clone] [--run-deploy-hooks] [--no-clean] [--no-archive] [--no-backup] [--no-cache] [--no-build-hooks] [--no-deps] [--working-copy] [--concurrency CONCURRENCY] [--lock] [--] [<app>]...
```


```bash
build
```


### `app`

指定要生成的应用程序

- 默认： `[]`

- 数组

### `--abslinks`, `-a`

使用绝对链接

- 默认： `false`
- 不接受值

### `--source`, `-s`

源目录。 默认为当前项目的根目录。

- 需要一个值

### `--destination`, `-d`

要将每个应用程序的Web根目录符号链接到的目标。 默认：_www

- 需要一个值

### `--copy`, `-c`

复制到生成目录，而不是从源进行符号链接

- 默认： `false`
- 不接受值

### `--clone`

使用Git将当前HEAD克隆到构建目录

- 默认： `false`
- 不接受值

### `--run-deploy-hooks`

运行部署和/或post_deploy挂钩

- 默认： `false`
- 不接受值

### `--no-clean`

不删除旧内部版本

- 默认： `false`
- 不接受值

### `--no-archive`

不要创建或使用生成存档

- 默认： `false`
- 不接受值

### `--no-backup`

不备份以前的内部版本

- 默认： `false`
- 不接受值

### `--no-cache`

禁用缓存

- 默认： `false`
- 不接受值

### `--no-build-hooks`

不要运行生成后挂接

- 默认： `false`
- 不接受值

### `--no-deps`

不在本机安装生成依赖关系

- 默认： `false`
- 不接受值

### `--working-copy`

Drush：使用Git克隆每个Drupal模块的存储库，而不只是下载版本

- 默认： `false`
- 不接受值

### `--concurrency`

Drush：设置将同时处理的并发项目数

- 默认： `4`
- 需要一个值

### `--lock`

Drush：创建或更新锁定文件（仅适用于Drush版本7+）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `local:clean`

删除旧的项目内部版本

```bash
magento-cloud clean [--keep KEEP] [--max-age MAX-AGE] [--include-active]
```


```bash
clean
```

### `--keep`

要保留的最大生成数

- 默认： `5`
- 需要一个值

### `--max-age`

内部版本的最长存在时间（以秒为单位）。 如果未设置，则忽略。

- 需要一个值

### `--include-active`

也删除活动内部版本

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `local:dir`

查找本地项目根目录

```bash
magento-cloud dir [<subdir>]
```


```bash
dir
```


### `subdir`

要查找的子目录（“local”、“web”或“shared”）


### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `metrics:disk-usage`

显示服务的磁盘使用情况

```bash
magento-cloud disk [-s|--service SERVICE] [--type TYPE] [-r|--range RANGE] [-i|--interval INTERVAL] [--to TO] [-B|--bytes] [-1|--latest] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```


```bash
disk
```

### `--service`, `-s`

服务名称

- 需要一个值

### `--type`

服务类型（如果未提供服务名称），如mysql、pgsql、mongodb等。 类型版本不是必需的。

- 需要一个值

### `--range`, `-r`

时间范围。 在结束时间(—to)之前，将一直加载量度。 您可以指定单位：小时(h)、分钟(m)或秒(s)。 最小值 &lt;comment>5分钟&lt;/comment>，最大值 &lt;comment>8h&lt;/comment> 或更多（取决于项目），默认 &lt;comment>10分钟&lt;/comment>.

- 需要一个值

### `--interval`, `-i`

时间间隔。 默认为范围的除数。 您可以指定单位：小时(h)、分钟(m)或秒(s)。 最小值 &lt;comment>1分钟&lt;/comment>，最大值 &lt;comment>1h&lt;/comment>.

- 需要一个值

### `--to`

结束时间。 默认为现在。

- 需要一个值

### `--bytes`, `-B`

以字节为单位显示大小

- 默认： `false`
- 不接受值

### `--latest`, `-1`

仅显示最新的单个数据点

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：timestamp*、used*、limit*、%*、ipercent*、limit、interval、iused （* =默认列）。 字符“+”可用作默认列的占位符。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `mount:download`

使用rsync从装载下载文件

```bash
magento-cloud mount:download [-a|--all] [-m|--mount MOUNT] [--target TARGET] [--source-path] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```

### `--all`, `-a`

从所有装载下载

- 默认： `false`
- 不接受值

### `--mount`, `-m`

装载（作为应用程序相对路径）

- 需要一个值

### `--target`

文件将下载到的目录。 如果 — all被使用，装载路径将被附加

- 需要一个值

### `--source-path`

当使用 — all时，使用装载的源路径（而不是装载路径）作为目标的子目录

- 默认： `false`
- 不接受值

### `--delete`

是否删除目标目录中的无关文件

- 默认： `false`
- 不接受值

### `--exclude`

要从下载中排除的文件（模式）

- 默认： `[]`
- 需要一个值

### `--include`

要包含在下载中的文件（模式）

- 默认： `[]`
- 需要一个值

### `--refresh`

是否刷新缓存

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--worker`

工作人员姓名

- 需要一个值

### `--instance`, `-I`

实例ID

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `mount:list`

获取装载列表

```bash
magento-cloud mounts [--paths] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE]
```


```bash
mounts
```

### `--paths`

仅输出装载路径（每行一个）

- 默认： `false`
- 不接受值

### `--refresh`

是否刷新缓存

- 默认： `false`
- 不接受值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：定义、路径。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--worker`

工作人员姓名

- 需要一个值

### `--instance`, `-I`

实例ID

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `mount:size`

检查装载的磁盘使用情况

```bash
magento-cloud mount:size [-B|--bytes] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE]
```

### `--bytes`, `-B`

以字节为单位显示大小

- 默认： `false`
- 不接受值

### `--refresh`

刷新缓存

- 默认： `false`
- 不接受值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：available、max、mounts、percent_used、sizes、used。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--worker`

工作人员姓名

- 需要一个值

### `--instance`, `-I`

实例ID

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `mount:upload`

使用rsync将文件上载到装载

```bash
magento-cloud mount:upload [--source SOURCE] [-m|--mount MOUNT] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```

### `--source`

包含要上载的文件的目录

- 需要一个值

### `--mount`, `-m`

装载（作为应用程序相对路径）

- 需要一个值

### `--delete`

是否删除装载中的无关文件

- 默认： `false`
- 不接受值

### `--exclude`

要从上载中排除的文件（模式）

- 默认： `[]`
- 需要一个值

### `--include`

要包含在上传中的文件（模式）

- 默认： `[]`
- 需要一个值

### `--refresh`

是否刷新缓存

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--worker`

工作人员姓名

- 需要一个值

### `--instance`, `-I`

实例ID

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `project:clear-build-cache`

清除项目的生成缓存

```bash
magento-cloud project:clear-build-cache [-p|--project PROJECT]
```

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `project:curl`

在项目的API上运行经过身份验证的cURL请求

```bash
magento-cloud project:curl [-X|--request REQUEST] [-d|--data DATA] [--json JSON] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [-p|--project PROJECT] [--] [<path>]
```


### `path`

API路径


### `--request`, `-X`

要使用的请求方法

- 需要一个值

### `--data`, `-d`

要发送的数据

- 需要一个值

### `--json`

要发送的JSON数据

- 需要一个值

### `--include`, `-i`

在输出中包含标头

- 默认： `false`
- 不接受值

### `--head`, `-I`

仅获取标头

- 默认： `false`
- 不接受值

### `--disable-compression`

不要使用curl —compressed标志

- 默认： `false`
- 不接受值

### `--enable-glob`

启用curl通配（删除 — globoff标志）

- 默认： `false`
- 不接受值

### `--fail`, `-f`

失败，错误响应中没有输出

- 默认： `false`
- 不接受值

### `--header`, `-H`

额外的标头

- 默认： `[]`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `project:get`

在本地克隆项目

```bash
magento-cloud get [-e|--environment ENVIRONMENT] [--depth DEPTH] [--build] [-p|--project PROJECT] [-i|--identity-file IDENTITY-FILE] [--] [<project>] [<directory>]
```


```bash
get
```


### `project`

项目Id


### `directory`

要克隆到的目录。 默认为项目标题


### `--environment`, `-e`

要克隆的环境ID。 默认为项目默认值，或第一个可用的环境

- 需要一个值

### `--depth`

创建浅层克隆：限制历史记录中的提交次数

- 需要一个值

### `--build`

克隆后生成项目

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `project:info`

读取或设置项目的属性

```bash
magento-cloud project:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```


```bash
project:metadata
```


### `property`

属性的名称


### `value`

为属性设置新值


### `--refresh`

是否刷新缓存

- 默认： `false`
- 不接受值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `project:list`

获取所有活动项目的列表

```bash
magento-cloud project:list [--pipe] [--host HOST] [--title TITLE] [--my] [--refresh REFRESH] [--sort SORT] [--reverse] [--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```


```bash
projects
```


```bash
pro
```

### `--pipe`

输出项目ID的简单列表。 禁用分页。

- 默认： `false`
- 不接受值

### `--host`

按区域主机名筛选（完全匹配）

- 需要一个值

### `--title`

按标题筛选（不区分大小写的搜索）

- 需要一个值

### `--my`

仅显示您拥有的项目

- 默认： `false`
- 不接受值

### `--refresh`

是否刷新列表

- 默认： `1`
- 需要一个值

### `--sort`

排序依据的属性

- 默认： `title`
- 需要一个值

### `--reverse`

按反向（降序）排序

- 默认： `false`
- 不接受值

### `--page`

页码。 无论配置还是 — count，这都支持分页。 如果指定了 — pipe，则忽略。

- 需要一个值

### `--count`, `-c`

每页显示的项目数。 使用0可禁用分页。 如果指定了 — page，则忽略。

- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`

要显示的列。 可用列：id*、title*、region*、created_at、endpoint、organization_id、organization_label、organization_name、region_label、status、ui_url （* =默认列）。 字符“+”可用作默认列的占位符。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `project:set-remote`

为当前Git存储库设置远程项目

```bash
magento-cloud project:set-remote [<project>]
```


### `project`

项目Id


### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `project:variable:delete`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已弃用 ]&lt;/>从项目中删除变量

```bash
magento-cloud project:variable:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

变量名称

- 必需

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `project:variable:get`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已弃用 ]&lt;/>查看项目的变量

```bash
magento-cloud project:variable:get [--pipe] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<name>]
```


```bash
project-variables
```


```bash
pvget
```


```bash
project:variable:list
```


### `name`

变量的名称


### `--pipe`

仅输出完整的变量值（必须指定“name”）

- 默认： `false`
- 不接受值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `project:variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已弃用 ]&lt;/>为项目设置变量

```bash
magento-cloud pvset [--json] [--no-visible-build] [--no-visible-runtime] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name> <value>
```


```bash
pvset
```


### `name`

变量名称

- 必需

### `value`

变量值

- 必需

### `--json`

将值标记为JSON

- 默认： `false`
- 不接受值

### `--no-visible-build`

不要在构建时公开此变量

- 默认： `false`
- 不接受值

### `--no-visible-runtime`

不要在运行时公开此变量

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `repo:cat`

读取项目存储库中的文件

```bash
magento-cloud repo:cat [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] <path>
```


### `path`

文件的路径

- 必需

### `--commit`, `-c`

承诺SHA。 这还可以接受父项提交的“HEAD”、脱字符号(^)或波状符号(~)后缀。

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `repo:ls`

列出项目存储库中的文件

```bash
magento-cloud repo:ls [-d|--directories] [-f|--files] [--git-style] [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


### `path`

子目录的路径


### `--directories`, `-d`

仅显示目录

- 默认： `false`
- 不接受值

### `--files`, `-f`

仅显示文件

- 默认： `false`
- 不接受值

### `--git-style`

与“git ls-tree”类似的样式输出

- 默认： `false`
- 不接受值

### `--commit`, `-c`

承诺SHA。 这还可以接受父项提交的“HEAD”、脱字符号(^)或波状符号(~)后缀。

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `repo:read`

读取项目存储库中的目录或文件

```bash
magento-cloud read [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


```bash
read
```


### `path`

目录或文件的路径


### `--commit`, `-c`

承诺SHA。 这还可以接受父项提交的“HEAD”、脱字符号(^)或波状符号(~)后缀。

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `route:get`

查看有关路由的详细信息

```bash
magento-cloud route:get [--id ID] [-1|--primary] [-P|--property PROPERTY] [--refresh] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<route>]
```


### `route`

路由的原始URL


### `--id`

要选择的路由ID

- 需要一个值

### `--primary`, `-1`

选择主要工艺路线

- 默认： `false`
- 不接受值

### `--property`, `-P`

要显示的属性

- 需要一个值

### `--refresh`

绕过路由缓存

- 默认： `false`
- 不接受值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

[已弃用选项，不再使用]

- 需要一个值

### `--identity-file`, `-i`

[已弃用选项，不再使用]

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `route:list`

列出环境的所有路由

```bash
magento-cloud routes [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<environment>]
```


```bash
routes
```


```bash
environment:routes
```


### `environment`

环境Id


### `--refresh`

绕过路由缓存

- 默认： `false`
- 不接受值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列： route*、type*、to*、url （* =默认列）。 字符“+”可用作默认列的占位符。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `self:install`

安装或更新命令行界面配置文件

```bash
magento-cloud self:install [--shell-type SHELL-TYPE]
```


```bash
local:install
```

### `--shell-type`

用于自动完成的外壳类型（bash或zsh）

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `self:stats`

查看GitHub包下载统计信息

```bash
magento-cloud self:stats [-p|--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

### `--page`, `-p`

页码

- 默认： `1`
- 需要一个值

### `--count`, `-c`

每页结果数（最多：100个）

- 默认： `20`
- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`

要显示的列。 可用列：资产、日期、下载、版本。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `self:update`

将CLI更新至最新版本

```bash
magento-cloud self-update [--no-major] [--unstable] [--manifest MANIFEST] [--current-version CURRENT-VERSION] [--timeout TIMEOUT]
```


```bash
self-update
```


```bash
update
```

### `--no-major`

仅在次要版本或修补程序版本之间更新

- 默认： `false`
- 不接受值

### `--unstable`

更新至不稳定的新版本（如果可用）

- 默认： `false`
- 不接受值

### `--manifest`

覆盖清单文件位置

- 需要一个值

### `--current-version`

覆盖当前版本

- 需要一个值

### `--timeout`

版本检查超时

- 默认： `30`
- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `service:list`

列出项目中的服务

```bash
magento-cloud services [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
services
```

### `--refresh`

是否刷新缓存

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：磁盘、名称、大小、类型。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `service:mongo:dump`

从MongoDB创建数据的二进制归档转储

```bash
magento-cloud mongodump [-c|--collection COLLECTION] [-z|--gzip] [-o|--stdout] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongodump
```

### `--collection`, `-c`

要转储的集合

- 需要一个值

### `--gzip`, `-z`

使用gzip压缩转储

- 默认： `false`
- 不接受值

### `--stdout`, `-o`

输出到STDOUT而不是文件

- 默认： `false`
- 不接受值

### `--relationship`, `-r`

要使用的服务关系

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `service:mongo:export`

从MongoDB导出数据

```bash
magento-cloud mongoexport [-c|--collection COLLECTION] [--jsonArray] [--type TYPE] [-f|--fields FIELDS] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongoexport
```

### `--collection`, `-c`

要导出的收藏集

- 需要一个值

### `--jsonArray`

将数据导出为单个JSON数组

- 默认： `false`
- 不接受值

### `--type`

导出类型，如“csv”

- 需要一个值

### `--fields`, `-f`

要导出的字段

- 默认： `[]`
- 需要一个值

### `--relationship`, `-r`

要使用的服务关系

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `service:mongo:restore`

将数据转储还原到MongoDB中

```bash
magento-cloud mongorestore [-c|--collection COLLECTION] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongorestore
```

### `--collection`, `-c`

要还原的收藏集

- 需要一个值

### `--relationship`, `-r`

要使用的服务关系

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `service:mongo:shell`

使用MongoDB shell

```bash
magento-cloud mongo [--eval EVAL] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongo
```

### `--eval`

将JavaScript片段传递给shell

- 需要一个值

### `--relationship`, `-r`

要使用的服务关系

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `service:redis-cli`

访问Redis CLI

```bash
magento-cloud redis [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--] [<args>]
```


```bash
redis
```


### `args`

要添加到Redis命令的参数


### `--relationship`, `-r`

要使用的服务关系

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `session:switch`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/>在会话之间切换

```bash
magento-cloud session:switch [<id>]
```


### `id`

新会话ID


### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `snapshot:create`

制作环境的快照

```bash
magento-cloud backup [--live] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```


```bash
backup
```


```bash
backup:create
```


```bash
environment:backup
```


### `environment`

环境


### `--live`

实时备份：不停止环境。 如果设置，这将使环境保持运行状态并在备份期间打开连接。 这减少了停机时间，但存在备份处于不一致状态的数据的风险。

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--unsafe`

已弃用选项：改用 — live

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `snapshot:list`

列出环境的可用快照

```bash
magento-cloud snapshots [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
snapshots
```


```bash
backups
```


```bash
backup:list
```

### `--limit`

[已弃用]  — 此选项未使用

- 需要一个值

### `--start`

[已弃用]  — 此选项未使用

- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `snapshot:restore`

恢复环境快照

```bash
magento-cloud snapshot:restore [--target TARGET] [--branch-from BRANCH-FROM] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<snapshot>]
```


```bash
environment:restore
```


```bash
backup:restore
```


### `snapshot`

快照的名称。 默认为最近的一个


### `--target`

要还原到的环境。 默认为快照的当前环境

- 需要一个值

### `--branch-from`

如果 — target尚不存在，这会指定新环境的父级

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `source-operation:run`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/>运行源操作

```bash
magento-cloud source-operation:run [--variable VARIABLE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <operation>
```


### `operation`

操作名称

- 必需

### `--variable`

操作过程中要设置的变量，格式为 &lt;info>type：name=value&lt;/info>

- 默认： `[]`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `ssh-cert:info`

显示有关当前SSH证书的信息

```bash
magento-cloud ssh-cert:info [--no-refresh] [-P|--property PROPERTY] [--date-fmt DATE-FMT]
```

### `--no-refresh`

如果证书无效，请勿刷新证书

- 默认： `false`
- 不接受值

### `--property`, `-P`

要显示的证书属性

- 需要一个值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `ssh-cert:load`

生成SSH证书

```bash
magento-cloud ssh-cert:load [--refresh-only] [--new] [--new-key]
```

### `--refresh-only`

仅在必要时刷新证书（不写入SSH配置）

- 默认： `false`
- 不接受值

### `--new`

强制刷新证书

- 默认： `false`
- 不接受值

### `--new-key`

[已弃用] 使用 — 改为新建

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `ssh-key:add`

添加新的SSH密钥

```bash
magento-cloud ssh-key:add [--name NAME] [--] [<path>]
```


### `path`

现有SSH公钥的路径


### `--name`

用于标识密钥的名称

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `ssh-key:delete`

删除SSH密钥

```bash
magento-cloud ssh-key:delete [<id>]
```


### `id`

要删除的SSH密钥的ID


### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `ssh-key:list`

获取帐户中的SSH密钥列表

```bash
magento-cloud ssh-keys [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
ssh-keys
```

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：id*、title*、path*、指纹（* =默认列）。 字符“+”可用作默认列的占位符。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `subscription:info`

读取或修改订阅属性

```bash
magento-cloud subscription:info [-s|--id ID] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<property>] [<value>]
```


### `property`

属性的名称


### `value`

为属性设置新值


### `--id`, `-s`

订阅ID

- 需要一个值

### `--date-fmt`

日期格式（作为PHP日期格式字符串）

- 默认： `c`
- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `tunnel:close`

关闭SSH通道

```bash
magento-cloud tunnel:close [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

### `--all`, `-a`

关闭所有隧道

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `tunnel:info`

查看SSH隧道的关系信息

```bash
magento-cloud tunnel:info [-P|--property PROPERTY] [-c|--encode] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

### `--property`, `-P`

要查看的关系属性

- 需要一个值

### `--encode`, `-c`

以base64编码JSON输出

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`

要显示的列。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `tunnel:list`

列出SSH通道

```bash
magento-cloud tunnels [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
tunnels
```

### `--all`, `-a`

查看所有隧道

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `tunnel:open`

打开SSH隧道以访问应用程序的关系

```bash
magento-cloud tunnel:open [-g|--gateway-ports] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

### `--gateway-ports`, `-g`

允许远程主机连接到本地转发端口

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `tunnel:single`

打开到应用程序关系的单个SSH通道

```bash
magento-cloud tunnel:single [--port PORT] [-g|--gateway-ports] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

### `--port`

本地端口

- 需要一个值

### `--gateway-ports`, `-g`

允许远程主机连接到本地转发端口

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--app`, `-A`

远程应用程序名称

- 需要一个值

### `--relationship`, `-r`

要使用的服务关系

- 需要一个值

### `--identity-file`, `-i`

要使用的SSH身份（私钥）

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `user:add`

将用户添加到项目

```bash
magento-cloud user:add [-r|--role ROLE] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<email>]
```


### `email`

用户的电子邮件地址


### `--role`, `-r`

用户的项目角色（“管理员”或“查看者”）或环境类型角色（例如“staging：contributor”或“production：viewer”）。 要从环境类型中删除用户，请将角色设置为“无”。 %字符可用作环境类型的通配符，例如“%：viewer”，为所有类型授予用户“viewer”角色。 角色可以缩写，例如“production：v”。

- 默认： `[]`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `user:delete`

从项目中删除用户

```bash
magento-cloud user:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <email>
```


### `email`

用户的电子邮件地址

- 必需

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `user:get`

查看用户的角色

```bash
magento-cloud user:get [-l|--level LEVEL] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-r|--role ROLE] [--] [<email>]
```


```bash
user:role
```


### `email`

用户的电子邮件地址


### `--level`, `-l`

角色级别（“项目”或“环境”）

- 需要一个值

### `--pipe`

将角色输出到stdout（在进行任何更改后）

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--role`, `-r`

[已弃用：使用user：update更改用户的角色]

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `user:list`

列出项目用户

```bash
magento-cloud users [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
users
```

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：电子邮件、id、名称、角色。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `user:update`

更新项目中的用户角色

```bash
magento-cloud user:update [-r|--role ROLE] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<email>]
```


### `email`

用户的电子邮件地址


### `--role`, `-r`

用户的项目角色（“管理员”或“查看者”）或环境类型角色（例如“staging：contributor”或“production：viewer”）。 要从环境类型中删除用户，请将角色设置为“无”。 %字符可用作环境类型的通配符，例如“%：viewer”，为所有类型授予用户“viewer”角色。 角色可以缩写，例如“production：v”。

- 默认： `[]`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `variable:create`

创建变量

```bash
magento-cloud variable:create [-l|--level LEVEL] [--name NAME] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--prefix PREFIX] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<name>]
```


### `name`

变量名称


### `--level`, `-l`

设置变量的级别（“项目”或“环境”）

- 需要一个值

### `--name`

变量名称

- 需要一个值

### `--value`

变量的值

- 需要一个值

### `--json`

变量是否为JSON格式

- 默认： `false`
- 需要一个值

### `--sensitive`

变量是否敏感

- 默认： `false`
- 需要一个值

### `--prefix`

变量名称的前缀（例如“none”或“env：”）

- 默认： `none`
- 需要一个值

### `--enabled`

是否应启用变量

- 默认： `true`
- 需要一个值

### `--inheritable`

变量是否可由子环境继承

- 默认： `true`
- 需要一个值

### `--visible-build`

变量在构建时是否应可见

- 需要一个值

### `--visible-runtime`

变量是否应在运行时可见

- 默认： `true`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `variable:delete`

删除变量

```bash
magento-cloud variable:delete [-l|--level LEVEL] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

变量名称

- 必需

### `--level`, `-l`

变量级别（“项目”、“环境”、“p”或“e”）

- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `variable:disable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已弃用 ]&lt;/>禁用启用的环境级别变量

```bash
magento-cloud variable:disable [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

变量的名称

- 必需

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `variable:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已弃用 ]&lt;/>启用禁用的环境级变量

```bash
magento-cloud variable:enable [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

变量的名称

- 必需

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `variable:get`

查看变量

```bash
magento-cloud vget [-P|--property PROPERTY] [-l|--level LEVEL] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--pipe] [--] [<name>]
```


```bash
vget
```


### `name`

变量的名称


### `--property`, `-P`

查看单个变量属性

- 需要一个值

### `--level`, `-l`

变量级别（“项目”、“环境”、“p”或“e”）

- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--pipe`

[已弃用选项] 仅输出变量值

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `variable:list`

列表变量

```bash
magento-cloud variable:list [-l|--level LEVEL] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
variables
```


```bash
var
```

### `--level`, `-l`

变量级别（“项目”、“环境”、“p”或“e”）

- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：is_enabled、level、name、value。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ 已弃用 ]&lt;/>为环境设置变量

```bash
magento-cloud vset [--json] [--disabled] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name> <value>
```


```bash
vset
```


### `name`

变量名称

- 必需

### `value`

变量值

- 必需

### `--json`

将值标记为JSON

- 默认： `false`
- 不接受值

### `--disabled`

将变量标记为已禁用

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `variable:update`

更新变量

```bash
magento-cloud variable:update [-l|--level LEVEL] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

变量名称

- 必需

### `--level`, `-l`

变量级别（“项目”、“环境”、“p”或“e”）

- 需要一个值

### `--value`

变量的值

- 需要一个值

### `--json`

变量是否为JSON格式

- 默认： `false`
- 需要一个值

### `--sensitive`

变量是否敏感

- 默认： `false`
- 需要一个值

### `--enabled`

是否应启用变量

- 默认： `true`
- 需要一个值

### `--inheritable`

变量是否可由子环境继承

- 默认： `true`
- 需要一个值

### `--visible-build`

变量在构建时是否应可见

- 需要一个值

### `--visible-runtime`

变量是否应在运行时可见

- 默认： `true`
- 需要一个值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--no-wait`, `-W`

不要等待操作完成

- 默认： `false`
- 不接受值

### `--wait`

等待操作完成（默认）

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `version:list`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ALPHA ]&lt;/>列出环境版本

```bash
magento-cloud versions [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
versions
```

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值


## `worker:list`

获取所有已部署工作人员的列表

```bash
magento-cloud workers [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
workers
```

### `--refresh`

是否刷新缓存

- 默认： `false`
- 不接受值

### `--project`, `-p`

项目ID或URL

- 需要一个值

### `--host`

已弃用选项，不再使用

- 需要一个值

### `--environment`, `-e`

环境Id

- 需要一个值

### `--format`

输出格式：table、csv、tsv或plain

- 默认： `table`
- 需要一个值

### `--columns`, `-c`

要显示的列。 可用列：命令、名称、类型。 如果列表作为单个值给出（例如“a，b，c”），则它将被逗号和/或空格拆分。

- 默认： `[]`
- 需要一个值

### `--no-header`

不输出表头

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示此帮助消息

- 默认： `false`
- 不接受值

### `--verbose`, `-v|-vv|-vvv`

增加消息的详细程度

- 默认： `false`
- 不接受值

### `--version`, `-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

### `--yes`, `-y`

对确认问题回答“是”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--no-interaction`

不要问任何交互式问题；接受默认值。 等效于使用环境变量： &lt;comment>Magento_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

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

### `--no`, `-n`

对确认问题回答“否”；接受其他问题的默认值；禁用交互

- 默认： `false`
- 不接受值

### `--quiet`, `-q`

不输出任何消息

- 默认： `false`
- 不接受值
