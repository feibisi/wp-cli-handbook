---
title: "WP_CLI\Utils\make_progress_bar()"
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

# WP_CLI\Utils\make_progress_bar()

创建一个进度条，用于显示给定操作的完成百分比。

***

## 用法

    WP_CLI\Utils\make_progress_bar( $message, $count, $interval = 100 )

<div>
<strong>$message</strong> (string) 进度条前显示的文本。<br />
<strong>$count</strong> (integer) 要执行的总刻度数。<br />
<strong>$interval</strong> (int) 可选。更新间隔（毫秒）。默认值为 100。<br />
<strong>@return</strong> (\cli\progress\Bar|\WP_CLI\NoOp) <br />
</div>

***

## Notes

Progress bar is written to STDOUT, and disabled when command is piped. Progress
advances with `$progress->tick()`, and completes with `$progress->finish()`.
Process bar also indicates elapsed time and expected total time.

```
# `wp user generate` ticks progress bar each time a new user is created.
#
# $ wp user generate --count=500
# Generating users  22 % [=======>                             ] 0:05 / 0:23

$progress = \WP_CLI\Utils\make_progress_bar( 'Generating users', $count );
for ( $i = 0; $i < $count; $i++ ) {
    // uses wp_insert_user() to insert the user
    $progress->tick();
}
$progress->finish();
```


*Internal API documentation is generated from the WP-CLI codebase on every release. To suggest improvements, please submit a pull request.*


***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-format-items/">WP_CLI\Utils\format_items()</a></strong> - 将项目集合渲染为 ASCII 表格、JSON、CSV、YAML、ID 列表或计数。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-colorize/">WP_CLI::colorize()</a></strong> - 为输出字符串着色。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-line/">WP_CLI::line()</a></strong> - 显示不带前缀的信息性消息，并忽略 `--quiet`。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-log/">WP_CLI::log()</a></strong> - 显示不带前缀的信息性消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-success/">WP_CLI::success()</a></strong> - 显示以“Success: ”为前缀的成功消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-debug/">WP_CLI::debug()</a></strong> - 当使用 `--debug` 时，显示以“Debug: ”为前缀的调试消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-warning/">WP_CLI::warning()</a></strong> - 显示以“Warning: ”为前缀的警告消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-error/">WP_CLI::error()</a></strong> - 显示以“Error: ”为前缀的错误消息并退出脚本。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-halt/">WP_CLI::halt()</a></strong> - 以特定返回代码停止脚本执行。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-error-multi-line/">WP_CLI::error_multi_line()</a></strong> - 在红色框中显示多行错误消息。不退出脚本。</li>



</ul>