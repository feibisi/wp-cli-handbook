---
title: "wp cli check-update"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Cli
    - Commands
    - Repos
---

# wp cli check-update

检查是否有可用的 WP-CLI 新版本。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

查询 GitHub 发布 API。如果有可用更新则返回可用版本，如果使用最新版本则返回成功消息。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，以详细了解所使用的语法约定。

[\--patch]
: 仅列出补丁更新。

[\--minor]
: 仅列出次要更新。

[\--major]
: 仅列出主要更新。

[\--field=&lt;field&gt;]
: 为每个更新打印单个字段的值。

[\--fields=&lt;fields&gt;]
: 将输出限制为特定的对象字段。默认为 version,update_type,package_url,status,requires_php。

[\--format=&lt;format&gt;]
: 以特定格式呈现输出。
\---
默认值: table
选项:
  - table
  - csv
  - json
  - count
  - yaml
\---

### 示例

    # 检查更新。
    $ wp cli check-update
    Success: WP-CLI 已是最新版本。

    # 检查更新且发现新版本可用。
    $ wp cli check-update
    +---------+-------------+-------------------------------------------------------------------------------+
    | version | update_type | package_url                                                                   |
    +---------+-------------+-------------------------------------------------------------------------------+
    | 0.24.1  | patch       | https://github.com/wp-cli/wp-cli/releases/download/v0.24.1/wp-cli-0.24.1.phar |
    +---------+-------------+-------------------------------------------------------------------------------+

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