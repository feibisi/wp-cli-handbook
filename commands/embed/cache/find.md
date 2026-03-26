---
title: "wp embed cache find"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Cache
    - Embed
    - Commands
---

# wp embed cache find

查找给定 URL 的 oEmbed 缓存文章 ID。

从 WordPress 4.9 开始，未与特定文章关联的嵌入内容将缓存在新的 oembed_cache 文章类型中。根据属性和上下文，一个 URL 可能对应多个此类条目。

请注意，不要与存储在文章元数据中的给定文章的 oEmbed 缓存混淆。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，详细了解所使用的语法约定。

&lt;url&gt;
: 要获取 oEmbed 数据的 URL。

[\--width=&lt;width&gt;]
: 嵌入内容的宽度（像素）。作为缓存键的一部分，因此必须匹配。如果设置了 `content_width` 则默认为该值，否则为 500px，因此取决于主题和上下文。

[\--height=&lt;height&gt;]
: 嵌入内容的高度（像素）。作为缓存键的一部分，因此必须匹配。默认为默认宽度（`content_width` 或 500px）的 1.5 倍，最大不超过 1000px。

[\--discover]
: 是否在设置了 discover 属性的情况下进行搜索。作为缓存键的一部分，因此必须匹配。如果未指定，将依次尝试属性：未设置、'1'、'0'，并返回第一个结果。

### EXAMPLES

    # Find cache post ID for a given URL.
    $ wp embed cache find https://www.youtube.com/watch?v=dQw4w9WgXcQ --width=500
    123

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