---
title: "wp plugin uninstall"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Plugin
    - Commands
    - Repos
---

# wp plugin uninstall

卸载一个或多个插件。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考文档。

[&lt;plugin&gt;...]
: 要卸载的一个或多个插件。

[\--deactivate]
: 卸载前先停用插件。默认行为是当插件处于活动状态时发出警告并跳过。

[\--skip-delete]
: 如果设置，将不会删除插件文件。仅运行卸载程序。

[\--all]
: 如果设置，将卸载所有插件。

[\--exclude=&lt;name&gt;]
: 逗号分隔的插件别名列表，这些插件将从卸载中排除。

### 示例

    $ wp plugin uninstall hello
    已卸载并删除 'hello' 插件。
    成功：已卸载 1 个插件中的 1 个。

    # 卸载除指定插件外的所有插件
    $ wp plugin uninstall --all --exclude=hello-dolly,jetpack
    已卸载并删除 'akismet' 插件。
    已卸载并删除 'tinymce-templates' 插件。
    成功：已卸载 2 个插件中的 2 个。

### 全局参数

这些[全局参数](https://make.wordpress.org/cli/handbook/config/)在所有命令中具有相同的行为，并影响 WP-CLI 与 WordPress 的交互方式。

| **参数**    | **描述**              |
|:----------------|:-----------------------------|
| `--path=<path>` | WordPress 文件的路径。 |
| `--url=<url>` | 假装请求来自给定的 URL。在多站点中，此参数用于指定目标站点。 |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | 通过 SSH 对远程服务器执行操作（或使用 "docker"、"docker-compose"、"docker-compose-run"、"vagrant" 方案对容器执行操作）。 |
| `--http=<http>` | 通过 HTTP 对远程 WordPress 安装执行操作。 |
| `--user=<id\|login\|email>` | 设置 WordPress 用户。 |
| `--skip-plugins[=<plugins>]` | 跳过加载所有插件，或逗号分隔的插件列表。注意：mu-plugins 仍会被加载。 |
| `--skip-themes[=<themes>]` | 跳过加载所有主题，或逗号分隔的主题列表。 |
| `--skip-packages` | 跳过加载所有已安装的包。 |
| `--require=<path>` | 运行命令前加载 PHP 文件（可多次使用）。 |
| `--exec=<php-code>` | 运行命令前执行 PHP 代码（可多次使用）。 |
| `--context=<context>` | 在给定上下文中加载 WordPress。 |
| `--[no-]color` | 是否对输出进行着色。 |
| `--debug[=<group>]` | 显示所有 PHP 错误并增加 WP-CLI 输出的详细程度。内置组包括：bootstrap、commandfactory 和 help。 |
| `--prompt[=<assoc>]` | 提示用户输入所有命令参数的值，或输入以逗号分隔的指定子集的值。 |
| `--quiet` | 抑制信息性消息。 |