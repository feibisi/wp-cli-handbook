---
title: "wp cache"
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

# wp cache

添加、移除、获取和清空 WP 对象缓存对象。

默认情况下，WP 对象缓存在 PHP 内存中存在于请求期间（并在结束时清空）。使用持久对象缓存插件可在请求之间保持对象缓存。

[阅读代码库文章](https://developer.wordpress.org/reference/classes/wp_object_cache)了解更多详情。

### 示例

    # 设置缓存。
    $ wp cache set my_key my_value my_group 300
    成功：在组 'my_group' 中设置对象 'my_key'。

    # 获取缓存。
    $ wp cache get my_key my_group
    my_value