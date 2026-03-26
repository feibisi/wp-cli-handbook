---
title: "wp user meta"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - User
    - Commands
    - Repos
---

# wp user meta

添加、更新、删除和列出用户自定义字段。

### 示例

    # 添加用户元数据
    $ wp user meta add 123 bio "Mary is an WordPress developer."
    Success: Added custom field.

    # 列出用户元数据
    $ wp user meta list 123 --keys=nickname,description,wp_capabilities
    +---------+-----------------+--------------------------------+
    | user_id | meta_key        | meta_value                     |
    +---------+-----------------+--------------------------------+
    | 123     | nickname        | supervisor                     |
    | 123     | description     | Mary is a WordPress developer. |
    | 123     | wp_capabilities | {"administrator":true}         |
    +---------+-----------------+--------------------------------+

    # 更新用户元数据
    $ wp user meta update 123 bio "Mary is an awesome WordPress developer."
    Success: Updated custom field 'bio'.

    # 删除用户元数据
    $ wp user meta delete 123 bio
    Success: Deleted custom field.