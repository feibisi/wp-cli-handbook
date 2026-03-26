---
title: "wp user create"
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

# wp user create

创建一个新用户。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;user-login&gt;
: 要创建用户的登录名。

&lt;user-email&gt;
: 要创建用户的电子邮件地址。

[\--role=&lt;role&gt;]
: 要创建用户的角色。默认值：默认角色。可能的值包括 'administrator'、'editor'、'author'、'contributor'、'subscriber'。

[\--user_pass=&lt;password&gt;]
: 用户密码。默认值：随机生成。

[\--user_registered=&lt;yyyy-mm-dd-hh-ii-ss&gt;]
: 用户注册日期。默认值：当前日期。

[\--display_name=&lt;name&gt;]
: 显示名称。

[\--user_nicename=&lt;nice_name&gt;]
: 包含用户 URL 友好名称的字符串。默认值为用户的用户名。

[\--user_url=&lt;url&gt;]
: 包含用户网站 URL 的字符串。

[\--nickname=&lt;nickname&gt;]
: 用户的昵称，默认为用户的用户名。

[\--first_name=&lt;first_name&gt;]
: 用户的名字。

[\--last_name=&lt;last_name&gt;]
: 用户的姓氏。

[\--description=&lt;description&gt;]
: 包含用户相关内容的字符串。

[\--rich_editing=&lt;rich_editing&gt;]
: 是否启用富文本编辑器的字符串。如果不为空，则为 False。

[\--send-email]
: 向用户发送包含其新账户详细信息的电子邮件。

[\--porcelain]
: 仅输出新用户 ID。

### 示例

    # 创建用户
    $ wp user create bob bob@example.com --role=author
    成功：已创建用户 3。
    密码：k9**&amp;I4vNH(&amp;

    # 创建用户，成功时不显示密码
    $ wp user create ann ann@example.com --porcelain
    4

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