---
title: "wp option"
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

# wp option

检索和设置站点选项，包括插件和 WordPress 设置。

有关添加自定义选项的更多信息，请参阅[插件设置 API](https://developer.wordpress.org/plugins/settings/settings-api/)和[主题选项](https://developer.wordpress.org/themes/customize-api/)。

### 示例

    # 获取站点 URL。
    $ wp option get siteurl
    http://example.com

    # 添加选项。
    $ wp option add my_option foobar
    Success: Added 'my_option' option.

    # 更新选项。
    $ wp option update my_option '{"foo": "bar"}' --format=json
    Success: Updated 'my_option' option.

    # 删除选项。
    $ wp option delete my_option
    Success: Deleted 'my_option' option.