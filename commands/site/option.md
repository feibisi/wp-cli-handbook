---
title: "wp site 选项"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Site
    - Commands
    - Repos
---

# wp site 选项

在多站点安装中添加、更新、删除和列出站点选项。

### 示例

    # 获取站点注册设置
    $ wp site option get registration
    none

    # 添加站点选项
    $ wp site option add my_option foobar
    成功：已添加 'my_option' 站点选项。

    # 更新站点选项
    $ wp site option update my_option '{"foo": "bar"}' --format=json
    成功：已更新 'my_option' 站点选项。

    # 删除站点选项
    $ wp site option delete my_option
    成功：已删除 'my_option' 站点选项。