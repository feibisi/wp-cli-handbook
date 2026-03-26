---
title: "wp site list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Site
    - Commands
    - Repos
---

# wp site list

列出多站点安装中的所有站点。

### 选项

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考。

[\--network=&lt;id&gt;]
: 站点所属的网络。

[\--&lt;field&gt;=&lt;value&gt;]
: 按一个或多个字段筛选（参见“可用字段”部分）。但是，'url' 不是一个可用的筛选器，因为它来自 wp_options 中的 'home'。

[\--site__in=&lt;value&gt;]
: 仅列出具有这些 blog_id 值的站点（逗号分隔）。

[\--site_user=&lt;value&gt;]
: 仅列出具有此用户的站点。

[\--field=&lt;field&gt;]
: 为每个站点打印单个字段的值。

[\--fields=&lt;fields&gt;]
: 要显示的字段列表，以逗号分隔。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: table
选项:
  - table
  - csv
  - count
  - ids
  - json
  - yaml
\---

### 可用字段

以下字段将默认显示在每个站点中：

* blog_id
* url
* last_updated
* registered

以下字段为可选可用：

* site_id
* domain
* path
* public
* archived
* mature
* spam
* deleted
* lang_id

### EXAMPLES

    # Output a simple list of site URLs
    $ wp site list --field=url
    http://www.example.com/
    http://www.example.com/subdir/

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