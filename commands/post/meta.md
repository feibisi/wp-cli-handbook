---
title: "wp post meta"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Post
    - Commands
    - Repos
---

# wp post meta

添加、更新、删除和列出文章自定义字段。

### 示例

    # 设置文章元数据
    $ wp post meta set 123 _wp_page_template about.php
    成功：已更新自定义字段 '_wp_page_template'。

    # 获取文章元数据
    $ wp post meta get 123 _wp_page_template
    about.php

    # 更新文章元数据
    $ wp post meta update 123 _wp_page_template contact.php
    成功：已更新自定义字段 '_wp_page_template'。

    # 删除文章元数据
    $ wp post meta delete 123 _wp_page_template
    成功：已删除自定义字段。