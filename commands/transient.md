---
title: "wp transient"
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

# wp transient

在 WordPress 瞬态缓存中添加、获取和删除条目。

默认情况下，瞬态缓存使用 WordPress 数据库在请求之间持久化值。在单站点安装中，值存储在 `wp_options` 表中。在多站点安装中，值根据 `--network` 标志的使用情况存储在 `wp_options` 表或 `wp_sitemeta` 表中。

当安装了持久化对象缓存插件（例如 Redis 或 Memcached）时，瞬态缓存会跳过数据库，直接包装 WP 对象缓存。

### 示例

    # 设置瞬态。
    $ wp transient set sample_key "test data" 3600
    成功：瞬态已添加。

    # 获取瞬态。
    $ wp transient get sample_key
    test data

    # 删除瞬态。
    $ wp transient delete sample_key
    成功：瞬态已删除。

    # 删除过期的瞬态。
    $ wp transient delete --expired
    成功：已从数据库中删除 12 个过期的瞬态。

    # 删除所有瞬态。
    $ wp transient delete --all
    成功：已从数据库中删除 14 个瞬态。

    # 删除所有站点瞬态。
    $ wp transient delete --all --network
    成功：已从数据库中删除 2 个瞬态。