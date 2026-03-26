---
title: "wp scaffold child-theme"
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

# wp scaffold child-theme

基于现有主题生成子主题。

创建包含 `functions.php` 和 `style.css` 文件的子主题文件夹。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;slug&gt;
: 新子主题的别名。

\--parent_theme=&lt;slug&gt;
: 在 'style.css' 的 'Template:' 头部信息中填写的内容。

[\--theme_name=&lt;title&gt;]
: 在 'style.css' 的 'Theme Name:' 头部信息中填写的内容。

[\--author=&lt;full-name&gt;]
: 在 'style.css' 的 'Author:' 头部信息中填写的内容。

[\--author_uri=&lt;uri&gt;]
: 在 'style.css' 的 'Author URI:' 头部信息中填写的内容。

[\--theme_uri=&lt;uri&gt;]
: 在 'style.css' 的 'Theme URI:' 头部信息中填写的内容。

[\--activate]
: 激活新创建的子主题。

[\--enable-network]
: 为整个网络启用新创建的子主题。

[\--force]
: 覆盖已存在的文件。

### 示例

    # 基于 TwentySixteen 生成一个名为 'sample-theme' 的子主题
    $ wp scaffold child-theme sample-theme --parent_theme=twentysixteen
    成功：已创建 '/var/www/example.com/public_html/wp-content/themes/sample-theme'。

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