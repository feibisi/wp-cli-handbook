---
title: "wp plugin auto-updates"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Plugin
    - Commands
    - Repos
---

# wp plugin auto-updates

管理插件自动更新。

### 示例

    # 为插件启用自动更新
    $ wp plugin auto-updates enable hello
    已启用插件 'hello' 的自动更新。
    成功：已启用 1 个插件的自动更新（共 1 个）。

    # 为插件禁用自动更新
    $ wp plugin auto-updates disable hello
    已禁用插件 'hello' 的自动更新。
    成功：已禁用 1 个插件的自动更新（共 1 个）。

    # 获取插件自动更新状态
    $ wp plugin auto-updates status hello
    插件 'hello' 的自动更新已禁用。