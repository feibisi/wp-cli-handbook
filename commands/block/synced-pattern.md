---
title: "wp block synced-pattern"
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

# wp block synced-pattern

管理同步模式（可重用区块）。

同步模式以 'wp_block' 文章类型存储，可以是同步的（更改在所有地方反映）或非同步的（常规模式）。

### 示例

    # 列出所有同步模式
    $ wp block synced-pattern list

    # 创建同步模式
    $ wp block synced-pattern create --title="我的模式" --content='&lt;!-- wp:paragraph --&gt;&lt;p&gt;你好&lt;/p&gt;&lt;!-- /wp:paragraph --&gt;'

    # 删除同步模式
    $ wp block synced-pattern delete 123