---
title: "wp core install-network"
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

# wp core install-network

将现有的单站点安装转换为多站点安装。

这是 `wp core multisite-convert` 命令的别名。

创建多站点数据库表，并将多站点常量添加到 wp-config.php 文件中。

对于使用 Apache 运行 WordPress 的用户，请记得使用适当的多站点重写规则更新 `.htaccess` 文件。

[查看多站点文档](https://wordpress.org/support/article/create-a-network/) 以获取有关多站点工作原理的更多详细信息。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，详细了解所使用的语法约定。

[\--title=&lt;network-title&gt;]
: 新网络的标题。

[\--base=&lt;url-path&gt;]
: 域名后每个站点 URL 将使用的基础路径。
\---
默认值: /
\---

[\--subdomains]
: 如果指定此参数，网络将使用子域名，而非子目录。不适用于 'localhost'。

[\--skip-config]
: 不向 wp-config.php 添加多站点常量。

### 示例

    $ wp core multisite-convert
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