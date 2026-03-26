---
title: "治理"
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

# 治理

## 谁负责？

WP-CLI 有一位维护者：[schlessera](http://github.com/schlessera)。在日常工作中，最终决策权由他负责。

项目路线图是在项目维护者、提交者和贡献者之间共同形成的有机、不断发展的愿景。通常，我们努力根据[项目理念](https://make.wordpress.org/cli/handbook/philosophy/)和[提交者信条](https://make.wordpress.org/cli/handbook/committers-credo/)来做出决策。

## 为什么有些人会成为 WP-CLI 组织的成员？

有时，我们会[授予贡献者写入权限](https://github.com/orgs/wp-cli/teams/committers)，这些贡献者在一段时间内已证明自己有能力并致力于推动项目发展。这些提交者应做到：

* 高度重视产品和代码质量。
* 展现出卓越的判断力和沟通能力。
* 持续参与项目。

成为提交者可能看起来很光鲜，但也伴随着责任、承诺和谦逊的期望。

[andreascreten](https://github.com/andreascreten) 是 WP-CLI 的原始作者。[scribu](https://github.com/scribu) 和 [danielbachhuber](https://github.com/danielbachhuber) 是长期维护者。[schlessera](https://github.com/schlessera) 是当前的维护者。

维护者是直接对项目的可靠性和长期性负责的人。他们应做到：

* 高度重视 WP-CLI 的整体质量。
* 完善项目的愿景和方向，并确保所有人都能理解。
* 帮助从新用户到经验丰富的提交者的每一个人。
* 处理日常的繁琐工作（保持 CI 通过、分类新问题等）。

## WP-CLI 与 WordPress 有何关联？

自 2017 年 12 月起，WP-CLI 已成为一个[正式的 WordPress 项目](https://make.wordpress.org/core/2016/12/28/supporting-the-future-of-wp-cli/)。

实际上，这意味着我们可以利用 WordPress 项目的人员和软件基础设施：

* 大部分 WP-CLI 文档托管在 wordpress.org 域名下。
* 我们可以在 [WordPress Slack 组织](https://make.wordpress.org/chat/)中使用 `#cli` 频道。
* 如果需要帮助，我们可以随时提问。
* 两位核心提交者（[dd32](https://github.com/dd32) 和 [pento](https://github.com/pento)）拥有 WP-CLI GitHub 组织的管理权限，以防万一其他成员无法履行职责。

除此之外，WP-CLI 独立运作。

## 这一切是如何运作的？

[WP-CLI GitHub 组织](https://github.com/wp-cli) 包含了所有项目代码仓库。部分命令与 WP-CLI 捆绑发布，而其他命令则可以独立安装。当命令稳定、与[项目理念](https://make.wordpress.org/cli/handbook/philosophy/)高度契合且对大多数用户有用时，它们才会被捆绑到 WP-CLI 中。

[wp-cli/wp-cli](https://github.com/wp-cli/wp-cli) 是主项目仓库，它通过 Composer 引入命令包和其他依赖项。Composer 定义了构建中包含的依赖项及其版本。当命令包被打上稳定版标签时，对其的更改才会被纳入正式的 WP-CLI 版本。

每日构建的 Phar 包由 Travis 任务创建，该任务调用 [deploy.sh](https://github.com/wp-cli/wp-cli/blob/master/ci/deploy.sh) 并将构建产物推送到[构建仓库](http://github.com/wp-cli/builds)。发布版本则根据[发布检查清单](https://make.wordpress.org/cli/handbook/release-checklist/)手动准备。

`wp-cli.org` 域名目前由 [andreascreten](https://github.com/andreascreten) 持有。DNS 通过一个 [Cloudflare](https://www.cloudflare.com/) 账户管理，该账户的凭证由 [danielbachhuber](https://github.com/danielbachhuber) 持有。

大部分 WP-CLI 文档（命令页面等）可以通过 [wp-cli/handbook](https://github.com/wp-cli/handbook/) 编辑，然后同步到 WordPress.org。WP-CLI.org 主页[托管在 GitHub Pages 上](http://github.com/wp-cli/wp-cli.github.com)。

有时，你可能会看到来自 `wp-make-coffee` 机器人的拉取请求。这些请求源自一台捐赠的 WebFaction 服务器，该服务器运行一些调用 bash 脚本的 cron 任务：

```bash
5 4 * * 1,3,5 source ~/.bash_profile; WP_CLI_DIR=~/wp-cli bash ~/wp-cli/utils/auto-composer-update.sh > ~/auto-composer-update.log 2>&1
5 6 * * 1,3,5 source ~/.bash_profile; WP_CLI_DIR=~/wp-cli-bundle bash ~/wp-cli-bundle/utils/auto-composer-update.sh > ~/auto-composer-update-bundle.log 2>&1
```

[wpcli](https://twitter.com/wpcli) Twitter 账户由 [schlessera](https://github.com/schlessera) 管理。

如果你[订阅了邮件更新](https://make.wordpress.org/cli/subscribe/)，你的电子邮件地址将通过 Automattic 的 Jetpack 插件在 WordPress.com 上注册。