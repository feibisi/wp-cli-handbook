---
title: "wp option list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Option
    - Commands
    - Repos
---

# wp option list

列出选项及其值。

### 选项

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考。

[\--search=&lt;pattern&gt;]
: 使用通配符（ * 和 ? ）来匹配选项名称。

[\--exclude=&lt;pattern&gt;]
: 要排除的模式。使用通配符（ * 和 ? ）来匹配选项名称。

[\--autoload=&lt;value&gt;]
: 当值为 on 时仅匹配自动加载选项，当值为 off 时仅匹配非自动加载选项。

[\--transients]
: 仅列出瞬态选项。使用 `--no-transients` 忽略所有瞬态选项。

[\--unserialize]
: 在输出中反序列化选项值。

[\--field=&lt;field&gt;]
: 打印单个字段的值。

[\--fields=&lt;fields&gt;]
: 将输出限制为特定的对象字段。

[\--format=&lt;format&gt;]
: 值的序列化格式。total_bytes 显示匹配选项的总大小（字节）。
\---
默认值: table
选项:
  - table
  - json
  - csv
  - count
  - yaml
  - total_bytes
\---

[\--orderby=&lt;fields&gt;]
: 设置按哪个字段排序。
\---
默认值: option_id
选项:
 - option_id
 - option_name
 - option_value
\---

[\--order=&lt;order&gt;]
: 设置升序或降序。
\---
默认值: asc
选项:
 - asc
 - desc
\---

### 可用字段

默认情况下，每个匹配的选项将显示以下字段：

* option_name
* option_value

以下字段可选显示：

* autoload
* size_bytes

### 示例

    # 获取所有自动加载选项的总大小。
    $ wp option list --autoload=on --format=total_bytes
    33198

    # 查找最大的瞬态选项。
    $ wp option list --search="*_transient_*" --fields=option_name,size_bytes | sort -n -k 2 | tail
    option_name size_bytes
    _site_transient_timeout_theme_roots 10
    _site_transient_theme_roots 76
    _site_transient_update_themes   181
    _site_transient_update_core 808
    _site_transient_update_plugins  6645

    # 列出所有以 "i2f_" 开头的选项。
    $ wp option list --search="i2f_*"
    +-------------+--------------+
    | option_name | option_value |
    +-------------+--------------+
    | i2f_version | 0.1.0        |
    +-------------+--------------+

    # 删除所有以 "theme_mods_" 开头的选项。
    $ wp option list --search="theme_mods_*" --field=option_name | xargs -I % wp option delete %
    Success: Deleted 'theme_mods_twentysixteen' option.
    Success: Deleted 'theme_mods_twentyfifteen' option.
    Success: Deleted 'theme_mods_twentyfourteen' option.

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