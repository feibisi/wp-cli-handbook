---
title: "wp embed"
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

# wp embed

检查 oEmbed 提供商、清除嵌入缓存等操作。

### 示例

    # 获取指定 URL 的嵌入 HTML。
    $ wp embed fetch https://www.youtube.com/watch?v=dQw4w9WgXcQ
    &lt;iframe width="525" height="295" src="https://www.youtube.com/embed/dQw4w9WgXcQ?feature=oembed" ...

    # 查找指定 URL 的缓存文章 ID。
    $ wp embed cache find https://www.youtube.com/watch?v=dQw4w9WgXcQ --width=500
    123

    # 列出可用提供商的格式和端点字段。
    $ wp embed provider list
    +------------------------------+-----------------------------------------+
    | format                       | endpoint                                |
    +------------------------------+-----------------------------------------+
    | #https?://youtu\.be/.*#i     | https://www.youtube.com/oembed          |
    | #https?://flic\.kr/.*#i      | https://www.flickr.com/services/oembed/ |
    | #https?://wordpress\.tv/.*#i | https://wordpress.tv/oembed/            |

    # 列出可用处理程序的 ID、正则表达式和优先级字段。
    $ wp embed handler list --fields=priority,id
    +----------+-------------------+
    | priority | id                |
    +----------+-------------------+
    | 10       | youtube_embed_url |
    | 9999     | audio             |
    | 9999     | video             |
    +----------+-------------------+