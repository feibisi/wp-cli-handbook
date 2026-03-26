---
title: "wp user session"
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

# wp user session

销毁并列出用户的会话。

### 示例

    # 列出用户的会话。
    $ wp user session list admin@example.com --format=csv
    login_time,expiration_time,ip,ua
    "2016-01-01 12:34:56","2016-02-01 12:34:56",127.0.0.1,"Mozilla/5.0..."

    # 销毁指定用户最近的会话。
    $ wp user session destroy admin
    成功：已销毁会话。剩余 3 个会话。