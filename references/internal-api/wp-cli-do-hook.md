---
title: "WP_CLI::do_hook()"
post_status: publish
comment_status: open
taxonomy:
  category:
    - wp-cli-handbook
  post_tag:
    - Internal Api
    - References
    - Repos
---

# WP_CLI::do_hook()

执行注册到指定钩子的回调函数。

***

## 使用方法

    WP_CLI::do_hook( $when, $args )

<div>
<strong>$when</strong> (string) 钩子的标识符。<br />
<strong>...$args</strong> (mixed) 可选。将传递给回调函数的参数。<br />
<strong>@return</strong> (null|mixed) 如果传递了可选参数，则返回第一个可选参数，否则返回 null。<br />
</div>

***

## 说明

关于 WP-CLI 内部钩子系统的详细信息，请参阅 `WP_CLI::add_hook()`。
命令可以提供并调用它们自己的钩子。
回调函数由 `WP_CLI::add_hook()` 提供。
如果传递了可选参数，则返回第一个可选参数，否则返回 null。

*内部 API 文档在每次发布时从 WP-CLI 代码库生成。如需改进建议，请提交拉取请求。*

***

## 相关函数

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-add-hook/">WP_CLI::add_hook()</a></strong> - 安排回调函数在特定时间点执行。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-add-wp-hook/">WP_CLI::add_wp_hook()</a></strong> - 向 WordPress 动作或过滤器添加回调函数。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-add-command/">WP_CLI::add_command()</a></strong> - 向 WP-CLI 注册命令。</li>



</ul>