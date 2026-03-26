---
title: "wp i18n make-json"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - I18N
    - Commands
    - Repos
---

# wp i18n make-json

从 PO 文件中提取 JavaScript 字符串，并将其添加到单独的 JSON 文件中。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

出于 JavaScript 国际化目的，WordPress 要求将翻译内容分割成每个 JavaScript 源文件对应一个 Jed 格式的 JSON 文件。

请访问 https://make.wordpress.org/core/2018/11/09/new-javascript-i18n-support-in-wordpress/ 以了解更多关于 WordPress JavaScript 国际化的信息。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，详细了解所使用的语法约定。

&lt;source&gt;
: 指向现有 PO 文件或包含多个 PO 文件的目录的路径。

[&lt;destination&gt;]
: 生成的 JSON 文件的目标目录路径。默认为源目录。

[\--domain=&lt;domain&gt;]
: 用于 JSON 文件名的文本域。覆盖从 PO 文件中提取的默认值。

[\--extensions=&lt;extensions&gt;]
: 额外的自定义 JS 扩展，以逗号分隔的列表。默认搜索 .min.js 和 .js 扩展。

[\--purge]
: 是否清除从原始源文件中提取的字符串。默认为 true，使用 `--no-purge` 可跳过移除。

[\--update-mo-files]
: 更新 PO 文件后是否也应更新 MO 文件。仅在与 `--purge` 结合使用时有效。

[\--pretty-print]
: 美化输出生成的 JSON 文件。

[\--use-map=&lt;paths_or_maps&gt;]
: 是否对字符串使用映射文件，作为 JSON 值，数组可指定多个。每个元素可以是字符串（文件路径）或对象（映射）。

### 示例

    # 为 languages 目录中的所有 PO 文件创建 JSON 文件
    $ wp i18n make-json languages

    # 为 my-plugin-de_DE.po 创建 JSON 文件，并保持 PO 文件不变
    $ wp i18n make-json my-plugin-de_DE.po /tmp --no-purge

    # 使用映射创建 JSON 文件
    $ wp i18n make-json languages --use-map=build/map.json

    # 使用多个映射创建 JSON 文件
    $ wp i18n make-json languages '--use-map=["build/map.json","build/map2.json"]'

    # 使用对象映射创建 JSON 文件
    $ wp i18n make-json languages '--use-map={"source/index.js":"build/index.js"}'

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