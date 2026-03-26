---
title: "核心理念"
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

# 核心理念

WP-CLI 是 WordPress 的命令行界面。它既提供可在 WordPress 后台执行的操作命令（例如 `wp theme activate` 和 `wp user create`），也包含没有对应网页界面的操作命令（例如 `wp cron event run`、`wp search-replace` 和 `wp scaffold child-theme`）。

WP-CLI 的核心指导原则是成为管理 WordPress 最快效且权威的方式：

* 命令行界面固有的简洁性，以及将多个命令串联成复杂操作的能力，天然具备速度优势。
* 当功能最终集成到 WP-CLI 时，其品质应足以成为解决该问题的实际标准方案。
* “管理 WordPress”是我们持续耕耘的演进领域。WP-CLI 应始终专注于提升*现有管理模式*的效率。

本页列出了影响功能范围、命令组织与行为决策的指导原则：

## 好的命令应简洁明了，与 WordPress 交互，并解决一个独特问题。

当命令实现 WordPress 现有功能时（例如 `wp export`），应尽可能镜像并复用 WordPress 的既有行为。这样做能确保其符合用户对行为的预期。

当命令添加 WordPress 管理界面中未有的功能时（例如 `wp search-replace`），应解决一个独特问题并以某种方式与 WordPress 交互。好的命令源于真实的用户需求；对于新提议的 WP-CLI 命令，生态系统中很可能已有先例。

若命令提供实用功能但与 WordPress 无关，则不属于 WP-CLI。同样，有时将命令构思转化为文档改进会是更佳选择。

## 一致性带来愉悦的用户体验

在可能的情况下，命令应通过一致的使用行为、参数名称和文档来相互模仿。

## 决策，而非选项

WordPress 的哲学[指出](https://wordpress.org/about/philosophy/)：

> [在做出实现决策时，最终用户被优先考虑]。这种考虑的一个很好的例子是软件选项。每次你给用户一个选项，你就是在要求他们做出决定。当用户不关心或不理解该选项时，这最终会导致挫败感。作为开发者，我们有时觉得为一切提供选项是件好事，选择永远不会太多，对吧？最终，这些选择变成了技术性的选择，普通最终用户对此毫无兴趣。作为开发者，我们有责任做出明智的设计决策，避免将技术选择的负担加在最终用户身上。

同样的原则也适用于 WP-CLI。在任何情况下，我们都应首先尝试改进默认行为。选项应谨慎添加，只有在需要解决方案且没有其他可用解决方案时才添加。

根据经验，一旦一个命令有半打或更多的选项，就很难理解该命令在每种条件下将如何运行。

## 可组合性总是一个好主意。

UNIX 中最有用的理念之一就是[管道](http://en.wikipedia.org/wiki/Pipeline_%28Unix%29)。

WP-CLI 命令应该是可组合的，即一个命令的输出应该能轻松地通过管道传递给另一个命令。

由此得出的推论是，命令应该是_正交的_，这意味着命令之间不应存在功能重叠。（`wp plugin install --activate` 是一个例外）。

关于这一理念如何应用的具体示例，请参阅 [Shell Friends](https://make.wordpress.org/cli/handbook/references/shell-friends/)。

## 可读性优于击键次数。

WP-CLI 中的大多数命令将以非交互方式使用，因此参数名称应具备自解释性。

## 不做任何预设。

捆绑命令必须能在任何给定的 WordPress 安装上运行（只要版本足够新），无论其如何配置或包含多少数据。

由此推论，捆绑命令不应预设任何插件或主题的存在。