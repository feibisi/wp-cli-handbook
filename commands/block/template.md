---
title: "wp block template"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Block
    - Commands
    - Repos
---

# wp block template

检索区块模板和模板部件的详细信息。

获取全站编辑（FSE）主题中使用的区块模板信息。

### 示例

    # 列出所有模板
    $ wp block template list

    # 列出页眉区域的模板部件
    $ wp block template list --type=wp_template_part --area=header

    # 获取特定模板
    $ wp block template get twentytwentyfour//single