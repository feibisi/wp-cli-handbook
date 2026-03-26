---
title: "wp embed provider"
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

# wp embed provider

检索 oEmbed 服务提供者。

### 示例

    # 列出可用提供者的格式和端点字段。
    $ wp embed provider list
    +------------------------------+-----------------------------------------+
    | format                       | endpoint                                |
    +------------------------------+-----------------------------------------+
    | #https?://youtu\.be/.*#i     | https://www.youtube.com/oembed          |
    | #https?://flic\.kr/.*#i      | https://www.flickr.com/services/oembed/ |
    | #https?://wordpress\.tv/.*#i | https://wordpress.tv/oembed/            |

    # 获取与 URL 匹配的服务提供者。
    $ wp embed provider match https://www.youtube.com/watch?v=dQw4w9WgXcQ
    https://www.youtube.com/oembed