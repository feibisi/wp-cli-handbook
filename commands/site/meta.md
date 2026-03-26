---
title: "wp site meta"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Site
    - Commands
    - Repos
---

# wp site meta

添加、更新、删除和列出站点的自定义字段。

### 示例

    # 设置站点元数据
    $ wp site meta set 123 bio "Mary is a WordPress developer."
    成功：已更新自定义字段 'bio'。

    # 获取站点元数据
    $ wp site meta get 123 bio
    Mary is a WordPress developer.

    # 更新站点元数据
    $ wp site meta update 123 bio "Mary is an awesome WordPress developer."
    成功：已更新自定义字段 'bio'。

    # 删除站点元数据
    $ wp site meta delete 123 bio
    成功：已删除自定义字段。