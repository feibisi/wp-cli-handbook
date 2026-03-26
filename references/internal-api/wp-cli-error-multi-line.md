---
title: "WP_CLI::error_multi_line()"
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

# WP_CLI::error_multi_line()

在红色方框中显示多行错误信息。不会退出脚本。

***

## 用法

    WP_CLI::error_multi_line( $message_lines )

<div>
<strong>$message_lines</strong> (array) 要显示的多行错误信息。<br />
</div>

***

## 说明

错误信息会写入 STDERR。


*内部 API 文档在每次发布时从 WP-CLI 代码库生成。如需改进建议，请提交拉取请求。*

***

## 相关函数

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-format-items/">WP_CLI\Utils\format_items()</a></strong> - 将项目集合渲染为 ASCII 表格、JSON、CSV、YAML、ID 列表或计数。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-make-progress-bar/">WP_CLI\Utils\make_progress_bar()</a></strong> - 创建进度条以显示给定操作的完成百分比。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-colorize/">WP_CLI::colorize()</a></strong> - 为输出字符串着色。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-line/">WP_CLI::line()</a></strong> - 显示不带前缀的信息性消息，并忽略 `--quiet`。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-log/">WP_CLI::log()</a></strong> - 显示不带前缀的信息性消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-success/">WP_CLI::success()</a></strong> - 显示以 "Success: " 为前缀的成功消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-debug/">WP_CLI::debug()</a></strong> - 当使用 `--debug` 时，显示以 "Debug: " 为前缀的调试消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-warning/">WP_CLI::warning()</a></strong> - 显示以 "Warning: " 为前缀的警告消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-error/">WP_CLI::error()</a></strong> - 显示以 "Error: " 为前缀的错误消息并退出脚本。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-halt/">WP_CLI::halt()</a></strong> - 以特定返回代码停止脚本执行。</li>



</ul>