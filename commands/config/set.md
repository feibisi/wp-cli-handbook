---
title: "wp config set"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Config
    - Commands
    - Repos
---

# wp config set

设置 wp-config.php 文件中定义的特定常量或变量的值。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

### 选项

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考。

&lt;名称&gt;
: wp-config.php 常量或变量的名称。

&lt;值&gt;
: 要为 wp-config.php 常量或变量设置的值。

[\--add]
: 如果值尚不存在，则添加它。这是默认行为，可使用 --no-add 覆盖。

[\--raw]
: 将值按原样放入 wp-config.php 文件，而不是作为带引号的字符串。

[\--anchor=&lt;锚点&gt;]
: 用于锚定新值添加位置的字符串。默认为 "/* That's all, stop editing!"。特殊情况 "EOF" 字符串使用文件末尾作为锚点。

[\--placement=&lt;放置位置&gt;]
: 相对于锚点字符串放置新值的位置。
\---
默认值: 'before'
选项:
  - before
  - after
\---

[\--separator=&lt;分隔符&gt;]
: 在添加的值与其锚点字符串之间放置的分隔符字符串。将识别并正确解释以下转义序列：'\n' => 换行，'\r' => 回车，'\t' => 制表符。默认为单个 EOL（在 *nix 上为 "\n"，在 Windows 上为 "\r\n"）。

[\--type=&lt;类型&gt;]
: 要设置的配置值的类型。默认为 'all'。
\---
默认值: all
选项:
  - constant
  - variable
  - all
\---

[\--config-file=&lt;路径&gt;]
: 指定要修改的配置文件的路径。默认为 WordPress 安装根目录下的文件名 "wp-config.php"。

### EXAMPLES

    # Set the WP_DEBUG constant to true.
    $ wp config set WP_DEBUG true --raw
    Success: Updated the constant 'WP_DEBUG' in the 'wp-config.php' file with the raw value 'true'.

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