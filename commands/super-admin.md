---
title: "wp super-admin"
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

# wp super-admin

在多站点安装中列出、添加或移除超级管理员用户。

### 示例

    # 列出具有超级管理员权限的用户。
    $ wp super-admin list
    supervisor
    administrator

    # 授予用户超级管理员权限。
    $ wp super-admin add superadmin2
    成功：已授予 1 个用户超级管理员权限。

    # 撤销用户的超级管理员权限。
    $ wp super-admin remove superadmin2
    成功：已撤销 1 个用户的超级管理员权限。