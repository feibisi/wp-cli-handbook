---
title: "WP_CLI::debug()"
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

# WP_CLI::debug()

当使用 `--debug` 参数时，显示以“Debug: ”为前缀的调试信息。

***

## 用法

    WP_CLI::debug( $message, $group = false )

<div>
<strong>$message</strong> (string|WP_Error|Exception|Throwable) 要写入 STDERR 的消息。<br />
<strong>$group</strong> (string|bool) 将调试信息组织到特定分组。<br />
<strong>@return</strong> (void) <br />
</div>

***

## 说明

调试信息会写入 STDERR，并包含脚本执行时间。

有助于在需要时选择性地显示更多细节。在整个 WP-CLI 引导过程中使用，以便于调试和性能分析。

```
# 在 `WP_CLI\Runner::set_wp_root()` 中调用。
private static function set_wp_root( $path ) {
    define( 'ABSPATH', Utils\trailingslashit( $path ) );
    WP_CLI::debug( 'ABSPATH defined: ' . ABSPATH );
    $_SERVER['DOCUMENT_ROOT'] = realpath( $path );
}

# 仅在使用 `--debug` 时显示调试详情。
# $ wp --debug
# [...]
# Debug: ABSPATH defined: /srv/www/wordpress-develop.dev/src/ (0.225s)
```
使用 `false` 可以不将消息分组。

*内部 API 文档会在每次发布时从 WP-CLI 代码库生成。如需改进，请提交拉取请求。*

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-format-items/">WP_CLI\Utils\format_items()</a></strong> - 将项目集合渲染为 ASCII 表格、JSON、CSV、YAML、ID 列表或计数。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-make-progress-bar/">WP_CLI\Utils\make_progress_bar()</a></strong> - 创建进度条以显示给定操作的完成百分比。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-colorize/">WP_CLI::colorize()</a></strong> - 为输出字符串着色。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-line/">WP_CLI::line()</a></strong> - 显示不带前缀的信息性消息，并忽略 `--quiet`。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-log/">WP_CLI::log()</a></strong> - 显示不带前缀的信息性消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-success/">WP_CLI::success()</a></strong> - 显示以 "Success: " 为前缀的成功消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-warning/">WP_CLI::warning()</a></strong> - 显示以 "Warning: " 为前缀的警告消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-error/">WP_CLI::error()</a></strong> - 显示以 "Error: " 为前缀的错误消息并退出脚本。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-halt/">WP_CLI::halt()</a></strong> - 以特定返回代码停止脚本执行。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-error-multi-line/">WP_CLI::error_multi_line()</a></strong> - 在红色框中显示多行错误消息。不退出脚本。</li>



</ul>