---
title: "wp cap"
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

# wp cap

添加、移除和列出用户角色的权限。

请参阅[角色与权限](https://wordpress.org/documentation/article/roles-and-capabilities)和[WP User 类](https://developer.wordpress.org/reference/classes/wp_user)的参考文档。

### 示例

    # 为 'author' 角色添加 'spectate' 权限。
    $ wp cap add 'author' 'spectate'
    成功：已为 'author' 角色添加 1 项权限。

    # 将 'editor' 角色的所有权限添加到 'author' 角色。
    $ wp cap list 'editor' | xargs wp cap add 'author'
    成功：已为 'author' 角色添加 24 项权限。

    # 从 'editor' 角色中移除所有同时存在于 'author' 角色的权限。
    $ wp cap list 'author' | xargs wp cap remove 'editor'
    成功：已从 'editor' 角色中移除 34 项权限。