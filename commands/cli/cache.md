---
title: "wp cli cache"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Cli
    - Commands
    - Repos
---

# wp cli cache

管理 WP-CLI 内部缓存。

除非被覆盖，这些命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

### 示例

    # 移除所有缓存文件。
    $ wp cli cache clear
    成功：缓存已清除。

    # 移除所有缓存文件，但保留每个文件的最新版本。
    $ wp cli cache prune
    成功：缓存已清理。