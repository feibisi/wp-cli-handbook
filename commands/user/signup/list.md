---
title: "wp user signup list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Signup
    - User
    - Commands
---

# wp user signup list

列出注册用户。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考文档。

[\--&lt;字段&gt;=&lt;值&gt;]
: 根据特定字段筛选列表。

[\--field=&lt;字段&gt;]
: 为每个注册用户打印单个字段的值。

[\--fields=&lt;字段&gt;]
: 将输出限制为特定的对象字段。

[\--format=&lt;格式&gt;]
: 以特定格式渲染输出。
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

[\--per_page=&lt;每页数量&gt;]
: 将注册用户数量限制为给定值。默认为无限制。

### 可用字段

以下字段将默认显示在每个注册记录中：

* signup_id
* user_login
* user_email
* registered
* active
* activation_key

以下字段为可选显示：

* domain
* path
* title
* activated
* meta

### 示例

    # 列出注册 ID。
    $ wp user signup list --field=signup_id
    1

    # 列出所有注册信息。
    $ wp user signup list
    +-----------+------------+---------------------+---------------------+--------+------------------+
    | signup_id | user_login | user_email          | registered          | active | activation_key   |
    +-----------+------------+---------------------+---------------------+--------+------------------+
    | 1         | bobuser    | bobuser@example.com | 2024-03-13 05:46:53 | 1      | 7320b2f009266618 |
    | 2         | johndoe    | johndoe@example.com | 2024-03-13 06:24:44 | 0      | 9068d859186cd0b5 |
    +-----------+------------+---------------------+---------------------+--------+------------------+

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