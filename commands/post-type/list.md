---
title: "wp post-type list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Post Type
    - Commands
    - Repos
---

# wp post-type list

列出已注册的文章类型。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

[\--&lt;字段&gt;=&lt;值&gt;]
: 根据一个或多个字段进行筛选（可用字段列表请参见 get_post_types() 的第一个参数）。

[\--field=&lt;字段&gt;]
: 为每个文章类型打印单个字段的值。

[\--fields=&lt;字段&gt;]
: 将输出限制为特定的文章类型字段。

[\--format=&lt;格式&gt;]
: 以特定格式渲染输出。
\---
默认值: table
可选值:
  - table
  - csv
  - json
  - count
  - yaml
\---

### 可用字段

以下字段将默认显示给每种文章类型：

* name
* label
* description
* hierarchical
* public
* capability_type

以下字段为可选可用：

* count

### 示例

    # 列出已注册的文章类型
    $ wp post-type list --format=csv
    name,label,description,hierarchical,public,capability_type
    post,Posts,,,1,post
    page,Pages,,1,1,page
    attachment,Media,,,1,post
    revision,Revisions,,,,post
    nav_menu_item,"Navigation Menu Items",,,,post

    # 列出具有 'post' 权限类型的文章类型
    $ wp post-type list --capability_type=post --fields=name,public
    +---------------+--------+
    | name          | public |
    +---------------+--------+
    | post          | 1      |
    | attachment    | 1      |
    | revision      |        |
    | nav_menu_item |        |
    +---------------+--------+

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