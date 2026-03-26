---
title: "wp package browse"
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

# wp package browse

浏览可供安装的 WP-CLI 软件包。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

列出可从[软件包索引](http://wp-cli.org/package-index/)安装的软件包。尽管出于向后兼容性考虑，软件包索引将继续保留，但它已被弃用且不再更新。请参阅 https://github.com/wp-cli/ideas/issues/51 了解其潜在替代方案。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，以详细了解所使用的语法约定。

[\--fields=&lt;fields&gt;]
: 将输出限制在特定字段。默认为所有字段。

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

* name（名称）
* description（描述）
* authors（作者）
* version（版本）

没有可选字段。

### 示例

    $ wp package browse --format=yaml
    ---
    10up/mu-migration:
      name: 10up/mu-migration
      description: 一组 WP-CLI 命令，用于支持将单个 WordPress 实例迁移到多站点
      authors: Nícholas André
      version: dev-main, dev-develop
    aaemnnosttv/wp-cli-dotenv-command:
      name: aaemnnosttv/wp-cli-dotenv-command
      description: WP-CLI 的 Dotenv 命令
      authors: Evan Mattson
      version: v0.1, v0.1-beta.1, v0.2, dev-main, dev-dev, dev-develop, dev-tests/behat
    aaemnnosttv/wp-cli-http-command:
      name: aaemnnosttv/wp-cli-http-command
      description: 使用 WordPress HTTP API 的 WP-CLI 命令
      authors: Evan Mattson
      version: dev-main

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