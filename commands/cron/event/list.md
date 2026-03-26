---
title: "wp cron event list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Event
    - Cron
    - Commands
---

# wp cron event list

列出已安排的 cron 事件。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考文档。

[\--fields=&lt;fields&gt;]
: 将输出限制为特定的对象字段。

[\--&lt;field&gt;=&lt;value&gt;]
: 根据一个或多个字段进行筛选。

[\--field=&lt;field&gt;]
: 为每个事件打印单个字段的值。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: table
可选值:
  - table
  - csv
  - ids
  - json
  - count
  - yaml
\---

### 可用字段

默认情况下，每个 cron 事件将显示以下字段：
* hook
* next_run_gmt
* next_run_relative
* recurrence

以下字段为可选可用：
* time
* sig
* args
* schedule
* interval
* next_run

### 示例

    # 列出已计划的 cron 事件
    $ wp cron event list
    +-------------------+---------------------+---------------------+------------+
    | hook              | next_run_gmt        | next_run_relative   | recurrence |
    +-------------------+---------------------+---------------------+------------+
    | wp_version_check  | 2016-05-31 22:15:13 | 11 小时 57 分钟     | 12 小时    |
    | wp_update_plugins | 2016-05-31 22:15:13 | 11 小时 57 分钟     | 12 小时    |
    | wp_update_themes  | 2016-05-31 22:15:14 | 11 小时 57 分钟     | 12 小时    |
    +-------------------+---------------------+---------------------+------------+

    # 以 JSON 格式列出已计划的 cron 事件
    $ wp cron event list --fields=hook,next_run --format=json
    [{"hook":"wp_version_check","next_run":"2016-05-31 10:15:13"},{"hook":"wp_update_plugins","next_run":"2016-05-31 10:15:13"},{"hook":"wp_update_themes","next_run":"2016-05-31 10:15:14"}]

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