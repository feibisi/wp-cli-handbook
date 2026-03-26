---
title: "wp term"
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

# wp term

管理分类法术语和术语元数据，包含创建、删除和列出命令。

查看[分类法及其术语](https://wordpress.org/documentation/article/taxonomies)的参考文档。

### 示例

    # 创建新术语
    $ wp term create category Apple --description="一种水果"
    成功：已创建分类 199。

    # 获取术语详情
    $ wp term get category 199 --format=json --fields=term_id,name,slug,count
    {"term_id":199,"name":"Apple","slug":"apple","count":1}

    # 更新现有术语
    $ wp term update category 15 --name=Apple
    成功：术语已更新。

    # 获取术语的 URL
    $ wp term list post_tag --include=123 --field=url
    http://example.com/tag/tips-and-tricks

    # 删除文章分类
    $ wp term delete category 15
    成功：已删除分类 15。

    # 重新统计分配给每个分类和标签的文章数量
    $ wp term recount category post_tag
    成功：已更新分类术语计数
    成功：已更新 post_tag 术语计数