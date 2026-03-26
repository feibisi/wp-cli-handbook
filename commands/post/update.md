---
title: "wp post update"
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

# wp post update

更新一个或多个现有文章。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;id&gt;...
: 要更新的一个或多个文章 ID。

[\--post_author=&lt;post_author&gt;]
: 添加文章的用户 ID。默认为当前用户 ID。

[\--post_date=&lt;post_date&gt;]
: 文章发布日期。默认为当前时间。

[\--post_date_gmt=&lt;post_date_gmt&gt;]
: 文章在 GMT 时区的发布日期。默认为 $post_date 的值。

[\--post_content=&lt;post_content&gt;]
: 文章内容。默认为空。

[\--post_content_filtered=&lt;post_content_filtered&gt;]
: 过滤后的文章内容。默认为空。

[\--post_title=&lt;post_title&gt;]
: 文章标题。默认为空。

[\--post_excerpt=&lt;post_excerpt&gt;]
: 文章摘要。默认为空。

[\--post_status=&lt;post_status&gt;]
: 文章状态。默认为 'draft'。

[\--post_type=&lt;post_type&gt;]
: 文章类型。默认为 'post'。

[\--comment_status=&lt;comment_status&gt;]
: 文章是否允许评论。接受 'open' 或 'closed'。默认为 'default_comment_status' 选项的值。

[\--ping_status=&lt;ping_status&gt;]
: 文章是否允许 ping。接受 'open' 或 'closed'。默认为 'default_ping_status' 选项的值。

[\--post_password=&lt;post_password&gt;]
: 访问文章的密码。默认为空。

[\--post_name=&lt;post_name&gt;]
: 文章名称。创建新文章时默认为经过清理的文章标题。

[\--to_ping=&lt;to_ping&gt;]
: 要 ping 的 URL 列表，以空格或回车分隔。默认为空。

[\--pinged=&lt;pinged&gt;]
: 已 ping 过的 URL 列表，以空格或回车分隔。默认为空。

[\--post_modified=&lt;post_modified&gt;]
: 文章最后修改日期。默认为当前时间。

[\--post_modified_gmt=&lt;post_modified_gmt&gt;]
: 文章在 GMT 时区的最后修改日期。默认为当前时间。

[\--post_parent=&lt;post_parent&gt;]
: 设置文章所属的父文章 ID（如果有）。默认为 0。

[\--menu_order=&lt;menu_order&gt;]
: 文章的显示顺序。默认为 0。

[\--post_mime_type=&lt;post_mime_type&gt;]
: 文章的 MIME 类型。默认为空。

[\--guid=&lt;guid&gt;]
: 引用文章的全局唯一 ID。默认为空。

[\--post_category=&lt;post_category&gt;]
: 分类名称、别名或 ID 的数组。默认为 'default_category' 选项的值。

[\--tags_input=&lt;tags_input&gt;]
: 标签名称、别名或 ID 的数组。默认为空。

[\--tax_input=&lt;tax_input&gt;]
: 按分类法名称键控的分类法术语数组。默认为空。

[\--meta_input=&lt;meta_input&gt;]
: 按文章元键键控的文章元值的 JSON 格式数组。默认为空。

[&lt;file&gt;]
: 从 &lt;file&gt; 读取文章内容。如果提供了此值，将忽略 `--post_content` 参数。

  将 `-` 作为文件名传递将使文章内容从 STDIN 读取。

\--&lt;field&gt;=&lt;value&gt;
: 要更新的一个或多个字段。参见 wp_insert_post()。

[\--defer-term-counting]
: 批量重新计算分类项数量，以提高性能。

### 示例

    $ wp post update 123 --post_name=something --post_status=draft
    成功：已更新文章 123。

    # 更新一个包含多个元值的文章。
    $ wp post update 123 --meta_input='{"key1":"value1","key2":"value2"}'
    成功：已更新文章 123。

    # 同时更新多篇文章。
    $ wp post update 123 456 --post_author=789
    成功：已更新文章 123。
    成功：已更新文章 456。

    # 同时更新给定文章类型的所有文章。
    $ wp post update $(wp post list --post_type=page --format=ids) --post_author=123
    成功：已更新文章 123。
    成功：已更新文章 456。

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