---
title: "wp embed handler"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Embed
    - Commands
    - Repos
---

# wp embed handler

检索嵌入处理器。

### 示例

    # 列出可用处理器的 id、regex、priority 字段。
    $ wp embed handler list --fields=priority,id
    +----------+-------------------+
    | priority | id                |
    +----------+-------------------+
    | 10       | youtube_embed_url |
    | 9999     | audio             |
    | 9999     | video             |