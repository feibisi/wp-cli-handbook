---
title: "wp theme auto-updates"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Theme
    - Commands
    - Repos
---

# wp theme auto-updates

管理主题自动更新。

### 示例

    # 为主题启用自动更新
    $ wp theme auto-updates enable twentysixteen
    主题 'twentysixteen' 的自动更新已启用。
    成功：已启用 1 个主题的自动更新（共 1 个）。

    # 为主题禁用自动更新
    $ wp theme auto-updates disable twentysixteen
    主题 'twentysixteen' 的自动更新已禁用。
    成功：已禁用 1 个主题的自动更新（共 1 个）。

    # 获取主题自动更新状态
    $ wp theme auto-updates status twentysixteen
    主题 'twentysixteen' 的自动更新已禁用。