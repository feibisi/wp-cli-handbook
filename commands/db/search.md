---
title: "wp db search"
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

# wp db search

在数据库中查找字符串。

在选定数据库表的所有文本列中搜索指定字符串，输出带颜色标记的字符串引用位置。

默认搜索所有注册到 $wpdb 的表。在多站点环境下，此默认设置仅限于当前站点的表。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;search&gt;
: 要搜索的字符串。默认情况下，搜索不区分大小写。

[&lt;tables&gt;...]
: 要搜索字符串的一个或多个表。

[\--network]
: 在多站点安装中，搜索所有注册到 $wpdb 的表。

[\--all-tables-with-prefix]
: 搜索所有与注册的表前缀匹配的表，即使它们未在 $wpdb 中注册。一方面，有时插件会使用未注册到 $wpdb 的表。另一方面，这可能会返回您不期望的表。覆盖 --network。

[\--all-tables]
: 搜索数据库中的所有表，无论前缀如何，即使未在 $wpdb 中注册。覆盖 --network 和 --all-tables-with-prefix。

[\--before_context=&lt;num&gt;]
: 在匹配项之前显示的字符数。
\---
默认值: 40
\---

[\--after_context=&lt;num&gt;]
: 在匹配项之后显示的字符数。
\---
默认值: 40
\---

[\--regex]
: 将搜索作为正则表达式运行（无分隔符）。搜索变为区分大小写（即不添加 PCRE 标志）。如果表达式中出现分隔符，则必须进行转义。由于搜索是在单个列上运行的，因此可以分别使用 `^` 和 `$` 标记来标记匹配的开始和结束。

[\--regex-flags=&lt;regex-flags&gt;]
: 将 PCRE 修饰符传递给正则表达式搜索（例如，'i' 表示不区分大小写）。

[\--regex-delimiter=&lt;regex-delimiter&gt;]
: 用于正则表达式的分隔符。如果它出现在搜索字符串中，则必须进行转义。默认值是 `chr(1)` 的结果。

[\--table_column_once]
: 在表列中所有匹配行之前输出一次 'table:column' 行，而不是在每行匹配之前输出。

[\--one_line]
: 将 'table:column' 输出与行 ID 和匹配项放在同一行（'table:column:id:match'）。覆盖 --table_column_once。

[\--matches_only]
: 仅输出字符串匹配项（包括上下文）。不输出 'table:column' 或行 ID。

[\--stats]
: 输出有关找到的匹配项数量、所用时间、搜索的表/列/行、跳过的表的统计信息。

[\--table_column_color=&lt;color_code&gt;]
: 用于 'table:column' 输出的百分比颜色代码。有关可用百分比颜色代码的列表，请参见下文。默认值为 '%G'（亮绿色）。

[\--id_color=&lt;color_code&gt;]
: 用于行 ID 输出的百分比颜色代码。有关可用百分比颜色代码的列表，请参见下文。默认值为 '%Y'（亮黄色）。

[\--match_color=&lt;color_code&gt;]
: 用于匹配项的百分比颜色代码（除非前后上下文均为 0，此时不使用颜色代码）。有关可用百分比颜色代码的列表，请参见下文。默认值为 '%3%k'（芥末黄背景上的黑色）。

[\--fields=&lt;fields&gt;]
: 获取字段的特定子集。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
选项:
  - table
  - csv
  - json
  - yaml
  - ids
  - count
\---

可用的百分比颜色代码有：

| 代码 | 颜色
| ---- | -----
|  %y  | 黄色（深色）（芥末黄）
|  %g  | 绿色（深色）
|  %b  | 蓝色（深色）
|  %r  | 红色（深色）
|  %m  | 洋红色（深色）
|  %c  | 青色（深色）
|  %w  | 白色（深色）（浅灰色）
|  %k  | 黑色
|  %Y  | 黄色（亮色）
|  %G  | 绿色（亮色）
|  %B  | 蓝色（亮色）
|  %R  | 红色（亮色）
|  %M  | 洋红色（亮色）
|  %C  | 青色（亮色）
|  %W  | 白色
|  %K  | 黑色（亮色）（深灰色）
|  %3  | 黄色背景（深色）（芥末黄）
|  %2  | 绿色背景（深色）
|  %4  | 蓝色背景（深色）
|  %1  | 红色背景（深色）
|  %5  | 洋红色背景（深色）
|  %6  | 青色背景（深色）
|  %7  | 白色背景（深色）（浅灰色）
|  %0  | 黑色背景
|  %8  | 反色
|  %U  | 下划线
|  %F  | 闪烁（可能无效）

它们可以组合使用。例如，默认的匹配颜色（芥末黄背景上的黑色 `%3%k`）可以通过 `%Y%0%8` 改为亮黄色背景上的黑色。

### 可用字段

默认情况下，每个结果将显示以下字段：

*   table
*   column
*   match
*   primary_key_name
*   primary_key_value

### 示例

    # 在数据库中搜索 'wordpress-develop' 字符串
    $ wp db search wordpress-develop
    wp_options:option_value
    1:http://wordpress-develop.dev
    wp_options:option_value
    1:https://example.com/foo
        ...

    # 在多站点数据库的子站点 'foo' 中搜索 'example.com' 字符串
    $ wp db search example.com --url=example.com/foo
    wp_2_comments:comment_author_url
    1:https://example.com/
    wp_2_options:option_value
        ...

    # 在数据库中搜索正则表达式 'https?://'，并打印统计信息。
    $ wp db search 'https?://' --regex --stats
    wp_comments:comment_author_url
    1:https://wordpress.org/
        ...
    Success: Found 99146 matches in 10.752s (10.559s searching). Searched 12 tables, 53 columns, 1358907 rows. 1 table skipped: wp_term_relationships.

    # SQL 搜索数据库表 'wp_options' 中 'option_name' 匹配 'foo' 的记录
    wp db query 'SELECT * FROM wp_options WHERE option_name like "%foo%"' --skip-column-names
    +----+--------------+--------------------------------+-----+
    | 98 | foo_options  | a:1:{s:12:"_multiwidget";i:1;} | yes |
    | 99 | foo_settings | a:0:{}                         | yes |
    +----+--------------+--------------------------------+-----+

    # SQL 搜索并删除数据库表 'wp_options' 中 'option_name' 匹配 'foo' 的记录
    wp db query "DELETE from wp_options where option_id in ($(wp db query "SELECT GROUP_CONCAT(option_id SEPARATOR ',') from wp_options where option_name like '%foo%';" --silent --skip-column-names))"

    # 搜索字符串并以表格形式打印结果
    $ wp db search https://localhost:8889 --format=table --fields=table,column,match
    +------------+--------------+-----------------------------+
    | table      | column       | match                       |
    +------------+--------------+-----------------------------+
    | wp_options | option_value | https://localhost:8889      |
    | wp_options | option_value | https://localhost:8889      |
    | wp_posts   | guid         | https://localhost:8889/?p=1 |
    | wp_users   | user_url     | https://localhost:8889      |
    +------------+--------------+-----------------------------+

    # 搜索字符串并仅获取 ID（仅适用于单个表）
    $ wp db search https://localhost:8889 wp_options --format=ids
    1 2

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