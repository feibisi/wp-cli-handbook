---
title: "wp scaffold post-type"
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

# wp scaffold post-type

生成用于注册自定义文章类型的 PHP 代码。

**别名：** `cpt`

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;slug&gt;
: 文章类型内部名称。

[\--label=&lt;label&gt;]
: 用于翻译更新消息的文本。

[\--textdomain=&lt;textdomain&gt;]
: 用于标签的文本域。

[\--dashicon=&lt;dashicon&gt;]
: 菜单中使用的 Dashicon 图标。

[\--theme]
: 在活动主题目录中创建文件，而不是输出到 STDOUT。使用 `--theme=<theme>` 指定主题，将文件放置在该主题中。

[\--plugin=&lt;plugin&gt;]
: 在给定插件的目录中创建文件，而不是输出到 STDOUT。

[\--raw]
: 仅生成 `register_post_type()` 调用，不包含其他内容。

[\--force]
: 覆盖已存在的文件。

### 示例

    # 为 'simple-life' 主题生成 'movie' 文章类型
    $ wp scaffold post-type movie --label=Movie --theme=simple-life
    成功：已创建 '/var/www/example.com/public_html/wp-content/themes/simple-life/post-types/movie.php'。

### 全局参数

这些[全局参数](https://make.wordpress.org/cli/handbook/config/)在所有命令中行为一致，并影响 WP-CLI 与 WordPress 的交互方式。

| **参数**    | **描述**              |
|:----------------|:-----------------------------|
| `--path=<path>` | WordPress 文件的路径。 |
| `--url=<url>` | 假定请求来自给定 URL。在多站点中，此参数用于指定目标站点。 |
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
| `--prompt[=<assoc>]` | 提示用户输入所有命令参数的值，或指定为逗号分隔值的子集。 |
| `--quiet` | 抑制信息性消息。 |