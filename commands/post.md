---
title: "wp post"
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

# wp post

管理文章、内容和元数据。

### 示例

    # 创建新文章
    $ wp post create --post_type=post --post_title='示例文章'
    Success: 已创建文章 123。

    # 更新现有文章
    $ wp post update 123 --post_status=draft
    Success: 已更新文章 123。

    # 删除现有文章
    $ wp post delete 123
    Success: 已移至回收站文章 123。