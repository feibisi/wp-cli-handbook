---
title: "wp profile hook"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Profile
    - Commands
    - Repos
---

# wp profile hook

分析 WordPress 钩子（动作和过滤器）的关键指标。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

为了分析特定钩子上的回调函数，该动作或过滤器需要在请求执行期间被触发。

### OPTIONS

请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考，以详细了解所使用的语法约定。

[&lt;hook&gt;]
: 深入查看特定 WordPress 钩子上的回调函数关键指标。

[\--all]
: 分析所有 WordPress 钩子的回调函数。

[\--spotlight]
: 从集合中过滤掉值接近零的日志。

[\--url=&lt;url&gt;]
: 针对指定 URL 执行请求。默认为首页 URL。

[\--fields=&lt;fields&gt;]
: 显示一个或多个字段。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
default: table
options:
  - table
  - json
  - yaml
  - csv
\---

[\--order=&lt;order&gt;]
: 升序或降序排列。
\---
default: ASC
options:
  - ASC
  - DESC
\---

[\--orderby=&lt;fields&gt;]
: 设置按哪个字段排序。

### 示例

    # 分析一个钩子
    $ wp profile hook template_redirect --fields=callback,cache_hits,cache_misses
    +--------------------------------+------------+--------------+
    | callback                       | cache_hits | cache_misses |
    +--------------------------------+------------+--------------+
    | _wp_admin_bar_init()           | 0          | 0            |
    | wp_old_slug_redirect()         | 0          | 0            |
    | redirect_canonical()           | 5          | 0            |
    | WP_Sitemaps-&gt;render_sitemaps() | 0          | 0            |
    | rest_output_link_header()      | 3          | 0            |
    | wp_shortlink_header()          | 0          | 0            |
    | wp_redirect_admin_locations()  | 0          | 0            |
    +--------------------------------+------------+--------------+
    | total (7)                      | 8          | 0            |
    +--------------------------------+------------+--------------+

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