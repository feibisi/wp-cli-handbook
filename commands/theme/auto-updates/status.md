---
title: "wp theme auto-updates status"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Auto Updates
    - Theme
    - Commands
---

# wp theme auto-updates status

显示主题的自动更新状态。

### 参数

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

[&lt;theme&gt;...]
: 一个或多个要显示其自动更新状态的主题。

[\--all]
: 如果设置，将显示所有主题的自动更新状态。

[\--enabled-only]
: 如果设置，将过滤主题列表，仅包含已启用自动更新的主题。

[\--disabled-only]
: 如果设置，将过滤主题列表，仅包含已禁用自动更新的主题。

[\--field=&lt;field&gt;]
: 仅显示指定的字段。

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
\---

### 示例

    # 获取主题自动更新状态
    $ wp theme auto-updates status twentysixteen
    +---------------+----------+
    | name          | status   |
    +---------------+----------+
    | twentysixteen | disabled |
    +---------------+----------+

    # 获取已启用自动更新的主题列表
    $ wp theme auto-updates status --all --enabled-only --field=name
    twentysixteen
    twentyseventeen

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