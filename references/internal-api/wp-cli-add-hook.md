---
title: "WP_CLI::add_hook()"
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

# WP_CLI::add_hook()

安排一个回调函数在特定时间点执行。

***

## 用法

    WP_CLI::add_hook( $when, $callback )

<div>
<strong>$when</strong> (string) 钩子的标识符。<br />
<strong>$callback</strong> (mixed) 钩子被调用时要执行的回调函数。<br />
<strong>@return</strong> (void) <br />
</div>


***

## 说明

钩子在概念上与 WordPress 操作非常相似。WP-CLI 钩子通常在 WordPress 加载之前调用。

WP-CLI 钩子包括：

* `before_add_command:<command>` - 在命令添加之前。
* `after_add_command:<command>` - 在命令添加之后。
* `before_invoke:<command>` (1) - 在命令即将调用之前。
* `after_invoke:<command>` (1) - 在命令刚刚调用之后。
* `find_command_to_run_pre` - 在 WP-CLI 找到要运行的命令之前。
* `before_registering_contexts` (1) - 在上下文注册之前。
* `before_wp_load` - 在 WP 加载过程开始之前。
* `before_wp_config_load` - 在定位到 wp-config.php 之后。
* `after_wp_config_load` - 在 wp-config.php 加载到作用域之后。
* `after_wp_load` - 在 WP 加载过程刚刚完成之后。
* `before_run_command` (3) - 在命令即将执行之前。

钩子名称后面的括号表示传递给钩子的参数数量。对于此类钩子，回调函数应再次返回第一个参数，使其像 WP 过滤器一样工作。

WP-CLI 命令可以使用 `WP_CLI::do_hook()` 创建自己的钩子。

如果通过 `WP_CLI::do_hook()` 调用传递了额外的参数，这些参数将传递给 `WP_CLI::add_hook()` 提供的回调函数。

```
# `wp network meta` 确认命令在多站点上下文中执行。
WP_CLI::add_command( 'network meta', 'Network_Meta_Command', array(
   'before_invoke' => function ( $name ) {
       if ( !is_multisite() ) {
           WP_CLI::error( 'This is not a multisite installation.' );
       }
   }
) );
```


*内部 API 文档在每个版本发布时从 WP-CLI 代码库生成。如需改进建议，请提交拉取请求。*


***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-do-hook/">WP_CLI::do_hook()</a></strong> - 执行注册到给定钩子的回调函数。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-add-wp-hook/">WP_CLI::add_wp_hook()</a></strong> - 向 WordPress 操作或过滤器添加回调函数。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-add-command/">WP_CLI::add_command()</a></strong> - 向 WP-CLI 注册一个命令。</li>



</ul>