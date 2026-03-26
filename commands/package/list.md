---
title: "wp package list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Package
    - Commands
    - Repos
---

# wp package list

列出已安装的 WP-CLI 包。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

[\--fields=&lt;fields&gt;]
: 将输出限制为特定字段。默认为所有字段。

[\--format=&lt;format&gt;]
: 以特定格式呈现输出。
\---
默认值: table
选项:
  - table
  - csv
  - ids
  - json
  - yaml
\---

### 可用字段

默认情况下，每个包将显示以下字段：

* name
* authors
* version
* update
* update_version

以下字段为可选可用：

* description

### 示例

    # 列出已安装的包。
    $ wp package list
    +-----------------------+------------------+----------+-----------+----------------+
    | name                  | authors          | version  | update    | update_version |
    +-----------------------+------------------+----------+-----------+----------------+
    | wp-cli/server-command | Daniel Bachhuber | dev-main | available | 2.x-dev        |
    +-----------------------+------------------+----------+-----------+----------------+

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