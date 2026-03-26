---
title: "wp db tables"
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

# wp db tables

列出数据库表。

默认列出所有注册到 $wpdb 数据库处理器的表。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

[&lt;table&gt;...]
: 基于通配符搜索列出表，例如 'wp_*_options' 或 'wp_post?'。

[\--scope=&lt;scope&gt;]
: 可以是 all、global、ms_global、blog 或 old 表。默认为 all。

[\--network]
: 列出多站点安装中的所有表。

[\--all-tables-with-prefix]
: 列出所有匹配表前缀的表，即使未在 $wpdb 上注册。覆盖 --network。

[\--all-tables]
: 列出数据库中的所有表，无论前缀如何，即使未在 $wpdb 上注册。覆盖 --all-tables-with-prefix。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: list
选项:
  - list
  - csv
\---

### 示例

    # 列出单个站点的数据表，不包含共享表如 'wp_users'
    $ wp db tables --scope=blog --url=sub.example.com
    wp_3_posts
    wp_3_comments
    wp_3_options
    wp_3_postmeta
    wp_3_terms
    wp_3_term_taxonomy
    wp_3_term_relationships
    wp_3_termmeta
    wp_3_commentmeta

    # 仅导出单个站点的数据表
    $ wp db export --tables=$(wp db tables --url=sub.example.com --format=csv)
    Success: Exported to wordpress_dbase.sql

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