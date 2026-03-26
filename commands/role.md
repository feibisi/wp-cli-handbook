---
title: "wp role"
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

# wp role

管理用户角色，包括创建新角色和重置为默认设置。

请参阅[角色与权限](https://wordpress.org/documentation/article/roles-and-capabilities)和[WP User 类](https://developer.wordpress.org/reference/classes/wp_user)的参考文档。

### 示例

    # 列出角色。
    $ wp role list --fields=role --format=csv
    role
    administrator
    editor
    author
    contributor
    subscriber

    # 检查角色是否存在。
    $ wp role exists editor
    Success: 存在 ID 为 'editor' 的角色。

    # 创建新角色。
    $ wp role create approver Approver
    Success: 已创建键为 'approver' 的角色。

    # 删除现有角色。
    $ wp role delete approver
    Success: 已删除键为 'approver' 的角色。

    # 将现有角色重置为其默认权限。
    $ wp role reset administrator author contributor
    Success: 已重置 3/3 个角色。