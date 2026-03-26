---
title: "wp user signup"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - User
    - Commands
    - Repos
---

# wp user signup

管理多站点安装中的用户注册。

### 示例

    # 列出注册信息。
    $ wp user signup list
    +-----------+------------+---------------------+---------------------+--------+------------------+
    | signup_id | user_login | user_email          | registered          | active | activation_key   |
    +-----------+------------+---------------------+---------------------+--------+------------------+
    | 1         | bobuser    | bobuser@example.com | 2024-03-13 05:46:53 | 1      | 7320b2f009266618 |
    | 2         | johndoe    | johndoe@example.com | 2024-03-13 06:24:44 | 0      | 9068d859186cd0b5 |
    +-----------+------------+---------------------+---------------------+--------+------------------+

    # 激活注册。
    $ wp user signup activate 2
    注册 2 已激活。密码: bZFSGsfzb9xs
    成功：已激活 1 个注册中的 1 个。

    # 删除注册。
    $ wp user signup delete 3
    注册 3 已删除。
    成功：已删除 1 个注册中的 1 个。