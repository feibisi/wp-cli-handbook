---
title: "wp cli update"
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

# wp cli update

将 WP-CLI 更新至最新版本。

此命令在 `before_wp_load` 钩子期间运行，恰好在 WP 加载流程开始前执行。

默认行为是检查版本发布 API 以获取最新稳定版本，并在有新版本时提示更新。

使用 `--stable` 参数可安装或重新安装最新的稳定版本。

使用 `--nightly` 参数可安装主分支的最新构建版本。虽然不推荐在生产环境使用，但 nightly 版本包含最新特性，通常足够稳定以用于开发和测试环境。

仅适用于 Phar 安装机制。

### 选项

关于所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考文档。

[\--patch]
: 仅执行补丁更新。

[\--minor]
: 仅执行次要更新。

[\--major]
: 仅执行主要更新。

[\--stable]
: 更新至最新的稳定版本。跳过更新检查。

[\--nightly]
: 更新至主分支的最新构建版本。可能不稳定。

[\--yes]
: 不提示确认。

[\--insecure]
: 如果 TLS 握手失败，则重试而不进行证书验证。注意：这会使请求容易受到中间人攻击。

### EXAMPLES

    # Update CLI.
    $ wp cli update
    You are currently using WP-CLI version 0.24.0. Would you like to update to 0.24.1? [y/n] y
    Downloading from https://github.com/wp-cli/wp-cli/releases/download/v0.24.1/wp-cli-0.24.1.phar...
    New version works. Proceeding to replace.
    Success: Updated WP-CLI to 0.24.1.

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