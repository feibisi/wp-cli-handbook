---
title: "wp menu item"
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

# wp menu item

列出、添加和删除与菜单关联的项。

### 示例

    # 将现有文章添加到现有菜单
    $ wp menu item add-post sidebar-menu 33 --title="自定义测试文章"
    成功：菜单项已添加。

    # 创建新的菜单链接项
    $ wp menu item add-custom sidebar-menu Apple http://apple.com
    成功：菜单项已添加。

    # 删除菜单项
    $ wp menu item delete 45
    成功：已删除 1 个菜单项中的 1 个。