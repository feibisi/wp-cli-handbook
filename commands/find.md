---
title: "wp find"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Commands
    - Repos
    - Data
---

# wp find

在文件系统中查找 WordPress 安装。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

递归遍历提供的 &lt;path&gt; 子目录以查找并报告 WordPress 安装。WordPress 安装是指包含 version.php 文件的 wp-includes 目录。

避免递归某些已知路径（例如 /node_modules/、隐藏系统目录）以显著提升性能。

显示找到 WordPress 安装的深度及其别名（如果存在）。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，以详细了解所使用的语法约定。

&lt;path&gt;
: 要搜索其子目录的路径。

[\--skip-ignored-paths]
: 跳过默认情况下被忽略的路径。

[\--include_ignored_paths=&lt;paths&gt;]
: 以 CSV 格式包含额外的被忽略路径（例如 '/sys-backup/,/temp/'）。

[\--max_depth=&lt;max-depth&gt;]
: 仅递归到指定的深度（包含该深度）。

[\--fields=&lt;fields&gt;]
: 将输出限制为特定的行字段。

[\--field=&lt;field&gt;]
: 为每一行输出一个特定的字段。

[\--format=&lt;format&gt;]
: 以特定格式呈现输出。
\---
默认值: table
选项:
  - table
  - json
  - csv
  - yaml
  - count
\---

[\--verbose]
: 将有用的信息记录到 STDOUT。

### 可用字段

以下字段将在每次安装时默认显示：

* version_path - version.php 文件的路径。
* version - WordPress 版本。
* depth - 发现安装的目录深度。
* alias - WP-CLI 别名（如果已注册）。

以下字段为可选可用：

* wp_path - 可传递给 `--path=<path>` 全局参数的路径。
* db_host - 数据库的主机名。
* db_user - 数据库的用户名。
* db_name - 数据库的名称。

### 示例

    # 查找 WordPress 安装。
    $ wp find ./
    +--------------------------------------+---------------------+-------+--------+
    | version_path                         | version             | depth | alias  |
    +--------------------------------------+---------------------+-------+--------+
    | /Users/wpcli/wp-includes/version.php | 4.8-alpha-39357-src | 2     | @wpcli |
    +--------------------------------------+---------------------+-------+--------+

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