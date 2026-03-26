---
title: "wp i18n make-pot"
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

# wp i18n make-pot

为 WordPress 项目创建 POT 文件。

此命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

扫描 PHP、Blade-PHP 和 JavaScript 文件中的可翻译字符串，如果检测到源目录是插件或主题，还会扫描主题样式表和插件文件。

### OPTIONS

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考文档。

&lt;source&gt;
: 用于扫描提取字符串的目录。

[&lt;destination&gt;]
: 生成的 POT 文件的名称。

[\--slug=&lt;slug&gt;]
: 插件或主题的别名。默认为源目录的基名。

[\--domain=&lt;domain&gt;]
: 在源代码中查找的文本域，除非使用了 `--ignore-domain` 选项。默认情况下，使用插件或主题的 "Text Domain" 标头。如果未提供，则回退到项目别名。

[\--ignore-domain]
: 完全忽略文本域，提取具有任何文本域的字符串。

[\--merge[=&lt;paths&gt;]]
: 逗号分隔的 POT 文件列表，其内容应与提取的字符串合并。如果留空，则默认为目标 POT 文件。POT 文件标头将被忽略。

[\--subtract=&lt;paths&gt;]
: 逗号分隔的 POT 文件列表，其内容应作为字符串提取的某种拒绝列表。任何在该拒绝列表中找到的字符串将不会被提取。当您想从同一源目录创建多个内容略有不同且没有重复字符串的 POT 文件时，这很有用。

[\--subtract-and-merge]
: 是否应将生成的 POT 文件中的源代码引用和注释添加到用于减法的 POT 文件中。警告：这会修改传递给 `--subtract` 的文件！

[\--include=&lt;paths&gt;]
: 逗号分隔的文件和路径列表，应用于字符串提取。如果提供，则仅考虑这些文件和文件夹进行字符串提取。例如，`--include="src,my-file.php` 将忽略 `my-file.php` 和 `src` 目录中的文件以外的任何内容。可以使用简单的通配符模式，例如 `--include=foo-*.php` 包含任何带有 `foo-` 前缀的 PHP 文件。前导和尾随斜杠将被忽略，例如 `/my/directory/` 与 `my/directory` 相同。

[\--exclude=&lt;paths&gt;]
: 逗号分隔的文件和路径列表，应在字符串提取时跳过。例如，`--exclude=.github,myfile.php` 将忽略在 `myfile.php` 或 `.github` 文件夹中找到的任何字符串。可以使用简单的通配符模式，例如 `--exclude=foo-*.php` 排除任何带有 `foo-` 前缀的 PHP 文件。前导和尾随斜杠将被忽略，例如 `/my/directory/` 与 `my/directory` 相同。以下文件和文件夹始终被排除：node_modules、.git、.svn、.CVS、.hg、vendor、*.min.js。

[\--headers=&lt;headers&gt;]
: 自定义标头的 JSON 格式数组，这些标头将添加到 POT 文件中。默认为空数组。

[\--location]
: 是否写入 `#: filename:line` 行。默认为 true，使用 `--no-location` 来跳过移除。请注意，禁用此选项会使技术熟练的翻译人员更难理解每条消息的上下文。

[\--skip-js]
: 跳过 JavaScript 字符串提取。当此步骤已在其他构建步骤（例如通过 Babel）完成时很有用。

[\--skip-php]
: 跳过 PHP 字符串提取。

[\--skip-blade]
: 跳过 Blade-PHP 字符串提取。

[\--skip-block-json]
: 跳过从 block.json 文件中提取字符串。

[\--skip-theme-json]
: 跳过从 theme.json 文件中提取字符串。

[\--skip-audit]
: 跳过字符串审核，即尝试在可翻译字符串中查找可能的错误。在自动化环境中运行时很有用。

[\--file-comment=&lt;file-comment&gt;]
: 应作为注释添加到生成的 POT 文件顶部的字符串。默认情况下，会为 WordPress 插件和主题添加如下格式的版权注释：

     ```
     Copyright (C) 2018 Example Plugin Author
     This file is distributed under the same license as the Example Plugin package.
     ```

     如果插件或主题在其主插件文件或样式表中指定了许可证，则注释如下所示：

     ```
     Copyright (C) 2018 Example Plugin Author
     This file is distributed under the GPLv2.
     ```

[\--package-name=&lt;name&gt;]
: 用于在生成的 POT 文件的 `Project-Id-Version` 标头中作为包名的名称。如果适用，将覆盖插件或主题的名称。

### 示例

    # 为当前目录下的 WordPress 插件/主题创建 POT 文件。
    $ wp i18n make-pot . languages/my-plugin.pot

    # 为 WordPress 核心中的大洲和城市列表创建 POT 文件。
    $ wp i18n make-pot . continents-and-cities.pot --include="wp-admin/includes/continents-cities.php" --ignore-domain

    # 为当前目录下的 WordPress 主题创建带有自定义标头的 POT 文件。
    $ wp i18n make-pot . languages/my-theme.pot --headers='{"Report-Msgid-Bugs-To":"https://github.com/theme-author/my-theme/","POT-Creation-Date":""}'

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