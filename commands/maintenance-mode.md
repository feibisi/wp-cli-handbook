---
title: "wp maintenance-mode"
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

# wp maintenance-mode

激活、停用或检查网站的维护模式状态。

### 示例

    # 激活维护模式。
    $ wp maintenance-mode activate
    正在启用维护模式...
    成功：已激活维护模式。

    # 停用维护模式。
    $ wp maintenance-mode deactivate
    正在禁用维护模式...
    成功：已停用维护模式。

    # 显示维护模式状态。
    $ wp maintenance-mode status
    维护模式已激活。

    # 为脚本目的获取维护模式状态。
    $ wp maintenance-mode is-active
    $ echo $?
    1