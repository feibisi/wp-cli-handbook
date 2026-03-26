---
title: "wp cli param-dump"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Cli
    - Commands
    - Repos
---

# wp cli param-dump

以 JSON 或 var_export 格式导出全局参数列表。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

### 选项

有关所用语法约定的详细说明，请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考。

[\--with-values]
: 同时显示当前值。

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: json
选项:
  - var_export
  - json
\---

### 示例

    # 导出全局参数列表。
    $ wp cli param-dump --format=var_export
    array (
      'path' =>
      array (
        'runtime' => '=&lt;path&gt;',
        'file' => '&lt;path&gt;',
        'synopsis' => '',
        'default' => NULL,
        'multiple' => false,
        'desc' => 'Path to the WordPress files.',
      ),
      'url' =>
      array (

### 全局参数

这些 [全局参数](https://make.wordpress.org/cli/handbook/config/) 在所有命令中具有相同的行为，并影响 WP-CLI 与 WordPress 的交互方式。

| **参数**    | **描述**              |
|:----------------|:-----------------------------|
| `--path=<path>` | 指向 WordPress 文件的路径。 |
| `--url=<url>` | 假设请求来自给定的 URL。在多站点中，此参数用于指定目标站点。 |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | 通过 SSH（或使用 "docker"、"docker-compose"、"docker-compose-run"、"vagrant" 方案的容器）对远程服务器执行操作。 |
| `--http=<http>` | 通过 HTTP 对远程 WordPress 安装执行操作。 |
| `--user=<id\|login\|email>` | 设置 WordPress 用户。 |
| `--skip-plugins[=<plugins>]` | 跳过加载所有插件，或跳过以逗号分隔的插件列表。注意：mu-plugins 仍会被加载。 |
| `--skip-themes[=<themes>]` | 跳过加载所有主题，或跳过以逗号分隔的主题列表。 |
| `--skip-packages` | 跳过加载所有已安装的包。 |
| `--require=<path>` | 在运行命令之前加载 PHP 文件（可多次使用）。 |
| `--exec=<php-code>` | 在运行命令之前执行 PHP 代码（可多次使用）。 |
| `--context=<context>` | 在给定的上下文中加载 WordPress。 |
| `--[no-]color` | 是否对输出进行着色。 |
| `--debug[=<group>]` | 显示所有 PHP 错误并增加 WP-CLI 输出的详细程度。内置组包括：bootstrap、commandfactory 和 help。 |
| `--prompt[=<assoc>]` | 提示用户输入所有命令参数的值，或输入以逗号分隔的指定子集的值。 |
| `--quiet` | 抑制信息性消息。 |