---
title: "wp profile stage"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Profile
    - Commands
    - Repos
---

# wp profile stage

分析 WordPress 加载过程中每个阶段的性能（引导、主查询、模板）。

此命令在 `before_wp_load` 钩子上运行，恰好在 WordPress 加载过程开始之前。

当 WordPress 处理来自浏览器的请求时，本质上是在执行一个长的 PHP 脚本。`wp profile stage` 将该脚本分为三个阶段：

* **引导阶段**：WordPress 进行自身设置，加载插件和主主题，并触发 `init` 钩子。
* **主查询阶段**：WordPress 将请求（例如 `/2016/10/21/moms-birthday/`）转换为主 WP_Query。
* **模板阶段**：WordPress 根据主查询确定要渲染的主题模板，并进行渲染。

### OPTIONS

请参阅 [参数语法](https://make.wordpress.org/cli/handbook/references/argument-syntax/) 参考，以详细了解所使用的语法约定。

[&lt;stage&gt;]
: 深入查看特定阶段。

[\--all]
: 展开所有阶段。

[\--spotlight]
: 从集合中过滤掉接近零值的日志。

[\--url=&lt;url&gt;]
: 针对指定 URL 执行请求。默认为首页 URL。

[\--fields=&lt;fields&gt;]
: 将输出限制在特定字段。默认为所有字段。

[\--format=&lt;format&gt;]
: 以特定格式呈现输出。
\---
默认值: table
选项:
  - table
  - json
  - yaml
  - csv
\---

[\--order=&lt;order&gt;]
: 升序或降序。
\---
默认值: ASC
选项:
  - ASC
  - DESC
\---

[\--orderby=&lt;fields&gt;]
: 设置按哪个字段排序。

### 示例

    # 查看加载过程每个阶段的概览。
    $ wp profile stage --fields=stage,time,cache_ratio
    +------------+---------+-------------+
    | stage      | time    | cache_ratio |
    +------------+---------+-------------+
    | bootstrap  | 0.7994s | 93.21%      |
    | main_query | 0.0123s | 94.29%      |
    | template   | 0.792s  | 91.23%      |
    +------------+---------+-------------+
    | total (3)  | 1.6037s | 92.91%      |
    +------------+---------+-------------+

    # 深入查看指定阶段的钩子性能。
    $ wp profile stage bootstrap --fields=hook,time,cache_ratio --spotlight
    +--------------------------+---------+-------------+
    | hook                     | time    | cache_ratio |
    +--------------------------+---------+-------------+
    | muplugins_loaded:before  | 0.2335s | 40%         |
    | muplugins_loaded         | 0.0007s | 50%         |
    | plugins_loaded:before    | 0.2792s | 77.63%      |
    | plugins_loaded           | 0.1502s | 100%        |
    | after_setup_theme:before | 0.068s  | 100%        |
    | init                     | 0.2643s | 96.88%      |
    | wp_loaded:after          | 0.0377s |             |
    +--------------------------+---------+-------------+
    | total (7)                | 1.0335s | 77.42%      |
    +--------------------------+---------+-------------+

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