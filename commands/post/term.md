---
title: "wp post term"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Post
    - Commands
    - Repos
---

# wp post term

添加、更新、移除和列出文章分类项。

### 示例

    # 将分类项 `test` 设置为文章 ID 123 的分类
    $ wp post term set 123 test category
    成功：已设置分类项。

    # 将分类项 `test` 和 `apple` 设置为文章 ID 123 的分类
    $ wp post term set 123 test apple category
    成功：已设置分类项。

    # 列出文章 ID 123 的分类项
    $ wp post term list 123 category --fields=term_id,slug
    +---------+-------+
    | term_id | slug  |
    +---------+-------+
    | 2       | apple |
    | 3       | test  |
    +----------+------+

    # 移除文章 ID 123 的分类项 `test` 和 `apple`
    $ wp post term remove 123 category test apple
    成功：已移除分类项。