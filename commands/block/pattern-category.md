---
title: "wp block pattern-category"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Block
    - Commands
    - Repos
---

# wp block pattern-category

检索已注册区块模式分类的详细信息。

从 WP_Block_Pattern_Categories_Registry 获取区块模式分类信息。

### 示例

    # 列出所有已注册的模式分类
    $ wp block pattern-category list

    # 获取特定分类的详细信息
    $ wp block pattern-category get featured --format=json