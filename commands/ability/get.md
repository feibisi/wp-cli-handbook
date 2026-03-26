---
title: "wp ability get"
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

# wp ability get

获取已注册能力的详细信息。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;name&gt;
: 能力名称（格式为：命名空间/能力名称）。

[\--field=&lt;field&gt;]
: 不返回整个能力，而是返回单个字段的值。

[\--fields=&lt;fields&gt;]
: 将输出限制在特定字段。默认为所有字段。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: table
选项:
  - table
  - csv
  - json
  - yaml
\---

### 可用字段

* name
* label
* category
* description
* input_schema
* output_schema
* readonly
* destructive
* idempotent
* show_in_rest

### 示例

    # 获取特定能力的详细信息。
    $ wp ability get core/get-site-info
    +---------------+----------------------+
    | Field         | Value                |
    +---------------+----------------------+
    | name          | core/get-site-info   |
    | label         | Get Site Information |
    | category      | site                 |
    | description   | Returns site info... |
    | input_schema  | {"type":"object"}    |
    | output_schema | {"type":"object"}    |
    | readonly      | 1                    |
    | destructive   | 0                    |
    | idempotent    | 1                    |
    | show_in_rest  | 1                    |
    +---------------+----------------------+

    # 以 JSON 格式获取能力信息。
    $ wp ability get core/get-site-info --format=json

    # 仅获取描述信息。
    $ wp ability get core/get-site-info --field=description
    Returns site information configured in WordPress.

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