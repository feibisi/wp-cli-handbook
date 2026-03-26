---
title: "wp menu location"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Menu
    - Commands
    - Repos
---

# wp menu location

分配、移除和列出菜单的位置。

### 示例

    # 列出可用的菜单位置
    $ wp menu location list
    +----------+-------------------+
    | location | description       |
    +----------+-------------------+
    | primary  | Primary Menu      |
    | social   | Social Links Menu |
    +----------+-------------------+

    # 将 'primary-menu' 菜单分配到 'primary' 位置
    $ wp menu location assign primary-menu primary
    Success: Assigned location primary to menu primary-menu.

    # 从 'primary' 位置移除 'primary-menu' 菜单
    $ wp menu location remove primary-menu primary
    Success: Removed location from menu.