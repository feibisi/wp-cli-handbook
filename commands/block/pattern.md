---
title: "wp block pattern"
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

# wp block pattern

检索已注册区块模式的详细信息。

从 WP_Block_Patterns_Registry 获取 WordPress 内置和自定义区块模式的信息。

### 示例

    # 列出所有已注册的区块模式
    $ wp block pattern list

    # 获取特定模式的详细信息
    $ wp block pattern get core/query-standard-posts --format=json

    # 列出特定分类中的模式
    $ wp block pattern list --category=featured