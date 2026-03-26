---
title: "wp db query"
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

# wp db query

对数据库执行 SQL 查询。

此命令在 `after_wp_config_load` 钩子上运行，在 wp-config.php 加载到作用域之后。

使用 wp-config.php 中指定的 `DB_HOST`、`DB_NAME`、`DB_USER` 和 `DB_PASSWORD` 数据库凭据执行任意 SQL 查询。

使用 `--skip-column-names` MySQL 参数从 SELECT 查询中排除表头。通过管道传输输出来完全移除 ASCII 表格。

### OPTIONS

请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考，以详细了解所使用的语法约定。

[&lt;sql&gt;]
: 一条 SQL 查询语句。如果未提供，将尝试从 STDIN 读取。

[\--dbuser=&lt;value&gt;]
: 传递给 mysql 的用户名。默认为 DB_USER。

[\--dbpass=&lt;value&gt;]
: 传递给 mysql 的密码。默认为 DB_PASSWORD。

[\--&lt;field&gt;=&lt;value&gt;]
: 传递给 mysql 的额外参数。[请参阅 mysql 文档](https://dev.mysql.com/doc/en/mysql-command-options.html)。

[\--defaults]
: 加载环境的 MySQL 选项文件。默认行为是跳过加载它们，以避免因配置错误而导致失败。

### 示例

    # 执行存储在文件中的查询
    $ wp db query < debug.sql

    # 查询数据库中的特定值（通过管道移除 ASCII 表格边框）
    $ wp db query 'SELECT option_value FROM wp_options WHERE option_name="home"' --skip-column-names
    +---------------------+
    | https://example.com |
    +---------------------+

    # 检查数据库中的所有表
    $ wp db query "CHECK TABLE $(wp db tables | paste -s -d, -);"
    +---------------------------------------+-------+----------+----------+
    | Table                                 | Op    | Msg_type | Msg_text |
    +---------------------------------------+-------+----------+----------+
    | wordpress_dbase.wp_users              | check | status   | OK       |
    | wordpress_dbase.wp_usermeta           | check | status   | OK       |
    | wordpress_dbase.wp_posts              | check | status   | OK       |
    | wordpress_dbase.wp_comments           | check | status   | OK       |
    | wordpress_dbase.wp_links              | check | status   | OK       |
    | wordpress_dbase.wp_options            | check | status   | OK       |
    | wordpress_dbase.wp_postmeta           | check | status   | OK       |
    | wordpress_dbase.wp_terms              | check | status   | OK       |
    | wordpress_dbase.wp_term_taxonomy      | check | status   | OK       |
    | wordpress_dbase.wp_term_relationships | check | status   | OK       |
    | wordpress_dbase.wp_termmeta           | check | status   | OK       |
    | wordpress_dbase.wp_commentmeta        | check | status   | OK       |
    +---------------------------------------+-------+----------+----------+

    # 将额外参数传递给 MySQL
    $ wp db query 'SELECT * FROM wp_options WHERE option_name="home"' --skip-column-names
    +---+------+------------------------------+-----+
    | 2 | home | http://wordpress-develop.dev | yes |
    +---+------+------------------------------+-----+

### 多站点使用说明

请注意，全局 `--url` 参数对此命令无效。如需查询主站点之外其他站点的数据，您需要手动修改表名，使用包含站点 ID 的前缀。

例如，要获取第二个站点的 `home` 选项值，请按如下方式修改上述示例：

    $ wp db query 'SELECT option_value FROM wp_2_options WHERE option_name="home"' --skip-column-names
    +----------------------+
    | https://example2.com |
    +----------------------+

要确认目标站点的 ID，可使用 `wp site list` 命令：

    # wp site list --fields=blog_id,url
    +---------+-----------------------+
    | blog_id | url                   |
    +---------+-----------------------+
    | 1       | https://example1.com/ |
    | 2       | https://example2.com/ |
    +---------+-----------------------+

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