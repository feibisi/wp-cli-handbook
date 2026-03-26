---
title: "wp config shuffle-salts"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Config
    - Commands
    - Repos
---

# wp config shuffle-salts

刷新 wp-config.php 文件中定义的盐值。

此命令在 `before_wp_load` 钩子上运行，恰好在 WordPress 加载过程开始之前。

### 选项

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考。

[&lt;keys&gt;...]
: 一个或多个要刷新的盐值键。如果未提供，则回退到默认的 WordPress 核心盐值键。

[\--force]
: 如果请求刷新未知的盐值键，则添加它而不是抛出警告。

[\--config-file=&lt;path&gt;]
: 指定要修改的配置文件路径。默认为 WordPress 安装根目录下的 "wp-config.php" 文件。

[\--insecure]
: 如果 TLS 握手失败，则在不进行证书验证的情况下重试 API 下载。注意：这会使请求容易受到中间人攻击。

### 示例

    # 为你的 wp-config.php 文件获取新的盐值
    $ wp config shuffle-salts
    Success: 已刷新盐值键。

    # 向 wp-config.php 文件添加一个缓存键盐值
    $ wp config shuffle-salts WP_CACHE_KEY_SALT --force
    Success: 已刷新盐值键。

### 全局参数

这些 [全局参数](https://make.wordpress.org/cli/handbook/config/) 在所有命令中具有相同的行为，并影响 WP-CLI 与 WordPress 的交互方式。

| **参数**    | **描述**              |
|:----------------|:-----------------------------|
| `--path=<path>` | WordPress 文件的路径。 |
| `--url=<url>` | 假装请求来自给定的 URL。在多站点中，此参数用于指定目标站点。 |
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