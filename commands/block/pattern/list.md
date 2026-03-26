---
title: "wp block pattern list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Pattern
    - Block
    - Commands
---

# wp block pattern list

列出已注册的区块模式。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考文档。

[\--category=&lt;category&gt;]
: 按模式类别筛选。

[\--search=&lt;search&gt;]
: 按标题或关键词搜索模式。

[\--inserter]
: 仅显示在插入器中可见的模式。

[\--field=&lt;field&gt;]
: 为每个模式打印单个字段的值。

[\--fields=&lt;fields&gt;]
: 将输出限制为特定的模式字段。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: table
选项:
  - table
  - csv
  - json
  - count
  - yaml
  - ids
\---

### 可用字段

以下字段将默认显示于每个模式：

* name
* title
* description
* categories

以下字段为可选可用：

* content
* keywords
* blockTypes
* postTypes
* templateTypes
* inserter
* viewportWidth

### 示例

    # 列出所有已注册的区块模式
    $ wp block pattern list

    # 列出 'buttons' 分类中的区块模式
    $ wp block pattern list --category=buttons

    # 搜索 hero 区块模式
    $ wp block pattern list --search=hero

    # 将所有区块模式导出为 JSON 格式
    $ wp block pattern list --format=json > patterns.json

### GLOBAL PARAMETERS

These [global parameters](https://make.wordpress.org/cli/handbook/config/) have the same behavior across all commands and affect how WP-CLI interacts with WordPress.

| **Argument**    | **Description**              |
|:----------------|:-----------------------------|
| `--path=<path>` | Path to the WordPress files. |
| `--url=<url>` | Pretend request came from given URL. In multisite, this argument is how the target site is specified. |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | Perform operation against a remote server over SSH (or a container using scheme of "docker", "docker-compose", "docker-compose-run", "vagrant"). |
| `--http=<http>` | Perform operation against a remote WordPress installation over HTTP. |
| `--user=<id\|login\|email>` | Set the WordPress user. |
| `--skip-plugins[=<plugins>]` | Skip loading all plugins, or a comma-separated list of plugins. Note: mu-plugins are still loaded. |
| `--skip-themes[=<themes>]` | Skip loading all themes, or a comma-separated list of themes. |
| `--skip-packages` | Skip loading all installed packages. |
| `--require=<path>` | Load PHP file before running the command (may be used more than once). |
| `--exec=<php-code>` | Execute PHP code before running the command (may be used more than once). |
| `--context=<context>` | Load WordPress in a given context. |
| `--[no-]color` | Whether to colorize the output. |
| `--debug[=<group>]` | Show all PHP errors and add verbosity to WP-CLI output. Built-in groups include: bootstrap, commandfactory, and help. |
| `--prompt[=<assoc>]` | Prompt the user to enter values for all command arguments, or a subset specified as comma-separated values. |
| `--quiet` | Suppress informational messages. |