---
title: "wp core install"
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

# wp core install

运行标准的 WordPress 安装流程。

使用提供的 URL、站点标题和默认管理员用户信息，在数据库中创建 WordPress 数据表。在数秒或更短时间内完成著名的"5分钟安装"。

注意：如果您将 WordPress 安装在了子目录中，则需要在执行 `wp core install` 后运行 `wp option update siteurl`。例如，如果 WordPress 安装在 `/wp` 目录下，且您的域名是 example.com，则需要运行 `wp option update siteurl http://example.com/wp` 才能使 WordPress 正常运行。

注意：当使用自定义用户表（例如 `CUSTOM_USER_TABLE`）时，如果 user_login 已存在，则管理员邮箱和密码将被忽略。如果 user_login 不存在，则会创建新用户。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考文档。

\--url=&lt;url&gt;
: 新站点的地址。

\--title=&lt;site-title&gt;
: 新站点的标题。

\--admin_user=&lt;username&gt;
: 管理员用户的名称。

[\--admin_password=&lt;password&gt;]
: 管理员用户的密码。默认为随机生成的字符串。

\--admin_email=&lt;email&gt;
: 管理员用户的电子邮件地址。

[\--locale=&lt;locale&gt;]
: 安装的语言环境/语言（例如 `de_DE`）。默认为 `en_US`。

[\--skip-email]
: 不向新管理员用户发送电子邮件通知。

### 示例

    # 在 5 秒内安装 WordPress
    $ wp core install --url=example.com --title=Example --admin_user=supervisor --admin_password=strongpassword --admin_email=info@example.com
    成功：WordPress 安装成功。

    # 安装 WordPress 而不将 admin_password 暴露给 bash 历史记录
    $ wp core install --url=example.com --title=Example --admin_user=supervisor --admin_email=info@example.com --prompt=admin_password < admin_password.txt

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