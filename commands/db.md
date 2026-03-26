---
title: "wp db"
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

# wp db

使用存储在 wp-config.php 中的凭据执行基本数据库操作。

除非被覆盖，这些命令会在 `after_wp_config_load` 钩子上运行，即在 wp-config.php 加载到作用域之后。

### 示例

    # 创建新数据库。
    $ wp db create
    成功：数据库已创建。

    # 删除现有数据库。
    $ wp db drop --yes
    成功：数据库已删除。

    # 重置当前数据库。
    $ wp db reset --yes
    成功：数据库已重置。

    # 执行存储在文件中的 SQL 查询。
    $ wp db query < debug.sql