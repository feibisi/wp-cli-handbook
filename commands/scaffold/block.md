---
title: "wp scaffold block"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Scaffold
    - Commands
    - Repos
---

# wp scaffold block

为插件或主题生成用于注册 Gutenberg 区块的 PHP、JS 和 CSS 代码。

**警告：`wp scaffold block` 已弃用。**

生成区块的官方脚本是 [@wordpress/create-block](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-create-block/) 包。

完整教程请参阅 [创建区块教程](https://developer.wordpress.org/block-editor/getting-started/tutorial/)。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，以详细了解所使用的语法约定。

&lt;slug&gt;
: 区块的内部名称。

[\--title=&lt;title&gt;]
: 区块的显示标题。

[\--dashicon=&lt;dashicon&gt;]
: 用于更轻松识别区块的 dashicon 图标。

[\--category=&lt;category&gt;]
: 用于帮助用户浏览和发现区块的分类名称。
\---
默认值: widgets
选项:
  - common
  - embed
  - formatting
  - layout
  - widgets
\---

[\--theme]
: 在活动主题目录中创建文件。使用 `--theme=<theme>` 指定一个主题，以将文件放置在该主题中。

[\--plugin=&lt;plugin&gt;]
: 在给定插件的目录中创建文件。

[\--force]
: 覆盖已存在的文件。

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