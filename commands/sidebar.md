---
title: "wp sidebar"
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

# wp sidebar

列出已注册的侧边栏。

[侧边栏](https://developer.wordpress.org/themes/functionality/sidebars/) 是您主题中任何支持小工具的区域。

### 示例

    # 列出侧边栏
    $ wp sidebar list --fields=name,id --format=csv
    name,id
    "Widget Area",sidebar-1
    "Inactive Widgets",wp_inactive_widgets