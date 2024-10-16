---
source-git-commit: a8f4df78dfec2a1e94d650cac03c7fba21f398e8
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 0%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->
**版本**： 3.0.19

此引用包含通过`bin/uct`命令行工具提供的9个命令。
初始列表是在Adobe Commerce中使用`bin/uct list`命令自动生成的。

## 常规

在[概述](/help/upgrade/upgrade-compatibility-tool/overview.md)中了解有关该工具的更多信息。

此参考文档从应用程序源代码生成。 要更改文档，您应在相关的[代码库](https://github.com/magento)存储库中打开相应命令的拉取请求。 有关详细信息，请参阅[代码贡献](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)。

### 全局选项

#### `--help`，`-h`

显示给定命令的帮助。 未给出任何命令时，显示list命令的帮助

- 默认： `false`
- 不接受值

#### `--quiet`，`-q`

不输出任何消息

- 默认： `false`
- 不接受值

#### `--verbose`，`-v|-vv|-vvv`

增加消息的详细程度：1表示正常输出，2表示更多详细输出，3表示调试

- 默认： `false`
- 不接受值

#### `--version`，`-V`

显示此应用程序版本

- 默认： `false`
- 不接受值

#### `--ansi`

强制（或禁用 — no-ansi） ANSI输出

- 不接受值

#### `--no-ansi`

否定“ — ansi”选项

- 默认： `false`
- 不接受值

#### `--no-interaction`，`-n`

不要问任何交互式问题

- 默认： `false`
- 不接受值


## `_complete`

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
```

用于提供外壳完成建议的内部命令

### 选项

有关全局选项，请参阅[全局选项](#global-options)。

#### `--shell`，`-s`

shell类型(“bash”)

- 需要一个值

#### `--input`，`-i`

输入令牌的数组（例如COMP_WORDS或argv）

- 默认： `[]`
- 需要一个值

#### `--current`，`-c`

光标所在的“输入”数组的索引（例如COMP_CWORD）

- 需要一个值

#### `--symfony`，`-S`

完成脚本的版本

- 需要一个值


## `completion`

```bash
bin/uct completion [--debug] [--] [<shell>]
```

转储shell完成脚本

```
The completion command dumps the shell completion script required
to use shell autocompletion (currently only bash completion is supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    uct/bin/uct completion bash | sudo tee /etc/bash_completion.d/uct

Or dump the script to a local file and source it:

    uct/bin/uct completion bash > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/jenkins/workspace/gendocs-uct-cli/uct/bin/uct completion bash)"
```

### 参数

#### `shell`

如果未提供shell类型（例如“bash”），则将使用“$SHELL”环境变量的值

### 选项

有关全局选项，请参阅[全局选项](#global-options)。

#### `--debug`

跟踪完成调试日志

- 默认： `false`
- 不接受值


## `help`

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```

显示命令的帮助

```
The help command displays help for a given command:

  uct/bin/uct help list

You can also output the help in other formats by using the --format option:

  uct/bin/uct help --format=xml list

To display the list of available commands, please use the list command.
```

### 参数

#### `command_name`

命令名称

- 默认： `help`

### 选项

有关全局选项，请参阅[全局选项](#global-options)。

#### `--format`

输出格式（txt、xml、json或md）

- 默认： `txt`
- 需要一个值

#### `--raw`

输出原始命令帮助

- 默认： `false`
- 不接受值


## `list`

```bash
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

列出命令

```
The list command lists all commands:

  uct/bin/uct list

You can also display the commands for a specific namespace:

  uct/bin/uct list test

You can also output the information in other formats by using the --format option:

  uct/bin/uct list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  uct/bin/uct list --raw
```

### 参数

#### `namespace`

命名空间名称

### 选项

有关全局选项，请参阅[全局选项](#global-options)。

#### `--raw`

输出原始命令列表

- 默认： `false`
- 不接受值

#### `--format`

输出格式（txt、xml、json或md）

- 默认： `txt`
- 需要一个值

#### `--short`

跳过描述命令的参数

- 默认： `false`
- 不接受值


## `refactor`

```bash
bin/uct refactor <path>
```

解决了可以自动修复的问题。 将更新所提供路径中的代码。

### 参数

#### `path`

解决中问题的路径。

- 必填

### 选项

有关全局选项，请参阅[全局选项](#global-options)。


## `core:code:changes`

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```

升级兼容性工具是一个命令行工具，可通过分析安装在Adobe Commerce实例中的所有非Adobe Commerce模块，针对特定版本检查该实例。 返回在升级到新版Adobe Commerce代码之前必须解决的错误和警告列表。

### 参数

#### `dir`

Adobe Commerce安装目录。

- 必填


#### `vanilla-dir`

Adobe Commerce vanilla安装目录。

### 选项

有关全局选项，请参阅[全局选项](#global-options)。

#### `--output`，`-o`

将导出输出的文件的路径（Json格式）

- 接受值


## `dbschema:diff`

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

允许列出两个选定版本之间的Adobe Commerce DB架构差异。 可用版本： 2.3.0 | 2.3.1 | 2.3.2 | 2.3.2-p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4-p1 | 2.3.4 - p2 | 2.3.5 | 2.3.5-p1 | 2.3.5 - p2 | 2.3.6 | 2.3.6-p1 | 2.3.7 | 2.3.7-p1 | 2.3.7 - p2 | 2.3.7 - p3 | 2.3.7-p4 | 2.4.0 | 2.4.0-p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2-p1 | 2.4.2 - p2 | 2.4.3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4 | 2.4.4-p1 | 2.4.5 | 2.4.4 - p2 | 2.4.5-p1 | 2.4.4 - p3 | 2.4.4-p4 | 2.4.4 - p5 | 2.4.5 - p2 | 2.4.5-p3 | 2.4.5-p4 | 2.4.6 | 2.4.6-p1 | 2.4.6 - p2 | 2.4.7-beta1 | 2.4.4-p6 | 2.4.5-p5 | 2.4.6-p3 | 2.4.7-beta2 | 2.4.4-p7 | 2.4.5-p6 | 2.4.6-p4 | 2.4.7-beta3 | 2.4.7 | 2.4.6 - p5 | 2.4.5-p7 | 2.4.4-p8 | 2.4.4 - p9 | 2.4.5-p8 | 2.4.6-p6 | 2.4.7 - p1 | 2.4.4-p10 | 2.4.5-p9 | 2.4.6-p7 | 2.4.7 - p2 | 2.4.4-p11 | 2.4.5-p10 | 2.4.6-p8 | 2.4.7 - p3 | 2.4.8-beta1

### 参数

#### `current-version`

当前版本（例如2.3.2）。

- 必填


#### `target-version`

目标版本（例如2.4.5）。

- 必填

### 选项

有关全局选项，请参阅[全局选项](#global-options)。


## `graphql:compare`

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```

GraphQL架构兼容性验证

### 参数

#### `schema1`

指向第一个GraphQL架构的端点URL。

- 必填


#### `schema2`

指向第二个GraphQL架构的端点URL。

- 必填

### 选项

有关全局选项，请参阅[全局选项](#global-options)。

#### `--output`，`-o`

将导出输出的文件的路径（JSON格式）

- 接受值


## `upgrade:check`

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```

升级兼容性工具是一种命令行工具，可通过分析安装在Adobe Commerce自定义实例中的所有模块，针对特定版本检查该实例。 返回在升级到最新版本的Adobe Commerce之前必须解决的错误和警告列表。

### 参数

#### `dir`

Adobe Commerce安装目录。

- 必填

### 选项

有关全局选项，请参阅[全局选项](#global-options)。

#### `--current-version`，`-a`

如果忽略，则将使用当前的Adobe Commerce版本Adobe Commerce安装的版本。

- 接受值

#### `--coming-version`，`-c`

定位Adobe Commerce版本。 如果忽略，将使用最新发布的稳定版Adobe Commerce。 可用的Adobe Commerce版本： 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2 - p2 \| 2.3.3 \| 2.3.3-p1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 \| 2.3.5 - p2 \| 2.3.6 \| 2.3.6-p1 \| 2.3.7 \| 2.3.7-p1 \| 2.3.7 - p2 \| 2.3.7 - p3 \| 2.3.7 - p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1-p1 \| 2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 \| 2.4.3-p2 \| 2.4.3 - p3 \| 2.4.4 \| 2.4.4-p1 \| 2.4.4-p2 \| 2.4.4 - p3 \| 2.4.4 - p4 \| 2.4.4-p5 \| 2.4.4-p6 \| 2.4.4-p7 \| 2.4.4 - p8 \| 2.4.4 - p9 \| 2.4.4-p10 \| 2.4.4-p11 \| 2.4.5 \| 2.4.5-p1 \| 2.4.5 - p2 \| 2.4.5 - p3 \| 2.4.5 - p4 \| 2.4.5 - p5 \| 2.4.5-p6 \| 2.4.5-p7 \| 2.4.5-p8 \| 2.4.5-p9 \| 2.4.5-p10 \| 2.4.6 \| 2.4.6-p1 \| 2.4.6-p2 \| 2.4.6 - p3 \| 2.4.6 - p4 \| 2.4.6-p5 \| 2.4.6-p6 \| 2.4.6-p7 \| 2.4.6-p8 \| 2.4.7-beta1 \| 2.4.7-beta2 \| 2.4.7-beta3 \| 2.4.7 \| 2.4.7-p1 \| 2.4.7 - p2 \| 2.4.7 - p3 \| 2.4.8-beta1

- 接受值

#### `--json-output-path`

输出将以json格式导出的文件的路径

- 接受值

#### `--html-output-path`

输出将以HTML格式导出的文件的路径

- 接受值

#### `--min-issue-level`

要在报告中看到的最小问题级别（警告、错误或严重）。

- 默认： `warning`
- 接受值

#### `--ignore-current-version-compatibility-issues`，`-i`

忽略当前版本和即将发布的版本的常见问题

- 默认： `false`
- 不接受值

#### `--context`

执行上下文。 此选项用于集成目的，不影响执行结果。

- 需要一个值

