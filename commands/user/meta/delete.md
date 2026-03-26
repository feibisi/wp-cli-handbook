---
title: "wp user meta delete"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Meta
    - User
    - Commands
---

# wp user meta delete

删除用户元数据字段。

### 参数选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考文档。

&lt;user&gt;
: 要删除元数据的用户登录名、用户邮箱或用户ID。

&lt;key&gt;
: 元数据键名。

[&lt;value&gt;]
: 要删除的值。如果省略，将删除该键名的所有数据行。

### 使用示例

    # 删除用户元数据
    $ wp user meta delete 123 bio
    成功：已删除自定义字段。

### 全局参数

这些[全局参数](https://make.wordpress.org/cli/handbook/config/)在所有命令中具有相同的行为，并影响WP-CLI与WordPress的交互方式。

| **参数**    | **说明**              |
|:----------------|:-----------------------------|
| `--path=<path>` | WordPress文件路径。 |
| `--url=<url>` | 模拟请求来自指定URL。在多站点中，此参数用于指定目标站点。 |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | 通过SSH对远程服务器执行操作（或使用"docker"、"docker-compose"、"docker-compose-run"、"vagrant"方案操作容器）。 |
| `--http=<http>` | 通过HTTP对远程WordPress安装执行操作。 |
| `--user=<id\|login\|email>` | 设置WordPress用户。 |
| `--skip-plugins[=<plugins>]` | 跳过加载所有插件，或逗号分隔的插件列表。注意：mu-plugins仍会被加载。 |
| `--skip-themes[=<themes>]` | 跳过加载所有主题，或逗号分隔的主题列表。 |
| `--skip-packages` | 跳过加载所有已安装的包。 |
| `--require=<path>` | 运行命令前加载PHP文件（可多次使用）。 |
| `--exec=<php-code>` | 运行命令前执行PHP代码（可多次使用）。 |
| `--context=<context>` | 在指定上下文中加载WordPress。 |
| `--[no-]color` | 是否彩色化输出。 |
| `--debug[=<group>]` | 显示所有PHP错误并增加WP-CLI输出的详细程度。内置组包括：bootstrap、commandfactory和help。 |
| `--prompt[=<assoc>]` | 提示用户输入所有命令参数的值，或逗号分隔的指定子集参数值。 |
| `--quiet` | 抑制信息性消息。 |