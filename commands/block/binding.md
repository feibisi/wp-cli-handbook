---
title: "wp block binding"
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

# wp block binding

检索已注册区块绑定源的详细信息。

从 WP_Block_Bindings_Registry 获取区块绑定源信息。区块绑定允许将动态数据连接到区块属性。

### 示例

    # 列出所有已注册的绑定源
    $ wp block binding list

    # 获取 post-meta 绑定的详细信息
    $ wp block binding get core/post-meta --format=json