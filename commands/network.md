---
title: "wp network"
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

# wp network

执行网络范围的操作。

### 示例

    # 获取超级管理员列表
    $ wp network meta get 1 site_admins
    array (
      0 => 'supervisor',
    )