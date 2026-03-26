---
title: "wp user application-password list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Application Password
    - User
    - Commands
---

# wp user application-password list

列出与用户关联的所有应用程序密码。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;user&gt;
: 要获取应用程序密码的用户的登录名、用户邮箱或用户ID。

[\--&lt;field&gt;=&lt;value&gt;]
: 根据特定字段筛选列表。

[\--field=&lt;field&gt;]
: 为每个应用程序密码打印单个字段的值。

[\--fields=&lt;fields&gt;]
: 将输出限制为特定字段。

[\--format=&lt;format&gt;]
: 以特定格式呈现输出。
\---
默认值: table
选项:
  - table
  - csv
  - json
  - count
  - yaml
  - ids
\---

[\--orderby=&lt;fields&gt;]
: 设置按哪个字段排序。
\---
默认值: created
选项:
 - uuid
 - app_id
 - name
 - password
 - created
 - last_used
 - last_ip
\---

[\--order=&lt;order&gt;]
: 设置升序或降序。
\---
默认值: desc
选项:
 - asc
 - desc
\---

### 示例

    # 列出用户应用密码，仅显示应用名称和密码哈希值
    $ wp user application-password list 123 --fields=name,password
    +--------+------------------------------------+
    | name   | password                           |
    +--------+------------------------------------+
    | myapp  | $P$BVGeou1CUot114YohIemgpwxQCzb8O/ |
    +--------+------------------------------------+

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