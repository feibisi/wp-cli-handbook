---
title: "WP_CLI::colorize()"
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

# WP_CLI::colorize()

为输出内容添加颜色。

***

## 用法

    WP_CLI::colorize( $string )

<div>
<strong>$string</strong> (string) 需要添加颜色标记的字符串，包含颜色标记。<br />
<strong>@return</strong> (string) 字符串。<br />
</div>

***

## 说明

是的，你也可以更改命令行文本的颜色。例如，`WP_CLI::success()` 对 "Success: " 进行颜色化的方式如下：

```
WP_CLI::colorize( "%GSuccess:%n " )
```

使用 `\cli\Colors::colorize()` 将颜色标记转换为显示设置。可从以下标记中选择（注意 'reset'）：

* %y => ['color' => 'yellow'],
* %g => ['color' => 'green'],
* %b => ['color' => 'blue'],
* %r => ['color' => 'red'],
* %p => ['color' => 'magenta'],
* %m => ['color' => 'magenta'],
* %c => ['color' => 'cyan'],
* %w => ['color' => 'grey'],
* %k => ['color' => 'black'],
* %n => ['color' => 'reset'],
* %Y => ['color' => 'yellow', 'style' => 'bright'],
* %G => ['color' => 'green', 'style' => 'bright'],
* %B => ['color' => 'blue', 'style' => 'bright'],
* %R => ['color' => 'red', 'style' => 'bright'],
* %P => ['color' => 'magenta', 'style' => 'bright'],
* %M => ['color' => 'magenta', 'style' => 'bright'],
* %C => ['color' => 'cyan', 'style' => 'bright'],
* %W => ['color' => 'grey', 'style' => 'bright'],
* %K => ['color' => 'black', 'style' => 'bright'],
* %N => ['color' => 'reset', 'style' => 'bright'],
* %3 => ['background' => 'yellow'],
* %2 => ['background' => 'green'],
* %4 => ['background' => 'blue'],
* %1 => ['background' => 'red'],
* %5 => ['background' => 'magenta'],
* %6 => ['background' => 'cyan'],
* %7 => ['background' => 'grey'],
* %0 => ['background' => 'black'],
* %F => ['style' => 'blink'],
* %U => ['style' => 'underline'],
* %8 => ['style' => 'inverse'],
* %9 => ['style' => 'bright'],
* %_ => ['style' => 'bright']


*内部 API 文档在每次发布时从 WP-CLI 代码库生成。如需改进建议，请提交拉取请求。*

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-format-items/">WP_CLI\Utils\format_items()</a></strong> - 将项目集合渲染为 ASCII 表格、JSON、CSV、YAML、ID 列表或计数。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-make-progress-bar/">WP_CLI\Utils\make_progress_bar()</a></strong> - 创建进度条以显示给定操作的完成百分比。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-line/">WP_CLI::line()</a></strong> - 显示不带前缀的信息性消息，并忽略 `--quiet` 参数。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-log/">WP_CLI::log()</a></strong> - 显示不带前缀的信息性消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-success/">WP_CLI::success()</a></strong> - 显示以 "Success: " 为前缀的成功消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-debug/">WP_CLI::debug()</a></strong> - 当使用 `--debug` 参数时，显示以 "Debug: " 为前缀的调试消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-warning/">WP_CLI::warning()</a></strong> - 显示以 "Warning: " 为前缀的警告消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-error/">WP_CLI::error()</a></strong> - 显示以 "Error: " 为前缀的错误消息并退出脚本。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-halt/">WP_CLI::halt()</a></strong> - 以特定的返回代码停止脚本执行。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-error-multi-line/">WP_CLI::error_multi_line()</a></strong> - 在红色框中显示多行错误消息。不会退出脚本。</li>



</ul>