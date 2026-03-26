---
title: "wp media fix-orientation"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Media
    - Commands
    - Repos
---

# wp media fix-orientation

修复一个或多个附件的图像方向。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

[&lt;attachment-id&gt;...]
: 要重新生成的一个或多个附件 ID。

[\--dry-run]
: 检查需要调整方向的图像但不执行操作。

### 示例

    # 修复所有图像的方向。
    $ wp media fix-orientation
    1/3 正在修复 "Landscape_4" (ID 62) 的方向。
    2/3 正在修复 "Landscape_3" (ID 61) 的方向。
    3/3 正在修复 "Landscape_2" (ID 60) 的方向。
    成功：已修复 3 张图像中的 3 张。

    # 修复方向试运行。
    $ wp media fix-orientation 63 --dry-run
    1/1 "Portrait_6" (ID 63) 将受到影响。
    成功：1 张图像中的 1 张将受到影响。

    # 修复特定图像的方向。
    $ wp media fix-orientation 63
    1/1 正在修复 "Portrait_6" (ID 63) 的方向。
    成功：已修复 1 张图像中的 1 张。

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