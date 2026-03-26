---
title: "wp embed fetch"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Embed
    - Commands
    - Repos
---

# wp embed fetch

尝试将 URL 转换为嵌入 HTML。

在非原始模式下，首先根据已注册嵌入处理器的正则表达式检查 URL。如果没有匹配项且功能已启用，则 URL 将被传递给 WP_oEmbed 类。

在原始模式下，直接检查提供程序并返回数据。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，了解所用语法约定的详细说明。

&lt;url&gt;
: 要获取 oEmbed 数据的 URL。

[\--width=&lt;width&gt;]
: 嵌入内容的宽度（像素）。

[\--height=&lt;height&gt;]
: 嵌入内容的高度（像素）。

[\--post-id=&lt;id&gt;]
: 为指定文章缓存 oEmbed 响应。

[\--discover]
: 启用 oEmbed 发现。默认为 true。

[\--skip-cache]
: 忽略已缓存的 oEmbed 响应。如果使用 'raw' 选项则无效，因为该选项不使用缓存。

[\--skip-sanitization]
: 移除 WordPress 4.4 及更高版本用于清理 oEmbed 响应的过滤器。如果使用 'raw' 选项则无效，因为该选项会绕过清理过程。

[\--do-shortcode]
: 如果 URL 由已注册的嵌入处理器处理并返回短代码，则执行短代码并返回结果。如果使用 'raw' 选项则无效，因为该选项会绕过处理器。

[\--limit-response-size=&lt;size&gt;]
: 使用发现功能时限制生成的 HTML 大小。默认为 150 KB（WordPress 标准限制）。与 'no-discover' 不兼容。

[\--raw]
: 返回原始的 oEmbed 响应，而不是生成的 HTML。忽略缓存，并且不清理响应或使用已注册的嵌入处理器。

[\--raw-format=&lt;json|xml&gt;]
: 以特定格式渲染原始 oEmbed 数据。默认为 json。只能与 'raw' 选项一起指定。
\---
options:
  - json
  - xml
\---

### 示例

    # 获取指定 URL 的嵌入 HTML。
    $ wp embed fetch https://www.youtube.com/watch?v=dQw4w9WgXcQ
    &lt;iframe width="525" height="295" src="https://www.youtube.com/embed/dQw4w9WgXcQ?feature=oembed" ...

    # 获取指定 URL 的原始 oEmbed 数据。
    $ wp embed fetch https://www.youtube.com/watch?v=dQw4w9WgXcQ --raw
    {"author_url":"https:\/\/www.youtube.com\/user\/RickAstleyVEVO","width":525,"version":"1.0", ...

### GLOBAL PARAMETERS

These [global parameters](https://make.wordpress.org/cli/handbook/config/) have the same behavior across all commands and affect how WP-CLI interacts with WordPress.

| **Argument**    | **Description**              |
|:----------------|:-----------------------------|
| `--path=<path>` | Path to the WordPress files. |
| `--url=<url>` | Pretend request came from given URL. In multisite, this argument is how the target site is specified. |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | Perform operation against a remote server over SSH (or a container using scheme of "docker", "docker-compose", "docker-compose-run", "vagrant"). |
| `--http=<http>` | Perform operation against a remote WordPress installation over HTTP. |
| `--user=<id\|login\|email>` | Set the WordPress user. |
| `--skip-plugins[=<plugins>]` | Skip loading all plugins, or a comma-separated list of plugins. Note: mu-plugins are still loaded. |
| `--skip-themes[=<themes>]` | Skip loading all themes, or a comma-separated list of themes. |
| `--skip-packages` | Skip loading all installed packages. |
| `--require=<path>` | Load PHP file before running the command (may be used more than once). |
| `--exec=<php-code>` | Execute PHP code before running the command (may be used more than once). |
| `--context=<context>` | Load WordPress in a given context. |
| `--[no-]color` | Whether to colorize the output. |
| `--debug[=<group>]` | Show all PHP errors and add verbosity to WP-CLI output. Built-in groups include: bootstrap, commandfactory, and help. |
| `--prompt[=<assoc>]` | Prompt the user to enter values for all command arguments, or a subset specified as comma-separated values. |
| `--quiet` | Suppress informational messages. |