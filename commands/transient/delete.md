---
title: "wp transient delete"
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

# wp transient delete

删除瞬态值。

关于瞬态缓存（包括网络|站点缓存）的更完整说明，请参阅 `wp transient` 的文档。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

[&lt;key&gt;]
: 瞬态的键名。

[\--network]
: 删除网络|站点瞬态的值。在单站点上，这是一个特殊命名的缓存键。在多站点上，这是一个全局缓存（而不是站点本地的）。

[\--all]
: 删除所有瞬态。

[\--expired]
: 删除所有已过期的瞬态。

### 示例

    # 删除瞬态数据。
    $ wp transient delete sample_key
    成功：瞬态数据已删除。

    # 删除已过期的瞬态数据。
    $ wp transient delete --expired
    成功：已从数据库中删除 12 个过期的瞬态数据。

    # 删除已过期的站点瞬态数据。
    $ wp transient delete --expired --network
    成功：已从数据库中删除 1 个过期的瞬态数据。

    # 删除所有瞬态数据。
    $ wp transient delete --all
    成功：已从数据库中删除 14 个瞬态数据。

    # 删除所有站点瞬态数据。
    $ wp transient delete --all --network
    成功：已从数据库中删除 2 个瞬态数据。

    # 在多站点网络中删除所有瞬态数据。
    $ wp transient delete --all --network && wp site list --field=url | xargs -n1 -I % wp --url=% transient delete --all

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