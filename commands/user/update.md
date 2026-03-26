---
title: "wp user update"
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

# wp user update

更新现有用户。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;user&gt;...
: 要更新的用户的登录名、电子邮箱或用户 ID。

[\--user_pass=&lt;password&gt;]
: 包含用户明文密码的字符串。

[\--user_nicename=&lt;nice_name&gt;]
: 包含用户 URL 友好名称的字符串。默认为用户的用户名。

[\--user_url=&lt;url&gt;]
: 包含用户网站 URL 的字符串。

[\--user_email=&lt;email&gt;]
: 包含用户电子邮箱地址的字符串。

[\--display_name=&lt;display_name&gt;]
: 将在网站上显示的名称字符串。默认为用户的用户名。

[\--nickname=&lt;nickname&gt;]
: 用户的昵称，默认为用户的用户名。

[\--first_name=&lt;first_name&gt;]
: 用户的名字。

[\--last_name=&lt;last_name&gt;]
: 用户的姓氏。

[\--description=&lt;description&gt;]
: 包含用户相关内容的字符串。

[\--rich_editing=&lt;rich_editing&gt;]
: 是否启用富文本编辑器的字符串。非空值表示禁用。

[\--user_registered=&lt;yyyy-mm-dd-hh-ii-ss&gt;]
: 用户注册日期。

[\--role=&lt;role&gt;]
: 用于设置用户角色的字符串。

\--&lt;field&gt;=&lt;value&gt;
: 要更新的一个或多个字段。有关可接受的字段，请参阅 wp_update_user()。

[\--skip-email]
: 不向用户发送电子邮件通知。

### EXAMPLES

    # Update user
    $ wp user update 123 --display_name=Mary --user_pass=marypass
    Success: Updated user 123.

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