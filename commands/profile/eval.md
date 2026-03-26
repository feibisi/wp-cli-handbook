---
title: "wp profile eval"
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

# wp profile eval

分析任意代码的执行情况。

代码执行发生在 WordPress 完全加载之后，这意味着您可以使用 WordPress、活动插件或当前主题中定义的任何实用工具。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;php-code&gt;
: 要执行的代码，以字符串形式提供。

[\--hook[=&lt;hook&gt;]]
: 关注所有钩子的关键指标，或特定钩子上的回调函数。

[\--fields=&lt;fields&gt;]
: 显示一个或多个字段。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: table
选项:
  - table
  - json
  - yaml
  - csv
\---

[\--order=&lt;order&gt;]
: 升序或降序排列。
\---
默认值: ASC
选项:
  - ASC
  - DESC
\---

[\--orderby=&lt;fields&gt;]
: 设置按哪个字段排序。

### 示例

    # 分析一个发起单个 HTTP 请求的函数。
    $ wp profile eval 'wp_remote_get( "https://www.apple.com/" );' --fields=time,cache_ratio,request_count
    +---------+-------------+---------------+
    | time    | cache_ratio | request_count |
    +---------+-------------+---------------+
    | 0.1009s | 100%        | 1             |
    +---------+-------------+---------------+

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