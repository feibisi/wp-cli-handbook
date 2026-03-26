---
title: "wp plugin list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Plugin
    - Commands
    - Repos
---

# wp plugin list

获取插件列表。

显示站点上已安装插件的列表，包括激活状态、是否有可用更新等信息。

使用 `--status=dropin` 可列出已安装的 dropins（例如 `object-cache.php`）。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，详细了解所使用的语法约定。

[\--&lt;field&gt;=&lt;value&gt;]
: 根据字段值筛选结果。

[\--field=&lt;field&gt;]
: 为每个插件打印单个字段的值。

[\--fields=&lt;fields&gt;]
: 将输出限制为特定的对象字段。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: table
选项:
  - table
  - csv
  - count
  - json
  - yaml
\---

[\--status=&lt;status&gt;]
: 按插件状态筛选输出。
\---
选项:
  - active
  - active-network
  - dropin
  - inactive
  - must-use
\---

[\--skip-update-check]
: 如果设置，将跳过插件更新检查。

[\--recently-active]
: 如果设置，将仅显示最近活动的插件，并且状态筛选器将被忽略。

### 可用字段

以下字段将默认显示在每个插件的信息中：

* name（名称）
* status（状态）
* update（更新）
* version（版本）
* update_version（更新版本）
* auto_update（自动更新）

以下字段为可选显示：

* update_package（更新包）
* update_id（更新ID）
* title（标题）
* description（描述）
* file（文件）
* author（作者）
* tested_up_to（测试至）
* requires（要求）
* requires_php（PHP要求）
* wporg_status（WordPress.org状态）
* wporg_last_updated（WordPress.org最后更新）

### 示例

    # 列出站点上处于活动状态的插件。
    $ wp plugin list --status=active --format=json
    [{"name":"dynamic-hostname","status":"active","update":"none","version":"0.4.2","update_version":"","auto_update":"off"},{"name":"tinymce-templates","status":"active","update":"none","version":"4.8.1","update_version":"","auto_update":"off"},{"name":"wp-multibyte-patch","status":"active","update":"none","version":"2.9","update_version":"","auto_update":"off"},{"name":"wp-total-hacks","status":"active","update":"none","version":"4.7.2","update_version":"","auto_update":"off"}]

    # 列出网络中每个站点上的插件。
    $ wp site list --field=url | xargs -I % wp plugin list --url=%
    +---------+----------------+-----------+---------+-----------------+------------+
    | name    | status         | update    | version | update_version | auto_update |
    +---------+----------------+-----------+---------+----------------+-------------+
    | akismet | active-network | none      | 5.3.1   |                | on          |
    | hello   | inactive       | available | 1.6     | 1.7.2          | off         |
    +---------+----------------+-----------+---------+----------------+-------------+
    +---------+----------------+-----------+---------+----------------+-------------+
    | name    | status         | update    | version | update_version | auto_update |
    +---------+----------------+-----------+---------+----------------+-------------+
    | akismet | active-network | none      | 5.3.1   |                | on          |
    | hello   | inactive       | available | 1.6     | 1.7.2          | off         |
    +---------+----------------+-----------+---------+----------------+-------------+

    # 检查插件在 WordPress.org 上是否仍处于活动状态。
    $ wp plugin list --fields=name,wporg_status,wporg_last_updated
    +--------------------+--------------+--------------------+
    | name               | wporg_status | wporg_last_updated |
    +--------------------+--------------+--------------------+
    | akismet            | active       | 2023-12-11         |
    | user-switching     | active       | 2023-11-17         |
    | wordpress-importer | active       | 2023-04-28         |
    | local              |              |                    |
    +--------------------+--------------+--------------------+

    # 列出站点上最近活动的插件。
    $ wp plugin list --recently-active --field=name --format=json
    ["akismet","bbpress","buddypress"]

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