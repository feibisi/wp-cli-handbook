---
title: "提交者信条"
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

# 提交者信条

部分人员拥有 WP-CLI 代码库的写入权限。这些人员归属于以下团队：

* [维护者](https://github.com/orgs/wp-cli/teams/maintainers) - 项目领导团队
* [提交者](https://github.com/orgs/wp-cli/teams/committers) - 受信任的贡献者

本《提交者信条》是动态文档。其旨在为提交者建立公认标准，并将持续演进完善。

## 产品质量

WP-CLI 是整个 WordPress 生态系统所依赖的项目。这份信任是通过提供稳定、可靠且高质量的产品赢得的。WP-CLI 的提交者将产品和代码质量视为最高准则。

具体而言：

* 在优质、快速和廉价之间做选择时，我们选择优质而缓慢。打造优秀软件是一段旅程，而非终点。
* 产品决策需[与我们的核心理念保持一致](https://make.wordpress.org/cli/handbook/philosophy/)。
* [代码审查是我们开发流程中不可或缺的部分](https://make.wordpress.org/cli/handbook/code-review/)。拉取请求在合并前需要至少一位其他提交者的批准。如果您希望获得不止一次代码审查，请随时提出请求。您可以向特定人员或 `@wp-cli/committers` 团队请求审查。
* 如果您需要帮助，请寻求帮助。真的，任何时候感觉需要帮助就请开口。没必要独自陷入困境。

## 卓越的判断力

优秀的产品源于深思熟虑、审慎周详的决策。WP-CLI 的贡献者们在处理新功能、修复错误、合并他人拉取请求以及项目日常工作时，展现出卓越的判断力。

决策的基础确保：

* 新功能符合 [WP-CLI 项目的范围和理念](https://make.wordpress.org/cli/handbook/philosophy/)。
* 错误修复被优先处理，因为错误会对产品质量产生负面影响。
* 拉取请求包含覆盖变更范围的测试。
* 潜在的代码添加会从维护负担和实用性两方面进行评估。

## 持续参与

有效参与 WP-CLI 项目需要持续投入、清晰沟通以及乐于助人的品质。

作为一个被广泛采用的项目，WP-CLI 拥有多元化的用户群体。帮助这些用户能产生巨大的影响力。WP-CLI 提交者优先处理他人遇到的障碍而非自己的工作，深知这是维护社区稳定的关键因素。

值得注意的是，"[待处理的代码审查代表被阻塞的执行线程](http://glen.nu/ramblings/oncodereview.php)"这一理念可广泛适用于所有协作形式。如果你的反馈会阻碍他人进展，请优先为他人提供反馈而非处理自己的工作。通过指派 `@wp-cli/committers` 团队进行审查，为拉取请求申请[代码审查](https://make.wordpress.org/cli/handbook/code-review/)。

提交者的参与不仅限于提交代码。通常，投入少量时间即可产生巨大影响：

* 完善现有文档或起草新文档
* 帮助贡献者完成拉取请求所需的任何工作
    * 若贡献者放弃接近可合并状态的拉取请求（如两周无活动），你可[直接提交到其分支进行必要清理](https://help.github.com/articles/committing-changes-to-a-pull-request-branch-created-from-a-fork/)并完成收尾工作
* 花 5-10 分钟进一步诊断问题报告，并通过评论补充发现的信息来进行问题分类