---
title: "wp site option list"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Option
    - Site
    - Commands
---

# wp site option list

列出站点选项。

### 参数

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考。

[\--search=&lt;pattern&gt;]
: 使用通配符（ * 和 ? ）来匹配选项名称。

[\--site_id=&lt;id&gt;]
: 将选项限制为特定站点 ID 的选项。

[\--field=&lt;field&gt;]
: 打印单个字段的值。

[\--fields=&lt;fields&gt;]
: 将输出限制为特定的对象字段。

[\--format=&lt;format&gt;]
: 值的序列化格式。total_bytes 显示匹配选项的总大小（字节）。
\---
默认值: table
选项:
  - table
  - json
  - csv
  - count
  - yaml
  - total_bytes
\---

### 可用字段

默认情况下，每个匹配的选项将显示此字段：

* meta_key
* meta_value

这些字段是可选的：

* meta_id
* site_id
* size_bytes

### 示例

    # 列出所有以 "i2f_" 开头的站点选项
    $ wp site option list --search="i2f_*"
    +-------------+--------------+
    | meta_key    | meta_value   |
    +-------------+--------------+
    | i2f_version | 0.1.0        |
    +-------------+--------------+

### 全局参数

这些 [全局参数](https://make.wordpress.org/cli/handbook/config/) 在所有命令中具有相同的行为，并影响 WP-CLI 与 WordPress 的交互方式。

| **参数**    | **描述**              |
|:----------------|:-----------------------------|
| `--path=<path>` | WordPress 文件的路径。 |
| `--url=<url>` | 假设请求来自给定的 URL。在多站点中，此参数用于指定目标站点。 |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | 通过 SSH 对远程服务器（或使用 "docker"、"docker-compose"、"docker-compose-run"、"vagrant" 方案的容器）执行操作。 |
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
| `--prompt[=<assoc>]` | 提示用户输入所有命令参数的值，或输入以逗号分隔的指定子集值。 |
| `--quiet` | 抑制信息性消息。 |