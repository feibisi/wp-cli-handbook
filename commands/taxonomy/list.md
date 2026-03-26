---
title: "wp taxonomy list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Taxonomy
    - Commands
    - Repos
---

# wp taxonomy list

列出已注册的分类法。

### 选项

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考文档。

[\--&lt;字段&gt;=&lt;值&gt;]
: 按一个或多个字段进行筛选（可用字段列表请参见 get_taxonomies() 函数的第一个参数）。

[\--field=&lt;字段&gt;]
: 为每个分类法打印单个字段的值。

[\--fields=&lt;字段&gt;]
: 将输出限制为特定的分类法字段。

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

默认情况下，每个术语将显示以下字段：

* 名称
* 标签
* 描述
* 对象类型
* 显示标签云
* 层级结构
* 公开

以下字段为可选可用：

* 计数

### 示例

    # 列出所有分类法。
    $ wp taxonomy list --format=csv
    name,label,description,object_type,show_tagcloud,hierarchical,public
    category,Categories,,post,1,1,1
    post_tag,Tags,,post,1,,1
    nav_menu,"Navigation Menus",,nav_menu_item,,,
    link_category,"Link Categories",,link,1,,
    post_format,Format,,post,,,1

    # 列出对象类型为 'post' 的所有分类法。
    $ wp taxonomy list --object_type=post --fields=name,public
    +-------------+--------+
    | name        | public |
    +-------------+--------+
    | category    | 1      |
    | post_tag    | 1      |
    | post_format | 1      |
    +-------------+--------+

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