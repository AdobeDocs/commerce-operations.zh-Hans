---
source-git-commit: adb585771fb1353614ea600117f18ba8b55b65f0
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**版本**：3.0.3

此参考包含9个命令，这些命令可通过 `bin/uct` 命令行工具。
初始列表是使用 `bin/uct list` Adobe Commerce命令。

在中了解有关该工具的更多信息 [概述](/help/upgrade/upgrade-compatibility-tool/overview.md).

>[!NOTE]
>
>此引用从应用程序代码库生成。 要更改内容，您可以更新中相应命令实施的源代码 [代码库](https://github.com/magento) 存储库并提交更改以供审核。 另一种方法是 _向我们提供反馈_ （在右上角找到链接）。 有关贡献准则，请参阅 [代码投稿](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

用于提供外壳完成建议的内部命令

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
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

显示给定命令的帮助。 未给出任何命令时，显示帮助 &lt;info>列表&lt;/info> 命令

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
bin/uct completion [--debug] [--] [<shell>]
```


### `shell`

如果未提供shell类型（例如“bash”），则将使用“$SHELL”环境变量的值


### `--debug`

跟踪完成调试日志

- 默认： `false`
- 不接受值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助 &lt;info>列表&lt;/info> 命令

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
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
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

显示给定命令的帮助。 未给出任何命令时，显示帮助 &lt;info>列表&lt;/info> 命令

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
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
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

显示给定命令的帮助。 未给出任何命令时，显示帮助 &lt;info>列表&lt;/info> 命令

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


## `refactor`

解决了可以自动修复的问题。 将更新所提供路径中的代码。

```bash
bin/uct refactor <path>
```


### `path`

解决中问题的路径。

- 必需

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助 &lt;info>列表&lt;/info> 命令

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


## `core:code:changes`

升级兼容性工具是一种命令行工具，通过分析安装在Adobe Commerce实例中的所有非Adobe Commerce模块，根据特定版本检查该实例。 返回在升级到新版Adobe Commerce代码之前必须解决的错误和警告列表。

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```


### `dir`

Adobe Commerce安装目录。

- 必需

### `vanilla-dir`

Adobe Commerce vanilla安装目录。


### `--output`, `-o`

将导出输出的文件的路径（Json格式）

- 接受一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助 &lt;info>列表&lt;/info> 命令

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


## `dbschema:diff`

允许列出两个选定版本之间的Adobe Commerce DB架构差异。
可用版本： 2.3.0 | 2.3.1 | 2.3.2 | 2.3.2-p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4 - p1 | 2.3.4 - p2 | 2.3.5 | 2.3.5-p1 | 2.3.5 - p2 | 2.3.6 | 2.3.6-p1 | 2.3.7 | 2.3.7 - p1 | 2.3.7 - p2 | 2.3.7 - p3 | 2.3.7-p4 | 2.4.0 | 2.4.0 - p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2-p1 | 2.4.2-p2 | 2.4.3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4 | 2.4.4 - p1 | 2.4.5 | 2.4.4 - p2 | 2.4.5-p1 | 2.4.4 - p3 | 2.4.5 - p2 | 2.4.6

```bash
bin/uct dbschema:diff <current-version> <target-version>
```


### `current-version`

当前版本（例如2.3.2）。

- 必需

### `target-version`

目标版本（例如2.4.5）。

- 必需

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助 &lt;info>列表&lt;/info> 命令

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


## `graphql:compare`

GraphQL架构兼容性验证

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```


### `schema1`

指向第一个GraphQL架构的端点URL。

- 必需

### `schema2`

指向第二个GraphQL架构的端点URL。

- 必需

### `--output`, `-o`

将导出输出的文件的路径（JSON格式）

- 接受一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助 &lt;info>列表&lt;/info> 命令

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


## `upgrade:check`

升级兼容性工具是一种命令行工具，它通过分析安装在Adobe Commerce自定义实例中的所有模块，根据特定版本检查该实例。 返回在升级到最新版本的Adobe Commerce之前必须解决的错误和警告列表。

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```


### `dir`

Adobe Commerce安装目录。

- 必需

### `--current-version`, `-a`

如果忽略，则将使用当前Adobe Commerce版本的Adobe Commerce安装版本。

- 接受一个值

### `--coming-version`, `-c`

如果忽略，则将使用Adobe Commerce的最新发布版本Target Adobe Commerce版本。 可用Adobe Commerce版本： 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3 - p1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p2 \| 2.3.6 \| 2.3.6-p1 \| 2.3.7 \| 2.3.7-p1 \| 2.3.7-p2 \| 2.3.7-p2 \| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1-p1 \| 2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 \| 2.4.3-p3 \| 2.4.4 \| 2.4.4-p1 \| 2.4.5 \| 2.4.4-p2 \| 2.4.5-p1 \| 2.4.4 p3 \| 2.4.5 - p2 \| 2.4.6

- 接受一个值

### `--json-output-path`

输出将以json格式导出的文件的路径

- 接受一个值

### `--html-output-path`

输出将以HTML格式导出的文件的路径

- 接受一个值

### `--min-issue-level`

要在报告中看到的最小问题级别（警告、错误或严重）。

- 默认： `warning`
- 接受一个值

### `--ignore-current-version-compatibility-issues`, `-i`

忽略当前版本和即将发布的版本的常见问题

- 默认： `false`
- 不接受值

### `--context`

执行上下文。 此选项用于集成目的，不影响执行结果。

- 需要一个值

### `--help`, `-h`

显示给定命令的帮助。 未给出任何命令时，显示帮助 &lt;info>列表&lt;/info> 命令

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

