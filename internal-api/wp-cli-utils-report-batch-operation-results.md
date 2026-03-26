---
title: "WP_CLI\Utils\report_batch_operation_results()"
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

# WP_CLI\Utils\report_batch_operation_results()

报告对多个资源执行相同操作的结果。

***

## 用法

    WP_CLI\Utils\report_batch_operation_results( $noun, $verb, $total, $successes, $failures, $skips = null )

<div>
<strong>$noun</strong> (string) 受影响的资源（例如插件）。<br />
<strong>$verb</strong> (string) 对资源执行的操作类型（例如激活）。<br />
<strong>$total</strong> (integer) 受影响的资源总数。<br />
<strong>$successes</strong> (integer) 成功操作的数量。<br />
<strong>$failures</strong> (integer) 失败操作的数量。<br />
<strong>$skips</strong> (null|integer) 可选。跳过操作的数量。默认为 null（不显示跳过）。<br />
<strong>@return</strong> (void) <br />
</div>


*内部 API 文档在每次发布时从 WP-CLI 代码库生成。如需改进，请提交拉取请求。*


***

## 相关

<ul>



<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-launch-editor-for-input/">WP_CLI\Utils\launch_editor_for_input()</a></strong> - 启动系统的 $EDITOR 供用户编辑文本。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-get-flag-value/">WP_CLI\Utils\get_flag_value()</a></strong> - 返回标志值，如果未设置则返回 $default 值。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-utils-parse-str-to-argv/">WP_CLI\Utils\parse_str_to_argv()</a></strong> - 将命令行参数字符串解析为类似 $argv 的变量。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-confirm/">WP_CLI::confirm()</a></strong> - 在执行破坏性操作前请求确认。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-read-value/">WP_CLI::read_value()</a></strong> - 从多种格式读取值。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-has-config/">WP_CLI::has_config()</a></strong> - 确认全局配置参数存在。</li>


<li><strong><a href="https://make.wordpress.org/cli/handbook/internal-api/wp-cli-get-config/">WP_CLI::get_config()</a></strong> - 获取全局配置参数的值。</li>



</ul>