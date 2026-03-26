---
title: "wp cli info"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Cli
    - Commands
    - Repos
---

# wp cli info

打印有关 WP-CLI 环境的各种详细信息。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

此命令有助于诊断目的，分享以下信息：

* 操作系统信息。
* Shell 信息。
* 使用的 PHP 二进制文件。
* PHP 二进制版本。
* 使用的 php.ini 配置文件（通常与 Web 环境不同）。
* WP-CLI 根目录：WP-CLI 的安装位置（如果是非 Phar 安装）。
* WP-CLI 全局配置：全局配置 YAML 文件的位置。
* WP-CLI 项目配置：项目配置 YAML 文件的位置。
* WP-CLI 版本：当前安装的版本。

有关全局和项目配置 YAML 文件的更多详细信息，请参阅[配置文档](https://make.wordpress.org/cli/handbook/references/config/)。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，以详细了解所使用的语法约定。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: list
选项:
  - list
  - json
\---

### 示例

    # 显示 CLI 环境的各类数据。
    $ wp cli info
    操作系统：Linux 4.10.0-42-generic #46~16.04.1-Ubuntu SMP Mon Dec 4 15:57:59 UTC 2017 x86_64
    Shell：   /usr/bin/zsh
    PHP 可执行文件：  /usr/bin/php
    PHP 版本：7.1.12-1+ubuntu16.04.1+deb.sury.org+1
    使用的 php.ini：    /etc/php/7.1/cli/php.ini
    WP-CLI 根目录：    phar://wp-cli.phar
    WP-CLI 包目录：    /home/person/.wp-cli/packages/
    WP-CLI 全局配置：
    WP-CLI 项目配置：
    WP-CLI 版本：1.5.0

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