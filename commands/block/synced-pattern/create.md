---
title: "wp block synced-pattern create"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Synced Pattern
    - Block
    - Commands
---

# wp block synced-pattern create

创建一个同步模式。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

[\--title=&lt;title&gt;]
: 模式标题。

[\--slug=&lt;slug&gt;]
: 模式别名。默认值：经过处理的标题。

[\--content=&lt;content&gt;]
: 区块内容。

[\--sync-status=&lt;status&gt;]
: 同步状态。
\---
默认值: synced
选项:
  - synced
  - unsynced
\---

[\--status=&lt;status&gt;]
: 文章状态。
\---
默认值: publish
\---

[&lt;file&gt;]
: 从文件读取内容。使用 '-' 表示 STDIN。

[\--porcelain]
: 仅输出新模式的 ID。

### 示例

    # 从内容创建同步模式
    $ wp block synced-pattern create --title="我的英雄" --content='&lt;!-- wp:paragraph --&gt;&lt;p&gt;你好&lt;/p&gt;&lt;!-- /wp:paragraph --&gt;'

    # 从文件创建
    $ wp block synced-pattern create --title="页眉" header.html

    # 创建非同步模式
    $ wp block synced-pattern create --title="页脚" --sync-status=unsynced footer.html

    # 从 STDIN 创建
    $ cat content.html | wp block synced-pattern create --title="来自 STDIN" -

### 全局参数

这些[全局参数](https://make.wordpress.org/cli/handbook/config/)在所有命令中具有相同的行为，并影响 WP-CLI 与 WordPress 的交互方式。

| **参数**    | **描述**              |
|:----------------|:-----------------------------|
| `--path=<path>` | WordPress 文件的路径。 |
| `--url=<url>` | 假设请求来自给定的 URL。在多站点中，此参数用于指定目标站点。 |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | 通过 SSH（或使用 "docker"、"docker-compose"、"docker-compose-run"、"vagrant" 方案的容器）对远程服务器执行操作。 |
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
| `--prompt[=<assoc>]` | 提示用户输入所有命令参数的值，或指定为逗号分隔值的子集。 |
| `--quiet` | 抑制信息性消息。 |