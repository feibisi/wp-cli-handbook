---
title: "wp db import"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Db
    - Commands
    - Repos
---

# wp db import

从文件或标准输入导入数据库。

此命令在 `after_wp_config_load` 钩子上运行，在 wp-config.php 加载到作用域之后。

使用 wp-config.php 中指定的 `DB_HOST`、`DB_NAME`、`DB_USER` 和 `DB_PASSWORD` 数据库凭据运行 SQL 查询。此命令本身不会创建数据库，仅执行 SQL 中定义的任何任务。

### OPTIONS

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考文档。

[&lt;file&gt;]
: 要导入的 SQL 文件名。如果为 '-'，则从 STDIN 读取。如果省略，将查找 '{dbname}.sql' 文件。

[\--dbuser=&lt;value&gt;]
: 传递给 mysql 的用户名。默认为 DB_USER。

[\--dbpass=&lt;value&gt;]
: 传递给 mysql 的密码。默认为 DB_PASSWORD。

[\--&lt;field&gt;=&lt;value&gt;]
: 传递给 mysql 的额外参数。[请参阅 mysql 二进制文档](https://dev.mysql.com/doc/refman/8.0/en/mysql-command-options.html)。

[\--skip-optimization]
: 使用 SQL 文件时，不包含速度优化，例如禁用自动提交和键检查。

[\--defaults]
: 加载环境的 MySQL 选项文件。默认行为是跳过加载它们，以避免因配置错误而导致失败。

### EXAMPLES

    # Import MySQL from a file.
    $ wp db import wordpress_dbase.sql
    Success: Imported from 'wordpress_dbase.sql'.

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