---
title: "WP_CLI::success()"
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

# WP_CLI::success()

显示以“Success: ”为前缀的成功消息。

***

## 用法

    WP_CLI::success( $message )

<div>
<strong>$message</strong> (string) 要写入 STDOUT 的消息。<br />
<strong>@return</strong> (void) <br />
</div>

***

## 说明

成功消息会写入 STDOUT，当提供 `--quiet` 标志时则会被丢弃。

通常建议用于通知用户脚本已成功完成。

```
# wp rewrite flush 期望刷新后 'rewrite_rules' 选项被设置。
flush_rewrite_rules( \WP_CLI\Utils\get_flag_value( $assoc_args, 'hard' ) );
if ( ! get_option( 'rewrite_rules' ) ) {
    WP_CLI::warning( "Rewrite rules are empty." );
} else {
    WP_CLI::success( 'Rewrite rules flushed.' );
}
```

*内部 API 文档在每次发布时从 WP-CLI 代码库生成。如需改进，请提交 pull request。*

***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-format-items/">WP_CLI\Utils\format_items()</a></strong> - 将项目集合渲染为 ASCII 表格、JSON、CSV、YAML、ID 列表或计数。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-make-progress-bar/">WP_CLI\Utils\make_progress_bar()</a></strong> - 创建进度条以显示给定操作的完成百分比。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-colorize/">WP_CLI::colorize()</a></strong> - 为输出字符串着色。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-line/">WP_CLI::line()</a></strong> - 显示不带前缀的信息性消息，并忽略 `--quiet`。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-log/">WP_CLI::log()</a></strong> - 显示不带前缀的信息性消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-debug/">WP_CLI::debug()</a></strong> - 当使用 `--debug` 时，显示以“Debug: ”为前缀的调试消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-warning/">WP_CLI::warning()</a></strong> - 显示以“Warning: ”为前缀的警告消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-error/">WP_CLI::error()</a></strong> - 显示以“Error: ”为前缀的错误消息并退出脚本。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-halt/">WP_CLI::halt()</a></strong> - 以特定返回代码停止脚本执行。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-error-multi-line/">WP_CLI::error_multi_line()</a></strong> - 在红色框中显示多行错误消息。不会退出脚本。</li>



</ul>