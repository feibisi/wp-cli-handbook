---
title: "wp network meta"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Network
    - Commands
    - Repos
---

# wp network meta

获取、添加、更新、删除和列出网络自定义字段。

### 示例

    # 获取超级管理员列表
    $ wp network meta get 1 site_admins
    array (
      0 => 'supervisor',
    )