---
title: "wp media import"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Media
    - Commands
    - Repos
---

# wp media import

从本地文件或 URL 创建附件。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;file&gt;...
: 要导入的文件路径。支持当前 shell 的 glob(3) 功能。
    如果文件被识别为 URL（例如，带有 http 或 ftp 协议），文件将在被旁加载之前下载到临时文件。

[\--post_id=&lt;post_id&gt;]
: 要将导入文件附加到的文章 ID。

[\--post_name=&lt;post_name&gt;]
: 要将导入文件附加到的文章名称。

[\--file_name=&lt;name&gt;]
: 附件名称（post_name 字段）。

[\--title=&lt;title&gt;]
: 附件标题（文章标题字段）。

[\--caption=&lt;caption&gt;]
: 附件说明文字（文章摘要字段）。

[\--alt=&lt;alt_text&gt;]
: 图片替代文本（保存为文章元数据）。

[\--desc=&lt;description&gt;]
: 附件文章的“描述”字段（文章内容）。

[\--skip-copy]
: 如果设置，媒体文件（仅限本地）将导入到媒体库但不会在磁盘上移动。设置此选项后，文件名将不会通过 wp_unique_filename() 处理。

[\--preserve-filetime]
: 使用文件修改时间作为文章发布日期和修改日期。远程文件将始终使用当前时间。

[\--featured_image]
: 如果设置，将导入的图片设置为其附加文章的“特色图片”。

[\--porcelain[=&lt;field&gt;]]
: 为每个导入的图片输出单个字段。用作标志时默认为附件 ID。
\---
选项:
  - url
\---

### 示例

    # 导入当前用户“图片”目录中的所有 jpg 文件，不附加到任何文章。
    $ wp media import ~/Pictures/**\/*.jpg
    已将文件 '/home/person/Pictures/landscape-photo.jpg' 作为附件 ID 1751 导入。
    已将文件 '/home/person/Pictures/fashion-icon.jpg' 作为附件 ID 1752 导入。
    成功：已导入 2 个项目中的 2 个。

    # 导入本地图片并将其设置为某篇文章的特色图片。
    $ wp media import ~/Downloads/image.png --post_id=123 --title="一张下载的图片" --featured_image
    已将文件 '/home/person/Downloads/image.png' 作为附件 ID 1753 导入并附加到文章 123 作为特色图片。
    成功：已导入 1 张图片中的 1 张。

    # 导入本地图片，但将其设置为所有文章的特色图片。
    # 1. 导入图片并获取其附件 ID。
    # 2. 将该附件 ID 分配为所有文章的特色图片。
    $ ATTACHMENT_ID="$(wp media import ~/Downloads/image.png --porcelain)"
    $ wp post list --post_type=post --format=ids | xargs -d ' ' -I % wp post meta add % _thumbnail_id $ATTACHMENT_ID
    成功：已添加自定义字段。
    成功：已添加自定义字段。

    # 从网络导入图片。
    $ wp media import http://s.wordpress.org/style/images/wp-header-logo.png --title='WordPress 徽标' --alt="语义化个人发布"
    已将文件 'http://s.wordpress.org/style/images/wp-header-logo.png' 作为附件 ID 1755 导入。
    成功：已导入 1 张图片中的 1 张。

    # 导入后获取附件的 URL。
    $ wp media import http://s.wordpress.org/style/images/wp-header-logo.png --porcelain | xargs -I {} wp post list --post__in={} --field=url --post_type=attachment
    http://wordpress-develop.dev/wp-header-logo/

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