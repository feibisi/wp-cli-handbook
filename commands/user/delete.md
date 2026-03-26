---
title: "wp user delete"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - User
    - Commands
    - Repos
---

# wp user delete

从当前站点删除一个或多个用户。

在多站点环境下，`wp user delete` 仅将用户从当前站点移除。包含 `--network` 参数以同时从数据库中删除该用户，但请确保在删除用户前重新分配其文章。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，详细了解所使用的语法约定。

&lt;user&gt;...
: 要删除用户的登录名、邮箱或用户 ID。

[\--network]
: 在多站点网络中，从整个网络删除该用户。

[\--reassign=&lt;user-id&gt;]
: 将文章重新分配给此用户 ID。

[\--yes]
: 对所有确认提示回答“是”。

### EXAMPLES

    # Delete user 123 and reassign posts to user 567
    $ wp user delete 123 --reassign=567
    Success: Removed user 123 from http://example.com.

    # Delete all contributors and reassign their posts to user 2
    $ wp user delete $(wp user list --role=contributor --field=ID) --reassign=2
    Success: Removed user 813 from http://example.com.
    Success: Removed user 578 from http://example.com.

    # Delete all contributors in batches of 100 (avoid error: argument list too long: wp)
    $ wp user delete $(wp user list --role=contributor --field=ID | head -n 100)

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