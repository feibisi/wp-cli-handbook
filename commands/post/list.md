---
title: "wp post list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Post
    - Commands
    - Repos
---

# wp post list

获取文章列表。

基于 [WP_Query()](https://developer.wordpress.org/reference/classes/wp_query/) 支持的所有参数显示文章。默认仅显示标记为文章类型的文章。

### OPTIONS

请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考，以详细了解所使用的语法约定。

[\--&lt;field&gt;=&lt;value&gt;]
: 传递给 WP_Query 的一个或多个参数。

[\--field=&lt;field&gt;]
: 为每篇文章打印单个字段的值。

[\--fields=&lt;fields&gt;]
: 将输出限制在特定的对象字段。

[\--format=&lt;format&gt;]
: 以特定格式呈现输出。
\---
默认值: table
选项:
  - table
  - csv
  - ids
  - json
  - count
  - yaml
\---

### 可用字段

默认情况下，每篇文章将显示以下字段：

* ID
* post_title
* post_name
* post_date
* post_status

以下字段为可选可用：

* post_author
* post_date_gmt
* post_content
* post_excerpt
* comment_status
* ping_status
* post_password
* to_ping
* pinged
* post_modified
* post_modified_gmt
* post_content_filtered
* post_parent
* guid
* menu_order
* post_type
* post_mime_type
* comment_count
* filter
* url

### 示例

    # 列出文章
    $ wp post list --field=ID
    568
    829
    1329
    1695

    # 以 JSON 格式列出文章
    $ wp post list --post_type=post --posts_per_page=5 --format=json
    [{"ID":1,"post_title":"Hello world!","post_name":"hello-world","post_date":"2015-06-20 09:00:10","post_status":"publish"},{"ID":1178,"post_title":"Markup: HTML Tags and Formatting","post_name":"markup-html-tags-and-formatting","post_date":"2013-01-11 20:22:19","post_status":"draft"}]

    # 列出所有页面
    $ wp post list --post_type=page --fields=post_title,post_status
    +-------------+-------------+
    | post_title  | post_status |
    +-------------+-------------+
    | Sample Page | publish     |
    +-------------+-------------+

    # 列出所有页面和文章的 ID
    $ wp post list --post_type=page,post --format=ids
    15 25 34 37 198

    # 列出指定文章
    $ wp post list --post__in=1,3
    +----+--------------+-------------+---------------------+-------------+
    | ID | post_title   | post_name   | post_date           | post_status |
    +----+--------------+-------------+---------------------+-------------+
    | 3  | Lorem Ipsum  | lorem-ipsum | 2016-06-01 14:34:36 | publish     |
    | 1  | Hello world! | hello-world | 2016-06-01 14:31:12 | publish     |
    +----+--------------+-------------+---------------------+-------------+

    # 列出指定作者的文章
    $ wp post list --author=2
    +----+-------------------+-------------------+---------------------+-------------+
    | ID | post_title        | post_name         | post_date           | post_status |
    +----+-------------------+-------------------+---------------------+-------------+
    | 14 | New documentation | new-documentation | 2021-06-18 21:05:11 | publish     |
    +----+-------------------+-------------------+---------------------+-------------+

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