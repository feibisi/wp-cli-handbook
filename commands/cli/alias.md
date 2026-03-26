---
title: "wp cli alias"
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

# wp cli alias

检索、设置和更新 WordPress 安装的别名。

除非被覆盖，这些命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

别名是 WordPress 安装的简写引用。例如，`@dev` 可以指代开发安装，`@prod` 可以指代生产安装。此命令为您提供添加、更新和删除可用注册别名的选项。

### 示例

    # 列出别名信息。
    $ wp cli alias list
    list
    ---
    @all: 对每个注册的别名运行命令。
    @local:
      user: wpcli
      path: /Users/wpcli/sites/testsite

    # 获取别名信息。
    $ wp cli alias get @dev
    ssh: dev@somedeve.env:12345/home/dev/

    # 添加别名。
    $ wp cli alias add @prod --set-ssh=login@host --set-path=/path/to/wordpress/install/ --set-user=wpcli
    成功：已添加 '@prod' 别名。

    # 更新别名。
    $ wp cli alias update @prod --set-user=newuser --set-path=/new/path/to/wordpress/install/
    成功：已更新 'prod' 别名。

    # 删除别名。
    $ wp cli alias delete @prod
    成功：已删除 '@prod' 别名。