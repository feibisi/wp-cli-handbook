---
title: "wp config list"
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

# wp config list

列出 wp-config.php 文件中定义的变量、常量和文件包含项。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

### 选项

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考。

[&lt;filter&gt;...]
: 用于过滤列表的名称或部分名称。

[\--fields=&lt;fields&gt;]
: 将输出限制为特定字段。默认为所有字段。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。Dotenv 格式仅限于非对象值。
\---
默认值: table
选项:
  - table
  - csv
  - json
  - yaml
  - dotenv
\---

[\--strict]
: 提供过滤器时强制执行严格匹配。

[\--config-file=&lt;path&gt;]
: 指定要读取的配置文件路径。默认为 WordPress 安装根目录下的 "wp-config.php" 文件。

### 示例

    # 列出 wp-config.php 文件中定义的常量和变量。
    $ wp config list
    +------------------+------------------------------------------------------------------+----------+
    | 键名             | 值                                                               | 类型     |
    +------------------+------------------------------------------------------------------+----------+
    | table_prefix     | wp_                                                              | variable |
    | DB_NAME          | wp_cli_test                                                      | constant |
    | DB_USER          | root                                                             | constant |
    | DB_PASSWORD      | root                                                             | constant |
    | AUTH_KEY         | r6+@shP1yO&amp;$)1gdu.hl[/j;7Zrvmt~o;#WxSsa0mlQOi24j2cR,7i+QM/#7S:o^ | constant |
    | SECURE_AUTH_KEY  | iO-z!_m--YH$Tx2tf/&amp;V,YW*13Z_HiRLqi)d?$o-tMdY+82pK$`T.NYW~iTLW;xp | constant |
    +------------------+------------------------------------------------------------------+----------+

    # 仅列出 wp-config.php 文件中的数据库用户名和密码。
    $ wp config list DB_USER DB_PASSWORD --strict
    +------------------+-------+----------+
    | 键名             | 值    | 类型     |
    +------------------+-------+----------+
    | DB_USER          | root  | constant |
    | DB_PASSWORD      | root  | constant |
    +------------------+-------+----------+

    # 列出 wp-config.php 文件中的所有盐值。
    $ wp config list _SALT
    +------------------+------------------------------------------------------------------+----------+
    | 键名             | 值                                                               | 类型     |
    +------------------+------------------------------------------------------------------+----------+
    | AUTH_SALT        | n:]Xditk+_7>Qi=>BmtZHiH-6/Ecrvl(V5ceeGP:{>?;BT^=[B3-0>,~F5z$(+Q$ | constant |
    | SECURE_AUTH_SALT | ?Z/p|XhDw3w}?c.z%|+BAr|(Iv*H%%U+Du&kKR y?cJOYyRVRBeB[2zF-`(&gt;+LCC | constant |
    | LOGGED_IN_SALT   | +$@(1{b~Z~s}Cs&gt;8Y]6[m6~TnoCDpE&gt;O%e75u}&amp;6kUH!&gt;q:7uM4lxbB6[1pa_X,q | constant |
    | NONCE_SALT       | _x+F li|QL?0OSQns1_JZ{|Ix3Jleox-71km/gifnyz8kmo=w-;@AE8W,(fP&lt;N}2 | constant |
    +------------------+------------------------------------------------------------------+----------+

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