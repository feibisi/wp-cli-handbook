---
title: "wp export"
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

# wp export

将 WordPress 内容导出为 WXR 文件。

生成一个或多个包含作者、分类、文章、评论和附件的 WXR 文件。WXR 文件不包含站点配置（选项）或附件文件本身。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，详细了解所使用的语法约定。

[\--dir=&lt;dirname&gt;]
: 存储 WXR 导出文件的目录的完整路径。默认为当前工作目录。

[\--stdout]
: 使用标准输出输出整个 XML（与 --dir= 选项不兼容）。

[\--skip_comments]
: 在 WXR 导出文件中不包含评论。

[\--max_file_size=&lt;MB&gt;]
: 单个导出文件的大小上限（单位：MB）。-1 表示无限制。
\---
默认值：15
\---

[\--filename_format=&lt;format&gt;]
: 为导出文件名使用自定义格式。默认为 '{site}.wordpress.{date}.{n}.xml'。

[\--include_once=&lt;before_posts&gt;]
: 仅在第一个导出文件中包含指定的导出部分。有效选项包括 categories、tags、nav_menu_items、custom_taxonomies_terms。多个部分用逗号分隔。默认为无。

[\--allow_orphan_terms]
: 导出 `parent=0` 的孤立分类项，而不是抛出异常。

### 过滤器

[\--start_date=&lt;日期&gt;]
: 仅导出在此日期之后发布的文章，格式为 YYYY-MM-DD。

[\--end_date=&lt;日期&gt;]
: 仅导出在此日期之前发布的文章，格式为 YYYY-MM-DD。

[\--post_type=&lt;文章类型&gt;]
: 仅导出具有此文章类型的文章。多个文章类型用逗号分隔。
\---
默认值：任意
\---

[\--post_type__not_in=&lt;文章类型&gt;]
: 导出除指定类型外的所有文章类型。多个文章类型用逗号分隔。默认为无。

[\--post__in=&lt;文章ID&gt;]
: 导出所有指定的文章，ID 列表以逗号或空格分隔。除非指定了 --with_attachments，否则文章的附件不会被导出。

[\--with_attachments]
: 当指定了 --post__in 时，强制包含附件。

[\--start_id=&lt;文章ID&gt;]
: 仅导出 ID 大于或等于此文章 ID 的文章。

[\--max_num_posts=&lt;数量&gt;]
: 导出不超过 &lt;数量&gt; 篇文章（不包括附件）。

[\--author=&lt;作者&gt;]
: 仅导出此作者的文章。可以是用户登录名或用户 ID。

[\--category=&lt;名称|ID&gt;]
: 仅导出此分类下的文章。

[\--post_status=&lt;状态&gt;]
: 仅导出具有此状态的文章。

### 示例

    # 导出用户在指定开始和结束日期之间发布的文章
    $ wp export --dir=/tmp/ --user=admin --post_type=post --start_date=2011-01-01 --end_date=2011-12-31
    开始导出过程...
    写入文件 /tmp/staging.wordpress.2016-05-24.000.xml
    成功：导出全部完成。

    # 按 ID 导出文章
    $ wp export --dir=/tmp/ --post__in=123,124,125
    开始导出过程...
    写入文件 /tmp/staging.wordpress.2016-05-24.000.xml
    成功：导出全部完成。

    # 导出随机内容子集
    $ wp export --post__in="$(wp post list --post_type=post --orderby=rand --posts_per_page=8 --format=ids)"
    开始导出过程...
    写入文件 /var/www/example.com/public_html/staging.wordpress.2016-05-24.000.xml
    成功：导出全部完成。

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