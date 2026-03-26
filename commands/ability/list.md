---
title: "wp ability list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Ability
    - Commands
    - Repos
---

# wp ability list

列出所有已注册的能力。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考文档。

[\--category=&lt;slug&gt;]
: 按分类别名筛选能力。

[\--namespace=&lt;prefix&gt;]
: 按命名空间前缀筛选能力（例如，'core' 对应 'core/*' 能力）。

[\--show-in-rest=&lt;bool&gt;]
: 按 REST API 公开状态筛选能力。

[\--field=&lt;field&gt;]
: 为每个能力打印单个字段的值。

[\--fields=&lt;fields&gt;]
: 将输出限制为特定的能力字段。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: table
选项:
  - table
  - csv
  - json
  - yaml
  - count
  - ids
\---

### 可用字段

以下字段默认会为每个能力显示：

* name
* label
* category
* description

以下字段为可选可用：

* readonly
* destructive
* idempotent
* show_in_rest

### 示例

    # 列出所有能力。
    $ wp ability list
    +---------------------------+----------------------+----------+------------------------------------------+
    | name                      | label                | category | description                              |
    +---------------------------+----------------------+----------+------------------------------------------+
    | core/get-site-info        | Get Site Information | site     | 返回配置的站点信息... |
    | core/get-user-info        | Get User Information | user     | 返回指定用户的基本资料详情... |
    +---------------------------+----------------------+----------+------------------------------------------+

    # 列出特定类别中的能力。
    $ wp ability list --category=site

    # 按命名空间列出能力。
    $ wp ability list --namespace=core

    # 列出暴露给 REST API 的能力。
    $ wp ability list --show-in-rest=true

    # 以 JSON 格式列出能力。
    $ wp ability list --format=json

    # 仅列出能力名称。
    $ wp ability list --field=name
    core/get-site-info
    core/get-user-info
    core/get-environment-info

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