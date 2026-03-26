---
title: "wp config create"
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

# wp config create

生成 wp-config.php 文件。

创建一个包含数据库常量的新 wp-config.php 文件，并验证数据库常量是否正确。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

\--dbname=&lt;dbname&gt;
: 设置数据库名称。

\--dbuser=&lt;dbuser&gt;
: 设置数据库用户。

[\--dbpass=&lt;dbpass&gt;]
: 设置数据库用户密码。

[\--dbhost=&lt;dbhost&gt;]
: 设置数据库主机。
\---
默认值：localhost
\---

[\--dbprefix=&lt;dbprefix&gt;]
: 设置数据库表前缀。
\---
默认值：wp_
\---

[\--dbcharset=&lt;dbcharset&gt;]
: 设置数据库字符集。
\---
默认值：utf8
\---

[\--dbcollate=&lt;dbcollate&gt;]
: 设置数据库排序规则。
\---
默认值：
\---

[\--locale=&lt;locale&gt;]
: 设置 WPLANG 常量。默认为 $wp_local_package 变量。

[\--extra-php]
: 如果设置，该命令会将额外的 PHP 代码从 STDIN 复制到 wp-config.php 中。

[\--skip-salts]
: 如果设置，将不会生成密钥和盐，而应通过 `--extra-php` 传递。

[\--skip-check]
: 如果设置，将不会检查数据库连接。

[\--force]
: 如果存在，则覆盖现有文件。

[\--config-file=&lt;path&gt;]
: 指定要创建的配置文件的路径。默认为 WordPress 安装根目录下的 "wp-config.php" 文件。

[\--insecure]
: 如果 TLS 握手失败，则在不验证证书的情况下重试 API 下载。注意：这会使请求容易受到中间人攻击。

[\--ssl]
: 检查数据库连接时使用 SSL。

### 示例

    # 标准 wp-config.php 文件
    $ wp config create --dbname=testing --dbuser=wp --dbpass=securepswd --locale=ro_RO
    成功：已生成 'wp-config.php' 文件。

    # 启用 WP_DEBUG 和 WP_DEBUG_LOG
    $ wp config create --dbname=testing --dbuser=wp --dbpass=securepswd --extra-php <<PHP
    define( 'WP_DEBUG', true );
    define( 'WP_DEBUG_LOG', true );
    PHP
    成功：已生成 'wp-config.php' 文件。

    # 通过从 password.txt 读取，避免在 bash 历史记录中泄露密码
    # 使用 --prompt=dbpass 将提示输入 'dbpass' 参数
    $ wp config create --dbname=testing --dbuser=wp --prompt=dbpass < password.txt
    成功：已生成 'wp-config.php' 文件。

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