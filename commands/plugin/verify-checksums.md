---
title: "wp plugin verify-checksums"
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

# wp plugin verify-checksums

根据 WordPress.org 的校验和验证插件文件。

### 参数

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考。

[&lt;plugin&gt;...]
: 要验证的一个或多个插件。

[\--all]
: 如果设置，将验证所有插件。

[\--strict]
: 如果设置，即使是像 readme.txt 更改这样的"软更改"也会触发校验和错误。

[\--version=&lt;version&gt;]
: 针对特定插件版本验证校验和。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: table
选项:
  - table
  - json
  - csv
  - yaml
  - count
\---

[\--insecure]
: 如果 TLS 握手失败，则在不进行证书验证的情况下重试下载。注意：这会使请求容易受到 MITM 攻击。

[\--exclude=&lt;name&gt;]
: 应从验证中排除的插件名称的逗号分隔列表。

### 示例

    # 验证所有已安装插件的校验和
    $ wp plugin verify-checksums --all
    Success: Verified 8 of 8 plugins.

    # 验证单个插件的校验和，本例中为 Akismet
    $ wp plugin verify-checksums akismet
    Success: Verified 1 of 1 plugins.

### 全局参数

这些 [全局参数](https://make.wordpress.org/cli/handbook/config/) 在所有命令中具有相同的行为，并影响 WP-CLI 与 WordPress 的交互方式。

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