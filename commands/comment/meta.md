---
title: "wp comment meta"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Comment
    - Commands
    - Repos
---

# wp comment meta

添加、更新、删除和列出评论自定义字段。

### 示例

    # 设置评论元数据
    $ wp comment meta set 123 description "Mary is a WordPress developer."
    成功：已更新自定义字段 'description'。

    # 获取评论元数据
    $ wp comment meta get 123 description
    Mary is a WordPress developer.

    # 更新评论元数据
    $ wp comment meta update 123 description "Mary is an awesome WordPress developer."
    成功：已更新自定义字段 'description'。

    # 删除评论元数据
    $ wp comment meta delete 123 description
    成功：已删除自定义字段。