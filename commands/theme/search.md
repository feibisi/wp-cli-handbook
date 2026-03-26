---
title: "wp theme search"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Theme
    - Commands
    - Repos
---

# wp theme search

搜索 WordPress.org 主题目录。

显示 WordPress.org 主题目录中与给定搜索查询匹配的主题。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;search&gt;
: 要搜索的字符串。

[\--page=&lt;page&gt;]
: 要显示的可选页码。
\---
默认值: 1
\---

[\--per-page=&lt;per-page&gt;]
: 要显示的可选结果数量。默认为 10。

[\--field=&lt;field&gt;]
: 打印每个主题的单个字段值。

[\--fields=&lt;fields&gt;]
: 从 API 请求特定字段。默认为 name,slug,author,rating。可接受的值：

    **name**: 主题名称
    **slug**: 主题别名
    **version**: 当前版本号
    **author**: 主题作者
    **preview_url**: 主题预览 URL
    **screenshot_url**: 主题截图 URL
    **rating**: 主题评分
    **num_ratings**: 主题评分数量
    **homepage**: 主题作者主页
    **description**: 主题描述
    **url**: 主题在 wordpress.org 上的 URL

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: table
选项:
  - table
  - csv
  - json
  - count
  - yaml
\---

### 示例

    $ wp theme search photo --per-page=6
    成功：显示 203 个主题中的 6 个。
    +----------------------+----------------------+--------+
    | 名称                 | 别名                 | 评分   |
    +----------------------+----------------------+--------+
    | Photos               | photos               | 100    |
    | Infinite Photography | infinite-photography | 100    |
    | PhotoBook            | photobook            | 100    |
    | BG Photo Frame       | bg-photo-frame       | 0      |
    | fPhotography         | fphotography         | 0      |
    | Photo Perfect        | photo-perfect        | 98     |
    +----------------------+----------------------+--------+

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