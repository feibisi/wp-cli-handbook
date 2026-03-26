---
title: "wp core check-update"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Core
    - Commands
    - Repos
---

# wp core check-update

通过版本检查 API 检查 WordPress 更新。

当有可用更新时列出最新版本，若已是最新版本则显示成功消息。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考文档。

[\--minor]
: 仅比较版本号的前两部分。

[\--major]
: 仅比较版本号的第一部分。

[\--force-check]
: 绕过临时缓存并强制进行全新更新检查。

[\--field=&lt;字段&gt;]
: 为每个更新打印单个字段的值。

[\--fields=&lt;字段&gt;]
: 将输出限制为特定对象字段。默认为 version,update_type,package_url。

[\--format=&lt;格式&gt;]
: 以特定格式渲染输出。
\---
默认值: table
选项:
  - table
  - csv
  - count
  - json
  - yaml
\---

### 示例

    $ wp core check-update
    +---------+-------------+-------------------------------------------------------------+
    | 版本    | 更新类型    | 软件包链接                                                 |
    +---------+-------------+-------------------------------------------------------------+
    | 4.5.2   | 主要更新    | https://downloads.wordpress.org/release/wordpress-4.5.2.zip |
    +---------+-------------+-------------------------------------------------------------+

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