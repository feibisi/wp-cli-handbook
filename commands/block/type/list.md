---
title: "wp block type list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Type
    - Block
    - Commands
---

# wp block type list

列出已注册的区块类型。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考文档。

[\--namespace=&lt;namespace&gt;]
: 按区块命名空间过滤（例如，'core'、'my-plugin'）。

[\--dynamic]
: 仅显示动态区块（具有 render_callback 的区块）。

[\--static]
: 仅显示静态区块（没有 render_callback 的区块）。

[\--field=&lt;field&gt;]
: 为每个区块类型打印单个字段的值。

[\--fields=&lt;fields&gt;]
: 将输出限制为特定的区块类型字段。

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

以下字段将默认显示于每种区块类型：

* name
* title
* description
* category
* is_dynamic

以下字段为可选可用：

* icon
* keywords
* parent
* ancestor
* supports
* attributes
* provides_context
* uses_context
* block_hooks
* editor_script_handles
* script_handles
* view_script_handles
* editor_style_handles
* style_handles
* view_style_handles
* api_version

### 示例

    # 列出所有已注册的区块类型
    $ wp block type list

    # 列出所有核心区块
    $ wp block type list --namespace=core --fields=name,title,category

    # 仅列出动态区块
    $ wp block type list --dynamic --format=json

    # 获取已注册区块类型的数量
    $ wp block type list --format=count

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