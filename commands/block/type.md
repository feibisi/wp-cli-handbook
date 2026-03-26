---
title: "wp block type"
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

# wp block type

检索已注册区块类型的详细信息。

从 WP_Block_Type_Registry 获取 WordPress 内置和自定义区块类型的信息。

### 示例

    # 列出所有已注册的区块类型
    $ wp block type list

    # 获取特定区块类型的详细信息
    $ wp block type get core/paragraph --format=json

    # 列出所有核心区块
    $ wp block type list --namespace=core