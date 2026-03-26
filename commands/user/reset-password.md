---
title: "wp user reset-password"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - User
    - Commands
    - Repos
---

# wp user reset-password

重置一个或多个用户的密码。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;user&gt;...
: 一个或多个用户登录名或 ID。

[\--skip-email]
: 不向受影响的用户发送电子邮件通知。

[\--show-password]
: 显示新密码。

[\--porcelain]
: 仅输出新密码。

### 示例

    # 为两个用户重置密码并发送变更邮件。
    $ wp user reset-password admin editor
    为 admin 重置密码。
    为 editor 重置密码。
    成功：已为 2 个用户重置密码。

    # 重置并显示密码。
    $ wp user reset-password editor --show-password
    为 editor 重置密码。
    密码：N6hAau0fXZMN#rLCIirdEGOh
    成功：已为 1 个用户重置密码。

    # 为一个用户重置密码，仅显示新密码，且不发送变更邮件。
    $ wp user reset-password admin --skip-email --porcelain
    yV6BP*!d70wg

    # 为所有用户重置密码。
    $ wp user reset-password $(wp user list --format=ids)
    为 admin 重置密码。
    为 editor 重置密码。
    为 subscriber 重置密码。
    成功：已为 3 个用户重置密码。

    # 为具有特定角色的所有用户重置密码。
    $ wp user reset-password $(wp user list --format=ids --role=administrator)
    为 admin 重置密码。
    成功：已为 1 个用户重置密码。

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