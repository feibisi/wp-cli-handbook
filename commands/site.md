---
title: "wp site"
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

# wp site

在多站点安装中创建、删除、清空、审核和列出一个或多个站点。

### 示例

    # 创建站点
    $ wp site create --slug=example
    成功：站点 3 已创建：www.example.com/example/

    # 输出站点 URL 的简单列表
    $ wp site list --field=url
    http://www.example.com/
    http://www.example.com/subdir/

    # 删除站点
    $ wp site delete 123
    确定要删除 'http://www.example.com/example' 站点吗？[y/n] y
    成功：位于 'http://www.example.com/example' 的站点已被删除。