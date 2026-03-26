---
title: "wp media regenerate"
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

# wp media regenerate

为一个或多个附件重新生成缩略图。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

[&lt;attachment-id&gt;...]
: 要重新生成缩略图的一个或多个附件的 ID。

[\--image_size=&lt;image_size&gt;]
: 要重新生成的图片尺寸名称。仅重新生成此图片尺寸的缩略图，其他图片尺寸的缩略图将保持不变。

[\--skip-delete]
: 跳过删除原始缩略图。如果您的缩略图被您无法控制的外部来源链接，最好保留它们。默认为 false。

[\--only-missing]
: 仅为缺少图片尺寸的图像生成缩略图。

[\--delete-unknown]
: 仅删除旧的未注册图片尺寸的缩略图。

[\--yes]
: 对确认消息回答“是”。仅当未传递 ID 作为参数时才会显示确认信息。

### 示例

    # 为指定的附件 ID 重新生成缩略图。
    $ wp media regenerate 123 124 125
    找到 3 张需要重新生成缩略图的图片。
    1/3 已为“竖版图片”(ID 123)重新生成缩略图。
    2/3 已为“横版图片”(ID 124)重新生成缩略图。
    3/3 已为“美丽图片”(ID 125)重新生成缩略图。
    成功：已重新生成 3 张图片中的 3 张。

    # 重新生成所有缩略图，无需确认。
    $ wp media regenerate --yes
    找到 3 张需要重新生成缩略图的图片。
    1/3 已为“悉尼海港大桥”(ID 760)重新生成缩略图。
    2/3 已为“海滨木板路”(ID 757)重新生成缩略图。
    3/3 已为“河上旭日”(ID 756)重新生成缩略图。
    成功：已重新生成 3 张图片中的 3 张。

    # 重新生成所有 ID 在 1000 到 2000 之间的缩略图。
    $ seq 1000 2000 | xargs wp media regenerate
    找到 4 张需要重新生成缩略图的图片。
    1/4 已为“竖版特色图片”(ID 1027)重新生成缩略图。
    2/4 已为“横版特色图片”(ID 1022)重新生成缩略图。
    3/4 已为“独角兽壁纸”(ID 1045)重新生成缩略图。
    4/4 已为“我值得被爱壁纸”(ID 1023)重新生成缩略图。
    成功：已重新生成 4 张图片中的 4 张。

    # 仅为所有图片重新生成“大尺寸”图像尺寸的缩略图。
    $ wp media regenerate --image_size=large
    确实要为所有图片重新生成“大尺寸”图像尺寸吗？[y/n] y
    找到 3 张需要重新生成缩略图的图片。
    1/3 已为“悉尼海港大桥”(ID 760)重新生成“大尺寸”缩略图。
    2/3 “海滨木板路”(ID 757)无需重新生成“大尺寸”缩略图。
    3/3 已为“河上旭日”(ID 756)重新生成“大尺寸”缩略图。
    成功：已重新生成 3 张图片中的 3 张。

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