---
title: "wp core verify-checksums"
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

# wp core verify-checksums

验证 WordPress 文件与 WordPress.org 校验和的一致性。

此命令在 `before_wp_load` 钩子上运行，恰好在 WordPress 加载过程开始之前。

从 WordPress.org 下载当前版本的 md5 校验和，并与当前已安装的文件进行比较。

出于安全考虑，验证校验和时避免加载 WordPress。

如果使用此命令验证时遇到问题，请确保根据网站管理区域 `仪表盘->更新` 菜单中的值传递相应的 `--locale` 和 `--version` 参数。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，了解所用语法约定的详细说明。

[\--include-root]
: 验证根目录中的所有文件和文件夹，如果发现任何非 WordPress 项目则发出警告。

[\--version=&lt;version&gt;]
: 针对特定版本的 WordPress 验证校验和。

[\--locale=&lt;locale&gt;]
: 针对特定区域设置的 WordPress 验证校验和。

[\--insecure]
: 如果 TLS 握手失败，则在不进行证书验证的情况下重试下载。注意：这会使请求容易受到中间人攻击。

[\--exclude=&lt;files&gt;]
: 从校验和验证中排除特定文件。提供以逗号分隔的文件路径列表。

[\--format=&lt;format&gt;]
: 以特定格式呈现输出。提供此选项时，消息将以所选格式显示。
\---
默认值: plain
选项:
  - plain
  - table
  - json
  - csv
  - yaml
  - count
\---

### 示例

    # 验证校验和
    $ wp core verify-checksums
    成功：WordPress 安装通过校验和验证。

    # 验证指定 WordPress 版本的校验和
    $ wp core verify-checksums --version=4.0
    成功：WordPress 安装通过校验和验证。

    # 验证指定语言环境的校验和
    $ wp core verify-checksums --locale=en_US
    成功：WordPress 安装通过校验和验证。

    # 验证指定语言环境的校验和
    $ wp core verify-checksums --locale=ja
    警告：文件未通过校验和验证：wp-includes/version.php
    警告：文件未通过校验和验证：readme.html
    警告：文件未通过校验和验证：wp-config-sample.php
    错误：WordPress 安装未通过校验和验证。

    # 验证校验和并排除文件
    $ wp core verify-checksums --exclude="readme.html"
    成功：WordPress 安装通过校验和验证。

    # 使用格式化输出验证校验和
    $ wp core verify-checksums --format=json
    [{"file":"readme.html","message":"File doesn't verify against checksum"}]
    错误：WordPress 安装未通过校验和验证。

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