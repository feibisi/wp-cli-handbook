---
title: "wp db export"
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

# wp db export

将数据库导出到文件或标准输出。

此命令在 `after_wp_config_load` 钩子上运行，在 wp-config.php 加载到作用域之后。

**别名：** `dump`

使用 wp-config.php 中指定的 `DB_HOST`、`DB_NAME`、`DB_USER` 和 `DB_PASSWORD` 数据库凭据运行 `mysqldump` 工具。接受任何有效的 `mysqldump` 标志。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考文档。

[&lt;file&gt;]
: 要导出的 SQL 文件名。如果为 '-'，则输出到 STDOUT。如果省略，将使用 '{dbname}-{Y-m-d}-{random-hash}.sql'。

[\--dbuser=&lt;value&gt;]
: 传递给 mysqldump 的用户名。默认为 DB_USER。

[\--dbpass=&lt;value&gt;]
: 传递给 mysqldump 的密码。默认为 DB_PASSWORD。

[\--&lt;field&gt;=&lt;value&gt;]
: 传递给 mysqldump 的额外参数。[请参阅 mysqldump 文档](https://dev.mysql.com/doc/en/mysqldump.html#mysqldump-option-summary)。

[\--tables=&lt;tables&gt;]
: 要导出的特定表的逗号分隔列表。省略此参数将导出数据库中的所有表。

[\--exclude_tables=&lt;tables&gt;]
: 应从导出中跳过的特定表的逗号分隔列表。省略此参数将导出数据库中的所有表。

[\--include-tablespaces]
: 跳过向 mysqldump 添加默认的 --no-tablespaces 选项。

[\--porcelain]
: 导出数据库的输出文件名。

[\--add-drop-table]
: 在每个 `CREATE TABLE` 语句前包含一个 `DROP TABLE IF EXISTS` 语句。

[\--defaults]
: 加载环境的 MySQL 选项文件。默认行为是跳过加载它们，以避免因配置错误而导致失败。

### 示例

    # 导出包含 DROP 语句的数据库
    $ wp db export --add-drop-table
    成功：已导出至 'wordpress_dbase-db72bb5.sql'。

    # 导出特定数据表
    $ wp db export --tables=wp_options,wp_users
    成功：已导出至 'wordpress_dbase-db72bb5.sql'。

    # 导出所有匹配通配符的数据表
    $ wp db export --tables=$(wp db tables 'wp_user*' --format=csv)
    成功：已导出至 'wordpress_dbase-db72bb5.sql'。

    # 导出所有匹配前缀的数据表
    $ wp db export --tables=$(wp db tables --all-tables-with-prefix --format=csv)
    成功：已导出至 'wordpress_dbase-db72bb5.sql'。

    # 导出特定文章（不包含建表语句）
    $ wp db export --no-create-info=true --tables=wp_posts --where="ID in (100,101,102)"
    成功：已导出至 'wordpress_dbase-db72bb5.sql'。

    # 导出特定文章的关联元数据（不包含建表语句）
    $ wp db export --no-create-info=true --tables=wp_postmeta --where="post_id in (100,101,102)"
    成功：已导出至 'wordpress_dbase-db72bb5.sql'。

    # 从导出的数据库中排除特定数据表
    $ wp db export --exclude_tables=wp_options,wp_users
    成功：已导出至 'wordpress_dbase-db72bb5.sql'。

    # 从导出的数据库中排除所有匹配通配符的数据表
    $ wp db export --exclude_tables=$(wp db tables 'wp_user*' --format=csv)
    成功：已导出至 'wordpress_dbase-db72bb5.sql'。

    # 从导出的数据库中排除所有匹配前缀的数据表
    $ wp db export --exclude_tables=$(wp db tables --all-tables-with-prefix --format=csv)
    成功：已导出至 'wordpress_dbase-db72bb5.sql'。

    # 将数据库导出到标准输出
    $ wp db export -
    -- MySQL dump 10.13  Distrib 5.7.19, for osx10.12 (x86_64)
    --
    -- Host: localhost    Database: wpdev
    -- ------------------------------------------------------
    -- Server version    5.7.19
    ...

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