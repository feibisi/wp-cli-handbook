---
title: "wp block template list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Template
    - Block
    - Commands
---

# wp block template list

列出区块模板或模板部件。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

[\--type=&lt;type&gt;]
: 模板类型。
\---
默认值: wp_template
选项:
  - wp_template
  - wp_template_part
\---

[\--slug=&lt;slug&gt;]
: 按模板别名过滤。接受单个别名或逗号分隔的列表。

[\--area=&lt;area&gt;]
: 对于模板部件，按区域过滤（header, footer, sidebar, uncategorized）。

[\--post-type=&lt;post-type&gt;]
: 按模板适用的文章类型过滤。

[\--source=&lt;source&gt;]
: 按来源过滤（theme, plugin, custom）。

[\--field=&lt;field&gt;]
: 为每个模板打印单个字段的值。

[\--fields=&lt;fields&gt;]
: 将输出限制为特定的模板字段。

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

以下字段将在每个模板中默认显示：

* id
* slug
* title
* source
* type

以下字段为可选可用：

* theme
* description
* status
* origin
* is_custom
* has_theme_file
* author
* area（仅限模板部件）
* content

### 示例

    # 列出所有模板
    $ wp block template list

    # 列出页眉区域的模板部件
    $ wp block template list --type=wp_template_part --area=header

    # 列出主题中的模板
    $ wp block template list --source=theme

    # 通过别名列出特定模板
    $ wp block template list --slug=single,archive

    # 列出特定文章类型的模板
    $ wp block template list --post-type=page

    # 将模板导出为 JSON 格式
    $ wp block template list --format=json

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