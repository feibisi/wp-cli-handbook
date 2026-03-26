---
title: "wp ability"
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

# wp ability

列出、检查并执行通过 WordPress 能力 API 注册的能力。

能力 API 于 WordPress 6.9 引入，提供了一种标准化的方式来注册和发现 WordPress 站点内的独立功能单元。

### 示例

    # 列出所有已注册的能力。
    $ wp ability list
    +---------------------------+----------------------+----------+------------------------------------------+
    | name                      | label                | category | description                              |
    +---------------------------+----------------------+----------+------------------------------------------+
    | core/get-site-info        | Get Site Information | site     | Returns site information configured i... |
    | core/get-user-info        | Get User Information | user     | Returns basic profile details for the... |
    | core/get-environment-info | Get Environment Info | site     | Returns core details about the site's... |
    +---------------------------+----------------------+----------+------------------------------------------+

    # 获取特定能力的详细信息。
    $ wp ability get core/get-site-info --fields=name,label,category,readonly,show_in_rest
    +---------------+----------------------+
    | Field         | Value                |
    +---------------+----------------------+
    | name          | core/get-site-info   |
    | label         | Get Site Information |
    | category      | site                 |
    | readonly      | 1                    |
    | show_in_rest  | 1                    |
    +---------------+----------------------+

    # 使用 JSON 输入执行能力（数组值必需）。
    $ wp ability run core/get-site-info --input='{"fields":["name","version"]}' --user=admin
    {
        "name": "Test Blog",
        "version": "6.9"
    }

    # 检查能力是否存在。
    $ wp ability exists core/get-site-info
    $ echo $?
    0

    # 检查用户是否可以运行能力。
    $ wp ability can-run core/get-site-info
    $ echo $?
    0

    # 在执行前验证输入。
    $ wp ability validate core/get-site-info --input='{"fields":["name","version"]}'
    Success: Input is valid.