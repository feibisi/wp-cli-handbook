---
title: "wp theme list"
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

# wp theme list

获取主题列表。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

[\--&lt;字段&gt;=&lt;值&gt;]
: 根据字段的值筛选结果。

[\--field=&lt;字段&gt;]
: 为每个主题打印单个字段的值。

[\--fields=&lt;字段&gt;]
: 将输出限制为特定的对象字段。

[\--format=&lt;格式&gt;]
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

[\--status=&lt;状态&gt;]
: 按主题状态筛选输出。
\---
选项:
  - active
  - parent
  - inactive
\---

[\--skip-update-check]
: 如果设置，将跳过主题更新检查。

### 可用字段

以下字段将在每个主题中默认显示：

* name
* status
* update
* version
* update_version
* auto_update

以下字段为可选字段：

* update_package
* update_id
* title
* description

### 示例

    # 列出非活动主题。
    $ wp theme list --status=inactive --format=csv
    name,status,update,version,update_version,auto_update
    twentyfourteen,inactive,none,3.8,,off
    twentysixteen,inactive,available,3.0,3.1,off

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