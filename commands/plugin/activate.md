---
title: "wp plugin activate"
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

# wp plugin activate

激活一个或多个插件。

### 选项

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考文档。

[&lt;plugin&gt;...]
: 要激活的一个或多个插件。

[\--all]
: 如果设置，将激活所有插件。

[\--exclude=&lt;name&gt;]
: 逗号分隔的插件别名列表，这些插件将被排除在激活操作之外。

[\--network]
: 如果设置，插件将在整个多站点网络中被激活。

### 示例

    # 激活插件
    $ wp plugin activate hello
    插件 'hello' 已激活。
    成功：已激活 1 个插件中的 1 个。

    # 在整个多站点网络中激活插件
    $ wp plugin activate hello --network
    插件 'hello' 已在网络中激活。
    成功：已在网络中激活 1 个插件中的 1 个。

    # 激活最近活跃过的插件
    $ wp plugin activate $(wp plugin list --recently-active --field=name)
    插件 'bbpress' 已激活。
    插件 'buddypress' 已激活。
    成功：已激活 2 个插件中的 2 个。

    # 在多站点上激活最近活跃过的插件
    $ wp plugin activate $(wp plugin list --recently-active --field=name) --network
    插件 'bbpress' 已在网络中激活。
    插件 'buddypress' 已在网络中激活。
    成功：已激活 2 个插件中的 2 个。

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