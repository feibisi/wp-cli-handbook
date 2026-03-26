---
title: "wp option patch"
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

# wp option patch

更新选项中的嵌套值。

### 参数

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;action&gt;
: 要执行的修补操作。
\---
options:
  - insert
  - update
  - delete
\---

&lt;key&gt;
: 选项名称。

&lt;key-path&gt;...
: 用于定位待修补值的键名（一个或多个）。

[&lt;value&gt;]
: 新值。如果省略，则从 STDIN 读取。

[\--format=&lt;format&gt;]
: 值的序列化格式。
\---
default: plaintext
options:
  - plaintext
  - json
\---

### 示例

    # 在名为 'option_name' 的选项上，向 'foo' 键添加 'bar'
    $ wp option patch insert option_name foo bar
    成功：已更新 'option_name' 选项。

    # 在名为 'option_name' 的选项上，将 'foo' 键的值更新为 'new'
    $ wp option patch update option_name foo new
    成功：已更新 'option_name' 选项。

    # 在名为 'option_name' 的选项上，将 'bar' 键的嵌套值设置为补丁文件中的值。
    $ wp option patch update option_name foo bar < patch
    成功：已更新 'option_name' 选项。

    # 在名为 'option_name' 的选项上，更新不存在的键 'not-a-key' 的值。
    $ wp option patch update option_name foo not-a-key new-value
    错误：键 "not-a-key" 不存在数据

    # 在名为 'option_name' 的选项上，更新 'foo' 键的值但未提供值。
    $ wp option patch update option_name foo
    错误：请提供要更新的值。

    # 在名为 'option_name' 的选项上，删除 'foo' 键下的嵌套键 'bar'。
    $ wp option patch delete option_name foo bar
    成功：已更新 'option_name' 选项。

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