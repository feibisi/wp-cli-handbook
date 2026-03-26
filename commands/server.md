---
title: "wp server"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Commands
    - Repos
    - Data
---

# wp server

启动 PHP 内置的 Web 服务器，用于特定的 WordPress 安装。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

使用 `php -S` 启动一个为 WordPress 网站根目录提供服务的 Web 服务器。
&lt;http://php.net/manual/en/features.commandline.webserver.php&gt;

重要的是，PHP 的内置 Web 服务器不支持 `.htaccess` 文件。如果需要此功能，请使用更高级的 Web 服务器。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，以详细了解所使用的语法约定。

[\--host=&lt;host&gt;]
: 服务器要绑定的主机名。
\---
默认值：localhost
\---

[\--port=&lt;port&gt;]
: 服务器要绑定的端口号。
\---
默认值：8080
\---

[\--docroot=&lt;path&gt;]
: 用作文档根目录的路径。如果设置了全局路径参数，则默认值为该参数值。

[\--config=&lt;file&gt;]
: 使用特定的 .ini 文件来配置服务器。

### 示例

    # 使实例可在任何地址访问（使用端口 8080）
    $ wp server --host=0.0.0.0
    PHP 5.6.9 Development Server started at Tue May 24 01:27:11 2016
    Listening on http://0.0.0.0:8080
    Document root is /
    Press Ctrl-C to quit.

    # 在端口 80 上运行（适用于多站点）
    $ wp server --host=localhost.localdomain --port=80
    PHP 5.6.9 Development Server started at Tue May 24 01:30:06 2016
    Listening on http://localhost1.localdomain1:80
    Document root is /
    Press Ctrl-C to quit.

    # 使用特定的 .ini 文件配置服务器
    $ wp server --config=development.ini
    PHP 7.0.9 Development Server started at Mon Aug 22 12:09:04 2016
    Listening on http://localhost:8080
    Document root is /
    Press Ctrl-C to quit.

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