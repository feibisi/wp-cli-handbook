---
title: "wp theme mod"
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

# wp theme mod

设置、获取和移除主题修改项。

### 示例

    # 将 'background_color' 主题修改项设置为 '000000'。
    $ wp theme mod set background_color 000000
    成功：主题修改项 background_color 已设置为 000000。

    # 以 JSON 格式获取单个主题修改项。
    $ wp theme mod get background_color --format=json
    [{"key":"background_color","value":"dd3333"}]

    # 移除所有主题修改项。
    $ wp theme mod remove --all
    成功：主题修改项已移除。