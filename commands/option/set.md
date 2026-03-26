---
title: "wp option set"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Option
    - Commands
    - Repos
---

# wp option set

更新选项值。

这是 `wp option update` 命令的别名。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;key&gt;
: 要更新的选项名称。

[&lt;value&gt;]
: 新值。如果省略，将从 STDIN 读取值。

[\--autoload=&lt;autoload&gt;]
: 需要 WordPress 4.2 或更高版本。指定此选项是否应自动加载。
\---
选项:
  - 'on'
  - 'off'
  - 'yes'
  - 'no'
\---

[\--format=&lt;format&gt;]
: 值的序列化格式。
\---
默认值: plaintext
选项:
  - plaintext
  - json
\---

### 示例

    # 从文件读取内容来更新选项。
    $ wp option update my_option < value.txt
    Success: Updated 'my_option' option.

    # 使用 xargs 在多个站点上更新一个选项。
    $ wp site list --field=url | xargs -n1 -I {} sh -c 'wp --url={} option update my_option my_value'
    Success: Updated 'my_option' option.
    Success: Updated 'my_option' option.

    # 更新站点博客名称。
    $ wp option update blogname "Random blog name"
    Success: Updated 'blogname' option.

    # 更新站点博客描述。
    $ wp option update blogdescription "Some random blog description"
    Success: Updated 'blogdescription' option.

    # 更新管理员电子邮件地址。
    $ wp option update admin_email someone@example.com
    Success: Updated 'admin_email' option.

    # 设置默认角色。
    $ wp option update default_role author
    Success: Updated 'default_role' option.

    # 设置时区字符串。
    $ wp option update timezone_string "America/New_York"
    Success: Updated 'timezone_string' option.

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