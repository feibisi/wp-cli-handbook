---
title: "贡献指南"
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

# 贡献指南

欢迎并感谢您的参与！

我们非常感谢您主动为 WP-CLI 项目贡献力量。正是因为您和您周围的社区成员，WP-CLI 才能成为如此优秀的项目。

**贡献不仅限于代码编写。** 我们鼓励您以最适合自己能力的方式参与贡献：可以撰写教程、在当地交流会上进行演示、帮助其他用户解决支持问题，或是修订我们的文档。

请花些时间仔细阅读以下指南。遵循这些指南能体现您对项目其他贡献者时间的尊重。相应地，他们也会跨越时区和地域，在与您协作时尽力回报这份尊重。

若对贡献流程有任何疑问，请加入 [WordPress.org Slack](https://make.wordpress.org/chat/) 的 `#cli` 频道进行交流。

### 报告安全问题

WP-CLI 团队和 WordPress 社区高度重视安全漏洞。我们感谢您负责任地披露发现的问题，并将尽力认可您的贡献。

如需报告安全问题，请访问 [WordPress HackerOne](https://hackerone.com/wordpress) 项目。

### 报告错误

认为自己发现了错误？我们非常希望您能协助我们修复它。

在创建新议题前，请先[搜索现有议题](https://github.com/search?q=org%3Awp-cli+label%3Abug+is%3Aopen+sort%3Aupdated-desc&type=issues)，查看是否已有解决方案，或该问题是否已在 WP-CLI 的更新版本中被修复。同时，请查阅我们[关于常见问题及其修复的文档](https://make.wordpress.org/cli/handbook/common-issues/)。

完成搜索并确认您的错误尚无公开议题或未被修复后，请[遵循我们的错误报告提交指南](https://make.wordpress.org/cli/handbook/bug-reports/)，以确保问题能得到及时处理。

### 创建拉取请求

想要贡献新功能吗？WP-CLI 是一个成熟的项目，已经包含了大量实用功能。请先[开启功能建议议题来提议新命令](https://github.com/wp-cli/ideas/issues/new)，或在相应仓库中开启议题来提议对现有命令的改进。在提交拉取请求前开启议题，有助于我们在您投入过多编码时间前提供架构和实现指导。

初次接触 WP-CLI 代码库？查看[标记为'good-first-issue'的议题](https://make.wordpress.org/cli/good-first-issues/)作为切入点。这些议题专门为新贡献者预留。

当您决定投入时间完成拉取请求时，请[遵循我们的拉取请求创建指南](https://make.wordpress.org/cli/handbook/pull-requests/)以确保良好体验。关于本地修改 WP-CLI 的详细信息，请参阅"[环境设置](https://make.wordpress.org/cli/handbook/pull-requests/#setting-up)"。请注意拉取请求[需要包含覆盖变更范围的测试](https://make.wordpress.org/cli/handbook/pull-requests/#running-and-writing-tests)。阅读[我们的代码审查指南](https://make.wordpress.org/cli/handbook/code-review/)能帮助您更好地理解拉取请求的评估标准。

### 改进我们的文档

文档编写是你的强项吗？请查看当前开放的[文档问题](https://github.com/search?q=org%3Awp-cli+label%3Ascope%3Adocumentation+is%3Aopen+sort%3Aupdated-desc&type=issues)，看看能否解决其中一些问题。

WP-CLI 目前包含几种不同类型的文档：

* 单个 WP-CLI 命令的文档（位于 [developer.wordpress.org/commands](https://developer.wordpress.org/cli/commands/) 下的所有内容）包含在每个命令的 PHPDoc 中。这意味着要编辑命令的文档，你需要编辑实际提供该命令功能的文件。Web 文档是在发布时从这些文件生成的，因此你可能需要等到下一次发布才能看到你的更改。
* 单个文档页面（位于 [make.wordpress.org/cli/handbook](https://make.wordpress.org/cli/handbook/) 下的所有内容）可以通过贡献到 [GitHub 上的手册仓库](https://github.com/wp-cli/handbook/) 来编辑。不过，你不一定需要浏览 GitHub 仓库；任何属于此仓库的页面都会在页面右上角有一个“编辑”链接，点击它将带你到 GitHub 上的相应文件。

### 其他参与方式

欢迎随时[创建问题](https://github.com/wp-cli/wp-cli/issues/new)提出疑问，我们将尽力为您解答。

此外，如果您拥有 WordPress.org 账户，也可以考虑加入 [WordPress.org Slack 组织](https://make.wordpress.org/chat/)中的 `#cli` 频道。