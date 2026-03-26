---
title: "wp widget"
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

# wp widget

管理小工具，包括在侧边栏中添加和移动它们。

[小工具](https://developer.wordpress.org/themes/functionality/widgets/) 向小工具区域（也称为[侧边栏](https://developer.wordpress.org/themes/functionality/sidebars/)）添加内容和功能。

### 示例

    # 列出指定侧边栏上的小工具
    $ wp widget list sidebar-1
    +----------+------------+----------+----------------------+
    | name     | id         | position | options              |
    +----------+------------+----------+----------------------+
    | meta     | meta-6     | 1        | {"title":"Meta"}     |
    | calendar | calendar-2 | 2        | {"title":"Calendar"} |
    +----------+------------+----------+----------------------+

    # 将日历小工具添加到侧边栏的第二个位置
    $ wp widget add calendar sidebar-1 2
    Success: Added widget to sidebar.

    # 更新与指定小工具关联的选项
    $ wp widget update calendar-1 --title="Calendar"
    Success: Widget updated.

    # 完全删除一个或多个小工具
    $ wp widget delete calendar-2 archive-1
    Success: 2 widgets removed from sidebar.