---
title: "wp import"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Commands
    - Repos
    - Data
---

# wp import

从给定的 WXR 文件导入内容。

为 WordPress 导入器插件提供命令行界面，用于执行数据迁移。

导入过程中使用 `define( 'IMPORT_DEBUG', true );` 以获得更详细的输出信息。

### OPTIONS

请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考，以详细了解所使用的语法约定。

&lt;file&gt;...
: 要导入的一个或多个有效 WXR 文件的路径。也接受目录。

\--authors=&lt;authors&gt;
: 应如何处理作者映射。选项为 'create'、'mapping.csv' 或 'skip'。第一个选项将为 WXR 文件中不存在的用户创建账户。第二个选项将从 CSV 文件读取作者映射关联，如果文件路径不存在，则会创建一个用于编辑的 CSV 文件。CSV 需要两列和一个标题行，例如 "old_user_login,new_user_login"。最后一个选项将跳过任何作者映射。

[\--skip=&lt;data-type&gt;]
: 跳过导入特定数据。支持的选项有：'attachment' 和 'image_resize'（跳过耗时的缩略图生成）。

[\--rewrite_urls]
: 更改所有当前链接到先前站点的导入 URL，使其现在链接到本站点。需要 WordPress Importer 版本 0.9.1 或更高版本。

### 示例

    # 从 WXR 文件导入内容
    $ wp import example.wordpress.2016-06-21.xml --authors=create
    开始导入过程...
    处理文章 #1 ("Hello world!") (post_type: post)
    -- 第 1 篇，共 1 篇
    -- 2016年6月21日 星期二 05:31:12 +0000
    -- 已导入文章，post_id 为 #1
    成功：已完成从 'example.wordpress.2016-06-21.xml' 文件的导入。

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