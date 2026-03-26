---
title: "wp cron schedule"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Cron
    - Commands
    - Repos
---

# wp cron schedule

获取 WP-Cron 计划任务。

### 示例

    # 列出可用的 cron 计划任务
    $ wp cron schedule list
    +------------+-------------+----------+
    | name       | display     | interval |
    +------------+-------------+----------+
    | hourly     | 每小时一次  | 3600     |
    | twicedaily | 每日两次    | 43200    |
    | daily      | 每日一次    | 86400    |
    +------------+-------------+----------+