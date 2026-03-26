---
title: "wp db size"
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

# wp db size

显示数据库名称和大小。

显示 wp-config.php 中指定的 `DB_NAME` 的数据库名称和大小。默认以人类可读的数字显示大小。

可用的尺寸格式包括：
* b (字节)
* kb (千字节)
* mb (兆字节)
* gb (吉字节)
* tb (太字节)
* B   (ISO 字节设置，无转换)
* KB  (ISO 千字节设置，1 KB = 1,000 B)
* KiB (ISO 千二进制字节设置，1 KiB = 1,024 B)
* MB  (ISO 兆字节设置，1 MB = 1,000 KB)
* MiB (ISO 兆二进制字节设置，1 MiB = 1,024 KiB)
* GB  (ISO 吉字节设置，1 GB = 1,000 MB)
* GiB (ISO 吉二进制字节设置，1 GiB = 1,024 MiB)
* TB  (ISO 太字节设置，1 TB = 1,000 GB)
* TiB (ISO 太二进制字节设置，1 TiB = 1,024 GiB)

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考文档。

[\--size_format=&lt;format&gt;]
: 仅显示数据库大小，为一个纯数字。
\---
选项:
  - b
  - kb
  - mb
  - gb
  - tb
  - B
  - KB
  - KiB
  - MB
  - MiB
  - GB
  - GiB
  - TB
  - TiB
\---

[\--tables]
: 显示每个表名及其大小，而不是数据库总大小。

[\--human-readable]
: 以人类可读的格式显示数据库大小。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
选项:
  - table
  - csv
  - json
  - yaml
\---

[\--scope=&lt;scope&gt;]
: 可以是 all、global、ms_global、blog 或 old。默认为 all。

[\--network]
: 列出多站点安装中的所有表。

[\--decimals=&lt;decimals&gt;]
: 小数点后的位数。默认为 0。

[\--all-tables-with-prefix]
: 列出所有匹配表前缀的表，即使未在 $wpdb 中注册。会覆盖 --network 选项。

[\--all-tables]
: 列出数据库中的所有表，无论前缀如何，即使未在 $wpdb 中注册。会覆盖 --all-tables-with-prefix 选项。

[\--order=&lt;order&gt;]
: 升序或降序排列。
\---
默认值: asc
选项:
  - asc
  - desc
\---

[\--orderby=&lt;orderby&gt;]
: 按字段排序。
\---
默认值: name
选项:
  - name
  - size
\---

### 示例

    $ wp db size
    +-------------------+------+
    | 名称              | 大小 |
    +-------------------+------+
    | wordpress_default | 6 MB |
    +-------------------+------+

    $ wp db size --tables
    +-----------------------+-------+
    | 名称                  | 大小  |
    +-----------------------+-------+
    | wp_users              | 64 KB |
    | wp_usermeta           | 48 KB |
    | wp_posts              | 80 KB |
    | wp_comments           | 96 KB |
    | wp_links              | 32 KB |
    | wp_options            | 32 KB |
    | wp_postmeta           | 48 KB |
    | wp_terms              | 48 KB |
    | wp_term_taxonomy      | 48 KB |
    | wp_term_relationships | 32 KB |
    | wp_termmeta           | 48 KB |
    | wp_commentmeta        | 48 KB |
    +-----------------------+-------+

    $ wp db size --size_format=b
    5865472

    $ wp db size --size_format=kb
    5728

    $ wp db size --size_format=mb
    6

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