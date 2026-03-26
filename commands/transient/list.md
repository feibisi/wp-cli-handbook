---
title: "wp transient list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Transient
    - Commands
    - Repos
---

# wp transient list

列出瞬态数据及其值。

### 选项

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考文档。

[\--search=&lt;pattern&gt;]
: 使用通配符（ * 和 ? ）来匹配瞬态数据名称。

[\--exclude=&lt;pattern&gt;]
: 要排除的模式。使用通配符（ * 和 ? ）来匹配瞬态数据名称。

[\--network]
: 获取网络|站点瞬态数据的值。在单站点上，这是一个特殊命名的缓存键。在多站点上，这是一个全局缓存（而不是站点本地的）。

[\--unserialize]
: 在输出中反序列化瞬态数据值。

[\--human-readable]
: 以人类可读的格式输出过期时间。

[\--fields=&lt;fields&gt;]
: 将输出限制为特定的对象字段。

[\--format=&lt;format&gt;]
: 值的序列化格式。
\---
默认值: table
选项:
  - table
  - json
  - csv
  - count
  - yaml
\---

### 可用字段

默认情况下，每个匹配选项将显示以下字段：

* name
* value
* expiration

### 示例

    # 列出所有瞬态数据
    $ wp transient list
     +------+-------+---------------+
     | name | value | expiration    |
     +------+-------+---------------+
     | foo  | bar   | 39 分钟后     |
     | foo2 | bar2  | 永不过期       |
     | foo3 | bar2  | 已过期         |
     | foo4 | bar4  | 4 小时后      |
     +------+-------+---------------+

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