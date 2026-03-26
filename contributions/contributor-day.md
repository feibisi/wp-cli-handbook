---
title: "WordCamp 贡献者日"
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

# WordCamp 贡献者日

欢迎来到 WordCamp 贡献者日！感谢您为 WP-CLI 贡献宝贵时间。

我们希望能帮助您至少提交一个拉取请求，因此我们准备了这份指南，力求让流程尽可能简单明了。我们将竭尽所能为您提供支持。

提交拉取请求时，请添加 `Related https://github.com/wp-cli/wp-cli/issues/5985` 标记，以便我们统计当天创建的所有拉取请求。我们将在下期发布说明中给予这些贡献特别推荐。

今日的桌长是：[schlessera](https://github.com/schlessera)、[BrianHenryIE](https://github.com/BrianHenryIE)

还有几位经验丰富的 WP-CLI 贡献者也将提供协助：待定

## 开始使用

如果您通常在虚拟主机上或通过 Brew 使用 WP-CLI，很可能您使用的是 Phar 可执行文件。Phar 可执行文件是 WP-CLI 的"已构建"单文件版本。它由 WP-CLI GitHub 组织中的数十个代码库编译而成，因此修改 WP-CLI 需要在这些代码库之间协同工作。

在开始开发 WP-CLI 之前，您需要首先确保已安装 PHP 以及可正常运行的 MySQL 或 MariaDB 服务器。满足这些先决条件后，安装 [`wp-cli-dev` 开发环境](https://github.com/wp-cli/wp-cli-dev)即可开始贡献：

```
git clone https://github.com/wp-cli/wp-cli-dev
cd wp-cli-dev
composer install
```

`wp-cli-dev` 安装过程会将所有 WP-CLI 代码库克隆到您的本地计算机。完成后，您就可以在任意代码库中进行修改。但您需要先 fork 该代码库并将其添加为远程仓库，才能推送您的功能分支。

所有 WP-CLI 拉取请求都需要包含测试。完整介绍请参阅[运行与编写测试](https://make.wordpress.org/cli/handbook/contributions/pull-requests/#running-and-writing-tests)。

## Suggested Tickets

To help you be successful during Contributor Day, we curated a list of reasonably approachable and actionable issues. Feel free to comment directly on the issue if you plan to work on it. We don't usually assign issues, so no need to worry about that.

**New contributors**

- ["wp config create" generates wrong DB_PASSWORD in wp-config.php when db password has "](https://github.com/wp-cli/config-command/issues/180)
- [Import into specific directory/location](https://github.com/wp-cli/media-command/issues/146)
- [Add --exclude=<file>,<file> argument to skip files](https://github.com/wp-cli/checksum-command/issues/64)
- [Not possible to install translations for en_US](https://github.com/wp-cli/language-command/issues/84)
- [Support WP-Stash in 'wp cache type'](https://github.com/wp-cli/cache-command/issues/68)
- [Add reason for skipping regeneration](https://github.com/wp-cli/media-command/issues/95)
- [wp export is not exporting term meta data](https://github.com/wp-cli/export-command/issues/42)

**Seasoned contributors**

- [Add commands to export and import SQLite databases](https://github.com/wp-cli/ideas/issues/188)
- [SQLite Compatibility (multiple issues)](https://github.com/wp-cli/.github/issues/94)
- [Regenerating a single image size (re-)generates auto-scaled big images & auto-rotated images](https://github.com/wp-cli/media-command/issues/196)
- [wp cron event run --due-now doesn't respect doing_cron transient](https://github.com/wp-cli/cron-command/issues/27)
- [Update command doesn't escape php_binary path, update fails when path has spaces](https://github.com/wp-cli/wp-cli/issues/5815)
- [Associative argument contains double quotes if the command is called with WP_CLI::runcommand()](https://github.com/wp-cli/wp-cli/issues/5541)

You're obviously welcome to work on any other issue you'd like too! Contributor Day can be a good opportunity to discuss trickier issues and brainstorm approaches.