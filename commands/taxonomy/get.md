---
title: "wp taxonomy get"
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

# wp taxonomy get

获取已注册分类法的详细信息。

### 选项

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考。

&lt;taxonomy&gt;
: 分类法别名。

[\--field=&lt;field&gt;]
: 不返回整个分类法，而是返回单个字段的值。

[\--fields=&lt;fields&gt;]
: 将输出限制在特定字段。默认为所有字段。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: table
选项:
  - table
  - csv
  - json
  - yaml
\---

### 可用字段

以下字段将默认显示于指定的分类法中：

* name
* label
* description
* object_type
* show_tagcloud
* hierarchical
* public
* labels
* cap

以下字段为可选可用：

* count

### 示例

    # 获取 `category` 分类法的详细信息。
    $ wp taxonomy get category --fields=name,label,object_type
    +-------------+------------+
    | Field       | Value      |
    +-------------+------------+
    | name        | category   |
    | label       | Categories |
    | object_type | ["post"]   |
    +-------------+------------+

    # 获取 'post_tag' 分类法的权限信息。
    $ wp taxonomy get post_tag --field=cap
    {"manage_terms":"manage_categories","edit_terms":"manage_categories","delete_terms":"manage_categories","assign_terms":"edit_posts"}

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