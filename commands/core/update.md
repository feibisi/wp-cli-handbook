---
title: "wp core update"
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

# wp core update

将 WordPress 更新至较新版本。

**别名：** `upgrade`

默认将 WordPress 更新至最新版本。

若出现“错误：另一更新正在进行中”提示，可在确认无其他更新运行后，执行 `wp option delete core_updater.lock` 命令。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，以详细了解所使用的语法约定。

[&lt;zip&gt;]
: 要使用的 zip 文件路径，而不是从 wordpress.org 下载。

[\--minor]
: 仅执行次要版本的更新（例如，从 WP 4.3 更新到 4.3.3，而不是 4.4.2）。

[\--version=&lt;version&gt;]
: 更新到特定版本，而不是最新版本。也可以接受 'nightly'。

[\--force]
: 即使已安装的 WP 版本高于请求的版本，也强制更新。

[\--locale=&lt;locale&gt;]
: 选择要下载的语言。

[\--insecure]
: 如果 TLS 握手失败，则在不进行证书验证的情况下重试下载。注意：这会使请求容易受到中间人攻击。

### EXAMPLES

    # Update WordPress
    $ wp core update
    Updating to version 4.5.2 (en_US)...
    Downloading update from https://downloads.wordpress.org/release/wordpress-4.5.2-no-content.zip...
    Unpacking the update...
    Cleaning up files...
    No files found that need cleaning up
    Success: WordPress updated successfully.

    # Update WordPress using zip file.
    $ wp core update ../latest.zip
    Starting update...
    Unpacking the update...
    Success: WordPress updated successfully.

    # Update WordPress to 3.1 forcefully
    $ wp core update --version=3.1 --force
    Updating to version 3.1 (en_US)...
    Downloading update from https://wordpress.org/wordpress-3.1.zip...
    Unpacking the update...
    Warning: Checksums not available for WordPress 3.1/en_US. Please cleanup files manually.
    Success: WordPress updated successfully.

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