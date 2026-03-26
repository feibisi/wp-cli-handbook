---
title: "wp config"
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

# wp config

生成和读取 wp-config.php 文件。

### 示例

    # 创建标准的 wp-config.php 文件。
    $ wp config create --dbname=testing --dbuser=wp --dbpass=securepswd --locale=ro_RO
    成功：已生成 'wp-config.php' 文件。

    # 列出 wp-config.php 文件中定义的常量和变量。
    $ wp config list
    +------------------+------------------------------------------------------------------+----------+
    | 键               | 值                                                                | 类型     |
    +------------------+------------------------------------------------------------------+----------+
    | table_prefix     | wp_                                                              | 变量     |
    | DB_NAME          | wp_cli_test                                                      | 常量     |
    | DB_USER          | root                                                             | 常量     |
    | DB_PASSWORD      | root                                                             | 常量     |
    | AUTH_KEY         | r6+@shP1yO&amp;$)1gdu.hl[/j;7Zrvmt~o;#WxSsa0mlQOi24j2cR,7i+QM/#7S:o^ | 常量     |
    | SECURE_AUTH_KEY  | iO-z!_m--YH$Tx2tf/&amp;V,YW*13Z_HiRLqi)d?$o-tMdY+82pK$`T.NYW~iTLW;xp | 常量     |
    +------------------+------------------------------------------------------------------+----------+

    # 获取 wp-config.php 文件路径。
    $ wp config path
    /home/person/htdocs/project/wp-config.php

    # 获取 wp-config.php 文件中定义的 table_prefix。
    $ wp config get table_prefix
    wp_

    # 将 WP_DEBUG 常量设置为 true。
    $ wp config set WP_DEBUG true --raw
    成功：已使用原始值 'true' 更新 'wp-config.php' 文件中的常量 'WP_DEBUG'。

    # 从 wp-config.php 文件中删除 COOKIE_DOMAIN 常量。
    $ wp config delete COOKIE_DOMAIN
    成功：已从 'wp-config.php' 文件中删除常量 'COOKIE_DOMAIN'。

    # 启动系统编辑器来编辑 wp-config.php 文件。
    $ wp config edit

    # 检查 DB_PASSWORD 常量是否存在于 wp-config.php 文件中。
    $ wp config has DB_PASSWORD
    $ echo $?
    0

    # 断言 MULTISITE 是否为 true。
    $ wp config is-true MULTISITE
    $ echo $?
    0

    # 为你的 wp-config.php 文件获取新的盐值。
    $ wp config shuffle-salts
    成功：已重新生成盐值密钥。