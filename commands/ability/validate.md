---
title: "wp ability validate"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Ability
    - Commands
    - Repos
---

# wp ability validate

根据能力的模式验证输入。

在不执行能力的情况下验证输入数据。适用于在执行前测试输入。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;name&gt;
: 能力名称（命名空间/能力名称格式）。

[\--input=&lt;json&gt;]
: 包含要验证的输入数据的 JSON 字符串。

[\--&lt;field&gt;=&lt;value&gt;]
: 要验证的单个输入字段。

### 示例

    # 验证能力的输入（对数组值使用 JSON）。
    $ wp ability validate core/get-site-info --input='{"fields":["name","version"]}'
    成功：输入有效。

    # 验证简单的字符串参数。
    $ wp ability validate my-plugin/greet --name=World
    成功：输入有效。

    # 验证失败会显示错误信息。
    $ wp ability validate core/get-site-info --input='{"fields":"invalid"}'
    错误：能力 "core/get-site-info" 的输入无效。原因：...

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