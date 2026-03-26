---
title: "wp cache patch"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Cache
    - Commands
    - Repos
---

# wp cache patch

更新缓存中的嵌套值。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;action&gt;
: 要执行的修补操作。
\---
选项:
  - insert
  - update
  - delete
\---

&lt;key&gt;
: 缓存键。

&lt;key-path&gt;...
: 用于定位待修补值的键名（一个或多个）。

[&lt;value&gt;]
: 新值。如果省略，则从 STDIN 读取。

[\--group=&lt;group&gt;]
: 缓存内数据分组的方法，允许在不同组中使用相同的键。
\---
默认值: default
\---

[\--expiration=&lt;expiration&gt;]
: 定义值保留时长（秒）。`0` 表示尽可能长。
\---
默认值: 0
\---

[\--format=&lt;format&gt;]
: 值的序列化格式。
\---
默认值: plaintext
选项:
  - plaintext
  - json
\---

### 全局参数

这些[全局参数](https://make.wordpress.org/cli/handbook/config/)在所有命令中行为一致，并影响 WP-CLI 与 WordPress 的交互方式。

| **参数**    | **描述**              |
|:----------------|:-----------------------------|
| `--path=<path>` | WordPress 文件的路径。 |
| `--url=<url>` | 伪装请求来自给定 URL。在多站点中，此参数用于指定目标站点。 |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | 通过 SSH 对远程服务器执行操作（或使用 "docker"、"docker-compose"、"docker-compose-run"、"vagrant" 方案对容器执行操作）。 |
| `--http=<http>` | 通过 HTTP 对远程 WordPress 安装执行操作。 |
| `--user=<id\|login\|email>` | 设置 WordPress 用户。 |
| `--skip-plugins[=<plugins>]` | 跳过加载所有插件，或逗号分隔的插件列表。注意：mu-plugins 仍会加载。 |
| `--skip-themes[=<themes>]` | 跳过加载所有主题，或逗号分隔的主题列表。 |
| `--skip-packages` | 跳过加载所有已安装的包。 |
| `--require=<path>` | 运行命令前加载 PHP 文件（可多次使用）。 |
| `--exec=<php-code>` | 运行命令前执行 PHP 代码（可多次使用）。 |
| `--context=<context>` | 在给定上下文中加载 WordPress。 |
| `--[no-]color` | 是否对输出着色。 |
| `--debug[=<group>]` | 显示所有 PHP 错误并增加 WP-CLI 输出的详细程度。内置组包括：bootstrap、commandfactory 和 help。 |
| `--prompt[=<assoc>]` | 提示用户输入所有命令参数的值，或指定为逗号分隔值的子集。 |
| `--quiet` | 抑制信息性消息。 |