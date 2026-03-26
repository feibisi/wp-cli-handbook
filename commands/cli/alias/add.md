---
title: "wp cli alias add"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Alias
    - Cli
    - Commands
---

# wp cli alias add

创建别名。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

### 选项

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考。

&lt;key&gt;
: 别名的键。

[\--set-user=&lt;user&gt;]
: 为别名设置用户。

[\--set-url=&lt;url&gt;]
: 为别名设置 URL。

[\--set-path=&lt;path&gt;]
: 为别名设置路径。

[\--set-ssh=&lt;ssh&gt;]
: 为别名设置 SSH。

[\--set-http=&lt;http&gt;]
: 为别名设置 HTTP。

[\--grouping=&lt;grouping&gt;]
: 用于分组多个别名。

[\--config=&lt;config&gt;]
: 操作时要考虑的配置文件。
\---
默认值: global
选项:
  - global
  - project
\---

### 示例

    # 向全局配置添加别名。
    $ wp cli alias add @prod  --set-ssh=login@host --set-path=/path/to/wordpress/install/ --set-user=wpcli
    Success: Added '@prod' alias.

    # 向项目配置添加别名。
    $ wp cli alias add @prod --set-ssh=login@host --set-path=/path/to/wordpress/install/ --set-user=wpcli --config=project
    Success: Added '@prod' alias.

    # 添加别名组。
    $ wp cli alias add @multiservers --grouping=servera,serverb
    Success: Added '@multiservers' alias.

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