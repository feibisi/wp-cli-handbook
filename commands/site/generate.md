---
title: "wp site generate"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Site
    - Commands
    - Repos
---

# wp site generate

生成一些站点。

创建指定数量的新站点。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

[\--count=&lt;number&gt;]
: 要生成多少个站点？
\---
默认值: 100
\---

[\--slug=&lt;slug&gt;]
: 新站点的路径。在子域名安装中是子域名，在子目录安装中是目录。

[\--email=&lt;email&gt;]
: 管理员用户的电子邮件。如果用户不存在，将会创建。如果未指定，将分配为超级管理员。

[\--network_id=&lt;network-id&gt;]
: 新站点要关联的网络。默认为当前网络（通常为 1）。

[\--private]
: 如果设置，新站点将是非公开的（不被索引）

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: progress
选项:
 - progress
 - ids
\---

### 示例

   # 生成 10 个站点。
   $ wp site generate --count=10
   正在生成站点  100% [================================================] 0:01 / 0:04

### 全局参数

这些[全局参数](https://make.wordpress.org/cli/handbook/config/)在所有命令中具有相同的行为，并影响 WP-CLI 与 WordPress 的交互方式。

| **参数**    | **描述**              |
|:----------------|:-----------------------------|
| `--path=<path>` | WordPress 文件的路径。 |
| `--url=<url>` | 假设请求来自给定的 URL。在多站点中，此参数用于指定目标站点。 |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | 通过 SSH（或使用 "docker"、"docker-compose"、"docker-compose-run"、"vagrant" 方案的容器）对远程服务器执行操作。 |
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