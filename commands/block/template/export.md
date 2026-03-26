---
title: "wp block template export"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Template
    - Block
    - Commands
---

# wp block template export

将区块模板导出到文件。

### 参数

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;id&gt;
: 要导出的模板 ID。

[\--type=&lt;type&gt;]
: 模板类型。
\---
默认值: wp_template
选项:
  - wp_template
  - wp_template_part
\---

[\--file=&lt;file&gt;]
: 导出到的文件路径。如果需要，将创建父目录。

[\--dir=&lt;directory&gt;]
: 导出到的目录。默认为当前目录。如果需要，将创建目录。

[\--stdout]
: 输出到 stdout 而不是文件。

### 示例

    # 将模板导出到文件
    $ wp block template export twentytwentyfour//single

    # 导出到 stdout
    $ wp block template export twentytwentyfour//single --stdout

    # 导出到特定目录
    $ wp block template export twentytwentyfour//single --dir=./templates/

    # 导出到特定文件路径
    $ wp block template export twentytwentyfour//single --file=exports/templates/single.html

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