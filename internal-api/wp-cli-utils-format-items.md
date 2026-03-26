---
title: "WP_CLI\Utils\format_items()"
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

# WP_CLI\Utils\format_items()

将项目集合渲染为 ASCII 表格、JSON、CSV、YAML、ID 列表或计数。

***

## 用法

    WP_CLI\Utils\format_items( $format, $items, $fields )

<div>
<strong>$format</strong> (string) 使用的格式：'table'、'json'、'csv'、'yaml'、'ids'、'count'。<br />
<strong>$items</strong> (array&lt;mixed&gt;) 要输出的项目数组。<br />
<strong>$fields</strong> (array&lt;string&gt;|string) 每个数据项的命名字段。可以是数组或逗号分隔的列表。<br />
</div>

***

## 说明

给定一组数据结构一致的条目：

```
$items = array(
    array(
        'key'   => 'foo',
        'value'  => 'bar',
    )
);
```

将 `$items` 渲染为 ASCII 表格：

```
WP_CLI\Utils\format_items( 'table', $items, array( 'key', 'value' ) );

# +-----+-------+
# | key | value |
# +-----+-------+
# | foo | bar   |
# +-----+-------+
```

或将 `$items` 渲染为 YAML：

```
WP_CLI\Utils\format_items( 'yaml', $items, array( 'key', 'value' ) );

# ---
# -
#   key: foo
#   value: bar
```


*内部 API 文档会在每次发布时从 WP-CLI 代码库生成。如需改进，请提交一个拉取请求。*

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-make-progress-bar/">WP_CLI\Utils\make_progress_bar()</a></strong> - 创建进度条以显示给定操作的完成百分比。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-colorize/">WP_CLI::colorize()</a></strong> - 为输出字符串着色。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-line/">WP_CLI::line()</a></strong> - 显示不带前缀的信息性消息，并忽略 `--quiet` 参数。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-log/">WP_CLI::log()</a></strong> - 显示不带前缀的信息性消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-success/">WP_CLI::success()</a></strong> - 显示以“Success: ”为前缀的成功消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-debug/">WP_CLI::debug()</a></strong> - 当使用 `--debug` 参数时，显示以“Debug: ”为前缀的调试消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-warning/">WP_CLI::warning()</a></strong> - 显示以“Warning: ”为前缀的警告消息。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-error/">WP_CLI::error()</a></strong> - 显示以“Error: ”为前缀的错误消息并退出脚本。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-halt/">WP_CLI::halt()</a></strong> - 以特定的返回代码停止脚本执行。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-error-multi-line/">WP_CLI::error_multi_line()</a></strong> - 在红色框中显示多行错误消息。不会退出脚本。</li>



</ul>