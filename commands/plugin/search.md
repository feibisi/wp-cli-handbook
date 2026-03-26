---
title: "wp plugin search"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Plugin
    - Commands
    - Repos
---

# wp plugin search

搜索 WordPress.org 插件目录。

显示 WordPress.org 插件目录中与给定搜索查询匹配的插件。

### 选项

有关所用语法约定的详细说明，请参阅[参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/)参考。

&lt;search&gt;
: 要搜索的字符串。

[\--page=&lt;page&gt;]
: 要显示的页面（可选）。
\---
默认值: 1
\---

[\--per-page=&lt;per-page&gt;]
: 要显示的结果数量（可选）。
\---
默认值: 10
\---

[\--field=&lt;field&gt;]
: 为每个插件打印单个字段的值。

[\--fields=&lt;fields&gt;]
: 向 API 请求特定字段。默认为 name,slug,author_profile,rating。可接受的值：

    **name**: 插件名称
    **slug**: 插件别名
    **version**: 当前版本号
    **author**: 插件作者
    **author_profile**: 插件作者资料
    **contributors**: 插件贡献者
    **requires**: 插件最低要求
    **tested**: 插件测试至
    **compatibility**: 插件兼容性
    **rating**: 插件评分（百分比和总数）
    **ratings**: 插件各星级评分（1-5）
    **num_ratings**: 插件评分数量
    **homepage**: 插件作者主页
    **description**: 插件描述
    **short_description**: 插件简短描述
    **sections**: 插件自述文件章节：描述、安装、常见问题、截图、其他说明和更新日志
    **downloaded**: 插件下载次数
    **last_updated**: 插件最后更新时间
    **added**: 插件添加到 wordpress.org 存储库的日期
    **tags**: 插件标签
    **versions**: 插件的可用版本及下载链接
    **donate_link**: 插件捐赠链接
    **banners**: 插件横幅图片链接
    **icons**: 插件图标图片链接
    **active_installs**: 插件活跃安装数
    **contributors**: 插件贡献者列表
    **url**: 插件在 wordpress.org 上的 URL

[\--format=&lt;format&gt;]
: 以特定格式渲染输出。
\---
默认值: table
选项:
  - table
  - csv
  - count
  - json
  - yaml
\---

### 示例

    $ wp plugin search dsgnwrks --per-page=20 --format=json
    Success: 显示 3 个插件中的 3 个。
    [{"name":"DsgnWrks Instagram Importer Debug","slug":"dsgnwrks-instagram-importer-debug","rating":0},{"name":"DsgnWrks Instagram Importer","slug":"dsgnwrks-instagram-importer","rating":84},{"name":"DsgnWrks Twitter Importer","slug":"dsgnwrks-twitter-importer","rating":80}]

    $ wp plugin search dsgnwrks --fields=name,version,slug,rating,num_ratings
    Success: 显示 3 个插件中的 3 个。
    +-----------------------------------+---------+-----------------------------------+--------+-------------+
    | name                              | version | slug                              | rating | num_ratings |
    +-----------------------------------+---------+-----------------------------------+--------+-------------+
    | DsgnWrks Instagram Importer Debug | 0.1.6   | dsgnwrks-instagram-importer-debug | 0      | 0           |
    | DsgnWrks Instagram Importer       | 1.3.7   | dsgnwrks-instagram-importer       | 84     | 23          |
    | DsgnWrks Twitter Importer         | 1.1.1   | dsgnwrks-twitter-importer         | 80     | 1           |
    +-----------------------------------+---------+-----------------------------------+--------+-------------+

### GLOBAL PARAMETERS

These [global parameters](https://make.wordpress.org/cli/handbook/config/) have the same behavior across all commands and affect how WP-CLI interacts with WordPress.

| **Argument**    | **Description**              |
|:----------------|:-----------------------------|
| `--path=<path>` | Path to the WordPress files. |
| `--url=<url>` | Pretend request came from given URL. In multisite, this argument is how the target site is specified. |
| `--ssh=[<scheme>:][<user>@]<host\|container>[:<port>][<path>]` | Perform operation against a remote server over SSH (or a container using scheme of "docker", "docker-compose", "docker-compose-run", "vagrant"). |
| `--http=<http>` | Perform operation against a remote WordPress installation over HTTP. |
| `--user=<id\|login\|email>` | Set the WordPress user. |
| `--skip-plugins[=<plugins>]` | Skip loading all plugins, or a comma-separated list of plugins. Note: mu-plugins are still loaded. |
| `--skip-themes[=<themes>]` | Skip loading all themes, or a comma-separated list of themes. |
| `--skip-packages` | Skip loading all installed packages. |
| `--require=<path>` | Load PHP file before running the command (may be used more than once). |
| `--exec=<php-code>` | Execute PHP code before running the command (may be used more than once). |
| `--context=<context>` | Load WordPress in a given context. |
| `--[no-]color` | Whether to colorize the output. |
| `--debug[=<group>]` | Show all PHP errors and add verbosity to WP-CLI output. Built-in groups include: bootstrap, commandfactory, and help. |
| `--prompt[=<assoc>]` | Prompt the user to enter values for all command arguments, or a subset specified as comma-separated values. |
| `--quiet` | Suppress informational messages. |