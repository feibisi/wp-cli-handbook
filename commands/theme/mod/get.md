---
title: "wp theme mod get"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Mod
    - Theme
    - Commands
---

# wp theme mod get

获取一个或多个主题自定义设置。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考文档。

[&lt;mod&gt;...]
: 要获取的一个或多个自定义设置。

[\--field=&lt;field&gt;]
: 返回单个字段的值。

[\--all]
: 列出所有主题自定义设置。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: table
选项:
  - table
  - json
  - csv
  - yaml
\---

### 示例

    # 获取所有主题修改项。
    $ wp theme mod get --all
    +------------------+---------+
    | key              | value   |
    +------------------+---------+
    | background_color | dd3333  |
    | link_color       | #dd9933 |
    | main_text_color  | #8224e3 |
    +------------------+---------+

    # 以 JSON 格式获取单个主题修改项。
    $ wp theme mod get background_color --format=json
    [{"key":"background_color","value":"dd3333"}]

    # 获取单个主题修改项的值。
    $ wp theme mod get background_color --field=value
    dd3333

    # 获取多个主题修改项。
    $ wp theme mod get background_color header_textcolor
    +------------------+--------+
    | key              | value  |
    +------------------+--------+
    | background_color | dd3333 |
    | header_textcolor |        |
    +------------------+--------+

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