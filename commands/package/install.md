---
title: "wp package install"
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

# wp package install

安装一个 WP-CLI 包。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

包必须是有效的 Composer 包，可以指定为：

* 来自 WP-CLI 包索引的包名称。
* 当前 shell 用户可访问的 Git URL。
* 本地机器上的目录路径。
* 本地或远程的 .zip 文件。

默认情况下，包安装到 `~/.wp-cli/packages/`。使用 `WP_CLI_PACKAGES_DIR` 环境变量提供自定义路径。

安装本地目录时，WP-CLI 仅注册对该目录的引用。如果移动或删除该目录，WP-CLI 的引用将失效。

安装 .zip 文件时，WP-CLI 将包解压到 `~/.wp-cli/packages/local/<package-name>`。

如果需要 Github 令牌授权，可以使用 GitHub 个人访问令牌 (https://github.com/settings/tokens)。以下命令将向 Composer 的全局配置添加 GitHub 个人访问令牌：
composer config -g github-oauth.github.com &lt;GITHUB_TOKEN&gt; 添加后，&lt;GITHUB_TOKEN&gt; 的值将用于未来的授权请求。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，详细了解所使用的语法约定。

&lt;name|git|path|zip&gt;
: 要安装的软件包名称、git URL、目录路径或 .zip 文件。名称可以可选地包含版本约束（例如 wp-cli/server-command:@stable）。

[\--insecure]
: 如果 TLS 握手失败，则在不验证证书的情况下重试下载。注意：这会使请求容易受到中间人攻击。

### 示例

    # 安装托管在 git URL 的包。
    $ wp package install runcommand/hook

    # 安装最新的稳定版本。
    $ wp package install wp-cli/server-command:@stable

    # 安装托管在 GitLab.com URL 的包。
    $ wp package install https://gitlab.com/foo/wp-cli-bar-command.git

    # 安装 .zip 文件中的包。
    $ wp package install google-sitemap-generator-cli.zip

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