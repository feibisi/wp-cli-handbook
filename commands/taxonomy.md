---
title: "wp taxonomy"
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

# wp taxonomy

检索已注册分类法的相关信息。

请参考[内置分类法](https://developer.wordpress.org/themes/basics/categories-tags-custom-taxonomies/)和[自定义分类法](https://developer.wordpress.org/plugins/taxonomies/working-with-custom-taxonomies/)的文档。

### 示例

    # 列出所有对象类型为 'post' 的分类法。
    $ wp taxonomy list --object_type=post --fields=name,public
    +-------------+--------+
    | name        | public |
    +-------------+--------+
    | category    | 1      |
    | post_tag    | 1      |
    | post_format | 1      |
    +-------------+--------+

    # 获取 'post_tag' 分类法的权限信息。
    $ wp taxonomy get post_tag --field=cap
    {"manage_terms":"manage_categories","edit_terms":"manage_categories","delete_terms":"manage_categories","assign_terms":"edit_posts"}