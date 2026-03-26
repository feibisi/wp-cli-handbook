---
title: "wp embed cache"
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

# wp embed cache

查找、触发和删除 oEmbed 缓存。

### 示例

    # 查找指定 URL 的缓存文章 ID。
    $ wp embed cache find https://www.youtube.com/watch?v=dQw4w9WgXcQ --width=500
    123

    # 清除文章的缓存。
    $ wp embed cache clear 123
    成功：已清除 oEmbed 缓存。

    # 触发文章的缓存。
    $ wp embed cache trigger 456
    成功：缓存已触发！