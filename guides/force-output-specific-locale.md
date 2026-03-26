---
title: "强制输出为特定语言环境"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Guides
    - Repos
    - Data
---

# 强制输出为特定语言环境

WP-CLI 始终输出英文，因为它不支持本地化。但由于 WordPress 支持本地化，在执行特定命令时您可能会看到非英文输出。

例如：

    $ wp theme update --all
    מעבר למצב תחזוקה...
    מוריד עדכונים מ-https://downloads.wordpress.org/theme/hueman.3.3.25.zip...
    Using cached file '/home/xxx/.wp-cli/cache/theme/hueman-3.3.25.zip'...
    פתיחת עדכון...
    התקנת גרסה חדשה...
    הסרת הגרסה הקודמת של התבנית...
    התבנית עודכנה בהצלחה.
    ביטול מצב תחזוקה...
    +--------+-------------+-------------+---------+
    | name   | old_version | new_version | status  |
    +--------+-------------+-------------+---------+
    | hueman | 3.3.24      | 3.3.25      | Updated |
    +--------+-------------+-------------+---------+
    Success: Updated 1 of 1 themes.

要强制 WordPress 在命令行始终输出英文，您需要过滤当前使用的语言环境。

假设有一个 `force-locale.php` 文件：

    <?php
    WP_CLI::add_wp_hook( 'pre_option_WPLANG', function() {
	    return 'en_US';
    });

您可以通过以下方式强制将语言环境设为 `en_US`：

    wp --require=force-locale.php

这种方法的一个优点是，您可以轻松地[通过配置文件](https://make.wordpress.org/cli/handbook/config/#config-files)将其应用于多个 WordPress 安装。