---
title: "识别插件或主题冲突"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - How To
    - Repos
    - Data
---

# 识别插件或主题冲突

WP-CLI 无法与您的 WordPress 安装配合工作，但您不知道原因吗？可能是某个插件或主题与 WP-CLI 的加载过程发生了冲突。

要验证这一点，首先运行 `wp --skip-plugins --skip-themes` 来执行 WP-CLI 而不加载插件或主题。如果跳过插件和主题后 WP-CLI 按预期运行，那么问题就是由其中一个插件或当前主题引起的。

要查看问题是否源于当前主题，请运行 `wp --skip-themes` 来检查 WP-CLI 是否按预期加载。

要查看问题是否源于某个活动插件，请对每个活动插件运行 `wp --skip-plugins=<plugin-slug>`，以找出哪个插件阻止了 WP-CLI 的完整执行。例如，跳过 Akismet 插件的命令是：

    wp --skip-plugins=akismet

或者，使用 `xargs` 来尝试整个活动插件列表：

    wp plugin list --field=name --status=active --skip-plugins | xargs -n1 -I % wp --skip-plugins=% plugin get % --field=name