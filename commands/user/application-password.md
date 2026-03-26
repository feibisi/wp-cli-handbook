---
title: "wp user application-password"
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

# wp user application-password

创建、更新、删除、列出和检索应用程序密码。

### 示例

    # 列出用户应用程序密码，仅显示应用名称和密码哈希值
    $ wp user application-password list 123 --fields=name,password
    +--------+------------------------------------+
    | name   | password                           |
    +--------+------------------------------------+
    | myapp  | $P$BVGeou1CUot114YohIemgpwxQCzb8O/ |
    +--------+------------------------------------+

    # 获取特定应用程序密码，仅显示应用名称和创建时间戳
    $ wp user application-password get 123 6633824d-c1d7-4f79-9dd5-4586f734d69e --fields=name,created
    +--------+------------+
    | name   | created    |
    +--------+------------+
    | myapp  | 1638395611 |
    +--------+------------+

    # 创建用户应用程序密码
    $ wp user application-password create 123 myapp
    成功：已创建应用程序密码。
    密码：ZG1bxdxdzjTwhsY8vK8l1C65

    # 仅打印密码，不显示任何额外信息
    $ wp user application-password create 123 myapp --porcelain
    ZG1bxdxdzjTwhsY8vK8l1C65

    # 更新现有应用程序密码
    $ wp user application-password update 123 6633824d-c1d7-4f79-9dd5-4586f734d69e --name=newappname
    成功：已更新应用程序密码。

    # 删除现有应用程序密码
    $ wp user application-password delete 123 6633824d-c1d7-4f79-9dd5-4586f734d69e
    成功：已删除 1 个应用程序密码（共 1 个）。

    # 检查给定应用程序的密码是否存在
    $ wp user application-password exists 123 myapp
    $ echo $?
    1

    # 用于检查应用程序密码是否存在，如果不存在则创建的 Bash 脚本
    if ! wp user application-password exists 123 myapp; then
        PASSWORD=$(wp user application-password create 123 myapp --porcelain)
    fi