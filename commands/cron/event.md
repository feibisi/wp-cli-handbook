---
title: "wp cron 事件"
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

# wp cron 事件

调度、运行和删除 WP-Cron 事件。

### 示例

    # 调度新的 cron 事件
    $ wp cron event schedule cron_test
    成功：已为 2016-05-31 10:19:16 GMT 调度钩子为 'cron_test' 的事件。

    # 立即运行所有到期的 cron 事件
    $ wp cron event run --due-now
    在 0.01 秒内执行了 cron 事件 'cron_test_1'。
    在 0.006 秒内执行了 cron 事件 'cron_test_2'。
    成功：总共执行了 2 个 cron 事件。

    # 删除给定钩子的所有已调度 cron 事件
    $ wp cron event delete cron_test
    成功：总共删除了 2 个 cron 事件。

    # 以 JSON 格式列出已调度的 cron 事件
    $ wp cron event list --fields=hook,next_run --format=json
    [{"hook":"wp_version_check","next_run":"2016-05-31 10:15:13"},{"hook":"wp_update_plugins","next_run":"2016-05-31 10:15:13"},{"hook":"wp_update_themes","next_run":"2016-05-31 10:15:14"}]