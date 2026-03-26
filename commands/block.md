---
title: "wp block"
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

# wp block

管理 WordPress 区块编辑器中的区块及相关实体。

### 示例

    # 列出所有已注册的区块类型
    $ wp block type list

    # 获取特定区块模式
    $ wp block pattern get my-theme/hero

    # 列出特定区块的区块样式
    $ wp block style list --block=core/button

    # 导出区块模板
    $ wp block template export twentytwentyfour//single --stdout

    # 创建同步模式
    $ wp block synced-pattern create --title="My Pattern" --content='&lt;!-- wp:paragraph --&gt;&lt;p&gt;Hello&lt;/p&gt;&lt;!-- /wp:paragraph --&gt;'