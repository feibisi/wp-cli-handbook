---
title: "wp core download"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Core
    - Commands
    - Repos
---

# wp core download

下载 WordPress 核心文件。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

下载并解压 WordPress 核心文件到指定路径。未指定路径时使用当前目录。下载的构建包会验证其 md5 校验值，然后缓存到本地文件系统。后续使用此命令时，若本地缓存仍存在，则会直接使用缓存。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，详细了解所使用的语法约定。

[&lt;download-url&gt;]
: 直接从提供的 URL 下载，而不是从 wordpress.org 服务器获取 URL。

[\--path=&lt;path&gt;]
: 指定安装 WordPress 的路径。默认为当前目录。

[\--locale=&lt;locale&gt;]
: 选择要下载的语言版本。

[\--version=&lt;version&gt;]
: 选择要下载的版本。接受版本号、'latest' 或 'nightly'。

[\--skip-content]
: 下载不包含默认主题和插件的 WordPress。

[\--force]
: 如果文件已存在，则覆盖现有文件。

[\--insecure]
: 如果 TLS 握手失败，则在不进行证书验证的情况下重试下载。注意：这会使请求容易受到中间人攻击。

[\--extract]
: 是否解压下载的文件。默认为 true。

### EXAMPLES

    $ wp core download --locale=nl_NL
    Downloading WordPress 4.5.2 (nl_NL)...
    md5 hash verified: c5366d05b521831dd0b29dfc386e56a5
    Success: WordPress downloaded.

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