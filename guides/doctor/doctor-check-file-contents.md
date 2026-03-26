---
title: "编写用于验证 WordPress 文件内容的检查项"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Doctor
    - Guides
    - Repos
---

# 编写用于验证 WordPress 文件内容的检查项

`wp doctor` 中包含的检查类型之一是 `File_Contents`，即能够检查所有或部分 WordPress 文件是否符合给定的正则表达式模式。该检查类型已被多个[默认诊断检查](https://make.wordpress.org/cli/handbook/guides/doctor/doctor-default-checks/)使用，你也可以在[自定义的 `doctor.yml` 配置文件](https://make.wordpress.org/cli/handbook/guides/doctor/doctor-customize-config/)中使用 `File_Contents` 检查类型。

`File_Contents` 检查类型是检查 WordPress 文件最有效的方式，因为它只遍历文件系统一次，无论你注册了多少个文件检查项。

例如，以下是两个使用 `File_Contents` 的检查项，一个确保插件未使用会话，另一个确保 `wp-config.php` 中未使用 `$_SERVER['SERVER_NAME']`：

    file-sessions:
      check: File_Contents
      options:
        regex: .*(session_start|\$_SESSION).*
        only_wp_content: true
    file-server-name-wp-config:
      check: File_Contents
      options:
        regex: define\(.+WP_(HOME|SITEURL).+\$_SERVER.+SERVER_NAME
        path: wp-config.php

一起运行时，你可能会看到：

    $ wp doctor check --config=file-contents.yml --all
    +----------------------------+---------+-----------------------------------------------------------------------------------------+
    | name                       | status  | message                                                                                 |
    +----------------------------+---------+-----------------------------------------------------------------------------------------+
    | file-sessions              | success | 所有 'php' 文件通过 '.*(session_start|\$_SESSION).*' 检查。                             |
    | file-server-name-wp-config | success | 所有 'php' 文件通过 'define\(.+WP_(HOME|SITEURL).+\$_SERVER.+SERVER_NAME' 检查。        |
    +----------------------------+---------+-----------------------------------------------------------------------------------------+

`File_Contents` 检查类型接受以下选项：

* 'regex'：用于检查每个文件内容的正则表达式模式。
* 'extension'：要检查的文件扩展名。默认为 'php'。多个文件扩展名用 '|' 分隔。
* 'path'：检查特定的文件路径。值应相对于 `ABSPATH`（例如 'wp-content' 或 'wp-config.php'）。
* 'only_wp_content'：仅检查 wp-content 目录。