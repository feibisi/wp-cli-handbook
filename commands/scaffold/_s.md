---
title: "wp scaffold _s"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Scaffold
    - Commands
    - Repos
---

# wp scaffold _s

基于 _s 生成主题的起始代码。

这是 `wp scaffold underscores` 命令的别名。

更多详情请参阅 [Underscores 网站](https://underscores.me/)。

### 选项

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考。

&lt;slug&gt;
: 新主题的别名，用于函数前缀。

[\--activate]
: 激活新下载的主题。

[\--enable-network]
: 为整个网络启用新下载的主题。

[\--theme_name=&lt;title&gt;]
: 在 'style.css' 文件的 'Theme Name:' 头部信息中填写的内容。

[\--author=&lt;full-name&gt;]
: 在 'style.css' 文件的 'Author:' 头部信息中填写的内容。

[\--author_uri=&lt;uri&gt;]
: 在 'style.css' 文件的 'Author URI:' 头部信息中填写的内容。

[\--sassify]
: 将样式表包含为 SASS 格式。

[\--woocommerce]
: 包含 WooCommerce 样板文件。

[\--force]
: 覆盖已存在的文件。

### 示例

    # 生成一个名为 "Sample Theme"、作者为 "John Doe" 的主题
    $ wp scaffold _s sample-theme --theme_name="Sample Theme" --author="John Doe"
    Success: Created theme 'Sample Theme'.

### 全局参数

这些 [全局参数](https://make.wordpress.org/cli/handbook/config/) 在所有命令中行为一致，并影响 WP-CLI 与 WordPress 的交互方式。

| **参数**    | **描述**              |
|:----------------|:-----------------------------|
| `--path=<path>` | WordPress 文件的路径。 |
| `--url=<url>` | 假设请求来自给定的 URL。在多站点中，此参数用于指定目标站点。 |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | 通过 SSH（或使用 "docker"、"docker-compose"、"docker-compose-run"、"vagrant" 方案的容器）对远程服务器执行操作。 |
| `--http=<http>` | 通过 HTTP 对远程 WordPress 安装执行操作。 |
| `--user=<id\|login\|email>` | 设置 WordPress 用户。 |
| `--skip-plugins[=<plugins>]` | 跳过加载所有插件，或跳过加载以逗号分隔的插件列表。注意：mu-plugins 仍会被加载。 |
| `--skip-themes[=<themes>]` | 跳过加载所有主题，或跳过加载以逗号分隔的主题列表。 |
| `--skip-packages` | 跳过加载所有已安装的包。 |
| `--require=<path>` | 在运行命令前加载 PHP 文件（可多次使用）。 |
| `--exec=<php-code>` | 在运行命令前执行 PHP 代码（可多次使用）。 |
| `--context=<context>` | 在给定的上下文中加载 WordPress。 |
| `--[no-]color` | 是否对输出进行着色。 |
| `--debug[=<group>]` | 显示所有 PHP 错误并增加 WP-CLI 输出的详细程度。内置组包括：bootstrap、commandfactory 和 help。 |
| `--prompt[=<assoc>]` | 提示用户输入所有命令参数的值，或输入以逗号分隔的指定子集的值。 |
| `--quiet` | 抑制信息性消息。 |