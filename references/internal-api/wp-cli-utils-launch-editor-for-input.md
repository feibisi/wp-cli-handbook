---
title: "WP_CLI\Utils\launch_editor_for_input()"
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

# WP_CLI\Utils\launch_editor_for_input()

启动系统的 $EDITOR 编辑器供用户编辑文本。

***

## 用法

    WP_CLI\Utils\launch_editor_for_input( $input, $title = WP-CLI, $ext = tmp )

<div>
<strong>$input</strong> (string) 待编辑的文本内容（例如文章内容）。<br />
<strong>$title</strong> (string) 在编辑器中显示的标题。<br />
<strong>$ext</strong> (string) 临时文件使用的扩展名。<br />
<strong>@return</strong> (string|bool) 如果文件从编辑器保存，则返回文本；如果文件未更改，则返回 false。<br />
</div>


*内部 API 文档在每个版本发布时从 WP-CLI 代码库生成。如需改进建议，请提交拉取请求。*


***

## 相关函数

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-get-flag-value/">WP_CLI\Utils\get_flag_value()</a></strong> - 返回标志值，如果未设置则返回 $default 值。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-report-batch-operation-results/">WP_CLI\Utils\report_batch_operation_results()</a></strong> - 报告对多个资源执行相同操作的结果。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-parse-str-to-argv/">WP_CLI\Utils\parse_str_to_argv()</a></strong> - 将命令行参数字符串解析为类似 $argv 的变量。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-confirm/">WP_CLI::confirm()</a></strong> - 在执行破坏性操作前请求确认。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-read-value/">WP_CLI::read_value()</a></strong> - 从多种格式读取值。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-has-config/">WP_CLI::has_config()</a></strong> - 确认全局配置参数是否存在。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-get-config/">WP_CLI::get_config()</a></strong> - 获取全局配置参数的值。</li>



</ul>