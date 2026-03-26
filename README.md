---
title: "Readme"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Repos
    - Data
    - Docs Translate
---

wp-cli/handbook
===============

这些文件构成了 WP-CLI 手册 ([make.wordpress.org/cli/handbook](https://make.wordpress.org/cli/handbook/)) 和 WP-CLI 命令目录 ([developer.wordpress.org/cli/commands](https://developer.wordpress.org/cli/commands/))。

文档托管在 GitHub 上，以便实现基于拉取请求的编辑工作流。

长篇文档（例如“命令手册”）可以直接编辑。

内部 API 文档和命令页面是使用 `wp handbook` 系列命令从 WP-CLI 代码库动态生成的。

运行这些命令之前，应先运行 bash 脚本 `bin/install_packages.sh` 来安装 `bin/packages` 中非捆绑命令的最新版本。请注意，`wp` 必须指向目标 WP-CLI 实例（即包含要生成文档块的 phar 或 git 版本），并且应使用 `WP_CLI_PACKAGES_DIR=bin/packages` 和 `WP_CLI_CONFIG_PATH=/dev/null` 环境变量运行。

例如，要针对 nightly phar 版本生成所有动态创建的文档，请运行：

```
wp cli update --nightly
bin/install_packages.sh
WP_CLI_PACKAGES_DIR=bin/packages WP_CLI_CONFIG_PATH=/dev/null wp handbook gen-all
```

## 自动化手册生成

手册可以使用“重新生成手册”GitHub Actions 工作流自动重新生成。该工作流可通过两种方式触发：

1. **手动触发**：在 GitHub 仓库的 Actions 选项卡中手动运行“重新生成手册”工作流。
2. **从 wp-cli/wp-cli 自动触发**：当新版本的 WP-CLI 发布时，主框架仓库可以使用类型为 `regenerate-handbook` 的 `repository_dispatch` 事件来触发此工作流。

工作流将：
- 安装 WP-CLI nightly 版本
- 安装非捆绑包
- 运行 `wp handbook gen-all`
- 提交并将任何更改推送到仓库

## 文档导入

所有文档通过两步过程自动导入到 WordPress.org：

1. WordPress 读取 `commands-manifest.json` 或 `handbook-manifest.json` 以了解需要创建的所有页面。
2. 每个 WordPress 页面都有一个 `markdown_source` 属性，指定要获取的 Markdown 文件，该文件将被转换为 HTML 并保存到数据库中。

对于 make.wordpress.org/cli，导入过程是一个 [WordPress 插件](https://meta.trac.wordpress.org/browser/sites/trunk/wordpress.org/public_html/wp-content/plugins/wporg-cli/inc/class-markdown-import.php)，每 15 分钟运行一次 WP Cron 任务。对于 developer.wordpress.org/cli，这是 [devhub 主题中的一个类](https://meta.trac.wordpress.org/browser/sites/trunk/wordpress.org/public_html/wp-content/themes/pub/wporg-developer/inc/cli.php)，每 12 小时运行一次 WP Cron 任务。