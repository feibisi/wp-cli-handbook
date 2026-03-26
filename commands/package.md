---
title: "wp package"
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

# wp package

列出、安装和移除 WP-CLI 包。

除非被覆盖，这些命令在 `before_wp_load` 钩子上运行，恰好在 WP 加载过程开始之前。

WP-CLI 包是基于 WP-CLI 构建的社区维护项目。它们可以包含 WP-CLI 命令，也可以只是以某种方式扩展 WP-CLI。

从 [命令手册](https://make.wordpress.org/cli/handbook/guides/commands-cookbook/) 学习如何创建你自己的命令。

### 示例

    # 列出已安装的包。
    $ wp package list
    +-----------------------+------------------+----------+-----------+----------------+
    | name                  | authors          | version  | update    | update_version |
    +-----------------------+------------------+----------+-----------+----------------+
    | wp-cli/server-command | Daniel Bachhuber | dev-main | available | 2.x-dev        |
    +-----------------------+------------------+----------+-----------+----------------+

    # 安装包的最新开发版本。
    $ wp package install wp-cli/server-command
    正在安装包 wp-cli/server-command (dev-main)
    更新 /home/person/.wp-cli/packages/composer.json 以要求该包...
    使用 Composer 安装包...
    ---
    正在加载包含包信息的 composer 仓库
    更新依赖项
    通过 SAT 解析依赖项
    依赖项解析在 0.005 秒内完成
    分析了 732 个包以解析依赖项
    分析了 1034 条规则以解析依赖项
     - 正在安装包
    写入锁定文件
    生成自动加载文件
    ---
    成功：包已安装。

    # 卸载包。
    $ wp package uninstall wp-cli/server-command
    从 /home/person/.wp-cli/packages/composer.json 中移除包 'wp-cli/server-command' 的 require 语句
    从 /home/person/.wp-cli/packages/composer.json 中移除仓库详情
    移除包目录并重新生成自动加载器...
    成功：包已卸载。