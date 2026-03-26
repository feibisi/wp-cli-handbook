---
title: "wp user session destroy"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Session
    - User
    - Commands
---

# wp user session destroy

销毁指定用户的会话。

### OPTIONS

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;user&gt;
: 用户 ID、用户邮箱或用户登录名。

[&lt;token&gt;]
: 要销毁的会话令牌。默认为最近创建的会话。

[\--all]
: 销毁该用户的所有会话。

### EXAMPLES

    # 销毁指定用户最近的会话。
    $ wp user session destroy admin
    Success: 已销毁会话。剩余 3 个会话。

    # 销毁指定用户的特定会话。
    $ wp user session destroy admin e073ad8540a9c2...
    Success: 已销毁会话。剩余 2 个会话。

    # 销毁指定用户的所有会话。
    $ wp user session destroy admin --all
    Success: 已销毁所有会话。

    # 销毁所有用户的所有会话。
    $ wp user list --field=ID | xargs -n 1 wp user session destroy --all
    Success: 已销毁所有会话。
    Success: 已销毁所有会话。

### GLOBAL PARAMETERS

这些[全局参数](https://make.wordpress.org/cli/handbook/config/)在所有命令中具有相同的行为，并影响 WP-CLI 与 WordPress 的交互方式。

| **参数**    | **描述**              |
|:----------------|:-----------------------------|
| `--path=<path>` | WordPress 文件的路径。 |
| `--url=<url>` | 模拟请求来自指定 URL。在多站点中，此参数用于指定目标站点。 |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | 通过 SSH（或使用 "docker"、"docker-compose"、"docker-compose-run"、"vagrant" 方案的容器）对远程服务器执行操作。 |
| `--http=<http>` | 通过 HTTP 对远程 WordPress 安装执行操作。 |
| `--user=<id\|login\|email>` | 设置 WordPress 用户。 |
| `--skip-plugins[=<plugins>]` | 跳过加载所有插件，或跳过以逗号分隔的插件列表。注意：mu-plugins 仍会被加载。 |
| `--skip-themes[=<themes>]` | 跳过加载所有主题，或跳过以逗号分隔的主题列表。 |
| `--skip-packages` | 跳过加载所有已安装的包。 |
| `--require=<path>` | 运行命令前加载 PHP 文件（可多次使用）。 |
| `--exec=<php-code>` | 运行命令前执行 PHP 代码（可多次使用）。 |
| `--context=<context>` | 在指定上下文中加载 WordPress。 |
| `--[no-]color` | 是否对输出进行着色。 |
| `--debug[=<group>]` | 显示所有 PHP 错误并增加 WP-CLI 输出的详细程度。内置组包括：bootstrap、commandfactory 和 help。 |
| `--prompt[=<assoc>]` | 提示用户输入所有命令参数的值，或输入以逗号分隔的指定子集的值。 |
| `--quiet` | 抑制信息性消息。 |