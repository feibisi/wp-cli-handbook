---
title: "wp ability run"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Ability
    - Commands
    - Repos
---

# wp ability run

执行已注册的能力。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;name&gt;
: 能力名称（格式为 namespace/ability-name）。

[\--input=&lt;json&gt;]
: 包含能力输入数据的 JSON 字符串。使用 '-' 从标准输入读取。

[\--&lt;field&gt;=&lt;value&gt;]
: 单独的输入字段。对于简单输入，可作为 --input 的替代方案。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: json
选项:
  - json
  - yaml
  - var_export
\---

### 示例

    # 执行一个能力。
    $ wp ability run core/get-site-info --user=admin
    {
        "name": "Test Blog",
        "description": "Just another WordPress site",
        "url": "http://example.com",
        ...
    }

    # 使用 JSON 输入执行一个能力（数组值必需）。
    $ wp ability run core/get-site-info --input='{"fields":["name","version"]}' --user=admin
    {
        "name": "Test Blog",
        "version": "6.9"
    }

    # 使用简单字符串参数执行一个能力。
    $ wp ability run my-plugin/greet --name=World

    # 执行并以 YAML 格式输出。
    $ wp ability run core/get-site-info --format=yaml --user=admin
    name: Test Blog
    description: Just another WordPress site
    ...

    # 使用标准输入（stdin）的输入执行。
    $ echo '{"fields":["name"]}' | wp ability run core/get-site-info --input=- --user=admin

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