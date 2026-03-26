---
title: "wp comment"
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

# wp comment

创建、更新、删除和管理评论。

### 示例

    # 创建新评论。
    $ wp comment create --comment_post_ID=15 --comment_content="hello blog" --comment_author="wp-cli"
    成功：已创建评论 932。

    # 更新现有评论。
    $ wp comment update 123 --comment_author='That Guy'
    成功：已更新评论 123。

    # 删除现有评论。
    $ wp comment delete 1337 --force
    成功：已删除评论 1337。

    # 将所有垃圾评论移至回收站。
    $ wp comment delete $(wp comment list --status=spam --format=ids)
    成功：评论 264 已移至回收站。
    成功：评论 262 已移至回收站。