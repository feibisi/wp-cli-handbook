---
title: "wp menu"
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

# wp menu

列出、创建、分配和删除当前主题的导航菜单。

请参阅主题手册中的[导航菜单](https://developer.wordpress.org/themes/functionality/navigation-menus/)参考。

### 示例

    # 创建新菜单
    $ wp menu create "My Menu"
    Success: Created menu 200.

    # 列出现有菜单
    $ wp menu list
    +---------+----------+----------+-----------+-------+
    | term_id | name     | slug     | locations | count |
    +---------+----------+----------+-----------+-------+
    | 200     | My Menu  | my-menu  |           | 0     |
    | 177     | Top Menu | top-menu | primary   | 7     |
    +---------+----------+----------+-----------+-------+

    # 创建新的自定义菜单链接项
    $ wp menu item add-custom my-menu Apple http://apple.com --porcelain
    1922

    # 将 'my-menu' 菜单分配到 'primary' 位置
    $ wp menu location assign my-menu primary
    Success: Assigned location primary to menu my-menu.