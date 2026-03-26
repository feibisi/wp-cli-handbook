---
title: "wp menu item add-term"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Item
    - Menu
    - Commands
---

# wp menu item add-term

将分类法术语添加为菜单项。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;menu&gt;
: 菜单的名称、别名或术语ID。

&lt;taxonomy&gt;
: 要添加术语的分类法。

&lt;term-id&gt;
: 要添加术语的术语ID。

[\--title=&lt;title&gt;]
: 为菜单项设置自定义标题。

[\--link=&lt;link&gt;]
: 为菜单项设置自定义URL。

[\--description=&lt;description&gt;]
: 为菜单项设置自定义描述。

[\--attr-title=&lt;attr-title&gt;]
: 为菜单项设置自定义标题属性。

[\--target=&lt;target&gt;]
: 为菜单项设置自定义链接目标。

[\--classes=&lt;classes&gt;]
: 为菜单项设置自定义链接类。

[\--position=&lt;position&gt;]
: 指定此菜单项的位置。

[\--parent-id=&lt;parent-id&gt;]
: 将此菜单项设为另一个菜单项的子项。

[\--porcelain]
: 仅输出新菜单项的ID。

### 示例

    $ wp menu item add-term sidebar-menu post_tag 24
    成功：菜单项已添加。

### 全局参数

这些[全局参数](https://make.wordpress.org/cli/handbook/config/)在所有命令中具有相同的行为，并影响WP-CLI与WordPress的交互方式。

| **参数**    | **描述**              |
|:----------------|:-----------------------------|
| `--path=<path>` | WordPress文件的路径。 |
| `--url=<url>` | 假设请求来自给定的URL。在多站点中，此参数用于指定目标站点。 |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | 通过SSH（或使用"docker"、"docker-compose"、"docker-compose-run"、"vagrant"方案的容器）对远程服务器执行操作。 |
| `--http=<http>` | 通过HTTP对远程WordPress安装执行操作。 |
| `--user=<id\|login\|email>` | 设置WordPress用户。 |
| `--skip-plugins[=<plugins>]` | 跳过加载所有插件，或逗号分隔的插件列表。注意：mu-plugins仍会被加载。 |
| `--skip-themes[=<themes>]` | 跳过加载所有主题，或逗号分隔的主题列表。 |
| `--skip-packages` | 跳过加载所有已安装的包。 |
| `--require=<path>` | 运行命令前加载PHP文件（可多次使用）。 |
| `--exec=<php-code>` | 运行命令前执行PHP代码（可多次使用）。 |
| `--context=<context>` | 在给定上下文中加载WordPress。 |
| `--[no-]color` | 是否对输出进行着色。 |
| `--debug[=<group>]` | 显示所有PHP错误并增加WP-CLI输出的详细程度。内置组包括：bootstrap、commandfactory和help。 |
| `--prompt[=<assoc>]` | 提示用户输入所有命令参数的值，或指定为逗号分隔值的子集。 |
| `--quiet` | 抑制信息性消息。 |