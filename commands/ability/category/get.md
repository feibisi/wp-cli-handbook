---
title: "wp ability category get"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Category
    - Ability
    - Commands
---

# wp ability category get

获取已注册能力类别的详细信息。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;slug&gt;
: 类别别名。

[\--field=&lt;field&gt;]
: 不返回整个类别，而是返回单个字段的值。

[\--fields=&lt;fields&gt;]
: 将输出限制在特定字段。默认为所有字段。

[\--format=&lt;format&gt;]
: 以特定格式呈现输出。
\---
默认值: table
选项:
  - table
  - csv
  - json
  - yaml
\---

### 可用字段

* slug
* label
* description
* meta

### 示例

    # 获取特定类别的详细信息。
    $ wp ability category get site
    +-------------+-----------------------------------------------------+
    | Field       | Value                                               |
    +-------------+-----------------------------------------------------+
    | slug        | site                                                |
    | label       | Site                                                |
    | description | 用于检索或修改站点信息的权限。                     |
    | meta        | {}                                                  |
    +-------------+-----------------------------------------------------+

    # 以 JSON 格式获取类别信息。
    $ wp ability category get site --format=json
    {"slug":"site","label":"Site","description":"...","meta":"{}"}

    # 仅获取标签。
    $ wp ability category get site --field=label
    Site

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