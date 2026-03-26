---
title: "wp user list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - User
    - Commands
    - Repos
---

# wp user list

列出用户。

基于 [WP_User_Query()](https://developer.wordpress.org/reference/classes/wp_user_query/prepare_query/) 支持的所有参数来显示 WordPress 用户。

### 选项

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考文档。

[\--role=&lt;role&gt;]
: 仅显示具有特定角色的用户。

[\--&lt;field&gt;=&lt;value&gt;]
: 通过一个或多个 WP_User_Query() 参数控制输出。

[\--network]
: 为多站点网络列出所有用户。

[\--field=&lt;field&gt;]
: 为每个用户打印单个字段的值。

[\--fields=&lt;fields&gt;]
: 将输出限制为特定的对象字段。

[\--format=&lt;format&gt;]
: 以特定格式呈现输出。
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

### 可用字段

默认情况下，每个用户将显示以下字段：

* ID
* user_login
* display_name
* user_email
* user_registered
* roles

以下字段为可选可用：

* user_pass
* user_nicename
* user_url
* user_activation_key
* user_status
* spam
* deleted
* caps
* cap_key
* allcaps
* filter
* url

### 示例

    # 列出用户 ID
    $ wp user list --field=ID
    1

    # 列出具有管理员角色的用户
    $ wp user list --role=administrator --format=csv
    ID,user_login,display_name,user_email,user_registered,roles
    1,supervisor,supervisor,supervisor@gmail.com,"2016-06-03 04:37:00",administrator

    # 仅列出指定字段的用户信息
    $ wp user list --fields=display_name,user_email --format=json
    [{"display_name":"supervisor","user_email":"supervisor@gmail.com"}]

    # 按 'last_activity' 元数据值排序列出用户
    $ wp user list --meta_key=last_activity --orderby=meta_value_num

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