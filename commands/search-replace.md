---
title: "wp search-replace"
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

# wp search-replace

在数据库中搜索/替换字符串。

在选定表的所有行中进行搜索，并将第一个字符串的出现替换为第二个字符串。

默认情况下，该命令使用注册到 `$wpdb` 对象的表。在多站点环境下，除非指定 `--network` 参数，否则仅针对当前站点的表。

搜索/替换功能会智能处理 PHP 序列化数据，且不会更改主键值。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;old&gt;
: 要在数据库中搜索的字符串。

&lt;new&gt;
: 用此新字符串替换第一个字符串的实例。

[&lt;table&gt;...]
: 限制替换操作所针对的数据库表列表。支持通配符，例如 `'wp_*options'` 或 `'wp_post*'`。

[\--dry-run]
: 运行整个搜索/替换操作并显示报告，但不将更改保存到数据库。

[\--network]
: 在多站点安装中，对所有注册到 $wpdb 的表进行搜索/替换。

[\--all-tables-with-prefix]
: 对任何匹配表前缀的表启用替换，即使它们未在 $wpdb 中注册。

[\--all-tables]
: 对数据库中的所有表启用替换，无论前缀如何，即使未在 $wpdb 中注册。此选项会覆盖 --network 和 --all-tables-with-prefix。

[\--export[=&lt;file&gt;]]
: 将转换后的数据写入 SQL 文件，而不是将替换保存到数据库。如果未提供 &lt;file&gt;，将输出到 STDOUT。

[\--export_insert_size=&lt;rows&gt;]
: 定义执行 SQL 导出时单个 INSERT 语句中的行数。您可能需要根据数据库配置更改此值（例如，如果需要减少查询次数）。默认值：50

[\--skip-tables=&lt;tables&gt;]
: 不对特定表执行替换。使用逗号分隔多个表。支持通配符，例如 `'wp_*options'` 或 `'wp_post*'`。

[\--skip-columns=&lt;columns&gt;]
: 不对特定列执行替换。使用逗号分隔多个列。

[\--include-columns=&lt;columns&gt;]
: 对特定列执行替换。使用逗号分隔多个列。

[\--precise]
: 强制使用 PHP（而非 SQL）进行替换，这种方式更彻底，但速度更慢。

[\--recurse-objects]
: 启用递归到对象中以替换字符串。默认为 true；传递 --no-recurse-objects 以禁用。

[\--verbose]
: 在更新行时将其打印到控制台。

[\--regex]
: 使用正则表达式（无分隔符）运行搜索。警告：使用 --regex 时，搜索替换所需时间将延长约 15-20 倍。

[\--regex-flags=&lt;regex-flags&gt;]
: 将 PCRE 修饰符传递给正则表达式搜索替换（例如，'i' 表示不区分大小写）。

[\--regex-delimiter=&lt;regex-delimiter&gt;]
: 用于正则表达式的分隔符。如果分隔符出现在搜索字符串中，则必须进行转义。默认值为 `chr(1)` 的结果。

[\--regex-limit=&lt;regex-limit&gt;]
: 正则表达式每行（或每行每个反序列化数据位）的最大可能替换次数。默认为 -1（无限制）。

[\--format=&lt;format&gt;]
: 以特定格式呈现输出。
\---
default: table
options:
  - table
  - count
\---

[\--report]
: 生成报告。默认为 true。

[\--report-changed-only]
: 仅报告已更改的字段。默认值为 false，除非启用日志记录，此时默认值为 true。

[\--log[=&lt;文件&gt;]]
: 记录已更改的项目。如果未提供 &lt;文件&gt; 或为 "-"，将输出到 STDOUT。警告：会导致显著减速，类似于或比启用 --precise 或 --regex 更慢。

[\--before_context=&lt;数量&gt;]
: 对于日志记录，显示旧匹配项和新替换项之前的字符数。默认 40。未启用日志记录时忽略。

[\--after_context=&lt;数量&gt;]
: 对于日志记录，显示旧匹配项和新替换项之后的字符数。默认 40。未启用日志记录时忽略。

### 示例

    # 搜索并替换但跳过指定列
    $ wp search-replace 'http://example.test' 'http://example.com' --skip-columns=guid

    # 执行搜索/替换操作但不保存到数据库
    $ wp search-replace 'foo' 'bar' wp_posts wp_postmeta wp_terms --dry-run

    # 执行不区分大小写的正则表达式搜索/替换操作（较慢）
    $ wp search-replace '\[foo id="([0-9]+)"' '[bar id="\1"' --regex --regex-flags='i'

    # 将生产环境的多站点数据库转换为本地开发数据库
    $ wp search-replace --url=example.com example.com example.test 'wp_*options' wp_blogs wp_site --network

    # 搜索/替换并导出到 SQL 文件而不修改数据库
    $ wp search-replace foo bar --export=database.sql

    # Bash 脚本：将生产环境 URL 搜索/替换为开发环境 URL（兼容多站点）
    #!/bin/bash
    if $(wp --url=http://example.com core is-installed --network); then
        wp search-replace --url=http://example.com 'http://example.com' 'http://example.test' --recurse-objects --network --skip-columns=guid --skip-tables=wp_users
    else
        wp search-replace 'http://example.com' 'http://example.test' --recurse-objects --skip-columns=guid --skip-tables=wp_users
    fi

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