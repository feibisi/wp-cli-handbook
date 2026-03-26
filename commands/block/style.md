---
title: "wp block style"
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

# wp block style

检索已注册区块样式的详细信息。

从 WP_Block_Styles_Registry 获取区块样式变体的信息。

### 示例

    # 列出所有已注册的区块样式
    $ wp block style list

    # 列出特定区块的样式
    $ wp block style list --block=core/button

    # 获取特定样式的详细信息
    $ wp block style get core/button outline