---
title: "wp comment list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Comment
    - Commands
    - Repos
---

# wp comment list

获取评论列表。

基于 [WP_Comment_Query()](https://developer.wordpress.org/reference/classes/WP_Comment_Query/__construct/) 支持的所有参数显示评论。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，了解所用语法约定的详细说明。

[\--&lt;field&gt;=&lt;value&gt;]
: 传递给 WP_Comment_Query 的一个或多个参数。

[\--field=&lt;field&gt;]
: 为每条评论打印单个字段的值。

[\--fields=&lt;fields&gt;]
: 将输出限制为特定的对象字段。

[\--format=&lt;format&gt;]
: 以特定格式呈现输出。
\---
默认值: table
选项:
  - table
  - ids
  - csv
  - json
  - count
  - yaml
\---

### 可用字段

默认情况下，每条评论将显示以下字段：

* comment_ID
* comment_post_ID
* comment_date
* comment_approved
* comment_author
* comment_author_email

以下字段为可选可用：

* comment_author_url
* comment_author_IP
* comment_date_gmt
* comment_content
* comment_karma
* comment_agent
* comment_type
* comment_parent
* user_id
* url

### 示例

    # 列出评论 ID。
    $ wp comment list --field=ID
    22
    23
    24

    # 列出某篇文章的评论。
    $ wp comment list --post_id=1 --fields=ID,comment_date,comment_author
    +------------+---------------------+----------------+
    | comment_ID | comment_date        | comment_author |
    +------------+---------------------+----------------+
    | 1          | 2015-06-20 09:00:10 | Mr WordPress   |
    +------------+---------------------+----------------+

    # 列出已批准的评论。
    $ wp comment list --number=3 --status=approve --fields=ID,comment_date,comment_author
    +------------+---------------------+----------------+
    | comment_ID | comment_date        | comment_author |
    +------------+---------------------+----------------+
    | 1          | 2015-06-20 09:00:10 | Mr WordPress   |
    | 30         | 2013-03-14 12:35:07 | John Doe       |
    | 29         | 2013-03-14 11:56:08 | Jane Doe       |
    +------------+---------------------+----------------+

    # 列出未批准的评论。
    $ wp comment list --number=3 --status=hold --fields=ID,comment_date,comment_author
    +------------+---------------------+----------------+
    | comment_ID | comment_date        | comment_author |
    +------------+---------------------+----------------+
    | 8          | 2023-11-10 13:13:06 | John Doe       |
    | 7          | 2023-11-10 13:09:55 | Mr WordPress   |
    | 9          | 2023-11-10 11:22:31 | Jane Doe       |
    +------------+---------------------+----------------+

    # 列出标记为垃圾的评论。
    $ wp comment list --status=spam --fields=ID,comment_date,comment_author
    +------------+---------------------+----------------+
    | comment_ID | comment_date        | comment_author |
    +------------+---------------------+----------------+
    | 2          | 2023-11-10 11:22:31 | Jane Doe       |
    +------------+---------------------+----------------+

    # 列出回收站中的评论。
    $ wp comment list --status=trash --fields=ID,comment_date,comment_author
    +------------+---------------------+----------------+
    | comment_ID | comment_date        | comment_author |
    +------------+---------------------+----------------+
    | 3          | 2023-11-10 11:22:31 | John Doe       |
    +------------+---------------------+----------------+

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