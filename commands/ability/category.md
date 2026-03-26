---
title: "wp ability category"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Ability
    - Commands
    - Repos
---

# wp ability category

列出并检查通过 WordPress 能力 API 注册的能力类别。

能力 API 于 WordPress 6.9 引入，使用类别来组织相关能力，以提高可发现性。

### 示例

    # 列出所有已注册的能力类别。
    $ wp ability category list
    +------+-------+-----------------------------------------------------+
    | slug | label | description                                         |
    +------+-------+-----------------------------------------------------+
    | site | Site  | 用于检索或修改站点信息的能力。                     |
    | user | User  | 用于检索或修改用户信息的能力。                     |
    +------+-------+-----------------------------------------------------+

    # 获取特定类别的详细信息。
    $ wp ability category get site
    +-------------+-----------------------------------------------------+
    | Field       | Value                                               |
    +-------------+-----------------------------------------------------+
    | slug        | site                                                |
    | label       | Site                                                |
    | description | 用于检索或修改站点信息的能力。                     |
    | meta        | {}                                                  |
    +-------------+-----------------------------------------------------+

    # 检查类别是否存在。
    $ wp ability category exists site
    $ echo $?
    0