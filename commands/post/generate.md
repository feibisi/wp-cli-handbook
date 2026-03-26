---
title: "wp post generate"
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

# wp post generate

生成一些文章。

创建指定数量的包含虚拟数据的新文章。

### 选项

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考。

[\--count=&lt;数量&gt;]
: 要生成多少篇文章？
\---
默认值: 100
\---

[\--post_type=&lt;类型&gt;]
: 生成文章的类型。
\---
默认值: post
\---

[\--post_status=&lt;状态&gt;]
: 生成文章的状态。
\---
默认值: publish
\---

[\--post_title=&lt;文章标题&gt;]
: 文章标题。
\---
默认值:
\---

[\--post_author=&lt;登录名&gt;]
: 生成文章的作者。
\---
默认值:
\---

[\--post_date=&lt;年-月-日-时-分-秒&gt;]
: 文章的日期。默认为当前时间。

[\--post_date_gmt=&lt;年-月-日-时-分-秒&gt;]
: 文章在 GMT 时区的日期。默认为 --post_date 的值。

[\--post_content]
: 如果设置，命令将从 STDIN 读取文章内容。

[\--max_depth=&lt;数字&gt;]
: 对于分层文章类型，生成子文章到特定深度。
\---
默认值: 1
\---

[\--format=&lt;格式&gt;]
: 以特定格式渲染输出。
\---
默认值: progress
选项:
  - progress
  - ids
\---

### 示例

    # 生成文章。
    $ wp post generate --count=10 --post_type=page --post_date=1999-01-04
    正在生成文章  100% [================================================] 0:01 / 0:04

    # 生成包含获取内容的文章。
    $ curl -N https://loripsum.net/api/5 | wp post generate --post_content --count=10
      % 总计    % 已接收 % 已传输   平均速度   时间    时间     时间    当前
                                     下载  上传   总计   已用    剩余   速度
    100  2509  100  2509    0     0    616      0  0:00:04  0:00:04 --:--:--   616
    正在生成文章  100% [================================================] 0:01 / 0:04

    # 为每个生成的文章添加元数据。
    $ wp post generate --format=ids | xargs -d ' ' -I % wp post meta add % foo bar
    成功：已添加自定义字段。
    成功：已添加自定义字段。
    成功：已添加自定义字段。

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