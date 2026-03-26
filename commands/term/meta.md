---
title: "wp term meta"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Term
    - Commands
    - Repos
---

# wp term meta

添加、更新、删除和列出分类法项目的自定义字段。

### 示例

    # 设置分类法项目元数据
    $ wp term meta set 123 bio "Mary is a WordPress developer."
    成功：已更新自定义字段 'bio'。

    # 获取分类法项目元数据
    $ wp term meta get 123 bio
    Mary is a WordPress developer.

    # 更新分类法项目元数据
    $ wp term meta update 123 bio "Mary is an awesome WordPress developer."
    成功：已更新自定义字段 'bio'。

    # 删除分类法项目元数据
    $ wp term meta delete 123 bio
    成功：已删除自定义字段。