---
title: "WP_CLI::error()"
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

# WP_CLI::error()

显示以“错误：”为前缀的错误信息并退出脚本。

***

## 用法

    WP_CLI::error( $message, $exit = true )

<div>
<strong>$message</strong> (string|WP_Error|Exception|Throwable) 写入 STDERR 的消息。<br />
<strong>$exit</strong> (boolean|integer) 为 true 时默认执行 exit(1)。<br />
<strong>@return</strong> (null) <br />
</div>

***

## 说明

错误信息会写入 STDERR。默认情况下会以返回码 1 终止脚本执行。

当需要允许脚本继续执行时，请改用 `WP_CLI::warning()`。

启用 `--debug` 参数时，此方法还会输出显示错误触发位置的回溯信息，便于定位问题代码。

```
# `wp cache flush` 将刷新失败视为致命错误。
if ( false === wp_cache_flush() ) {
    WP_CLI::error( 'The object cache could not be flushed.' );
}
```

*内部 API 文档会在每次发布时根据 WP-CLI 代码库生成。如需改进建议，请提交拉取请求。*

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-format-items/">WP_CLI\Utils\format_items()</a></strong> - 将项目集合渲染为 ASCII 表格、JSON、CSV、YAML、ID 列表或计数。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-make-progress-bar/">WP_CLI\Utils\make_progress_bar()</a></strong> - 创建进度条以显示给定操作的完成百分比。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-colorize/">WP_CLI::colorize()</a></strong> - 为输出字符串着色。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-line/">WP_CLI::line()</a></strong> - 显示不带前缀的信息性消息，并忽略 `--quiet`。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-log/">WP_CLI::log()</a></strong> - 显示不带前缀的信息性消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-success/">WP_CLI::success()</a></strong> - 显示以“Success: ”为前缀的成功消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-debug/">WP_CLI::debug()</a></strong> - 当使用 `--debug` 时，显示以“Debug: ”为前缀的调试消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-warning/">WP_CLI::warning()</a></strong> - 显示以“Warning: ”为前缀的警告消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-halt/">WP_CLI::halt()</a></strong> - 以特定返回代码停止脚本执行。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-error-multi-line/">WP_CLI::error_multi_line()</a></strong> - 在红色框中显示多行错误消息。不会退出脚本。</li>



</ul>