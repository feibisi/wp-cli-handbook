---
title: "wp rewrite"
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

# wp rewrite

列出或刷新站点的重写规则，更新固定链接结构。

请参阅 WordPress [Rewrite API](https://developer.wordpress.org/apis/rewrite) 和
[WP Rewrite](https://developer.wordpress.org/reference/classes/wp_rewrite) 类参考。

### 示例

    # 刷新重写规则
    $ wp rewrite flush
    成功：重写规则已刷新。

    # 更新固定链接结构
    $ wp rewrite structure '/%year%/%monthnum%/%postname%'
    成功：重写结构已设置。

    # 列出重写规则
    $ wp rewrite list --format=csv
    match,query,source
    ^wp-json/?$,index.php?rest_route=/,other
    ^wp-json/(.*)?,index.php?rest_route=/$matches[1],other
    category/(.+?)/feed/(feed|rdf|rss|rss2|atom)/?$,index.php?category_name=$matches[1]&amp;feed=$matches[2],category
    category/(.+?)/(feed|rdf|rss|rss2|atom)/?$,index.php?category_name=$matches[1]&amp;feed=$matches[2],category
    category/(.+?)/embed/?$,index.php?category_name=$matches[1]&amp;embed=true,category