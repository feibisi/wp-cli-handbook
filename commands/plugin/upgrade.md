---
title: "wp plugin upgrade"
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

# wp plugin upgrade

更新一个或多个插件。

这是 `wp plugin update` 命令的别名。

### 选项

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考文档。

[&lt;plugin&gt;...]
: 要更新的一个或多个插件。

[\--all]
: 如果设置此选项，所有有可用更新的插件都将被更新。

[\--exclude=&lt;name&gt;]
: 逗号分隔的插件名称列表，这些插件将被排除在更新之外。

[\--minor]
: 仅执行次要版本的更新（例如，从 1.3 更新到 1.4，而不是 2.0）。

[\--patch]
: 仅执行补丁版本的更新（例如，从 1.3 更新到 1.3.3，而不是 1.4）。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: table
可选值:
  - table
  - csv
  - json
  - summary
\---

[\--version=&lt;version&gt;]
: 如果设置此选项，插件将更新到指定的版本。

[\--dry-run]
: 预览哪些插件将被更新。

[\--insecure]
: 如果 TLS 握手失败，则在不进行证书验证的情况下重试下载。注意：这会使请求容易受到中间人攻击。

### EXAMPLES

    $ wp plugin update bbpress --version=dev
    Installing bbPress (Development Version)
    Downloading install package from https://downloads.wordpress.org/plugin/bbpress.zip...
    Unpacking the package...
    Installing the plugin...
    Removing the old version of the plugin...
    Plugin updated successfully.
    Success: Updated 1 of 2 plugins.

    $ wp plugin update --all
    Enabling Maintenance mode...
    Downloading update from https://downloads.wordpress.org/plugin/akismet.3.1.11.zip...
    Unpacking the update...
    Installing the latest version...
    Removing the old version of the plugin...
    Plugin updated successfully.
    Downloading update from https://downloads.wordpress.org/plugin/nginx-champuru.3.2.0.zip...
    Unpacking the update...
    Installing the latest version...
    Removing the old version of the plugin...
    Plugin updated successfully.
    Disabling Maintenance mode...
    +------------------------+-------------+-------------+---------+
    | name                   | old_version | new_version | status  |
    +------------------------+-------------+-------------+---------+
    | akismet                | 3.1.3       | 3.1.11      | Updated |
    | nginx-cache-controller | 3.1.1       | 3.2.0       | Updated |
    +------------------------+-------------+-------------+---------+
    Success: Updated 2 of 2 plugins.

    $ wp plugin update --all --exclude=akismet
    Enabling Maintenance mode...
    Downloading update from https://downloads.wordpress.org/plugin/nginx-champuru.3.2.0.zip...
    Unpacking the update...
    Installing the latest version...
    Removing the old version of the plugin...
    Plugin updated successfully.
    Disabling Maintenance mode...
    +------------------------+-------------+-------------+---------+
    | name                   | old_version | new_version | status  |
    +------------------------+-------------+-------------+---------+
    | nginx-cache-controller | 3.1.1       | 3.2.0       | Updated |
    +------------------------+-------------+-------------+---------+

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