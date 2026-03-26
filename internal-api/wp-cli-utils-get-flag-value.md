---
title: "WP_CLI\Utils\get_flag_value()"
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

# WP_CLI\Utils\get_flag_value()

返回标志值，如果未设置，则返回 $default 值。

***

## 用法

    WP_CLI\Utils\get_flag_value( $assoc_args, $flag, $default = null )

<div>
<strong>$assoc_args</strong> (array&lt;string|int,string|bool&gt;) 参数数组。<br />
<strong>$flag</strong> (string|int) 要获取值的标志。<br />
<strong>$default</strong> (string|bool|int|null) 标志的默认值。默认值：NULL。<br />
<strong>@return</strong> (string|bool|int|null) <br />
</div>


***

## 说明

由于标志可以被否定（例如使用 --no-quiet 来否定 --quiet），此函数提供了比使用 `isset( $assoc_args['quiet'] )` 或类似方法更安全的替代方案。


*内部 API 文档在每次发布时从 WP-CLI 代码库生成。如需改进建议，请提交拉取请求。*


***

## 相关函数

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-launch-editor-for-input/">WP_CLI\Utils\launch_editor_for_input()</a></strong> - 启动系统的 $EDITOR 供用户编辑文本。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-report-batch-operation-results/">WP_CLI\Utils\report_batch_operation_results()</a></strong> - 报告对多个资源执行相同操作的结果。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-parse-str-to-argv/">WP_CLI\Utils\parse_str_to_argv()</a></strong> - 将命令行参数字符串解析为类似 $argv 的变量。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-confirm/">WP_CLI::confirm()</a></strong> - 在执行破坏性操作前请求确认。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-read-value/">WP_CLI::read_value()</a></strong> - 从各种格式读取值。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-has-config/">WP_CLI::has_config()</a></strong> - 确认全局配置参数确实存在。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-get-config/">WP_CLI::get_config()</a></strong> - 获取全局配置参数的值。</li>



</ul>