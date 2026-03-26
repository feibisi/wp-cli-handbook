---
title: "WP_CLI::add_wp_hook()"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Internal Api
    - Repos
    - Data
---

# WP_CLI::add_wp_hook()

向 WordPress 动作或过滤器添加回调函数。

***

## 用法

    WP_CLI::add_wp_hook( $tag, $function_to_add, $priority = 10, $accepted_args = 1 )

<div>
<strong>$tag</strong> (string) WordPress 动作或过滤器的名称。<br />
<strong>$function_to_add</strong> (callable) 当动作或过滤器被触发时要执行的回调函数。<br />
<strong>$priority</strong> (integer) 回调函数的优先级。<br />
<strong>$accepted_args</strong> (integer) 传递给回调函数的参数数量。<br />
<strong>@return</strong> (true) <br />
</div>

***

## 说明

无需访问 `add_action()` 即可实现 `add_action()` 的功能。但如果 WordPress 已经加载，则应改用 `add_action()`（以及 `add_filter()`）。

*内部 API 文档在每次发布时从 WP-CLI 代码库生成。如需改进建议，请提交拉取请求。*

***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-add-hook/">WP_CLI::add_hook()</a></strong> - 安排回调函数在特定时间点执行。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-do-hook/">WP_CLI::do_hook()</a></strong> - 执行注册到指定钩子的回调函数。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-add-command/">WP_CLI::add_command()</a></strong> - 向 WP-CLI 注册命令。</li>



</ul>