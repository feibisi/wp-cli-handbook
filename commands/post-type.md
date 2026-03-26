---
title: "wp post-type"
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

# wp post-type

获取站点已注册文章类型的详细信息。

获取 WordPress 内置及站点[自定义文章类型](https://developer.wordpress.org/plugins/post-types/)的信息。

### 示例

    # 获取文章类型的详细信息
    $ wp post-type get page --fields=name,label,hierarchical --format=json
    {"name":"page","label":"Pages","hierarchical":true}

    # 列出具有 'post' 权限类型的文章类型
    $ wp post-type list --capability_type=post --fields=name,public
    +---------------+--------+
    | name          | public |
    +---------------+--------+
    | post          | 1      |
    | attachment    | 1      |
    | revision      |        |
    | nav_menu_item |        |
    +---------------+--------+