---
title: "wp comment update"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Comment
    - Commands
    - Repos
---

# wp comment update

更新一条或多条评论。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;id&gt;...
: 要更新的一个或多个评论 ID。

\--&lt;field&gt;=&lt;value&gt;
: 要更新的一个或多个字段。参见 wp_update_comment()。

### 示例

    # 更新评论。
    $ wp comment update 123 --comment_author='That Guy'
    Success: Updated comment 123.

### 全局参数

这些[全局参数](https://make.wordpress.org/cli/handbook/config/)在所有命令中行为一致，并影响 WP-CLI 与 WordPress 的交互方式。

| **参数**    | **描述**              |
|:----------------|:-----------------------------|
| `--path=<path>` | WordPress 文件的路径。 |
| `--url=<url>` | 假定请求来自指定 URL。在多站点中，此参数用于指定目标站点。 |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | 通过 SSH 对远程服务器执行操作（或使用 "docker"、"docker-compose"、"docker-compose-run"、"vagrant" 方案对容器执行操作）。 |
| `--http=<http>` | 通过 HTTP 对远程 WordPress 安装执行操作。 |
| `--user=<id\|login\|email>` | 设置 WordPress 用户。 |
| `--skip-plugins[=<plugins>]` | 跳过加载所有插件，或跳过加载以逗号分隔的插件列表。注意：mu-plugins 仍会被加载。 |
| `--skip-themes[=<themes>]` | 跳过加载所有主题，或跳过加载以逗号分隔的主题列表。 |
| `--skip-packages` | 跳过加载所有已安装的包。 |
| `--require=<path>` | 运行命令前加载指定的 PHP 文件（可多次使用）。 |
| `--exec=<php-code>` | 运行命令前执行指定的 PHP 代码（可多次使用）。 |
| `--context=<context>` | 在指定上下文中加载 WordPress。 |
| `--[no-]color` | 是否对输出进行着色。 |
| `--debug[=<group>]` | 显示所有 PHP 错误并增加 WP-CLI 输出的详细程度。内置组包括：bootstrap、commandfactory 和 help。 |
| `--prompt[=<assoc>]` | 提示用户输入所有命令参数的值，或输入以逗号分隔的指定子集参数值。 |
| `--quiet` | 抑制信息性消息的输出。 |