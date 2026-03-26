---
title: "wp core multisite-install"
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

# wp core multisite-install

全新安装 WordPress 多站点。

使用提供的 URL、站点标题和默认管理员用户信息，在数据库中创建 WordPress 数据表。随后，在数据库中创建多站点专用数据表，并将多站点常量添加至 wp-config.php 文件。

对于使用 Apache 运行 WordPress 的用户，请记得使用相应的多站点重写规则更新 `.htaccess` 文件。

### OPTIONS

请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考，了解所用语法约定的详细说明。

[\--url=&lt;url&gt;]
: 新站点的地址。

[\--base=&lt;url-path&gt;]
: 域名后每个站点 URL 将以此开头的基本路径。
\---
默认值: /
\---

[\--subdomains]
: 如果指定此参数，网络将使用子域名，而不是子目录。不适用于 'localhost'。

\--title=&lt;site-title&gt;
: 新站点的标题。

\--admin_user=&lt;username&gt;
: 管理员用户的名称。
\---
默认值: admin
\---

[\--admin_password=&lt;password&gt;]
: 管理员用户的密码。默认为随机生成的字符串。

\--admin_email=&lt;email&gt;
: 管理员用户的电子邮件地址。

[\--skip-email]
: 不向新管理员用户发送电子邮件通知。

[\--skip-config]
: 不向 wp-config.php 添加多站点常量。

### 示例

    $ wp core multisite-install --title="欢迎使用 WordPress" \
    > --admin_user="admin" --admin_password="password" \
    > --admin_email="user@example.com"
    单站点数据库表已存在。
    设置多站点数据库表。
    已将多站点常量添加到 wp-config.php。
    成功：网络已安装。别忘了设置重写规则。

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