---
title: "wp config has"
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

# wp config has

检查 wp-config.php 文件中是否存在特定的常量或变量。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

### 参数

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考。

&lt;name&gt;
: wp-config.php 常量或变量的名称。

[\--type=&lt;type&gt;]
: 要设置的配置值类型。默认为 'all'。
\---
default: all
options:
  - constant
  - variable
  - all
\---

[\--config-file=&lt;path&gt;]
: 指定要检查的配置文件的路径。默认为 WordPress 安装根目录下的 "wp-config.php" 文件。

### 示例

    # 检查 wp-config.php 文件中是否存在 DB_PASSWORD 常量。
    $ wp config has DB_PASSWORD

### 全局参数

这些 [全局参数](https://make.wordpress.org/cli/handbook/config/) 在所有命令中具有相同的行为，并影响 WP-CLI 与 WordPress 的交互方式。

| **参数**    | **描述**              |
|:----------------|:-----------------------------|
| `--path=<path>` | WordPress 文件的路径。 |
| `--url=<url>` | 假设请求来自给定的 URL。在多站点中，此参数用于指定目标站点。 |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | 通过 SSH 对远程服务器执行操作（或使用 "docker"、"docker-compose"、"docker-compose-run"、"vagrant" 方案对容器执行操作）。 |
| `--http=<http>` | 通过 HTTP 对远程 WordPress 安装执行操作。 |
| `--user=<id\|login\|email>` | 设置 WordPress 用户。 |
| `--skip-plugins[=<plugins>]` | 跳过加载所有插件，或跳过加载以逗号分隔的插件列表。注意：mu-plugins 仍会被加载。 |
| `--skip-themes[=<themes>]` | 跳过加载所有主题，或跳过加载以逗号分隔的主题列表。 |
| `--skip-packages` | 跳过加载所有已安装的包。 |
| `--require=<path>` | 在运行命令之前加载 PHP 文件（可多次使用）。 |
| `--exec=<php-code>` | 在运行命令之前执行 PHP 代码（可多次使用）。 |
| `--context=<context>` | 在给定的上下文中加载 WordPress。 |
| `--[no-]color` | 是否对输出进行着色。 |
| `--debug[=<group>]` | 显示所有 PHP 错误并增加 WP-CLI 输出的详细程度。内置组包括：bootstrap、commandfactory 和 help。 |
| `--prompt[=<assoc>]` | 提示用户输入所有命令参数的值，或输入以逗号分隔的指定子集的值。 |
| `--quiet` | 抑制信息性消息。 |