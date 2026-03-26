---
title: "WP-CLI 黑客日"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Contributions
    - Repos
    - Data
---

# WP-CLI 黑客日

欢迎参加 [WP-CLI 黑客日](https://make.wordpress.org/cli/2024/04/02/save-the-date-wp-cli-hack-day-on-friday-april-26th/)！感谢您抽出时间为项目做出贡献。

**我们希望能帮助您今天至少提交一个拉取请求**。基于这个目标，您可能希望**从一些小而可实现的任务开始**。在提交了当天的第一个拉取请求后，欢迎您尝试更具挑战性的工作。

在黑客日期间提交拉取请求时，请添加 <code>Related https://github.com/wp-cli/wp-cli/issues/5935</code> 以便我们轻松追踪。我们将在当天结束时的总结文章中收录这些提交。

我们整理了这份指南，旨在让贡献过程尽可能简单明了。也请加入 [WordPress.org Slack 的 #cli 频道](https://wordpress.slack.com/messages/C02RP4T41)（[注册说明](https://make.wordpress.org/chat/)）与其他贡献者交流、提问等。

今天的负责人是：[schlessera](https://github.com/schlessera)、[danielbachhuber](https://github.com/danielbachhuber)、[swissspidy](https://github.com/swissspidy)

## 开放视频交流时段

在黑客日期间，我们将举办两场开放视频交流时段：

- [🕓 太平洋时间 02:00-03:00 / 东部时间 05:00-06:00 / 世界协调时 09:00-10:00 / 中欧夏令时 11:00-12:00 / 日本标准时间 18:00-19:00](https://www.timeanddate.com/worldclock/fixedtime.html?iso=20240426T0900)
- [🕓 太平洋时间 08:00-09:00 / 东部时间 11:00-12:00 / 世界协调时 15:00-16:00 / 中欧夏令时 17:00-18:00 / 日本标准时间 00:00-01:00](https://www.timeanddate.com/worldclock/fixedtime.html?iso=20240426T1500)

这些时段是实时讨论剩余问题、交流进展并与社区成员建立联系的绝佳机会。欢迎随时加入，分享挑战或更新你的进展！

## 开始使用

如果您通常在虚拟主机上或通过 Brew 使用 WP-CLI，很可能使用的是 Phar 可执行文件 (`wp-cli.phar`)。这个 Phar 可执行文件是 WP-CLI 的"构建"单一版本，它由 WP-CLI GitHub 组织中的数十个代码库编译而成。

若要对 WP-CLI 进行代码修改，您需要在本地计算机上搭建 `wp-cli-dev` 开发环境。但在开始之前，请确保本地已安装 [Composer](https://getcomposer.org/)、PHP 以及可正常运行的 MySQL 或 MariaDB 服务器。

满足前提条件后，克隆 GitHub 仓库并运行安装流程：

```bash
git clone https://github.com/wp-cli/wp-cli-dev wp-cli-dev
cd wp-cli-dev
composer install
composer prepare-tests
```

`wp-cli-dev` 安装过程会将 WP-CLI 的所有代码库克隆到本地计算机。安装完成后，您可以在任意代码库中进行修改。但需要先 Fork 该仓库才能推送功能分支。[GitHub CLI](https://github.com/cli/cli) 对此非常有用：

```bash
cd core-command
gh repo fork
```

我们已启动视频教程系列，您可以在此观看：[WP-CLI 贡献教程](https://www.youtube.com/playlist?list=PL_B8Y6K6MH2d6T7pYa6dloUgk67mfBT4K)。这些视频将概述各个软件包，并演示如何搭建开发环境以便在本地运行自动化测试。

所有 WP-CLI 拉取请求都需要包含测试。[观看约 10 分钟的视频介绍](https://github.com/wp-cli/wp-cli/issues/5858)，或查阅文字版文档了解[运行和编写测试](https://make.wordpress.org/cli/handbook/contributions/pull-requests/#running-and-writing-tests)。

## 推荐工单

为了帮助您在当天取得成功，我们整理了一份相对容易上手且可操作的问题列表。

如果您计划处理某个问题，请直接在工单上留言。我们通常不分配问题，所以无需担心这一点。

**新贡献者**

- [重新生成单个图像尺寸会（重新）生成自动缩放的大图像和自动旋转的图像](https://github.com/wp-cli/media-command/issues/196)
- [wp plugin update all 不显示正在更新的插件信息](https://github.com/wp-cli/extension-command/issues/261)
- [使用 `media import` 导入 PDF 文件时没有缩略图](https://github.com/wp-cli/media-command/issues/195)
- [允许重命名主题别名](https://github.com/wp-cli/extension-command/issues/74)
- [如果先尝试安装子主题，则在安装主主题后子主题安装会因遗留目录而失败](https://github.com/wp-cli/extension-command/issues/410)
- [在 wp plugin list 中包含更多信息](https://github.com/wp-cli/extension-command/issues/241)
- [在 db search 中仅输出匹配的 ID](https://github.com/wp-cli/db-command/issues/158)
- [如果数据库需要 SSL，DB-Check 会失败](https://github.com/wp-cli/config-command/issues/113)

查看[标记为 'good-first-issue' 的问题](https://github.com/issues?q=is%3Aopen+org%3Awp-cli+is%3Aissue+sort%3Aupdated-desc+label%3Agood-first-issue+) 或[标记为 'contributor-day' 的问题](https://github.com/issues?q=is%3Aopen+org%3Awp-cli+is%3Aissue+sort%3Aupdated-desc+label%3Acontributor-day) 以获取更广泛的列表。

**资深贡献者**

- [插件依赖支持](https://github.com/wp-cli/extension-command/issues/407)
- [在配置文件中设置 WP_CLI_PACKAGES_DIR](https://github.com/wp-cli/wp-cli/issues/5645)
- [缓存从 GitHub 安装的 wp plugin](https://github.com/wp-cli/extension-command/issues/363)
- [当上传文件本地可用时提高导入速度](https://github.com/wp-cli/import-command/issues/83)
- [引入专用的 search-replace url 命令](https://github.com/wp-cli/search-replace-command/issues/186)

当然，您也完全可以处理[任何其他您感兴趣的问题](https://github.com/issues?q=is%3Aopen+org%3Awp-cli+is%3Aissue+sort%3Aupdated-desc)！[特别欢迎修复错误](https://github.com/issues?q=is%3Aopen%20org%3Awp-cli%20is%3Aissue%20sort%3Acreated-desc%20label%3Abug)。今天可以是讨论棘手问题和集思广益的好机会。

## 感谢您的贡献

感谢您抽出时间参与黑客日并为 `wp-cli` 做出贡献。祝您玩得开心，期待在 [Slack](https://wordpress.slack.com/messages/C02RP4T41) 上见到您！