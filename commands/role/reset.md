---
title: "wp role reset"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Role
    - Commands
    - Repos
---

# wp role reset

将任何默认角色重置为默认权限。

使用 WordPress 的 `populate_roles()` 函数将一个或多个角色恢复到全新 WordPress 安装时的状态。移除所有已添加的权限，并恢复所有已移除的权限。自定义角色不受影响。

### 参数

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

[&lt;role-key&gt;...]
: 要重置的一个或多个角色的内部名称。

[\--all]
: 如果设置，将重置所有默认角色。

### 示例

    # 重置三个角色。
    $ wp role reset administrator author contributor
    已为 'administrator' 角色恢复 1 个权限并移除 0 个权限。
    'author' 角色无需更改。
    'contributor' 角色无需更改。
    成功：3 个角色中的 1 个已重置。

    # 重置自定义角色。
    $ wp role reset custom_role
    自定义角色 'custom_role' 不受影响。
    错误：必须指定要重置的默认角色。

    # 重置所有默认角色。
    $ wp role reset --all
    成功：所有默认角色已重置。

### 全局参数

这些[全局参数](https://make.wordpress.org/cli/handbook/config/)在所有命令中具有相同的行为，并影响 WP-CLI 与 WordPress 的交互方式。

| **参数**    | **描述**              |
|:----------------|:-----------------------------|
| `--path=<path>` | WordPress 文件的路径。 |
| `--url=<url>` | 模拟请求来自给定 URL。在多站点中，此参数用于指定目标站点。 |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | 通过 SSH 对远程服务器执行操作（或使用 "docker"、"docker-compose"、"docker-compose-run"、"vagrant" 方案对容器执行操作）。 |
| `--http=<http>` | 通过 HTTP 对远程 WordPress 安装执行操作。 |
| `--user=<id\|login\|email>` | 设置 WordPress 用户。 |
| `--skip-plugins[=<plugins>]` | 跳过加载所有插件，或逗号分隔的插件列表。注意：mu-plugins 仍会加载。 |
| `--skip-themes[=<themes>]` | 跳过加载所有主题，或逗号分隔的主题列表。 |
| `--skip-packages` | 跳过加载所有已安装的包。 |
| `--require=<path>` | 运行命令前加载 PHP 文件（可多次使用）。 |
| `--exec=<php-code>` | 运行命令前执行 PHP 代码（可多次使用）。 |
| `--context=<context>` | 在给定上下文中加载 WordPress。 |
| `--[no-]color` | 是否对输出进行着色。 |
| `--debug[=<group>]` | 显示所有 PHP 错误并增加 WP-CLI 输出的详细程度。内置组包括：bootstrap、commandfactory 和 help。 |
| `--prompt[=<assoc>]` | 提示用户输入所有命令参数的值，或指定为逗号分隔值的子集。 |
| `--quiet` | 抑制信息性消息。 |